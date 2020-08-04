# Lesson 1: Preparing the Lab

To prepare for this module's lab, you will need to install Python, `pip`, and set up a virtual environment.

In the lab environment, switch to your Linux VM. To do so, click the **TightVNC Viewer** icon on the jumpbox desktop. 

![](https://user-images.githubusercontent.com/29388592/89324611-68a13a80-d63c-11ea-96b8-c0a507e8d33c.png)

Click **Connect** and enter the lab password.

![](https://user-images.githubusercontent.com/29388592/89324685-8a022680-d63c-11ea-971e-e2c2aed75404.png)

Once authenticated, open up the terminal. 

![](https://user-images.githubusercontent.com/29388592/89324823-bcac1f00-d63c-11ea-8fe9-637809800f7b.png)

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
