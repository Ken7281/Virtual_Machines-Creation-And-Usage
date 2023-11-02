# Virtual_Machines-Creation-And-Usage

This tutorial will explain the following:
How to create and use virtual machines, resource groups, virtual networks
Environments Used: Microsoft Azure, Windows 10, Linux, 
Technology Used: Remote Desktop, Wireshark

In the Microsoft Azure home page select Resource Groups and select create resource group
![Creating The Resource Group](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/ecefe4a5-39d3-44bb-a5a8-ecac8624450e)

Name your recource group and select review+create 
After the resource group has passed its validation select create to complete the resource group's creation

In the Microsoft Azure home page select Virtual Machines and select create Azure virtual machine
When creating the virtual machine select the resource group that you previously created and select windows 10 as the image
![Creating The 1st Virtual Machine](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/85d50f7b-9b60-43a6-9020-cc4d721878ab)

Select a size for the virtual machine that will allow you to use 2 vcpus
Name the virtual machine and create a password 
![Creating The 1st Virtual Machine 2](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/ae35854a-a1fa-4661-bf9d-32fc40a34d6d)

Click on the licensing agreement box and select review+create
After the virtual machine has passed its validation selcet create to complete the virtual machine's creation

Now create a second virtual machine within the same resource group that was created earlier using Ubuntu as the image
![Creating The 2nd Virtual Machine](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/9650a13d-dfa5-4e2d-861e-bcdf7ecf7a0e)

Name the virtual machine and select password instead of SSH public key
![Creating The 2nd Virtual Machine 2](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/f6073b02-9051-4b7c-8239-d51e6389e833)

Create a Username and password and select review+create after the virtual machine passes the validation check select create to complete the virtual machine's creation

Now there should be two virtual machines within the same resource group. One running Windows 10 and one running Ubuntu also know as Linux
![The Two Virtual Machines](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/4ba7e14f-1eb1-4ea2-a583-474b4887c728)

Open the first virtual machine and copy it's public IP address
![Finding The IP Address Of The 1st VM](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/baf8d482-e0ed-444a-895e-eeb12a28c152)

Connect to the first virtual machine using remote desktop, by opening remote desktop and pasting the public IP Address of the first virtual machine
![Connecting To The First VM](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/12ddd9b6-ede2-4359-a45c-f99b6f5736e7)

Enter the username and password for the first virtual machine and connect to it via remote desktop

Once connected to the virtual machine open the internet and download wireshark

*Wireshark is a network protocol analyzer* which we will use to inspect traffic between both virtual machines
Select WindowsX 64 installer and install onto the virtual machine 
![Downloading Wireshark onto the VM](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/0a337839-7efe-4b21-ab9d-5afb1da3a140)

On the second virtual machine scroll down to find the private IP Address
![Private IP Address Of VM2](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/75a62686-d853-436f-aa0e-7b82dbd67f12)

Open the wireshark app from the start menu and click on the blue fin to start the analysis process
Wire shark will begin showing all of the traffic running in the background of the virtual machine
![Using Wireshark](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/9508d356-4643-4ff5-a655-e828a67da7cb)

In the virtual machine open Windows PowerShell 
![Opening Powershell](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/cd567309-89de-4537-a9cd-62037bebb2cd)

Reset wireshark by clicking the green fin at the top, and the on windows powershell ping the private IP address of the second virtual machine by typing ping and the private IP address

There should be a successful ping between the virtual machines, and it should be visible on both Wireshark And Windows PowerShell
![Successful Ping Between The Virtual Machines On Wireshark And PowerShell](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/76aee27f-689f-4023-bb65-c4fad219dce6)

You can also ping other websites as well 
Successful ping of Youtube.com
![Successful Ping Of Youtube](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/8b8b4289-de2f-483a-986a-09f5054a3202)

Successful ping of Github
![Successful Ping Of Github](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/b9bea225-183b-422e-9050-b84180f4d500)

Successful ping of CourseCareers.com 
![Successful Ping Of CourseCareers](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/a46a0a78-548c-47a7-8e7f-027fac6fb4f6)

