# Hyper-V (Hypervisor)

Introduction to Hyper-V on Windows 10
06/25/2018
3 minutes to read






+1
Whether you are a software developer, an IT professional, or a technology enthusiast, many of you need to run multiple operating systems. Hyper-V lets you run multiple operating systems as virtual machines on Windows.

Virtual machine running Windows

Hyper-V specifically provides hardware virtualization. That means each virtual machine runs on virtual hardware. Hyper-V lets you create virtual hard drives, virtual switches, and a number of other virtual devices all of which can be added to virtual machines.

Reasons to use virtualization
Virtualization allows you to:

Run software that requires an older versions of Windows or non-Windows operating systems.

Experiment with other operating systems. Hyper-V makes it very easy to create and remove different operating systems.

Test software on multiple operating systems using multiple virtual machines. With Hyper-V, you can run them all on a single desktop or laptop computer. These virtual machines can be exported and then imported into any other Hyper-V system, including Azure.

System requirements
Hyper-V is available on 64-bit versions of Windows 10 Pro, Enterprise, and Education. It is not available on the Home edition.

Upgrade from Windows 10 Home edition to Windows 10 Pro by opening Settings > Update and Security > Activation. Here you can visit the store and purchase an upgrade.

Most computers run Hyper-V, however each virtual machine runs a completely separate operating system. You can generally run one or more virtual machines on a computer with 4GB of RAM, though you'll need more resources for additional virtual machines or to install and run resource intense software like games, video editing, or engineering design software.

For more information about Hyper-V's system requirements and how to verify that Hyper-V runs on your machine, see the Hyper-V Requirements Reference.

Operating systems you can run in a virtual machine
Hyper-V on Windows supports many different operating systems in a virtual machine including various releases of Linux, FreeBSD, and Windows.

As a reminder, you'll need to have a valid license for any operating systems you use in the VMs.

For information about which operating systems are supported as guests in Hyper-V on Windows, see Supported Windows Guest Operating Systems and Supported Linux Guest Operating Systems.

Differences between Hyper-V on Windows and Hyper-V on Windows Server
There are some features that work differently in Hyper-V on Windows than they do in Hyper-V running on Windows Server.

Hyper-V features only available on Windows Server:

Live migration of virtual machines from one host to another
Hyper-V Replica
Virtual Fiber Channel
SR-IOV networking
Shared .VHDX
Hyper-V features only available on Windows 10:

Quick Create and the VM Gallery
Default network (NAT switch)
The memory management model is different for Hyper-V on Windows. On a server, Hyper-V memory is managed with the assumption that only the virtual machines are running on the server. In Hyper-V on Windows, memory is managed with the expectation that most client machines are running software on host in addition to running virtual machines.

Limitations
Programs that depend on specific hardware will not work well in a virtual machine. For example, games or applications that require processing with GPUs might not work well. Also, applications relying on sub-10ms timers such as live music mixing applications or high precision times could have issues running in a virtual machine.

In addition, if you have Hyper-V enabled, those latency-sensitive, high-precision applications may also have issues running in the host. This is because with virtualization enabled, the host OS also runs on top of the Hyper-V virtualization layer, just as guest operating systems do. However, unlike guests, the host OS is special in that it has direct access to all the hardware, which means that applications with special hardware requirements can still run without issues in the host OS.

Next step
Install Hyper-V on Windows 10

Install Hyper-V on Windows 10
02/15/2019
2 minutes to read






+5
Enable Hyper-V to create virtual machines on Windows 10.
Hyper-V can be enabled in many ways including using the Windows 10 control panel, PowerShell or using the Deployment Imaging Servicing and Management tool (DISM). This documents walks through each option.

Note: Hyper-V is built into Windows as an optional feature -- there is no Hyper-V download.

Check Requirements
Windows 10 Enterprise, Pro, or Education
64-bit Processor with Second Level Address Translation (SLAT).
CPU support for VM Monitor Mode Extension (VT-c on Intel CPUs).
Minimum of 4 GB memory.
The Hyper-V role cannot be installed on Windows 10 Home.

Upgrade from Windows 10 Home edition to Windows 10 Pro by opening up Settings > Update and Security > Activation.

For more information and troubleshooting, see Windows 10 Hyper-V System Requirements.

Enable Hyper-V using PowerShell
Open a PowerShell console as Administrator.

Run the following command:

PowerShell

Copy
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
If the command couldn't be found, make sure you're running PowerShell as Administrator.

When the installation has completed, reboot.

Enable Hyper-V with CMD and DISM
The Deployment Image Servicing and Management tool (DISM) helps configure Windows and Windows images. Among its many applications, DISM can enable Windows features while the operating system is running.

