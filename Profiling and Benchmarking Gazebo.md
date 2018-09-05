In order to get optimal performance from Gazebo, it may sometimes be necessary to benchmark or profile execution to identify bottlenecks or places where speedups may be possible.  There are several tools and techniques available to find these hot-spots in the code.

# Benchmarking Approaches #

* Sampler-based benchmarking
    * Uses `perf`, a tool on Linux that works with the kernel to interface with CPU performance counters , which can be used to do profiling of various executables.
* Graphics pipeline benchmarking
    * Use NVidia tooling and diagnostics to identify hotspots in the graphics pipeline.
* OGRE Profiler
    * Use OGRE's built-in profiler to identify hotspots in the graphics engine.
* Gazebo Diagnostics
    * Use Gazebo's built-in DiagnosticTimer to measure specific parts of the code
* Gazebo Heirarchal Profiler
    * Use a heirarchal profiler that can keep track of timing per thread throughout the call stack.

# Sampler-Base Profiler (perf-tools) #

> Determining why CPUs are busy is a routine task for performance analysis, which often involves profiling stack traces. Profiling by sampling at a fixed rate is a coarse but effective way to see which code-paths are hot (busy on-CPU). It usually works by creating a timed interrupt that collects the current program counter, function address, or entire stack back trace, and translates these to something human readable when printing a summary report.

To perform sample-based profiling, first make sure that perf is installed on the system, on Ubuntu, this is in the `linux-tools` package.  To help inspect and understand the output of the perf tool, it is best to use the FlameGraph tool: http://www.brendangregg.com/FlameGraphs/cpuflamegraphs.html

In order to generate FlameGraphs, there are three distinct steps:

1. Record a series of samples of the execution

Use one of the following commands to generate a `perf` recording of the desired executable:
```
# Sample on-CPU functions for the specified command, at 99 Hertz: 
perf record -F 99 command 
# Sample on-CPU functions for the specified PID, at 99 Hertz, until Ctrl-C: 
perf record -F 99 -p PID 
# Sample on-CPU functions for the specified PID, at 99 Hertz, for 10 seconds: 
perf record -F 99 -p PID sleep 10 
# Sample CPU stack traces (via frame pointers) for the specified PID, at 99 Hertz, for 10 seconds: 
perf record -F 99 -p PID -g -- sleep 10 
```

2. Restructure the recordings to be in a format that is easily visualized (folding)
```
git clone https://github.com/brendangregg/FlameGraph  # or download it from github
cd FlameGraph
perf script | ./stackcollapse-perf.pl > out.perf-folded
```

3. Generate flamegraph visualizations using the tooling available.
```
./flamegraph.pl out.perf-folded > out.svg
```

## Other Notes:

* Use a sample rate that’s not an exactly even number (eg 99 vs 100) to make sure that it’s not in lockstep with the task under inspection
* Recompile with `-fno-omit-frame-pointer`

# NVidia Graphics Pipeline Benchmarking #

NVidia Linux Graphics Debugger: https://developer.nvidia.com/linux-graphics-debugger

> Linux Graphics Debugger is a 3D graphics development tool that allows developers to debug and profile OpenGL 4.x on Linux. It enables professional graphics developers to get the most out of their NVIDIA GeForce and Quadro GPUs on a variety of Linux distributions. This tool supports desktop class GPUs and inherits from the many man-years of investment in OpenGL development tools from the Tegra Graphics Debugger and NVIDIA® Nsight™ Visual Studio Edition.

Note: Linux Graphics Debugger has been deprecated in favor of Nsight: https://developer.nvidia.com/nsight-graphics

With either method, the executable must be launched from within the Graphics Debugger or Nsight context.  Due to the way that we use OGRE, it may be necessary to change the frame end command to `glFlushMappedBufferRange` or equivalent, otherwise the debugger cannot accurately detect the end of frames.  

# OGRE Profiler #

OGRE has a built-in profiler, but it must be enabled as part of the build process (release versions of OGRE do not have it).

To build OGRE with the profiler, use a source checkout and configure the build with `-DOGRE_PROFILING=ON` via CMake.

Gazebo must then be modified to use the profiler.  At the beginning of execution, add:

```
Ogre::Profiler::getSingleton().setEnabled(true);
```
And at the end of execution: 

```
Ogre::Profiler.getSingleton().logResults();
```

To instrument a piece of code, place an `OgreProfiler` call in the scope of interest.  The timer will start when the `OgreProfiler` method is called and will stop when the method goes out of scope.
```
OgreProfile("outside_loop");
for(size_t ii = 0; ii < 100; ++ii) {
  OgreProfile("test_sleep");
  usleep(100);
}
```


# Gazebo Diagnostics #

Uses the Gazebo `DiagnosticManager` and `DiagnosticTimer` objects: https://bitbucket.org/osrf/gazebo/src/default/gazebo/util/Diagnostics.hh


# Gazebo Heirarchal Profiler #

Uses a heirarchal profiler: https://bitbucket.org/osrf/gazebo/pull-requests/2977