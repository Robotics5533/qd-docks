# Installation

## Installing Packages In Python

In order to run python on the robot, you need to install
the proper libraries on the robot

generally speaking python uses the package manager pip to install and
interact with libraries on the system.

We can tell pip to install a package with

```bash
pip install <package name>
```

we need to be careful though, since there are different versions
of python, different libraries might require that our python
version be at different values. That also means that pip might get
confused if we have more than one version of python on our machine
and accidentally install the wrong library.

In order to avoid this problem, we can run pip as a module inside of
an existing version of python to be CERTAIN that we are installing for
the right version. To run any python package as a module we can type

```bash
<python run command> -m <module name> [module arguments]
```

the run command to start your version of python will vary from
system to system but generally the interpreter commands will take
on the following forms

```bash
py3
python3
py -3
```

you will know you have the right command when you run it, and the python
shell appears in your terminal or command line

putting it all together, a full install command for a package could look like the following

```bash
python3 -m pip install numpy
```

I will use python3 in this documentation, as it is what my system uses,
but generally replace python3 with the command that will invoke python on 
your computer.


## Installing robotpy packages

The primary FIRST package python uses is called robotpy, this is the main code snippit
that we use to push code to and from the robot. 

We can install it with the following command.

```bash
python3 -m pip install robotpy
```

Now this isn't the ONLY library that we need for first, it contains the basics for sure, but since
LOTS of differen't people and companies supply FIRST with hardware, there are several third party
libraries that are also needed depending on what hardware you have on your robot.

## Installing Packages On The RoboRio


the basic setup for getting the robot working from the ground up can be found here:
[robotpy setup](https://docs.wpilib.org/en/latest/docs/zero-to-robot/step-2/python-setup.html)

note when creating pyproject.toml with robotpy init the commands2 package is not included in the generated output
to include the commands two package you can add "robotpy-commands-v2==2024.0.0b4" to the requires list. See
[robotpy github](https://robotpy.github.io/) for more information regaruding this.

Note that at the current moment commands2 is beta release so use at your own risk.

---

Note: if for whatever reason, the robotpy_version in your pyproject file is off, you can list out the version
of installed packages with

```bash
python3 -m pip freeze
```

you can then match the robotpy version in this output to the toml file manually.
