### adabot_gazebo

This packages enables the simulation of adabot in Gazebo.

### Launching Adabot in Gazebo
Gazebo allows a robot described in a .xacro file to be launched in a dynamic environment.

Command to launch adabot in a gazebo world:

`roslaunch adabot_gazebo adabot.<world_name>.launch`

#### Gazebo Worlds
Replace `<world_name>` in the above command with one of the following worlds to launch adabot in. [This folder](https://github.com/anthony-jclark/adabot/tree/master/adabot_gazebo/worlds) contains the different gazebo worlds.
```
WORLD NAME      DESCRIPTION
empty           An empty gazebo world
fast-rocky3     ...
fast-step       ...
rocky           ...
rocky3          ...
step            ...
```

#### Launching with parameters
Multiple parameters can be passed in to adjust different dimensions of adabot

`roslaunch adabot_gazebo adabot.world.launch <prameter>:=<value>`

Example:

`roslaunch adabot_gazebo adabot.world.launch ch_width:=.75 wg_per_wheel:=3`

Parameter List
```
PARAMETER       DESCRIPTION                               EXAMPLE
ch_width        width of the chasis                       0.100
ch_length       length of the chasis                      0.070
wh_radius       radius for each wheel                     0.020
ax_radius       radius of the axle (limits extnesion)     0.008
wg_per_wheel    number of wegs on each of wheels          5
scale           scaling factor for the entire device      4
```

Parameters are defined in the `adabot.model.launch` file [here](https://github.com/anthony-jclark/adabot/blob/master/adabot_description/launch/adabot.model.launch#L23-L35). Each parameter has a default value that will be overridden by any that are passed in through the command line (as shown above).

These values are then passed [here](https://github.com/anthony-jclark/adabot/blob/master/adabot_description/urdf/adabot.parameters.xacro#L8-L19) to the `adabot.parameters.xacro` file. The xacro file also has defaults that will be overridden by any value passed in from the `adabot.model.launch` file above.

### File Structure
```
adabot_gazebo
├── CMakeLists.txt
├── package.xml
├── launch
|   └── adabot.world.launch
└── worlds
    ├── adabot.empty.xacro
    ├── ...
    └── worldModels
      └── ...
```
#### 'worlds' folder

This folder contains different worlds that adabot can be launched within. They use the name schema `adabot.<world_name>.xacro`.
