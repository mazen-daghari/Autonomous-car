# Autonomous-car
Autonomous car based on autoware

Here's a detailed tutorial on how to install Autoware, along with the required software and hardware specifications:

Hardware Requirements
-
CPU: Multi-core processor (4 cores or more recommended).

RAM: At least 16 GB of RAM.

Storage: Minimum of 100 GB of disk space.

GPU: A dedicated GPU (NVIDIA recommended) for tasks involving perception and deep learning.

Software Requirements
-
Operating System: Ubuntu 20.04 or later.

ROS 2: ROS 2 Humble Hawksbill or later.

PCL (Point Cloud Library): For processing point cloud data.

OpenCV: For computer vision tasks.

CUDA: If using an NVIDIA GPU, CUDA is required for GPU acceleration.

Docker: For containerized environments.

Colcon: For building ROS 2 workspaces.

Step-by-Step Installation Guide
-
Step 1: Install Ubuntu
-
Download the Ubuntu 20.04 ISO from the official website.

Create a bootable USB drive using tools like Rufus or Etcher.

Boot from the USB drive and follow the installation instructions.

Step 2: Install ROS 2
-
Set up the ROS 2 repository:

sh
sudo apt update && sudo apt install curl gnupg2 lsb-release
curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo sh -c 'echo "deb http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2-latest.list'
Install ROS 2 Humble:

sh
sudo apt update
sudo apt install ros-humble-desktop
Source the ROS 2 setup file:

sh
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
Step 3: Install Dependencies
Install PCL and OpenCV:

sh
sudo apt install libpcl-dev libopencv-dev
Install CUDA (if using an NVIDIA GPU): Follow the instructions on the NVIDIA CUDA Toolkit website.

Step 4: Install Docker
-
Install Docker:

sh
sudo apt update
sudo apt install docker.io
sudo systemctl start docker
sudo systemctl enable docker
Add your user to the Docker group:

sh
sudo usermod -aG docker $USER
Step 5: Install Colcon
-
Install Colcon:

sh
sudo apt install python3-colcon-common-extensions

Step 6: Clone and Build Autoware
-
Create a workspace directory:

sh
mkdir -p ~/autoware/src
cd ~/autoware/src
Clone the Autoware repository:

sh
git clone https://github.com/autowarefoundation/autoware.universe.git
Install dependencies using rosdep:

sh
cd ~/autoware
rosdep update
rosdep install --from-paths src --ignore-src -r -y
Build the workspace:

sh
colcon build --symlink-install --cmake-args -DCMAKE_BUILD_TYPE=RelWithDebInfo
Step 7: Source the Workspace
-
Source the setup file:

sh
source install/setup.bash
Step 8: Run Autoware
-
Launch Autoware:

sh
ros2 launch autoware_launch planning_simulator.launch.xml map_path:=$HOME/autoware_map/sample-map-planning vehicle_model:=sample_vehicle sensor_model:=sample_sensor_kit
By following these steps, you should be able to install and run Autoware on your system. If you encounter any issues or need further assistance, feel free to ask! You can mail me on ; 

mailto: dagmazen@gmail.com
-

Note : you must have good internet connection to install this software with out any issue . 
-
