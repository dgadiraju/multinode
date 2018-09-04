# multinode
This is to create multiple virtual machines using vagrant script

# Reference video
* We have demonstrated as part of video in YouTube channel
* You can watch the video from this [blog post](https://kaizen.itversity.com/courses/linux-fundamentals-for-software-professionals/lessons/session-11-setup-virtual-environment-using-virtual-box-and-vagrant/)

# Instructions on Server with Linux, KVM, libvirt and Vagrant
* Clone the repository
* Make necessary changes to manifest.yml
* It can create up to 10 virtual machines
* Here are the default settings in manifest.yml
```
---
  instances: 7
  provider: libvirt
  name_prefix: server0
  name_suffix: .itversity.com
  ip_prefix: 192.168.100.20
  storage_devices: 2
  disk_size: 60G
  memory: 2048
  cpus: 2
  box: centos/7
  path: bootstrap.sh
```
* This will create 7 virtual machines from 192.168.100.200 to 192.168.100.206
* Each virtual machine is of size 8 GB memory and 2 CPUs
* Each virtual machine will be created with 2 virtual hard drives which can expand up to 60 GB each using libvirt
* Values related to virtual hard drives are hardcoded and hence make sure to understand side effects if you use to create them on local PC. 

# Instructions on PC or Mac with Windows or Mac OS, virtualbox and vagrant
* Clone the repository
* Make necessary changes to manifest.yml
* It can create up to 10 virtual machines
* Make sure to update instances to 2 or 3 based up on the capacity of your PC or Mac.
* Change the provider to virtualbox
* Here is the example manifest file where 3 virtual machines will be created.
```
---
  instances: 3
  provider: virtualbox
  name_prefix: server0
  name_suffix: .itversity.com
  ip_prefix: 192.168.100.20
  storage_devices: 2
  disk_size: 60G
  memory: 2048
  cpus: 2
  box: centos/7
  path: bootstrap.sh
```
* This will create 7 virtual machines from 192.168.100.200 to 192.168.100.206
* Each virtual machine is of size 8 GB memory and 2 CPUs
* Additional storage will not be added
* Values related to virtual hard drives are hardcoded and hence make sure to understand side effects if you use to create them on local PC. 
