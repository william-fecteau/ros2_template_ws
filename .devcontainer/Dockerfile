FROM ros:humble

# Add arguments for user ID and group ID
ARG USER_ID=1000
ARG GROUP_ID=1000
ARG USERNAME=robot

RUN apt-get update -y && apt-get install -y ros-${ROS_DISTRO}-foxglove-bridge \
    clangd \
    clang-format \
    ros-${ROS_DISTRO}-rosbag2-storage-mcap \
    python3-pip \
    openssh-client \
    sudo

# ros2_unbag deps
RUN apt install -y libxcb-cursor0 libxcb-shape0 libxcb-icccm4 libxcb-keysyms1 libxkbcommon-x11-0 libegl1-mesa libgl1-mesa-glx
RUN pip install ros2-unbag

# Create a user with the same UID/GID as the host user
RUN groupadd --gid $GROUP_ID $USERNAME && \
    useradd --uid $USER_ID --gid $GROUP_ID --create-home --shell /bin/bash $USERNAME && \
    echo "$USERNAME ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/$USERNAME && \
    chmod 0440 /etc/sudoers.d/$USERNAME

# Make sure user can use sudo
RUN adduser $USERNAME sudo
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/nopasswd && chmod 0440 /etc/sudoers.d/nopasswd

# Switch to the new user
USER $USERNAME
WORKDIR /home/$USERNAME

# Set up ROS environment for the new user
RUN echo "source /opt/ros/${ROS_DISTRO}/setup.bash && [ -f ~/ros2_ws/install/setup.bash ] && source ~/ros2_ws/install/setup.bash" >> ~/.bashrc
