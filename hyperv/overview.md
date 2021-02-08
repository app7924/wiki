## Hyper-V: Overview

Hyper-V is a virtualization platform by Microsoft. It lets you create and run a software version of a computer, called a virtual machine

. Each virtual machine acts like a complete computer, running an operating system and programs

. When you need computing resources, virtual machines give you more flexibility, help save time and money, and are a more efficient way to use hardware than just running one operating system on physical hardware
.

Hyper-V runs each virtual machine in its own isolated space, which means you can run more than one virtual machine on the same hardware at the same time.

 You might want to do this to avoid problems such as a crash affecting the other workloads, or to give different people, groups or services access to different systems
 .

Some ways Hyper-V can help you
Hyper-V can help you:

Establish or expand a private cloud environment
. Provide more flexible, on-demand IT services by moving to or expanding your use of shared resources and adjust utilization as demand changes
.

Use your hardware more effectively

. Consolidate servers and workloads onto fewer, more powerful physical computers to use less power and physical space
.

Improve business continuity

. Minimize the impact of both scheduled and unscheduled downtime of your workloads.

Establish or expand a virtual desktop infrastructure (VDI)

. Use a centralized desktop strategy with VDI can help you increase business agility and data security, as well as simplify regulatory compliance and manage desktop operating systems and applications

. Deploy Hyper-V and Remote Desktop Virtualization Host (RD Virtualization Host) on the same server to make personal virtual desktops or virtual desktop pools available to your users
.

Make development and test more efficient

. Reproduce different computing environments without having to buy or maintain all the hardware you'd need if you only used physical systems
.

Hyper-V and other virtualization products

Hyper-V in Windows and Windows Server replaces older hardware virtualization products, such as Microsoft Virtual PC, Microsoft Virtual Server, and Windows Virtual PC
. Hyper-V offers networking, performance, storage and security features not available in these older products
.

Hyper-V and most third-party virtualization applications that require the same processor features aren't compatible

. That's because the processor features, known as hardware virtualization extensions, are designed to not be shared

. For details, see Virtualization applications do not work together with Hyper-V, Device Guard, and Credential Guard
.

What features does Hyper-V have?
Hyper-V offers many features

. This is an overview, grouped by what the features provide or help you do.

Computing environment - A Hyper-V virtual machine includes the same basic parts as a physical computer, such as memory, processor, storage, and networking

. All these parts have features and options that you can configure different ways to meet different needs

. Storage and networking can each be considered categories of their own, because of the many ways you can configure them
.

Disaster recovery and backup - For disaster recovery, Hyper-V Replica creates copies of virtual machines, intended to be stored in another physical location, so you can restore the virtual machine from the copy

. For backup, Hyper-V offers two types

. One uses saved states and the other uses Volume Shadow Copy Service (VSS) so you can make application-consistent backups for programs that support VSS
.

Optimization - Each supported guest operating system has a customized set of services and drivers, called integration services, that make it easier to use the operating system in a Hyper-V virtual machine
.

Portability - Features such as live migration, storage migration, and import/export make it easier to move or distribute a virtual machine
.

Remote connectivity - Hyper-V includes Virtual Machine Connection, a remote connection tool for use with both Windows and Linux

. Unlike Remote Desktop, this tool gives you console access, so you can see what's happening in the guest even when the operating system isn't booted yet
.

Security - Secure boot and shielded virtual machines help protect against malware and other unauthorized access to a virtual machine and its data
.

For a summary of the features introduced in this version, see What's new in Hyper-V on Windows Server

. Some features or parts have a limit to how many can be configured

. For details, see Plan for Hyper-V scalability in Windows Server 2016.