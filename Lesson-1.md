# Lesson 1: Preparing the Lab

To prepare for this module's lab, you will need to install Python, `pip`, and set up a virtual environment.

## Installing Python

Right-click Visual Studio Code and `Run as Administrator`. In the menu, go to **Terminal** > **New Terminal**. 

```
choco install python3
```

When prompted, specify `[Y]es` to run the script to install Python.

Once the install is successful, type:

```
py -3
```

Once you see the `>>>` means you are running an interactive Python interpreter. If you need to exit for any reason, use `CTRL + D` or `exit()`.

To type your first line of code, specify:

```
print("Python is fun!")
```

Hit **Enter**, you should see:

```
Python is fun!
```

Or do simple calculation:

```
4+7
```

In this case, disable security warning for self-signed certificates:

```
import urllib3
urllib3.disable_warnings()
```

Once done, you can use `exit()` to leave the Python Shell.

## Installing the Rubrik SDK for Python

There are two way we can install Rubrik SDK for Python:

* Using `pip`
* Downloading package and manually installing

The easiest way is to use `pip`. First, install `pip`:

```
choco install pip
```

When prompted, specify `[Y]es` to run the script to install `pip`.

```
pip install rubrik_cdm
```

Or you can download the package from the GitHub repository and install it:

```
git clone https://github.com/rubrikinc/rubrik-sdk-for-python
cd rubrik-sdk-for-python
python setup.py install
```

## Setting Up a Virtual Environment

A virtual environment is a tool that helps to keep dependencies required by different projects separate by creating isolated Python virtual environments.

In your Command Prompt navigate to your project:

```
cd $your_project
```

Run this command within your project:

```
virtualenv env
```

Activate your virtualenv, a batch file is created in Windows:

```
\env\Scripts\activate.bat
```

Example: `C:\Users\'Username'\venv\Scripts\activate.bat`