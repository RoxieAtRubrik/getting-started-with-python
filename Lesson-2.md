# Lesson 2: Setting Variables and Authenticating

This lesson will walk you through setting environment variables and authenticating to a Rubrik cluster using Python.

## Authenticating to a Rubrik Cluster

Open command prompt and type:

```
py -3
```

Now we need to define some variables that are required for connecting to our Rubrik cluster.

There are three variables required for authenticating:

* `node_ip` - the IP address of the Rubrik cluster
* `username` - username, which is admin in this case
* `password` - password for admin

This information can be found by accessing the [Lab Topology](/lab-topology.md). Now, import the Rubik CDM module in Python so the Rubrik cluster functions can be called and then specify variables:

```
import rubrik_cdm

node_ip = "192.168.2.150"
username = "admin"
password = "Rubrik123!!"

rubrik = rubrik_cdm.Connect(node_ip, username, password)
```

| **Note**: A module is a Python object with arbitrarily named attributes that you can bind and reference. Or in simple way a module is a file consisting of Python code. A module can define functions, classes and variables. A module can also include runnable code. |
| --- |

```

Next check the version of our Rubrik cluster by calling the function to get the version:

```
cluster_version = rubrik.cluster_version()
```

The output should return something similar to the following:

```
[DEBUG] -- cluster_version: getting the software version of the Rubrik cluster.
[DEBUG] -- GET https://192.168.2.150/api/v1/cluster/me/version
[DEBUG] -- <Response [200]>
```

Notice the GET call and the status code response of 200 being returned. A 2xx response means it was a successful call.

Now we display the version:

```
print(cluster_version)
```

The cluster version returned should resemble the following:

```
4.2.0-p2-1102
```