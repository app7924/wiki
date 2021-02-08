
How to get Hyper-V
Hyper-V is available in Windows Server and Windows, as a server role available for x64 versions of Windows Server. For server instructions, see Install the Hyper-V role on Windows Server. On Windows, it's available as feature in some 64-bit versions of Windows. It's also available as a downloadable, standalone server product, Microsoft Hyper-V Server.

Supported operating systems
Many operating systems will run on virtual machines. In general, an operating system that uses an x86 architecture will run on a Hyper-V virtual machine. Not all operating systems that can be run are tested and supported by Microsoft, however. For lists of what's supported, see:

Supported Linux and FreeBSD virtual machines for Hyper-V on Windows

Supported Windows guest operating systems for Hyper-V on Windows Server

How Hyper-V works
Hyper-V is a hypervisor-based virtualization technology. Hyper-V uses the Windows hypervisor, which requires a physical processor with specific features. For hardware details, see System requirements for Hyper-V on Windows Server.

In most cases, the hypervisor manages the interactions between the hardware and the virtual machines. This hypervisor-controlled access to the hardware gives virtual machines the isolated environment in which they run. In some configurations, a virtual machine or the operating system running in the virtual machine has direct access to graphics, networking, or storage hardware.

What does Hyper-V consist of?
Hyper-V has required parts that work together so you can create and run virtual machines. Together, these parts are called the virtualization platform. They're installed as a set when you install the Hyper-V role. The required parts include Windows hypervisor, Hyper-V Virtual Machine Management Service, the virtualization WMI provider, the virtual machine bus (VMbus), virtualization service provider (VSP) and virtual infrastructure driver (VID).

Hyper-V also has tools for management and connectivity. You can install these on the same computer that Hyper-V role is installed on, and on computers without the Hyper-V role installed. These tools are:

Hyper-V Manager
Hyper-V module for Windows PowerShell
Virtual Machine Connection (sometimes called VMConnect)
Windows PowerShell Direct
