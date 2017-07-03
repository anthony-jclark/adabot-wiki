
Below is the top-level (workspace) directory structure. I've decided to keep all adabot packages together. This makes it easier to develop code, and this code is not likely to be reused by other projects. [This ROS Answers Post](http://answers.ros.org/question/257855/git-strategy-for-catkin-and-package-folders/) has a good explanation of how to effectively use a git repository for multiple packages.

```
adabot
├── .gitignore
├── .travis.sh
├── .travis.yml
├── LICENSE
├── README.md
├── adabot_control
|   └── ...
├── adabot_description
|   ├── CMakeLists.txt
|   ├── package.xml
|   ├── launch
|   |   ├── adabot.display.launch
|   |   └── adabot.model.launch
|   ├── rviz
|   |   └── adabot.rviz
|   └── urdf
|       ├── adabot.gazebo.xacro
|       ├── adabot.macros.xacro
|       ├── adabot.main.xacro
|       ├── adabot.materials.xacro
|       └── adabot.parameters.xacro
├── adabot_gazebo
|   ├── CMakeLists.txt
|   ├── package.xml
|   ├── launch
|   |   └── adabot.world.launch
|   └── worlds
|      ├── adabot.empty.xacro
|      ├── ...
|      └── worldModels
|         └── ...
└── adabot_localization
    └── ...
```

ros workspace
