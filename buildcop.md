# Build Cop

A build cop monitors the [continuous integration system](build.osrfoundation.org), reports build and test failures, and farms out work to resolve issues. The role of build cop rotates on a weekly basis between OSRF developers.

A build cop:

1. Sets their email address to the Jenkins alias. Jenkins will send build notifications to this email address.

1. Actively monitors the build reports for failures. At a minimum this should be done hourly.

1. Notify another OSRF developer to create an issue for a failure. The build cop should maintain a rotating list of developers who receive these requests. The build cop should send a link to the failure, and a short description, such as failing test name, of the problem.

    1. The developer assigned to create an issue should analyze the build, and create an issue with a title that has the "Build Cop" prefix.
    1. The issue should be assigned to the person who broke the build or test. Do not assign a person if a culprit cannot be identified.
    1. The person assigned to the issue should work to resolve the issue ASAP. Volunteers should step forward to handle unassigned issues.

1. Send out a daily report about the build status, and create an entry on this wiki (see the report list below).

1. Sent out a weekly report on Friday that summarizes the build status over the past week.
   
## Reports

### 2016

[October build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2016/10)
[November build report](https://bitbucket.org/osrf/gazebo/wiki/buildcop/2016/11)
