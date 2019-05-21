# Lesson 2: Setting Variables and Authenticating

This lesson will walk you through setting environment variables and authenticating to a Rubrik cluster using Python.

## Defining Variables

Now we need to define some variables that are required for connecting to our Rubrik cluster.

There are three variables required for authenticating:

* `node_ip` - the IP address of the Rubrik cluster
* `username` - username, which is admin in this case
* `password` - password for admin

This information can be found by accessing the [Lab Topology](/lab-topology.md). Now, import the Rubik CDM module in Python so the Rubrik cluster functions can be called and then specify variables:

```
export rubrik_cdm_node_ip=192.168.2.150
export rubrik_cdm_username=admin
export rubrik_cdm_password='Rubrik123!!'
```

Use the echo command to show the value of the variables:

```
echo $rubrik_cdm_node_ip
echo $rubrik_cdm_username
echo $rubrik_cdm_password
```

To use SDK, define the Rubrik variable:

```
export rubrik='rubrik_cdm.Connect()'
```

To begin using Python, type:

```
python
```

Once you see the `>>>`, you are running an interactive Python interpreter.

If you need to exit, type `exit.()`.

Run a simple test:

```
print('Hello, world!')
```

And do simple calculation:

```
4+7
```

Next, disable security warning for self-signed certificate:

```
import urllib3
urllib3.disable_warnings()
```

## Connect to the Rubrik Cluster

Import the Rubik module in Python to use its functions:

```
import rubrik_cdm
```

| A module is a Python object with arbitrarily named attributes that you can bind and reference. Or in simple way a module is a file consisting of Python code. A module can define functions, classes and variables. A module can also include runnable code. |
| --- |

Connect to Rubrik cluster:

```
rubrik = rubrik_cdm.Connect(enable_logging=True)
```

You should see a respond similar to: 

```
[2019-05-04 17:30:30,867] [DEBUG] -- Node IP: 192.168.2.150
[2019-05-04 17:30:30,867] [DEBUG] -- Username: admin
[2019-05-04 17:30:30,867] [DEBUG] -- Password: *******
```

Next, check the version of the Rubrik cluster:

```
cluster_version = rubrik.cluster_version()
```

The return should resemble:

```
[DEBUG] -- cluster_version: Getting the software version of the Rubrik cluster.
[DEBUG] -- GET https://10.0.2.10/api/v1/cluster/me/version
[DEBUG] -- <Response [200]>
```

You can see that we are sending a GET call and getting 200 back, which means it was a successful call. 

Use print function to display the version:

```
print(cluster_version)
```

The cluster version should resemble: 

```
5.0.0-1234
```
