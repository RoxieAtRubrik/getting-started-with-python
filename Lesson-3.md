# Lesson 3: Using the Rubrik SDK for Python

This lesson will walk you through a few common workflows for managing Rubrik CDM using Python. 

## Take an On-Demand Snapshot

Next, take an on-demand snapshot of the Windows VM.
First we are going to define the VM name and object type. This example uses a vSphere VM:

```
vm_name = "windows-2016"
object_type = "vmware"
```

Then call the snapshot function for that VM:

```
snapshot = rubrik.on_demand_snapshot(vm_name, object_type)
```

The output should return something similar to:

```
[DEBUG] -- on_demand_snapshot: Searching the Rubrik cluster for the vSphere VM 'win2016-vm1'.
[DEBUG] -- object_id: Getting the object id for the vmware object 'win2016-vm1'.
[DEBUG] -- GET https://192.168.2.150/api/v1/vmware/vm?primary_cluster_id=local&is_relic=false&name=win2016-vm1
[DEBUG] -- <Response [200]>

[DEBUG] -- on_demand_snapshot: Searching the Rubrik cluster for the SLA Domain assigned to the vSphere VM 'win2016-vm1'.
[DEBUG] -- GET https://192.168.2.150/api/v1/vmware/vm/VirtualMachine:::7644cc5f-f718-4177-8630-1fe4428fa1c6-vm-979
[DEBUG] -- <Response [200]>

[DEBUG] -- on_demand_snapshot: Initiating snapshot for the vSphere VM 'win2016-vm1'.
[DEBUG] -- POST https://192.168.2.150/api/v1/vmware/vm/VirtualMachine:::7644cc5f-f718-4177-8630-1fe4428fa1c6-vm-979/snapshot
[DEBUG] -- Config: {"slaId": "41f69fcb-d316-4c75-b63a-a2ad0596d17f"}
[DEBUG] -- <Response [202]>
```

You can see that this resulted in two GET calls and one POST. All 3 calls should be successful.

Log into the Rubrik Cluster UI and verify that an on-demand snapshot has begun. The cluster URL and credentials can be found by accessing [Lab Topology](/lab-topology.md).

## Live Mount a VM

To Live Mount a virtual machine, begin by defining the VM name:

```
vm_name1 = "ubuntu-lamp"
```

and then call the Live Mount function:

```
live_mount = rubrik.vsphere_live_mount(vm_name1)
```

The output should look similar to the following:

```
[DEBUG] -- vsphere_live_mount: Searching the Rubrik cluster for the vSphere VM 'centos7-vm1'.
[DEBUG] -- object_id: Getting the object id for the vmware object 'centos7-wv1'.
[DEBUG] -- GET https://192.168.2.150/api/v1/vmware/vm?primary_cluster_id=local&is_relic=false&name=centos7-wv1
[DEBUG] -- <Response [200]>

[DEBUG] -- vsphere_live_mount: Getting a list of all Snapshots for vSphere VM 'centos7-vm1'.
[DEBUG] -- GET https://192.168.2.150/api/v1/vmware/vm/VirtualMachine:::7644cc5f-f718-4177-8630-1fe4428fa1c6-vm-979
[DEBUG] -- <Response [200]>

[DEBUG] -- vsphere_live_mount: Live Mounting the snapshot taken on latest at latest for vSphere VM 'centos7-vm1'.
[DEBUG] -- POST https://192.168.2.150/api/v1/vmware/vm/snapshot/3ec9e413-651d-491b-a0c8-03c186300d28/mount
[DEBUG] -- Config: {"powerOn": true, "hostId": "VmwareHost:::7644cc5f-f718-4177-8630-1fe4428fa1c6-host-29", "removeNetworkDevices": false}
[DEBUG] -- <Response [202]>
```

You can see for each one of these VMs, there are two GET calls to gather the information needed to then conduct one POST call to send the Live Mount request.

Switch to the Windows Jumpbox both on vCenter and Rubrik CDM and verify Live Mount. Lab topology information can be found [here](/lab-topology.md).

## SLA Domain Assignments

As last exercise, we are going to get the list of all object in our Gold SLA:

```
vms_in_sla = rubrik.get_sla_objects(“Gold”,”vmware”)
```


The reponse should resemble: 

```
[DEBUG] -- <Response [200]>
```

To view the list of VMs, type: 

```
print(vms_in_sla)
```

## Documentation

For more information, please see the Rubrik SDK for Python [Documentation](https://rubrik.gitbook.io/rubrik-sdk-for-python/) and the [GitHub Repository](https://github.com/rubrikinc/rubrik-sdk-for-python).
