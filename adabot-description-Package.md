### adabot_description

This packages specifies adabot's structure in a Xacro file. Xacro is an XML macro language that enables the writing of shorter more readable XML files (you can use variables, include other files, etc.). The URDF files generated from the Xacro files can be viewed with rviz.

### Launching Adabot in rviz

rviz is a basic visualization tool that will build robot model based on an .xacro description file. The model itself will be stationary, but any joints will be movable as described by the model.

Default command to launch adabot in rviz:

`roslaunch adabot_description adabot.display.launch`

#### Launching with parameters

`roslaunch adabot_description adabot.display.launch <prameter>:= <value>`

Parameter List
```
PARAMETER       DESCRIPTION                               DEFAULT
ch_width        width of the chasis                       0.100
ch_length       length of the chasis                      0.070
wh_radius       radius for each wheel                     0.020
ax_radius       radius of the axle (limits extnesion)     0.008
wg_per_wheel    number of wegs on each of wheels          5
scale           scaling factor for the entire device      4
```

### File Structure
```
adabot_description
├── CMakeLists.txt
├── package.xml
├── launch
|   ├── adabot.display.launch
|   └── adabot.model.launch
├── rviz
|   └── adabot.rviz
└── urdf
    ├── adabot.gazebo.xacro
    ├── adabot.macros.xacro
    ├── adabot.main.xacro
    ├── adabot.materials.xacro
    └── adabot.parameters.xacro
```
