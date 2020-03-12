# Build Cop

A build cop monitors the [continuous integration system](http://build.osrfoundation.org), reports build and test failures, and farms out work to resolve issues. The role of build cop rotates on a weekly basis between OSRF developers.

Use the [buildcop_stats.bash](https://bitbucket.org/osrf/release-tools/src/default/jenkins-scripts/tools/buildcop_stats.bash) script from release-tools to count the number of jobs of a given color.
It will generate output like the following:

~~~
# Build Cop Report 2018-MM-DD

## Aggregate Results as of 2018-MM-DD time

| Type | Count | Percent | Change |
|--|--|--|--|
| total | 175 | |  |
| blue | 104/175 | 59.4% |  |
| yellow | 59/175 | 33.7% |  |
| red | 10/175 | 5.7% |  |
| aborted | 2/175 | 1.1% |  |
| notbuilt | 0/175 | 0.0% |  |

## [Failing Builds](https://build.osrfoundation.org/view/main/view/BuildCopFail/)


### Builds with no record of passing

...


### Builds that have succeeded in the past, but are failing now

...
~~~

that renders in markdown as shown below. You can manually add entries to the change column by comparing to the entries in the previous build cop entry.

---

# Build Cop Report 2018-MM-DD

## Aggregate Results as of 2018-MM-DD time

| Type | Count | Percent | Change |
|--|--|--|--|
| total | 175 | |  |
| blue | 104/175 | 59.4% |  |
| yellow | 59/175 | 33.7% |  |
| red | 10/175 | 5.7% |  |
| aborted | 2/175 | 1.1% |  |
| notbuilt | 0/175 | 0.0% |  |

## [Failing Builds](https://build.osrfoundation.org/view/main/view/BuildCopFail/)


### Builds with no record of passing

...


### Builds that have succeeded in the past, but are failing now

...

---

## Tasks

A build cop:

1. Actively monitors the [Gazebo](https://github.com/osrf/buildfarmer/blob/master/Gazebo.md) and [Ignition](https://github.com/osrf/buildfarmer/blob/master/Ignition.md) pages for failures. At a minimum this should be done once per day.

1. Restart any builds that appear to have failed for spurious reasons.

1. Notifies the pull request creator and reviewers when a build breaks due to their pull request. Under normal circumstances, the build cop should not debug the failure.

1. If you cannot easily determine which pull-request broke the build, then all associated pull requests will be notified.

1. Send out a daily report about the build status, and create an entry on this wiki (see the report list below).

1. Sent out a weekly report on Friday that summarizes the build status over the past week.

A person who breaks the build:

1. Debugs the failure, and does one of the following:

    1. Fixes the problem

    1. Disable the failing test if it's flaky, and create an issue.

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
* [March build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/03)
* [April build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/04)
* [May build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/05)
* [June build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/06)
* [July build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/07)
* [August build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/08)
* [September build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/09)
* [October build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/10)
* [November build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/11)
* [December build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/12)

### 2019

* [January build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2019/01)
* [February build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2019/02)
* [March build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2019/03)
* [April build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2019/04)
* [May build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2019/05)
* [June build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2019/06)
* [July build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2019/07)
* [August build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2019/08)
* [September build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2019/09)
* [October build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2019/10)
* [November build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2019/11)
* [December build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2019/12)

### 2020

* [January build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2020/01)
* [February build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2020/02)
* [March build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2020/03)