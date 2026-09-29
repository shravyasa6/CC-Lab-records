# CC-Lab-records
Performance Analysis of Type-1 and Type-2 Hypervisors
Executive Summary
This repository contains the experimental setup, benchmark results, performance visualizations, screenshots, and technical analysis for comparing a Type-1 Hypervisor (Proxmox VE) and a Type-2 Hypervisor (VMware Workstation).

Both environments were configured with comparable Ubuntu virtual machines using 2 vCPU, 2 GB RAM, and 20 GB virtual disk. The same sysbench CPU benchmark was executed using a prime-number calculation limit of 20,000.

Key Finding
Under the tested experimental conditions, Proxmox VE recorded 1,689.43 events/sec, while VMware Workstation recorded 983.84 events/sec. The measured average latency was 0.59 ms for Proxmox VE and 1.02 ms for VMware Workstation.

Table of Contents
Project Objectives
Hypervisor Architectural Comparison
Virtual Machine Specifications
Experimental Procedure
Empirical Results & Screenshots
Performance Comparison Table
Metric Explanations & Visualizations
Technical Analysis & Discussion
Conclusion & Engineering Takeaways
Repository Structure & Reproduction
1. Project Objectives
The primary objectives of this Cloud Computing laboratory experiment are:

Deployment: Configure Ubuntu virtual machines using two different hypervisor architectures:

Type-1: Proxmox VE
Type-2: VMware Workstation
Standardization: Use comparable virtual-machine resources:

2 vCPU
2 GB RAM
20 GB virtual disk
Benchmarking: Execute the sysbench CPU benchmark using a prime-number limit of 20,000.

Metric Collection: Record:

Total execution time
Total events
Events per second
Minimum latency
Average latency
Maximum latency
Architectural Evaluation: Compare the measured CPU performance and latency characteristics of the two virtualization environments.

2. Hypervisor Architectural Comparison
Type-1 Hypervisor — Proxmox VE
Proxmox VE is a virtualization platform based on Linux and KVM. In the experimental setup, the Ubuntu guest virtual machine operates through the Proxmox VE/KVM virtualization layer.

+-------------------------------------------------------------------+
|                 Ubuntu Virtual Machine                            |
|                                                                   |
|                 Sysbench CPU Benchmark                            |
+-------------------------------------------------------------------+
|                 Proxmox VE / KVM                                   |
|                    Type-1 Layer                                   |
+-------------------------------------------------------------------+
|                 Physical Host Hardware                             |
|                 CPU / RAM / Storage                                |
+-------------------------------------------------------------------+
Type-2 Hypervisor — VMware Workstation
VMware Workstation operates as a hosted virtualization application on a host operating system. The Ubuntu guest virtual machine runs through the VMware virtualization layer.

+-------------------------------------------------------------------+
|                 Ubuntu Virtual Machine                            |
|                                                                   |
|                 Sysbench CPU Benchmark                            |
+-------------------------------------------------------------------+
|                 VMware Workstation                                |
|                    Type-2 Layer                                   |
+-------------------------------------------------------------------+
|                 Host Operating System                              |
+-------------------------------------------------------------------+
|                 Physical Host Hardware                             |
|                 CPU / RAM / Storage                                |
+-------------------------------------------------------------------+
Architectural Difference
Feature	Proxmox VE	VMware Workstation
Hypervisor Type	Type-1	Type-2
Virtualization Layer	Proxmox VE / KVM	VMware Workstation
Host OS Dependency	Virtualization platform	Runs on host OS
Guest OS	Ubuntu 22.04.5 LTS	Ubuntu 22.04.5 LTS
CPU Benchmark	Sysbench CPU	Sysbench CPU
3. Virtual Machine Specifications
To make the benchmark comparison meaningful, the virtual machines were configured with comparable resources.

Resource Parameter	Proxmox VE (Type-1)	VMware Workstation (Type-2)	Status
Guest Operating System	Ubuntu 22.04.5 LTS x86_64	Ubuntu 22.04.5 LTS x86_64	Matched
CPU Allocation	2 vCPU	2 vCPU	Identical
RAM Allocation	2 GB	2 GB	Identical
Virtual Disk	20 GB	20 GB	Identical
Benchmark	sysbench cpu	sysbench cpu	Identical
CPU Prime Limit	20,000	20,000	Identical
4. Experimental Procedure
Step 1: Virtual Machine Configuration
The virtual machines were configured using comparable resource allocations.

Proxmox VE
Ubuntu 22.04.5 LTS guest
2 vCPU
2 GB RAM
20 GB virtual disk
Proxmox VE / KVM virtualization
VMware Workstation
Ubuntu 22.04.5 LTS guest
2 vCPU
2 GB RAM
20 GB virtual disk
VMware Workstation virtualization
Step 2: System Configuration Verification
The following commands were used inside the Ubuntu guest systems:

hostnamectl
lscpu
free -h
df -h
top
These commands were used to verify:

Command	Purpose
hostnamectl	Operating system and system information
lscpu	CPU architecture and processor information
free -h	RAM and swap information
df -h	Disk-space information
top	Real-time system and process monitoring
Step 3: Sysbench Installation
sudo apt update
sudo apt install sysbench -y
Step 4: Verify Sysbench
sysbench --version
Step 5: Execute CPU Benchmark
The same benchmark command was executed in both virtual machines:

sysbench cpu --cpu-max-prime=20000 run
The same workload was used in both environments to allow comparison of the measured performance.

