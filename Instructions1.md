#Exploring the Lab Environment

##Scenario

In this lab, you will familiarize yourself with the systems you will be using in this series of activities. 

##Using the Lab Interface

To complete most of the labs in this course, you will use one or more Virtual Machines (VMs) hosted on a cloud platform. Each VM works very much like a physical computer, but you access them via your browser. The main thing to remember is that your **WINDOWS**/**START** key will work _on your own computer_ not the VM. 

Take a few moments to familiarize yourself with some other features of the lab browser controls.

1. [] In this pane, select the **Resources** tab heading. When you have reviewed the Resources tab contents, select the **Instructions** tab to follow these steps again.
    
    The Resources area is used to show the VMs you have available to you plus any downloadable files that may be useful during a lab. You can choose a different ISO disc to load in each VM's DVD drive and also change the virtual network that the VM is connected to. You can also open each VM in a new window if you find it easier to switch between them that way.

1. [] Looking at the **Instructions** tab again, notice that each of these tasks has a check box for you to use to record your progress. As you complete each step, select the box to mark it as complete.

1. [] Select the **Help** tab. Select the **Instructions** tab to view these steps again afterwards.
    
    You can use the Help page to get assistance with technical issues and view more advanced information about using the lab interface.

    Also note that the Help tab features a zoom control to allow you to make these instructions appear in larger or smaller font. Finally, note the timer counting down below the lab title. You have the option of extending the lab when this reaches 10 minutes so do not worry too much about running out of time.

1. [] Looking at the pane containing the VM, in the top-left corner, select the **Display** icon !IMAGE[Screenshot of Display icon](lod%20icon%20display.png) and select **Full Screen**.

    Working in full screen mode is usually best because it allows the maximum possible screen resolution for the VM you are operating. The other options in this menu allow you to fit the VM screen to the browser window or refresh the display, if it does not seem to be updating.

1. [] If you are using a Windows computer to access these labs, press the **START** key on your keyboard. Notice that this activates the Taskbar on _your_ PC. In some browsers, this might also cause the lab environment to exit full screen mode.

1. [] If necessary, switch to Full Screen mode again then select the **Commands** icon !IMAGE[Screenshot of Commands icon](lod%20icon%20lightning.png) to open the menu—do not select anything from the menu yet.

    This menu allows you to send **START** key combinations and the **CTRL+ALT+DEL** key sequence _to the VM_. 
    
    There is also a virtual keyboard for use if you find you have trouble typing particular characters. The VMs use a US keyboard layout so if your own physical keyboard has a different layout you may find that some keys do not type the same symbols. 
    
    You can also use the **Power** menu to reset or turn off the VM. You should generally only do this if instructed.

1. [] Select the following @lab.CtrlAltDelete button embedded in the instructions. This activates sign-in on the Windows VM.

1. [] Now that you are familiar with the lab interface, let's look at the guest VMs you will be using. Select the **Next** button to continue.

===

##Explore Windows VMs

The Windows network contains a server subnet and a client subnet:

- @lab.VirtualMachine(DC10).Selectlink is configured as the network's domain controller (DC) and runs Windows Server 2019. Normally the DC role should not be combined with other roles, but to minimize the number of VMs you have to run, this machine is also configured as a DNS server, DHCP server, and CA (certificate authority) server. This VM is configured with a static IP address (10.1.0.1). 

- @lab.VirtualMachine(MS10).Selectlink is a Windows Server 2016 instance configured as a member server for running applications. It has the web server IIS and the email server hMail installed and will be used for a number of other services and configurations. This VM is also configured with a static IP address (10.1.0.2). 

- @lab.VirtualMachine(PC10).Selectlink is configured as a desktop client computer (though it is actually running Server 2019 for licensing reasons).

The +++515support\Administrator+++ account is the domain administrator, but you will often sign on to VMs using different accounts. Pay close attention to the account that you should use for any given task. Each user account uses the password +++Pa$$w0rd+++ (awful security practice, but it makes the activities simpler for you to complete). 

1. [] At each point in an activity, you should ensure that you are working within the correct virtual machine. The correct VM may usually be accessed by selecting a shortcut link in the instructions. For example, the MS1 VM is currently selected. To switch to the DC1 virtual machine, select @lab.VirtualMachine(DC10).SelectLink

    >[!TIP] Virtual machines may also be selected from a menu at the top of the lab user interface or from the **Resources** tab in this pane.

1. [] With the @lab.VirtualMachine(DC10).Selectlink VM active, select @lab.CtrlAltDelete and then select the password box. Select the icon preceeding the following text to autotype it +++Pa$$w0rd+++.

1. [] Press **ENTER** or select the arrow button to submit the password and log on.

1. [] Point to the network icon in the taskbar. The tooltip should read "corp.515support.com."

    >[!HINT] Note that the "No Internet access" warning is expected. The VMs do not have any access to the Internet by design.

  If a lab is not working as you expect, check that DC10 has identified the network link. If it is listed as "Unknown," disable and enable the adapter to reset it. Also verify that the DHCP service is running.

1. [] Right-click the **Start** button and select **Network Connections**. Select **Change adapter options**.

1. [] In the Network Connections console, right-click the **Ethernet** adapter and select **Disable**.

1. [] Right-click the **Ethernet** adapter and select **Enable**.

 The connection should be identified as "corp.515support.com."

1. [] In Server Manager, select **Tools > DHCP**. Expand the **dc10.corp.515support.com** server node.

    The IPv4 node should show with a green tick. If the network on DC10 has been listed as "Unknown," you may also need to restart the DHCP server to activate the scope.

1. [] Right-click the **dc10.corp.515support.com** server node, select **All Tasks**, and select **Restart**.

1. [] Right-click the **dc10.corp.515support.com** server node and select **Refresh**.
   
1. [] Select the **IPv4** node and confirm that it is shown with a green tick icon.

1. [] Switch to the @lab.VirtualMachine(PC10).Selectlink VM and select the following link to submit @lab.CtrlAltDelete and unlock the desktop. 

1. [] With the account +++Jaime+++ selected, enter the password +++Pa$$w0rd+++.

1. [] Point to the network icon in the taskbar. Again, the tooltip should read "corp.515support.com."

    In some tasks, you will be asked to install software or other resources from a DVD. The lab user interface can load DVD ISO images for you. 

1. [] Select this link @lab.OpticalMedia(14447).LoadLink to load a DVD in PC10's optical drive.

1. [] Open **File Explorer** from the taskbar and browse to the DVD drive. You should see the contents of the Windows Setup DVD.

1. [] Right-click **Start** and select **Windows PowerShell (Admin)** to open an elevated PowerShell prompt. Select **Yes** in the UAC prompt.

  The lab interface can automatically type commands for you when you are using Windows virtual machines. 

1. [] Select the following "T" icon: `hostname` and observe that the command is typed in the PowerShell console of the VM. Press **ENTER** to execute the command.

1. [] Enter `Get-NetIPAddress` to display the IP address configuration for each interface.

1. [] Enter `exit` to close PowerShell.

===

## Identify Linux Server VMs

There are also two Linux servers: 

 - @lab.VirtualMachine(SMB10).SelectLink is a Fedora Linux distribution ([getfedora.org](https://getfedora.org/)) that you will configure as a file server. As a server distribution, this VM has no GUI shell. This VM is positioned on the local network with the Windows Server VMs and has a DHCP reservation for the address <tt>10.1.16.11</tt>. The username is either <tt>root</tt> or <tt>smb</tt> and the password is <tt>Pa$$w0rd</tt>.

 - @lab.VirtualMachine(LAMP10).SelectLink is built on the Ubuntu Server distribution (<[ubuntu.com](https://ubuntu.com)) and runs the familiar Linux, Apache, MySQL, and PHP functions of a web server. As a server distribution, this VM has no GUI shell. This VM is positioned on the local network with the Windows Server VMs and has a DHCP reservation for the address <tt>10.1.16.12</tt>. The username is <tt>lamp</tt> and the password is <tt>Pa$$w0rd</tt>.

 - @lab.VirtualMachine(rLAN10).SelectLink is running the VyOS Linux distribution (<[vyos.io](http://vyos.io)) and is used to route traffic between the different subnets configured on the various virtual switches. You will be discovering more about the network topology in later activities so we will not explain more here. 

    >[!KNOWLEDGE] If you do want to investigate the VyOS configurations, the username is <tt>vyos</tt> and the password is <tt>Pa$$w0rd</tt>. 

You can either operate the Linux servers directly at their local terminals or use remote connection software on a Windows VM. If you work at the local console, type/copy text features will NOT work. Using a remote client will allow you to type text or copy and paste command strings.

1. [] To use SSH, select the @lab.VirtualMachine(PC10).SelectLink VM. Open the **PuTTY** desktop shortcut icon.

  PuTTY is a freeware terminal emulation tool written and maintained primarily by [Simon Tatham](https://www.chiark.greenend.org.uk/~sgtatham/putty/).

1. [] In the Host Name box, type +++lamp10+++ and then select the **Open** button.

1. [] At the prompt dialog, select **Yes** to trust the server.

1. [] At the command prompt, enter the user name +++lamp+++ and then the password +++Pa$$w0rd+++. Note that no characters or placeholders will be shown as you type the password.

1. [] Run the following command to show the IP configuration: `ip a`

>[!HINT] If pressing keys does not enter text into a VM, check that your cursor is clicked into the VM window. 

===

## Assisted and Applied Lab Activities
To complete the labs in this series, you must submit a response to each scored task. This lab series comprises two different types of activity with different rules for scoring:
- Assisted labs confirm your knowledge and guide you through the steps to achieve a given configuration. In an assisted lab, if you get a scored item incorrect, you may repeat the question and achieve the correct answer.

- Applied labs challenge your ability to configure given settings and display knowledge of concepts, tools, and options without detailed step instructions. In an applied lab, if you get a scored item incorrect, you may not repeat the assessment or change your answer.

The type of activity—assisted or applied—is indicated in the lab title.

Many of the tasks are scored by a script that checks whether you have completed the required configuration or output. When completing a scripted task, you must use the same case-sensitive name, output folder, or other label as directed by the lab instructions or your response may be marked as incorrect. For example, if the task instructs you to create a user account named <tt>user01</tt>, then <tt>user1</tt> or <tt>User01</tt> would be marked as incorrect.

1. [] On the @lab.VirtualMachine(PC10).Selectlink VM, open Windows PowerShell.

1. [] Run the following command to output the IP configuration to a text file:

    ```Cmd
    ipconfig /all >$env:USERPROFILE\Desktop\ipconfig.txt
    ```

1. [] @lab.Activity(q01)

1. [] @lab.Activity(q02)

===

## Comprehensive questions

Each assisted lab ends with a set of comprehensive questions. Answer these to ensure that you recognize the importance of the activity steps and the uses for the information you have learned.

1. [] @lab.Activity(q03)

1. [] @lab.Activity(q04)

===

## Grade lab

That concludes this lab. Please ensure you end it properly rather than just closing the browser window. 

Once you select **Submit**, you will not be able to return to this lab instance. If you want to repeat the lab, you can launch a new instance from your lab portal.

1. Check the step boxes to mark all tasks as complete and make sure you have submitted responses to all the activities.

1. Select **Submit** below to grade the lab.

>[!TIP] You can use the **Menu** button !IMAGE[Screenshot of Menu icon](lod%20icon%20menu.png) to save the lab state and return to it later. Note that you can only have a limited number of labs in a save state at any one time. You can also use the **Menu** to end (cancel) a lab. This means that no score will be recorded and that the next time you launch the lab it will be reset to its starting conditions.

