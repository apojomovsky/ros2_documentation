### ROS 2 Bouncy Bolson (codename 'bouncy'; June 2018)

Welcome to the latest release of ROS 2 software named *Bouncy Bolson*!

### Supported Platforms

This version of ROS 2 is supported on four platforms (see [REP 2000](http://www.ros.org/reps/rep-2000.html#bouncy-bolson-june-2018-june-2019)):
- Ubuntu 18.04 (Bionic)
  - Debian packages for amd64 as well as arm64
- Ubuntu 16.04 (Xenial)
  - no Debian packages but building from source is supported
- Mac OS X 10.12 (Sierra)
- Windows 10 with Visual Studio 2017

Binary packages as well as instructions for how to compile from source are provided (see [install instructions](Installation.md) as well as [documentation](http://docs.ros2.org/bouncy/)).

### Features

#### New features in this ROS 2 release

- [New launch system](Launch-system.md) featuring a much more capable and flexible Python API.
- Parameters can be passed as [command line arguments](Node-arguments.md) to C++ executables.
- Static remapping via [command line arguments](Node-arguments.md).
- Various improvements to the Python client library.
- Support for publishing and subscribing to serialized data.
  This is the foundation for the upcoming work towards a native rosbag implementation.
- More [command line tools](Introspection-with-command-line-tools.md), e.g. for working with parameters and lifecycle states.
- Binary packages / fat archives support three RMW implementations by default (without the need to build from source):
  - eProsima's FastRTPS (default)
  - RTI's Connext
  - ADLINK's OpenSplice

For an overview of all features available, including those from earlier releases, please see the [Features](Features.md) page.

#### Changes since the Ardent release

Changes since the [Ardent Apalone](Release-Ardent-Apalone.md) release:
- The Python package `launch` has been redesigned.
  The previous Python API has been moved into a submodule `launch.legacy`.
  You can update existing launch files to continue to use the legacy API if a transition to the new Python API is not desired.
- The ROS topic names containing namespaces are mapped to DDS topics including their namespaces.
  DDS partitions are not being used anymore for this.
- The recommended build tool is now `colcon` instead of `ament_tools`.
  This switch has no [implications](http://design.ros2.org/articles/build_tool.html#implications) for the code in each ROS 2 package.
  The install instructions have been updated and the [read-the-docs page](http://colcon.readthedocs.io/en/latest/migration/ament_tools.html) describes how to map an existing `ament_tools` call to `colcon`.
- The argument order of [this `rclcpp::Node::create_subscription()` signature](http://docs.ros2.org/bouncy/api/rclcpp/classrclcpp_1_1_node.html#a283fb006c46470cf43a4ae5ef4a16ccd) has been modified.

### Known Issues

- New-style launch files [may hang on shutdown](https://github.com/ros2/launch/issues/89) for some combinations of platform and RMW implementation.
- Static remapping of namespaces [not working correctly](https://github.com/ros2/rcl/issues/262) when addressed to a particular node.
- [Opensplice error messages may be printed](https://github.com/ros2/rmw_opensplice/issues/237) when using `ros2 param` and `ros2 lifecycle` command-line tools.