To enable the Hyper-V role using DISM:

Open up a PowerShell or CMD session as Administrator.

Type the following command:

PowerShell

Copy
DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V
Console window showing Hyper-V being enabled.

For more information about DISM, see the DISM Technical Reference.

Enable the Hyper-V role through Settings
Right click on the Windows button and select ‘Apps and Features’.

Select Programs and Features on the right under related settings.

Select Turn Windows Features on or off.

Select Hyper-V and click OK.

Windows programs and features dialogue box

When the installation has completed you are prompted to restart your computer.

Make virtual machines
Create your first virtual machine


Create a virtual network
05/02/2016
3 minutes to read






+2
Your virtual machines will need a virtual network to share a network with your computer. Creating a virtual network is optional -- if your virtual machine doesn't need to be connected to the internet or a network, skip ahead to creating a Windows Virtual Machine.

Connect virtual machines to the internet
Hyper-V has three types of virtual switches -- external, internal, and private. Create an external switch to share your computer's network with the virtual machines running on it.

This exercise walks through creating an external virtual switch. Once completed, your Hyper-V host will have a virtual switch that can connect virtual machines to the internet through your computer's network connection.

Create a Virtual Switch with Hyper-V Manager
Open Hyper-V Manager. A quick way to do this is by hitting the Windows button or key then type "Hyper-V Manager".
If search doesn't find Hyper-V Manager, Hyper-V or the Hyper-V management tools are not enabled. See the instructions to enable Hyper-V.

Select the server in the left pane, or click "Connect to Server..." in the right pane.

In Hyper-V Manager, select Virtual Switch Manager... from the 'Actions' menu on the right.

Under the 'Virtual Switches' section, select New virtual network switch.

Under 'What type of virtual switch do you want to create?', select External.

Select the Create Virtual Switch button.

Under ‘Virtual Switch Properties’, give the new switch a name such as External VM Switch.

Under ‘Connection Type’, ensure that External Network has been selected.

Select the physical network card to be paired with the new virtual switch. This is the network card that is physically connected to the network.



Select Apply to create the virtual switch. At this point you will most likely see the following message. Click Yes to continue.



Select OK to close the Virtual Switch Manager Window.

Create a Virtual Switch with PowerShell
The following steps can be used to create a virtual switch with an external connection using PowerShell.

Use Get-NetAdapter to return a list of network adapters connected to the Windows 10 system.

PowerShell

Copy
PS C:\> Get-NetAdapter

Name                      InterfaceDescription                    ifIndex Status       MacAddress             LinkSpeed
----                      --------------------                    ------- ------       ----------             ---------
Ethernet 2                Broadcom NetXtreme 57xx Gigabit Cont...       5 Up           BC-30-5B-A8-C1-7F         1 Gbps
Ethernet                  Intel(R) PRO/100 M Desktop Adapter            3 Up           00-0E-0C-A8-DC-31        10 Mbps  
Select the network adapter to use with the Hyper-V switch and place an instance in a variable named $net.

PowerShell

Copy
$net = Get-NetAdapter -Name 'Ethernet'
Execute the following command to create the new Hyper-V virtual switch.

PowerShell

Copy
New-VMSwitch -Name "External VM Switch" -AllowManagementOS $True -NetAdapterName $net.Name
Virtual networking on a laptop
NAT networking
Network Address Translation (NAT) gives a virtual machine access to your computer's network by combining the host computer's IP address with a port through an internal Hyper-V Virtual Switch.

This has a few useful properties:

NAT Conserves IP addresses by mapping an external IP address and port to a much larger set of internal IP addresses.
NAT allows multiple virtual machines to host applications that require identical (internal) communication ports by mapping these to unique external ports.
NAT uses an internal switch -- creating an internal switch doesn't cause you to use network connection and tends to interfere less with a computer's networking.
To set up a NAT network and connect it to a virtual machine, follow the NAT networking user guide.

The two switch approach
If you’re running Windows 10 Hyper-V on a laptop and frequently switch between wireless networking and a wired network, you may want to create a virtual switch for both the ethernet and wireless network cards. Depending on how the laptop connects to the network, you can change your virtual machines between these switches. Virtual machines do not switch between wired and wireless automatically.

 Important

The two switch approach does not support External vSwitch over wireless card and should be used for testing purposes only.

Next Step - Create a Virtual Machine
Create a Windows Virtual Machine

Create Virtual Machine with Hyper-V on Windows 10
05/02/2016
4 minutes to read



