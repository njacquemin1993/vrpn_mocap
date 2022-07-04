# vrpn\_ros2

ROS2 [VRPN](https://github.com/vrpn/vrpn) client built pirmarily to interface
with motion capture devices such as VICON and OptiTrack. A detailed list of
supported hardware can be found on
[vrpn wiki](https://github.com/vrpn/vrpn/wiki/Available-hardware-devices).

## Installation

#### Install From Binary Release
- [ ] TODO

#### Build From Source
1. Clone this repo into your ROS2 workspace
2. Run `rosdep install --from-paths src -y --ignore-src` to install dependencies
3. Run `colcon build`
4. Your usual ROS2 routines: `source install/setup.zsh`, etc.

## Usage

#### Launch Default Configuration from Command Line
Run the following command,
```bash
ros2 launch client.launch.yaml server:=<server ip> port:=<port>
```
replacing `<server ip>` and `<port>` with your VRPN server ip and port, e.g.
```bash
ros2 launch client.launch.yaml server:=192.168.0.4 port:=3883
```
Then with `ros2 topic list`, you should be able to see the following topics
```bash
/vrpn_mocap/client_node/<tracker_name>/pose
/vrpn_mocap/client_node/<tracker_name>/twist # optional when mocap reports velocity data
/vrpn_mocap/client_node/<tracker_name>/accel # optional when mocap reports acceleration data
```
where `<tracker_name>` is usually the name of your tracked objects.

#### Customized Launch
Check out the default [parameter file](config/client.yaml) and
[launch file](launch/client.launch.yaml). You can then write your own launch
file with custom configurations.

### Acknowledgement
Some ideas are borrowed from the well known
[vrpn\_client\_ros](https://github.com/ros-drivers/vrpn_client_ros) -- a ROS1
package for interfacing with VRPN devices. I thank the authors and developers
for delivering and maintaining the original implementation.