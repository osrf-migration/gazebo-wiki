# Build Cop

A build cop monitors the [continuous integration system](http://build.osrfoundation.org), reports build and test failures, and farms out work to resolve issues. The role of build cop rotates on a weekly basis between OSRF developers.

* [Jenkins Build Fail](http://build.osrfoundation.org/view/main/view/BuildCopFail/)

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
* [March build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/03)
* [April build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/04)
* [May build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/05)
* [June build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/06)
* [July build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2018/07)