Learn how to create a virtual machine and install an operating system in your new virtual machine. You will need an .iso file for the operating system that you would like to run. If needed, grab an evaluation copy of Windows 10 from the TechNet Evaluation Center.

Create a Virtual Machine with Hyper-V Manager
Open Hyper-V Manager by either pressing the Window's key and typing "Hyper-V Manager" or by finding Hyper-V Manager in your applications.

In Hyper-V Manager, click Action > New > Virtual Machine to bring up the New Virtual Machine Wizard.

Review the ‘Before You Begin’ content and click Next.

Give the virtual machine a name.

Note: This is the name Hyper-V uses for the virtual machine, not the computer name given to the guest operating system that will be deployed inside the virtual machine.

Choose a location where the virtual machine files will be stored such as c:\virtualmachine. You can also accept the default location. Click Next when done.


Select a generation for the machine and click Next.
Generation 2 virtual machines were introduced with Windows Server 2012 R2 and provide a simplified virtual hardware model and some additional functionality. You can only install a 64-bit operating system on a Generation 2 virtual machine. For more information on Generation 2 virtual machines, see the Generation 2 Virtual Machine Overview.

If the new virtual machine is configured as Generation 2 and will be running a Linux distribution, secure boot will need to be disabled. For more information on secure boot, see Secure Boot.

Select 2048 MB for the Startup Memory value and leave Use Dynamic Memory selected. Click the Next button.
Memory is shared between a Hyper-V host and the virtual machine running on the host. The number of virtual machines that can run on a single host is in part dependent on available memory. A virtual machine can also be configured to use Dynamic Memory. When enabled, dynamic memory reclaims unused memory from the running virtual machine. This allows more virtual machines to run on the host. For more information on Dynamic Memory, see the Hyper-V Dynamic Memory Overview.

On the Configure Networking wizard, select a virtual switch for the virtual machine and click Next. For more information, see Create a Virtual Switch.

Give the virtual hard drive a name, select a location or keep the default, and finally specify a size. Click Next when ready.

A virtual hard drive provides storage for a virtual machine similar to a physical hard drive. A virtual hard drive is required so that you can install an operating system on the virtual machine.



On the Installation Options wizard, select Install an operating system from a bootable image file and then select an operating system .iso file. Click Next once completed.
When creating a virtual machine, you can configure some operating system installation options. The three options available are:

Install an operating system later – this option makes no additional modification to the virtual machine.

Install an operating system from a bootable image file – this is similar to inserting a CD into the physical CD-ROM drive of a physical computer. To configure this option, select a .iso image. This image will be mounted to the virtual CD-ROM drive of the virtual machine. The boot order of the virtual machine is changed to boot first from the CD-ROM drive.

Install an operating system from a network-based installation server – This option is not available unless you have connected the virtual machine to a network switch. In this configuration, the virtual machine attempts to boot from the network.

Review the virtual machine details and click Finish to complete the virtual machine creation.
Create a Virtual Machine with PowerShell
Open up the PowerShell ISE as Administrator.

Run the following script.

PowerShell

Copy
# Set VM Name, Switch Name, and Installation Media Path.
$VMName = 'TESTVM'
$Switch = 'External VM Switch'
$InstallMedia = 'C:\Users\Administrator\Desktop\en_windows_10_enterprise_x64_dvd_6851151.iso'

# Create New Virtual Machine
New-VM -Name $VMName -MemoryStartupBytes 2147483648 -Generation 2 -NewVHDPath "D:\Virtual Machines\$VMName\$VMName.vhdx" -NewVHDSizeBytes 53687091200 -Path "D:\Virtual Machines\$VMName" -SwitchName $Switch

# Add DVD Drive to Virtual Machine
Add-VMScsiController -VMName $VMName
Add-VMDvdDrive -VMName $VMName -ControllerNumber 1 -ControllerLocation 0 -Path $InstallMedia

# Mount Installation Media
$DVDDrive = Get-VMDvdDrive -VMName $VMName

# Configure Virtual Machine to Boot from DVD
Set-VMFirmware -VMName $VMName -FirstBootDevice $DVDDrive
Complete the Operating System Deployment
In order to finish building your virtual machine, you need to start the virtual machine and walk through the operating system installation.

In Hyper-V Manager, double-click on the virtual machine. This launches the VMConnect tool.

In VMConnect, click on the green Start button. This is like pressing the power button on a physical computer. You may be prompted to ‘Press any key to boot from CD or DVD’. Go ahead and do so.

Note: You may need to click inside the VMConnect window to ensure that your keystrokes are sent to the virtual machine.

The virtual machine boots into setup and you can walk through the installation like you would on a physical computer.

