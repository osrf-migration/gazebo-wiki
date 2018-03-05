# Build Cop

A build cop monitors the [continuous integration system](http://build.osrfoundation.org), reports build and test failures, and farms out work to resolve issues. The role of build cop rotates on a weekly basis between OSRF developers.

* [Jenkins Build Fail](http://build.osrfoundation.org/view/main/view/BuildCopFail/)

Use the [buildcop_stats.bash](https://bitbucket.org/osrf/release-tools/src/7bc7933e953c0906b1e1e84c7c4681209bd0c932/jenkins-scripts/tools/buildcop_stats.bash?at=default&fileviewer=file-view-default) script from release-tools to count the number of jobs of a given color:

~~~
curl https://build.osrfoundation.org/view/main/view/BuildCopFail/api/json 2>/dev/null | python -c '\
import json, sys;
jobs = json.loads(sys.stdin.read())["jobs"];
print("| Type | Count | Percent | Change |")
print("|--|--|--|--|")
print("| total | %d | |  |" % len(jobs));
for c in ["blue", "yellow", "red", "aborted"]:
    jc = [j for j in jobs if j["color"].startswith(c)]
    print("| %s | %d/%d | %.1f%% |  |" % (c, len(jc), len(jobs), 100*float(len(jc)) / len(jobs)))'
~~~

It will generate output like the following:

~~~
| Type | Count | Percent | Change |
|--|--|--|--|
| total | 115 | |  |
| blue | 72/115 | 62.6% |  |
| yellow | 34/115 | 29.6% |  |
| red | 9/115 | 7.8% |  |
| aborted | 0/115 | 0.0% |  |
~~~

that renders in markdown like the following:

| Type | Count | Percent | Change |
|--|--|--|--|
| total | 115 | |  |
| blue | 72/115 | 62.6% |  |
| yellow | 34/115 | 29.6% |  |
| red | 9/115 | 7.8% |  |
| aborted | 0/115 | 0.0% |  |

You can manually add entries to the change column by comparing to the entries in the previous build cop entry.

## Tasks

A build cop:

1. Actively monitors the [BuildCopFail page](https://build.osrfoundation.org/view/main/view/BuildCopFail/) for failures. At a minimum this should be done once per day.

1. Restart any builds that appear to have failed for spurious reasons.

1. Send out a daily report about the build status, and create an entry on this wiki (see the report list below).

1. Sent out a weekly report on Friday that summarizes the build status over the past week.

## Reports

### 2016

* [October build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2016/10)
* [November build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2016/11)
* [December build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2016/12)

### 2017

* [January build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2017/01)
* [February build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2017/02)
* [March build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2017/03/15)
* [April build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2017/04)
* [May build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2017/05)
* [July build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2017/07)
* [August build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2017/08)
* [September build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2017/09)
* [October build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2017/10)
* [November build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2017/11)
* [December build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2017/12)

### 2018

* [January build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/01)
* [February build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/02)