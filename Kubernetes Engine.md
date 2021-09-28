# Kubernetes Engine

## A short history lesson

First a small history lesson to motivate the usage of containers:

Back in the day, web apps where build and deployed on individual physical servers. When you needed to scale up, you needed a new computer. Apps were also not very portable since the setup of tailor-made for a specific type of system. If you wanted to deploy an app, you needed to get a physical computer, install the OS, all dependencies and finally the app itself. As you can imagine, this approach required a lot of resources and effort to deploy and scale apps. 

Then came virtual machines. Instead of using a physical machine for a single server you can run multiple VMs on one physical machine, improving scaleability, portability and reducing costs for hardware. Deployment now merely took minutes. But VMs have low isolation, VMs compete for hardware resources with each other, and are tied to the host OS. They still scale badly, since each VM requires its own OS and dependencies, even if they are the same for all apps. Booting up a VM equals booting up an OS, which is still relatively slow.

Then came containers. Containers are not as isolated as VMs, they use host resources like the OS as much as possible, they don't carry full OS like a VM. When starting a Container, you start the process of your application, not booting up an entire OS, improving startup time.

On GCP, you will combine the best of the VM and Container world by running Containers within VMs.

## Images

Images in the context of containers are blueprints for containers.

### Building images with Docker and Cloud Build

## Container Registry



## Summary

### Docker commands

