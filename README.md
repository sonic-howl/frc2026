# FRC 2026

## Using the Lab PCs

Each lab PC has a dedicated github account associated with it (`lab1-3985`). Since we still want to know who coded what, make sure to include your name in the commit message. See the example below:
```sh
git commit -m "[Nathan] {your commit message here}"
```

## Build and Deploy Commands

To view all available robotpy commands, use the following command:

```bash
# Windows
py -3 -m robotpy

# Linux
python3 -m robotpy
```

> You can pass the `--help` argument to see more information about the subcommand.
>
> For example, to see help for the sim command you can do the following:
>
> ```bash
> # Windows
> py -3 -m robotpy sim --help
> 
> # Linux
> python3 -m robotpy sim --help
> ```

### Running Robot Code

In order to run the robot code, use the following command:

```bash
# Windows
py -3 robot.py

# Linux
python3 robot.py
```

> See full guide on running robot code [here](https://robotpy.readthedocs.io/en/stable/guide/running.html)

### Deploying Code to Robot

You can deploy robot code to a robot you're connected to using:

```bash
# Windows
py -3 robot.py deploy

# Linux
python3 robot.py deploy
```

> Before deploying, make sure you have used the `cd` command to navigate to the `/src` directory. This needs to be done because we only want to deploy the code present in the `/src` folder to the robot (due to memory limitations).

> See full guide on deploying robot code [here](https://robotpy.readthedocs.io/en/stable/guide/deploy.html)

## Simulation Testing

WPILib provides a [simulator](https://docs.wpilib.org/en/stable/docs/software/wpilib-tools/robot-simulation/introduction.html) to test your code without being physically connected to a robot.

### Running the Robot Simulation

A robot simulation is available for testing. Read the full documentation [here](https://docs.wpilib.org/en/stable/docs/software/wpilib-tools/robot-simulation/introduction.html).

You can run it with the following command:

```bash
# Windows
py -3 -m robotpy sim

# Linux and macOS
python3 -m robotpy sim
```

### Running Robot Dashboards during a Simulation

Follow [this guide](https://docs.wpilib.org/en/stable/docs/software/wpilib-tools/robot-simulation/introduction.html#running-robot-dashboards) to enable whichever dashboard you plan on using during the simulation.

### Run Tests

You can also manually run unit tests using:

```bash
# Windows
py -3 -m robot.py test

# Linux
python3 -m robot.py test
```

## Getting started

### Installing Wpilib and Other Tools

Follow [this guide](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-2/wpilib-setup.html#wpilib-installation-guide).

> Make sure to select `Tools Only` as we install the software related dependencies in [this section](#installing-robotpy-and-dependencies).

### Installing FRC Game Tools

To install FRC's game tools for 2026, follow [this guide](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-2/frc-game-tools.html).

> Make sure to choose the most recent version. FRC comes out with patches fairly often throughout the season.

> Note: If you're on windows and you don't see the mount option after right clicking the iso file, you can open the file using `Open with` then `Windows Explorer`.
>
> ![Alt text](./static/mount-alternative.png)

Once installed, you'll have access to these tools:

- FRC Driver Station
- FRC roboRIO Imaging Tool and Images

### Installing WPILib 2026 (Python)

To install the 2026 WPILib programming environment for python, either follow [this guide](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-2/python-setup.html).

**If you're unsure of what options to choose during the install, follow these steps:**
#### Installing Python

To get started, install python version 3.14.2 from these links and run the installer:

**[Windows](https://www.python.org/ftp/python/3.14.2/python-3.14.2-amd64.exe)**

**Installation Steps:**
1. Select Modify
2. Click Next
3. Select `Associate files with Python` then click install
4. After installing you can check if everything worked by:
     - Opening a terminal (Press the windows key and search for `cmd`)
     - Using the following command to check the version of python installed on your system: `py --version`

#### Install VSCode

Follow the instructions [here](https://code.visualstudio.com/download) to install VSCode.

#### Getting Started with VSCode

If you're new to VSCode, WPILib's docs have a good [starting guide](https://docs.wpilib.org/en/stable/docs/software/vscode-overview/vscode-basics.html#visual-studio-code-basics-and-the-wpilib-extension) explaining the basics.

> Note: Since our team uses **Python** to program the robot, we can't make use of the WPILib VsCode extension (So there's no need to install it).

### Cloning the GitHub Repository

In order to gain access to the robot code, clone the [Sonic Howl frc2026 repo](https://github.com/sonic-howl/frc2026).

If you don't know how to do this, follow these steps:

1. Open the repository [link](https://github.com/sonic-howl/frc2026) in your browser
2. Click on the **green** `<> Code` button, choose HTTPS and copy the link to your clipboard.
3. Launch the `VS Code` application.
4. Open the terminal by pressing the `CTRL + ~` keys.
5. Try to navigate to the `code` directory using the following commands:
     - **Windows:** `cd ~; cd code`
     - **Linux / MacOS:** `cd ~ && cd code`
6. If you get an error saying "Cannot find path 'C:\code' because it does not exist." or similar, use the following command to create a new `code` directory: `mkdir code`
7. Enter the command `git clone <<the link you copied here>>`. (The command should look like this: `git clone https://github.com/sonic-howl/frc2026`)
8. Use the following command to open the newly cloned repository: `cd frc2026`
9. From the terminal, you can use the `code .` command to open VsCode in the current directory. Just make sure you're in the `~/code/frc2026` directory before using it (The `~` represents your system's home directory [Example: `C:\Users\Nathan`]).
10. **Extra:** Ask one of the organization admins to add you to the repo. (Neil, Nathan, Ramez).

> If you get an error mentioning that git isn't installed (or that no command named git exists), download and install it [here](https://git-scm.com/downloads).

### Installing RobotPy and Dependencies

Now that you've cloned the project we can proceed to downloading the project's dependencies. 

Depending on your operating system, run the appropriate command in your terminal to install the project's dependencies.

**For Windows**

```bash
# Uninstall old version of robotpy
py -m pip uninstall robotpy
```

```bash
# Install robotpy
py -3 -m pip install robotpy

# You can use the --upgrade flag before the robotpy command to upgrade your version
py -3 -m pip install --upgrade robotpy
```

```bash
# Install project's dependancies
py -3 -m robotpy sync
```

> I got a lot of issues with my python packages since they were previously installed globally. If you encounter any issues with the install, try running this command `py -3 -m pip freeze | ForEach-Object { py -3 -m pip uninstall -y $_ }` to uninstall all of your packages. Then, rerun the installation steps above.

**For Linux and macOS**

```bash
# Uninstall old version of robotpy
python3 -m pip uninstall robotpy
```

```bash
# Install robotpy
python3 -m pip install robotpy

# You can use the --upgrade flag before the robotpy command to upgrade your version
python3 -m pip install --upgrade robotpy
```

```bash
# Install project's dependancies
python3 -m robotpy sync
```

### **Optional:** Creating an Alias

Through the season we're going to be typing `py -3 -m` A LOT. In order to simplify things, we can create an alias for this command.

**Windows:**
1. Open your terminal (In VsCode press `~`, or press the windows key and search for `cmd`)
2. Check if you already have a windows profile file by typing `$PROFILE` in your terminal.
  - If the file doesn't exist create it with `New-Item -Path $PROFILE -ItemType File -Force` 
3. Open the file by using `code $PROFILE`
4. Insert and save this block of code in the file:
    ```ps1
    Set-Alias cl clear
    
    Function pym {
        py -3 -m $args
    }
    ```
5. Reload the profile file by using `. $PROFILE`
6. Now instead of typing `py -3 -m` you can simply use the much shorter command `pym`.
    
> If you get an error saying "running scripts is disabled on this system", use this command to change windows execution policy: `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`

Here's an example of how you'd use the command before and after adding the alias:
- Before: `py -3 -m pip install robotpy`
- After: `pym pip install robotpy`

## Configuring Hardware

In order to complete these steps, you will need to [install the FRC Game Tools](#installing-frc-game-tools).

### RoboRIO Image Update

The FRC 2026 season will require all RoboRIOs to be flashed with a new image. To update the RoboRIOs, please follow the [guide](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-3/index.html) depending on what version of RIO you have.

[**RoboRIO 2.0**](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-3/roborio2-imaging.html)

<img src="./static/roborio_2.png" width="400" height="400">

---

[**RoboRIO 1.0**](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-3/imaging-your-roborio.html)

<img src="./static/roborio_1.png" width="400" height="400">

### Programming the Radio

Similar to the RoboRIO, the radio used to communicate with the bot must also be flashed with the latest firmware. Follow [this guide](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-3/radio-programming.html) to do so.