# Use the ROS2 base image
FROM ros:foxy

# Install any additional dependencies
RUN apt-get update && apt-get install -y \
    git \
    build-essential \
    python3-colcon-common-extensions

# Clone your ROS2 package from GitHub
RUN mkdir -p /ros_ws/src
WORKDIR /ros_ws/src
#change the link to the github repo
RUN git clone https://github.com/<username>/<repo>.git

# Build your ROS2 package
WORKDIR /ros_ws
RUN . /opt/ros/foxy/setup.sh && \
    colcon build
