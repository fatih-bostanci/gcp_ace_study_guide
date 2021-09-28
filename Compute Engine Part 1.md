# Compute Engine Part 1

In this chapter we will learn ...

* what Virtual Machines are
* how to create VMs on GCP
* how to connect to them
* and run commands on them using the Bash command line interface



## What is a Virtual Machine



## Virtual Machines on GCP

We will show how VMs work on GCP by going through the creation process on the console.

Go to: **Navigation > Compute Engine > VM instances > Create instance**

![goto_vm_instances](C:\Users\fatih.bostanci\Desktop\GCP_ACE_Unofficial_Study_Guide\Gifs\goto_vm_instances.gif) 

### Name, Labels, Region, Zone, Machine Configuration

![image-20210918182503837](C:\Users\fatih.bostanci\AppData\Roaming\Typora\typora-user-images\image-20210918182503837.png)

---

In the first field you have to enter the **name** of your VM. Names must start with a lowercase letter followed by up to 62 lowercase letters, numbers, or hyphens, and cannot end with a hyphen.

**Labels** are optional. They help you organizing your resources.

You have to pick a **region** and then a **zone** within that region, where your VM will reside. The region of your VM will factor into the costs, network latency as well as available resources.

Next you will configure your actual VM:

First you choose the **Machine Family** out of four options: General purpose, Compute optimized, Memory-optimized and GPU.

1. General-purpose offers different machine types with the best price-performance ratio for a variety of workloads
2. Compute-optimized machine family offers the highest performance per core on Compute Engine and are optimized for compute-intensive workloads
3. Memory-optimized offer more memory per core
4. GPU aka accelerator-optimized machines optimized for massive parallel operations

See [2] to read more about machine familes.

Depending on the chosen family you can pick a **Series** . See [3] for the details.

Finally you pick the concrete **Machine type** of your VM, which determines the number of CPUs and working memory of your machine.

Clicking on **CPU platform and GPU** expands further configuration options

---

![image-20210920152913842](C:\Users\fatih.bostanci\AppData\Roaming\Typora\typora-user-images\image-20210920152913842.png)

---

Depending on the **machine type** you may further specify the micro-architecture of your machine and add GPUs. If you want to use a display device and a GPU is overkill, you can *"turn on display device"* instead [4]

---

![image-20210920153736586](C:\Users\fatih.bostanci\AppData\Roaming\Typora\typora-user-images\image-20210920153736586.png)

---

For some machine types you can turn on *"Confidential VM service"* which will encrypt data in memory.

You can also provide a container image. We will talk more about containers in the Docker chapter, thus we'll skip the container options for now. What you should know for now is that checking the container box will limit your options when choosing a **boot disk**, which comes next.

### Boot Disk

---

![image-20210920154310306](C:\Users\fatih.bostanci\AppData\Roaming\Typora\typora-user-images\image-20210920154310306.png)

---

The boot disk contains the operating system of your machine. Some OS like linux are free, whereas Windows based OS incur further costs.

Clicking on *"change"* lets you configure your boot disk.

---

![image-20210925144310507](C:\Users\fatih.bostanci\AppData\Roaming\Typora\typora-user-images\image-20210925144310507.png)

---

You can create a new disk from custom and public images and snapshots. Alternatively you can attach a disk you have created earlier but didn't attach to another VM. 

The focus here is on creating new disks from public images.

When going with a public image, you can choose from a range of Linux and Windows operating systems. Keep in mind that some OS are not free !

You also have to pick a disk type and how much space in gigabyte you want the disk to have.

The available disk types are:

1. Balanced persistent disk
2. Extreme persistent disk
3. SSD persistent disk
4. Standard persistent disk

Again, we will go into more details in the respective chapter about block storage. 

---

![image-20210925191409546](C:\Users\fatih.bostanci\AppData\Roaming\Typora\typora-user-images\image-20210925191409546.png)

---

Clicking on "Show Advanced Configuration" in the public image tab of the boot disk configuration allows you to decide whether...

* the disk should be deleted if the attached VM is deleted, this can be changed later
* who manages encryption keys
* if you want to create regular backups of your disk
*  and if you want to give the disk a custom name







## Compute Engine Free Tier

The free tier for compute engine currently (2021-09-27) consists of the following:

> | 1 non-preemptible `e2-micro` VM instance per month in one of the following US regions:Oregon: `us-west1`Iowa: `us-central1`South Carolina: `us-east1`30 GB-months standard persistent disk 5 GB-month snapshot storage in the following regions:Oregon: `us-west1`Iowa: `us-central1`South Carolina: `us-east1`Taiwan: `asia-east1`Belgium: `europe-west1`1 GB network egress from North America to all region destinations (excluding China and Australia) per month |
> | ------------------------------------------------------------ |
> | Your Free Tier `e2-micro` instance limit is by time, not by instance. Each month, eligible use of all of your `e2-micro` instance is free until you have used a number of hours equal to the total hours in the current month. Usage calculations are combined across the supported [regions](https://cloud.google.com/compute/docs/regions-zones).Google Cloud Free Tier does not include external IP addresses.GPUs and TPUs are not included in the Free Tier offer. You are always charged for GPUs and TPUs that you add to VM instances. |

* Source: <a name="compute-free-tier-back" href=#compute-free-tier>[5]</a> 

Please double-check if this is still accurate and open an issue on github if it is not.

## Billing of Compute Engine

Depending on VM configuration per second

## Hands On: Create VMs

## Summary



### Google SDK Commands

You can read the details of each command with all possible flags in the official documentation.

| Commands                                                     | Description                                            |
| ------------------------------------------------------------ | ------------------------------------------------------ |
| gcloud compute instances create INSTANCE_NAME                | Creates a VM                                           |
| gcloud compute instances set-disk-auto-delete --zone=ZONE VM_NAME | Turn off auto-delete for the boot disk of the given VM |
|                                                              |                                                        |

### Bash commands

## Disks, Snapshots and Images

## Image Templates

## Quiz

1. What factors influencing the cost of virtual machines do you set during creation ? See [1] for hints.

## References

1. Pricing Calculator : https://cloud.google.com/products/calculator
2. Machine Family Categories : [https://cloud.google.com/compute/docs/machine-types#machine_types](https://cloud.google.com/compute/docs/machine-types#machine_types)
3. Machine Series Comparison: [https://cloud.google.com/compute/docs/machine-types#machine_type_comparison](https://cloud.google.com/compute/docs/machine-types#machine_type_comparison)
4. Enabling virtual displays : https://cloud.google.com/compute/docs/instances/enable-instance-virtual-display
5. <a name="compute-free-tier" href=#compute-free-tier-back> Compute Free Tier </a> : https://cloud.google.com/free/docs/gcp-free-tier/#compute

