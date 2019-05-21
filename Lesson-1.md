# Lesson 1: Preparing the Lab

To prepare for this module's lab, you will need to install Python, `pip`, and set up a virtual environment.

In the lab environment, switch to your CentOS VM. To do so, click **Consoles** on the left hand of the VLP screen, scroll down, and click `CENTOS`. 

![](https://user-images.githubusercontent.com/47801550/58071945-733df400-7b9e-11e9-8188-7fd6e99ce9ec.png)

Select **Not Listed?** and type `root` as the username. 

![](https://user-images.githubusercontent.com/47801550/58072043-c021ca80-7b9e-11e9-857b-72e378f33e24.png)

Use the password listed in the [lab topology](/lab-topology.md). 

## Installing Python

(Optional) As a matter of good practice, first update packages:

```
yum -y update
```

(Optional) Next step would be install `yum-Utils`:

```
yum -y install yum-utils
```

| Note: `yum-utils` is a collection of utilities and plugins extending and supplementing yum in various ways. |
| --- |

Python 2.7 should have been installed on the CentOS VM. To verify:

```
python --version
```

Next, let's verify that `pip` is installed and using version 19.1.1:

```
pip --version
```

| Note: `pip` is a package management system used to install and manage software packages written in Python. |
| --- |

## Installing the Rubrik SDK for Python

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
