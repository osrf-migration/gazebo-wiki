# Introduction

This page is for collecting and organizing tips on debugging the gazebo simulator. In order to ease debugging, please add links to screenshots or videos of a failure mode so that users can try to match up the behavior they're seeing previously encountered problems. 

**This page is for _strategies_ for resolving issues that are inherent to 3D simulation with gazebo, and are not specific to any version,  build, or platform.**

## Bugs

If you find a bug or a potential bug in gazebo, please report it on the [http://bitbucket.org/osrf/gazebo/issues?status=new&status=open bugtracker]. If you're unsure if it's a bug or just user error, please ask about it on [http://answers.gazebosim.org/questions/ask/ answers.gazebosim.org].

## General Problems

The first places to look are [http://answers.gazebosim.org answers.gazebosim.org] and (legacy [http://answers.ros.org/questions/scope:all/sort:activity-desc/query:gazebo/page:1/ answers.ros.org]). Search these Q&A sites for posts from other users who might have encountered the same problem as you describe it.

If you encounter a problem that isn't resolved by the information on this page nor the previously-asked questions, please [http://answers.gazebosim.org/questions/ask/ ask your question here]. 

# Simulation Problems

## Simulation Instability (Exploding-Robot Syndrome)

If you find your simulation [http://www.youtube.com/watch?v=RAOHp73ZGYM going unstable and consequently exploding], you might want to look into the following:

 * Consider reducing the physics solver timestep.
 * A link with a small amount of mass and might go unstable if it has a large `<damping>` value in its `<dynamics>` tag. ([http://www.youtube.com/watch?v=RAOHp73ZGYM example])

# Crashes

See [[help]] to see how you can run Gazebo in debug mode.

## Ogre Exceptions

Note that sometimes gazebo may crash due to bugs or incompatibilities in your graphics driver and graphics chipset.

# Profiling

Profiling Gazebo can pinpoint functions that consume a lot of cycles, and help to identify where code improvements should be made. 

There a few tools which provide profile analysis, and they each have pros and cons. We will describe how to use valgrind, and perf. The following are links to more information about these tools:

[https://access.redhat.com/knowledge/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Developer_Guide/profiling.html https://access.redhat.com/knowledge/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Developer_Guide/profiling.html]

[http://en.wikipedia.org/wiki/Valgrind http://en.wikipedia.org/wiki/Valgrind]

[http://stackoverflow.com/questions/13906911/valgrind-vs-linux-perf-correlation http://stackoverflow.com/questions/13906911/valgrind-vs-linux-perf-correlation]

## Valgrind

Install valgrind and kcachegrind (a graphical tools to visualize the results of valgrind)
~~~
sudo apt-get install valgrind kcachegrind
~~~

Run the valgrind's callgrind tool
~~~
valgrind --tool=callgrind gzserver worlds/pr2.world
~~~

Let valgrind run for a while, then `ctrl-c` to stop gzserver and valgrind.

A callgrind file will be in your working directory. Use kcachegrind to view it.
~~~
kcachegrind <the_callgrind_file>
~~~

## Perf

Install perf
~~~
sudo apt-get install linux-tools
~~~

Record data
~~~
perf record gzserver worlds/pr2.world
~~~

Generate a report
~~~
perf report
~~~
