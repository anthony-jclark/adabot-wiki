
Below are a set of instructions for setting up your development environment. This might be a dual booted Ubuntu environment, Ubuntu running in a virtual machine, or an Ubuntu-only computer (as we have in the lab).

These instructions have only been tested with the following setup:

- [Ubuntu 16.04.2 LTS (Xenial Xerus)](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)
- [ROS Kinetic Kame](http://wiki.ros.org/kinetic/Installation/Ubuntu) (install ros-kinetic-desktop-full unless you are working on a headless server)

The first several sections below require administrator privilidges. If you are working on the an ARCS Lab machine you can skip down to [User Configuration](#user-configuration) for my suggestions on how to setup your account.

### General Utilities

Here are a few utilities that will need to be installed:

```bash
# Retrieve information about available packages
sudo apt-get update

# Install git (version control software)
sudo apt-get intstall git

# Install a visual merge tool or git
sudo apt-get install meld

# A utility for using the clipboard from the command line
sudo apt-get install xclip

# Enable SSH service for remote login
sudo apt-get install openssh-server

# Install a mesh viewer editor
sudo apt-get install meshlab
```

### Install Terminator

[Terminator](https://gnometerminator.blogspot.com/p/introduction.html) is an improved terminal emulator. I prefer this over the built-in terminal emulator options since it includes tabs and panes.

```bash
sudo add-apt-repository ppa:gnome-terminator
sudo apt-get update
sudo apt-get install terminator
```

### Install Zsh

Zsh is my preferred shell on linux. It includes a few extra features and simplifies a few scripting tasks.

```bash
sudo apt-get install zsh
chsh -s $(which zsh)
```

### Install hub

[`hub`](https://hub.github.com/) is a wrapper for git that can be used to work more effectively with github. It provides an easier means (a command-line interface) to fork repositories and perform pull requests.

```bash
# Download the latest version of hub (a git wrapper for github)
curl -s -L https://github.com/github/hub/releases/latest \
	| egrep -o '/github/hub/releases/download/[v]?[0-9.]*/hub-linux-amd64.*tgz' \
	| wget --base=http://github.com/ -i - -O hub.tgz

# Install hub
mkdir hub/ && tar zvxvf hub.tgz -C hub --strip-components 1
sudo ./hub/install
mv ./hub/etc/hub.zsh_completion $ZSH/completions/_hub

# Cleanup the downloaded directory
rm -rf hub/
```

### Neovim

Vim is my preferred command-line text editor, and the [neovim](https://neovim.io/) project seems to be headed in a good direction with regard to improving the vim backend (you could just as easily use pure vim).

```bash
# Install neovim
sudo add-apt-repository ppa:neovim-ppa/stable
sudo apt-get update
sudo apt-get install neovim

# Grab a basic vim configuration file from github
git clone git://github.com/amix/vimrc.git ~/.vim_runtime
sh ~/.vim_runtime/install_basic_vimrc.sh
```

### ROS

Now we are ready to install ROS and its related tools. All of these commands are taken from the [ROS wiki about kinetic](http://wiki.ros.org/kinetic/Installation/Ubuntu) and from the [Catkin tools documentation](http://catkin-tools.readthedocs.io/en/latest/installing.html).

```bash
# Tell apt-get about ROS
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116
sudo apt-get update

# Install the full desktop version, unless you are working on a
# headless server--in which case you would use:
#    sudo apt-get install ros-kinetic-ros-base
sudo apt-get install ros-kinetic-desktop-full

# Install additional ROS tools
sudo rosdep init
rosdep update

# Tell your shell about the ROS environment
source /opt/ros/kinetic/setup.zsh

# Install additional ROS tools
sudo apt-get install python-rosinstall

# Install the (nicer-to-use) catkin tools
wget http://packages.ros.org/ros.key -O - | sudo apt-key add -
sudo apt-get update
sudo apt-get install python-catkin-tools

# Install ROS Control
sudo apt-get install ros-kinetic-ros-control ros-kinetic-ros-controllers
```

### User Configuration

To create a non-administrator on the system you use the `adduser` command:

```bash
# Update /etc/adduser.conf and /etc/skel to reflect a new user's
# state prior to running the following
adduser USERNAME
```

Now install [Oh My Zsh](http://ohmyz.sh/), a framework for easy Zsh configuration.

```bash
# Install Oh My Zsh
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```
