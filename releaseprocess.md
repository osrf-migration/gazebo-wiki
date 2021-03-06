This page contains information about creating a new major release of Gazebo.

1. Dependency freeze

    * **When**: First Thursday in December.
    * **What**: The version of each Gazebo dependency is locked. New releases of packages that are maintained by Open Robotics, such as Ignition Math, should be generated when appropriate. Start the works in Debian to introduce the new versions. Each dependency must have a prerelease.

2. Feature freeze 

    * **When**: First Thursday in January.
    * **What**: The release branch in Gazebo is created. If there are existing pull requests then some or all will be re-targeted to the release branch. The choice of pull requests is determined by the Gazebo team. No new pull requests will be accepted into the release branch unless the pull request fixes a major bug.

3. Pull request focus

    * **When**: After feature freeze.
    * **What**: Focus on reviewing pull requests that target the release branch. Also focus on existing tutorial pull requests.

4. Upcoming release announcement

    * **When**: Day after feature freeze.
    * **What**: Send an announcement that notifies the community of an upcoming release. Also announce the tutorial party. 

5. Code freeze

    * **When**: 1 week after feature freeze.
    * **What**:
        * The release branch of Gazebo is frozen. No new code unless it fixes a bug.

6. Documentation review

    * **When**: Between code freeze and creation of prerelease.
    * **What**: Make sure gazebo and dependency documentation is correct and up to date.

7. Create prerelease

    * **When**: ASAP after code freeze.
    * **What**: Create a debian prerelease of Gazebo.

8. Tutorial party

    * **When**: First Tuesday after code freeze.
    * **What**:
        * Create spreadsheet of tutorials to review
        * Coordinate tutorial party on community.gazebosim.org
        * Review existing tutorials using Gazebo prerelease.

9. Release

    * **When**: ~1 week after code freeze.
    * **What**:
        * Create blog post and release announcement.
        * Update website with new links, statistics, and roadmap. For statistic generation, refer to the `app/controller/home_controller.rb` file in the `gazebo_web_app`.
        * Release the final Gazebo debian.