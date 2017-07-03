### adabot_gazebo

This packages enables the simulation of adabot in Gazebo.

### Launching Adabot in Gazebo
Gazebo allows a robot described in a .xacro file to be launched in a dynamic environment.

Command to launch adabot in a gazebo world:

`roslaunch adabot_gazebo adabot.<world_name>.launch`

#### Gazebo Worlds
Replace `<world_name>` in the above command with one of the following worlds to launch adabot in
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

`roslaunch adabot_gazebo adabot.world.launch <prameter>:= <value>`

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
