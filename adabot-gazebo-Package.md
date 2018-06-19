### adabot_gazebo

This packages enables the simulation of adabot in Gazebo.

### Launching Adabot in Gazebo
Gazebo allows a robot described in a .xacro file to be launched in a dynamic environment.

Command to launch adabot in a gazebo world:

`roslaunch adabot_gazebo adabot.world.launch`

#### Launching with parameters
Multiple parameters can be passed in to adjust different dimensions of adabot

`roslaunch adabot_gazebo adabot.world.launch <parameter>:=<value>`

Example:

`roslaunch adabot_gazebo adabot.world.launch ch_width:=.75 wg_per_wheel:=3 world:=rocky`

Parameter List
```
PARAMETER       DESCRIPTION                                   EXAMPLE
debug_visuals   if true uses collision geometry for visuals   false
ch_width        width of the chasis                           0.100
ch_length       length of the chasis                          0.070
wh_radius       radius for each wheel                         0.020
ax_radius       radius of the axle (limits extnesion)         0.008
wg_per_wheel    number of wegs on each of wheels              5
scale           scaling factor for the entire device          4
world           gazebo world to launch adabot in              rocky
```

Parameters are defined in the `adabot.model.launch` file [here](https://github.com/anthony-jclark/adabot/blob/master/adabot_description/launch/adabot.model.launch#L23-L35). Each parameter has a default value that will be overridden by any that are passed in through the command line (as shown above).

These values are then passed [here](https://github.com/anthony-jclark/adabot/blob/master/adabot_description/urdf/adabot.parameters.xacro#L8-L19) to the `adabot.parameters.xacro` file. The xacro file also has defaults that will be overridden by any value passed in from the `adabot.model.launch` file above.

#### Gazebo Worlds
Pass in the `world` parameter to the launch file (as described above) to launch adabot in one of the following worlds. [This folder](https://github.com/anthony-jclark/adabot/tree/master/adabot_gazebo/worlds) contains the different gazebo worlds available.
```
WORLD NAME      DESCRIPTION
empty           (Default) An empty gazebo world
fast-rocky3     ...
fast-step       ...
rocky           ...
rocky3          ...
step            ...
```

__NOTE:__ Any world files created must be kept in the `adabot_gazebo` folder and use the naming schema, `adabot.<world_name>.world`.

### File Structure
```
adabot_gazebo
├── CMakeLists.txt
├── package.xml
├── launch
|   └── adabot.world.launch
└── worlds
    ├── adabot.empty.world
    ├── ...
    └── worldModels
      └── ...
```
