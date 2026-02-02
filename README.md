# ROS 2 Development Workspace

A ROS 2 Humble workspace with DevContainer support for robotics development. Includes development tools and rosbag tools.

## Features

- **ROS 2 Humble** base environment. (Can be changed in the `Dockerfile`)
- **DevContainer** with pre-configured vscode extensions (clangd, clang-format, etc.)
- **Foxglove** for visualization
- **[ros2bag_tools](https://github.com/AIT-Assistive-Autonomous-Systems/ros2bag_tools)** for rosbag operations and analysis
- **[ros2_unbag](https://github.com/ika-rwth-aachen/ros2_unbag.git)** for rosbag extraction

## Quick Start

1. **Setup Git/SSH forwarding** — [Follow this guide](https://code.visualstudio.com/remote/advancedcontainers/sharing-git-credentials)

2. **Import dependencies**
   ```bash
   vcs import ros/deps < ros2.repos
   ```

3. **Open in DevContainer** — VS Code will prompt to reopen in container

4. **Build workspace** Ctrl+Shift+b

## Requirements

- Ubuntu 22.04 (tested)
- Docker + VS Code Remote Containers
- SSH agent with forwarded credentials
