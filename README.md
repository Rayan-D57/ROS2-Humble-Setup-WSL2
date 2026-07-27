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

# What is Linux?

Linux is a free and open-source operating system kernel developed by Linus Torvalds in 1991. It is widely used in servers, cloud computing, embedded systems, and robotics because of its stability, security, flexibility, and high performance. Linux provides powerful command-line tools and allows developers to efficiently manage system resources, making it the preferred platform for robotics and software development.

---

# What is Ubuntu?

Ubuntu is one of the most popular Linux distributions developed by Canonical Ltd. It is based on Debian and provides a user-friendly environment while maintaining the power and flexibility of Linux. Ubuntu offers Long-Term Support (LTS) releases that receive security updates and maintenance for several years. Because of its stability and compatibility, Ubuntu has become the standard operating system for robotics development and is officially supported by ROS 2.

---

# What is ROS?

Robot Operating System (ROS) is an open-source robotics middleware that provides a collection of libraries, frameworks, and development tools for building robotic applications. Rather than being a traditional operating system, ROS serves as a communication layer that enables different software components (nodes) to exchange information efficiently. It provides hardware abstraction, package management, visualization tools, simulation support, device drivers, and communication services that significantly simplify robotics software development.

---

# What is ROS 2 Humble?

ROS 2 Humble Hawksbill is a Long-Term Support (LTS) release of ROS 2 designed to provide improved reliability, performance, scalability, and security. It uses the Data Distribution Service (DDS) communication standard, allowing efficient communication between distributed robotic systems. ROS 2 Humble supports real-time applications, multi-platform development, and modern robotics architectures, making it one of the most widely used versions in both academia and industry.

---

# Why Ubuntu 22.04 and ROS 2 Humble?

Ubuntu 22.04 LTS is the officially supported operating system for ROS 2 Humble. This combination offers long-term stability, compatibility with robotics packages, continuous security updates, and a reliable environment for developing robotic applications. For these reasons, Ubuntu 22.04 and ROS 2 Humble are the recommended platform for learning robotics and developing autonomous systems.

---

## Features

- Installation of Ubuntu 22.04 LTS using WSL2.
- Complete installation of ROS 2 Humble Desktop.
- ROS environment configuration.
- Installation verification.
- Documentation of common installation issues and their solutions.

---

## Prerequisites

Before starting the installation, make sure you have:

- Windows 10 or Windows 11
- Windows Subsystem for Linux 2 (WSL2)
- Stable Internet Connection
- Administrator Privileges


---

## Technologies Used

- Ubuntu 22.04 LTS
- Linux
- WSL2
- ROS 2 Humble Hawksbill
- Bash Shell
- APT Package Manager

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



---

## Author

**Rayan Alshalawi**

Computer Engineering Student  
Taif University



