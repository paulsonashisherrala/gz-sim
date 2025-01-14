# Gazebo Harmonic Installation and Usage Instructions

This document provides a comprehensive guide for installing and using Gazebo Harmonic on Ubuntu 22.04. It includes steps for installation, running simulations, creating custom worlds, and exploring additional resources.

## Step 1: Install Gazebo Harmonic

### 1. Open a Terminal
You can do this by searching for "Terminal" in your applications menu.

### 2. Update Package List
```bash
sudo apt-get update
```
This command updates the list of available packages and their versions.

### 3. Install Necessary Tools
```bash
sudo apt-get install curl lsb-release gnupg
```
This command installs essential tools required for adding repositories.

### 4. Add the Gazebo Package Repository

#### Download the GPG Key
```bash
sudo curl https://packages.osrfoundation.org/gazebo.gpg --output /usr/share/keyrings/pkgs-osrf-archive-keyring.gpg
```
This command downloads the GPG key for the Gazebo repository.

#### Add the Gazebo Repository to Your Sources List
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/pkgs-osrf-archive-keyring.gpg] http://packages.osrfoundation.org/gazebo/ubuntu-stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/gazebo-stable.list > /dev/null
```
This command adds the Gazebo repository to your system's package sources.

### 5. Update Package List Again
```bash
sudo apt-get update
```
This command updates the package list again to include the new Gazebo repository.

### 6. Install Gazebo Harmonic
```bash
sudo apt-get install gz-harmonic
```
This command installs the Gazebo Harmonic simulator.

## Step 2: Run Gazebo

### 1. Launch Gazebo with Shapes World
```bash
gz sim shapes.sdf
```
This command launches Gazebo with a predefined world that contains three simple shapes.

### 2. Launch Gazebo with Verbose Output
```bash
gz sim shapes.sdf -v 4
```
This command launches Gazebo and shows detailed error, warning, informational, and debugging messages in the console.

### 3. Run Gazebo in Headless Mode
```bash
gz sim -s shapes.sdf -v 4
```
This command runs Gazebo without the GUI (server only).

### 4. Run the GUI Independently
```bash
gz sim -g
```
This command starts the Gazebo GUI without launching the server.

## Step 3: Create Your Own World

### 1. Understanding SDF
SDF (Simulation Description Format) is used to specify the contents of your simulation. You can find tutorials on SDF to get started with creating your own worlds.

### 2. Modify Existing SDF Worlds
Gazebo ships with several example SDF worlds that you can copy and modify. These files are typically located in:
```bash
/usr/share/gazebo-<version>/worlds/
```
Copy an existing SDF file to your working directory and modify it as needed. For example:
```bash
cp /usr/share/gazebo-<version>/worlds/example_world.sdf ~/my_custom_world.sdf
```

### 3. Using Models from Gazebo Fuel
You can find a variety of models at [Gazebo Fuel](https://app.gazebosim.org/fuel). Click on the `<>` icon on a model's description page to copy an SDF snippet, which you can then paste into your custom SDF file.

### 4. Creating a Custom SDF File
Create a new SDF file in your working directory. For example:
```bash
nano ~/my_custom_world.sdf
```
Add your SDF content, including any models or elements you want to include.

### 5. Run Your Custom World
Launch your custom world using:
```bash
gz sim ~/my_custom_world.sdf
```

## Step 4: Explore and Learn

### Tutorials and Resources
Explore the available tutorials on the [Gazebo website](https://gazebosim.org/) to learn more about the GUI, creating worlds, and building robots. Each Gazebo library has a set of tutorials and examples. Visit [Gazebo Answers](https://answers.gazebosim.org) for community support and questions.

## macOS Instructions

If you are using macOS, you will need to run Gazebo using two terminals:

### 1. Launch the Server in One Terminal
```bash
gz sim -v 4 shapes.sdf -s
```

### 2. Launch the GUI in a Separate Terminal
```bash
gz sim -v 4 -g
```

## Summary of Commands

Here’s a summary of all the commands you need to run in order:

### Step 1: Install Gazebo Harmonic
```bash
sudo apt-get update
sudo apt-get install curl lsb-release gnupg
sudo curl https://packages.osrfoundation.org/gazebo.gpg --output /usr/share/keyrings/pkgs-osrf-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/pkgs-osrf-archive-keyring.gpg] http://packages.osrfoundation.org/gazebo/ubuntu-stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/gazebo-stable.list > /dev/null
sudo apt-get update
sudo apt-get install gz-harmonic
```

### Step 2: Run Gazebo
```bash
gz sim shapes.sdf
gz sim shapes.sdf -v 4
gz sim -s shapes.sdf -v 4
gz sim -g
```

### Step 3: Create Your Own World

#### Modify Existing SDF World
```bash
cp /usr/share/gazebo-<version>/worlds/example_world.sdf ~/my_custom_world.sdf
nano ~/my_custom_world.sdf  # Edit your custom world
```

#### Run Your Custom World
```bash
gz sim ~/my_custom_world.sdf
```

### macOS Instructions

#### Launch Server in One Terminal
```bash
gz sim -v 4 shapes.sdf -s
```

#### Launch GUI in a Separate Terminal
```bash
gz sim -v 4 -g
