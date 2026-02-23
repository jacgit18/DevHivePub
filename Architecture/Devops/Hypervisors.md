---
tags:
  - devops
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses what are Hypervisors.
Status: Done
Started: 
EditDate: 2024-02-22
Relates: 
Peer Reviewed: 0
dg-publish:
---
A hypervisor, also known as a virtual machine monitor (VMM), is a software or hardware component that enables the creation and management of virtual machines (VMs) on a physical computer or server. The primary purpose of a hypervisor is to allow multiple operating systems to run simultaneously on the same hardware, each within its isolated virtual environment. Here are some key points about hypervisors:  
  
1. **Virtualization**: Hypervisors enable virtualization, which is the abstraction of physical hardware resources into multiple virtual instances. These instances, or VMs, behave as if they are running on dedicated physical hardware, even though they share the underlying resources.  
  
2. **Types of Hypervisors**:  
	- **Type 1 Hypervisor (Bare-Metal)**: These hypervisors run directly on the physical hardware without the need for a host operating system. Examples include VMware vSphere/ESXi, Microsoft Hyper-V, and Xen.  
	- **Type 2 Hypervisor (Hosted)**: Type 2 hypervisors run on top of a host operating system. They are often used for development and testing purposes. Examples include Oracle VirtualBox and VMware Workstation.  
  
3. **Isolation**: Hypervisors provide strong isolation between VMs. Each VM operates independently and is unaware of the existence of other VMs running on the same physical host. This isolation is essential for security and stability.  
  
4. **Resource Allocation**: Hypervisors allocate physical resources, such as CPU, memory, storage, and network bandwidth, to VMs based on predefined configurations or dynamically as needed.  
  
5. **VM Management**: Hypervisors offer tools and interfaces for creating, configuring, starting, stopping, and migrating VMs. Administrators can manage VMs remotely and adjust resource allocations as required.  
  
6. **Snapshot and Cloning**: Many hypervisors support features like VM snapshots (a point-in-time copy of a VM) and cloning (creating identical copies of a VM). These features are useful for backup, testing, and development.  
  
7. **Live Migration**: Some hypervisors allow for live migration, which means moving a running VM from one physical host to another without interruption. This is valuable for load balancing and hardware maintenance.  
  
8. **Hardware Virtualization Support**: Modern CPUs often include hardware virtualization support (e.g., Intel VT-x or AMD-V) that enhances the performance and security of VMs when used with hypervisors.  
  
9. **Use Cases**: Hypervisors are widely used in data centers and cloud computing environments to consolidate multiple workloads onto a smaller number of physical servers, improving resource utilization and reducing hardware costs. They are also used for development, testing, and sandboxing environments.  
  
Hypervisors have played a significant role in the growth of virtualization technologies, allowing organizations to efficiently manage and optimize their IT infrastructure while maintaining high levels of security and isolation between workloads.