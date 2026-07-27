# ROS 2 Humble Installation on Ubuntu 22.04 (WSL2)

## Introduction

This project documents the installation of Ubuntu 22.04 LTS on Windows Subsystem for Linux 2 (WSL2) and the installation of ROS 2 Humble Desktop. The process followed the provided training material and included resolving several installation issues until the environment was configured successfully.

---

## Objective

The objective of this task was to:

- Install Ubuntu 22.04 using WSL2.
- Install ROS 2 Humble Desktop.
- Configure the ROS environment.
- Verify that the installation was completed successfully.

---

## Installation Steps

### 1. Install Ubuntu 22.04

The installation started by enabling WSL2 and installing Ubuntu 22.04 using:
wsl --install -d Ubuntu-22.04

After the installation finished, a Linux username and password were created.

---

### 2. Update Ubuntu

The system packages were updated to the latest version:
sudo apt update
sudo apt upgrade -y

---

### 3. Install Required Packages

The required packages for installing ROS were installed:
sudo apt install software-properties-common curl -y

---

### 4. Add the ROS GPG Key

The official ROS security key was downloaded:
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

---

### 5. Add the ROS Repository

The ROS 2 repository was added to Ubuntu:
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu jammy main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

---

### 6. Update Package Lists
sudo apt update

---

### 7. Install ROS 2 Humble Desktop
sudo apt install ros-humble-desktop -y

---

### 8. Configure the ROS Environment

The ROS environment was added to the Bash configuration file:
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc

---

### 9. Verify the Installation

The installation was verified by checking the ROS distribution:
echo $ROS_DISTRO

Output:
humble

This confirms that ROS 2 Humble was installed and configured successfully.

---

# Problems Encountered

## Problem 1: Wrong Ubuntu Version

### Issue

Initially, Ubuntu 26.04 was installed instead of Ubuntu 22.04.

This caused the following error:
Unable to locate package ros-humble-desktop

### Solution

The incorrect Ubuntu distribution was removed from WSL using:
wsl --unregister Ubuntu

Ubuntu 22.04 was then installed again:
wsl --install -d Ubuntu-22.04

---

## Problem 2: Incorrect curl Command

### Issue

The command used to download the ROS key was entered on multiple lines instead of a single line, causing errors such as:
curl: no URL specified

and
No such file or directory

### Solution

The complete command was entered correctly on a single line.

---

## Problem 3: Incorrect Repository Command

### Issue

The repository command was copied with missing quotation marks and line breaks, resulting in:
command not found

### Solution

The repository command was rewritten correctly as a single command.

---

## Problem 4: ROS Version Verification

### Issue

The following command was used:
ros2 --version

which produced:
ros2: error: unrecognized arguments: --version

### Solution

Instead of checking the version using ros2 --version, the installation was verified using:
echo $ROS_DISTRO

The output:
humble

confirmed that ROS 2 Humble was installed successfully.

---

## Result

The installation process was completed successfully.

The final verification confirmed that the active ROS distribution is:
humble

This indicates that Ubuntu 22.04, WSL2, and ROS 2 Humble Desktop were installed and configured correctly, and the environment is ready for future ROS development and robotics applications.







