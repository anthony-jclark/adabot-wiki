## Directory Structure

Below is the top-level (workspace) directory structure. I've decided to keep all adabot packages together. This makes it easier to develop code, and this code is not likely to be reused by other projects. [This ROS Answers Post](http://answers.ros.org/question/257855/git-strategy-for-catkin-and-package-folders/) has a good explanation of how to effectively use a git repository for multiple packages.

```
adabot
└── src
    ├── CMakeLists.txt -> /opt/ros/kinetic/share/catkin/cmake/toplevel.cmake
    ├── adabot_description
    └── adabot_gazebo
```


