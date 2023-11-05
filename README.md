# Virtual_Machines-Creation-And-Usage

This tutorial will explain the following:

How to create and use virtual machines, resource groups, virtual networks.

Environments Used: Microsoft Azure, Windows 10, Linux. 

Technology Used: Remote Desktop, Wireshark.

*A virtual machine is a virtual computer. Virtual machines use software instead of a physical computer and are capable of running programs, surfing the internet, and downloading apps.*

*A virtual network is a networking system that allows virtual machins and data centers to connect wirelessly*

In the Microsoft Azure home page select Resource Groups and select create resource group.
![Creating The Resource Group](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/ecefe4a5-39d3-44bb-a5a8-ecac8624450e)

Name your recource group and select review+create. 
After the resource group has passed its validation select create to complete the resource group's creation.

In the Microsoft Azure home page select Virtual Machines and select create Azure virtual machine.
When creating the virtual machine select the resource group that you previously created and select windows 10 as the image.
![Creating The 1st Virtual Machine](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/85d50f7b-9b60-43a6-9020-cc4d721878ab)

Select a size for the virtual machine that will allow you to use 2 vcpus.
Name the virtual machine and create a password. 
![Creating The 1st Virtual Machine 2](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/ae35854a-a1fa-4661-bf9d-32fc40a34d6d)

Click on the licensing agreement box and select review+create.
After the virtual machine has passed its validation selcet create to complete the virtual machine's creation.

Now create a second virtual machine within the same resource group that was created earlier using Ubuntu as the image.
![Creating The 2nd Virtual Machine](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/9650a13d-dfa5-4e2d-861e-bcdf7ecf7a0e)

Name the virtual machine and select password instead of SSH public key.
![Creating The 2nd Virtual Machine 2](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/f6073b02-9051-4b7c-8239-d51e6389e833)

Create a Username and password and select review+create after the virtual machine passes the validation.
Check select create to complete the virtual machine's creation.

Now there should be two virtual machines within the same resource group. One running Windows 10 and one running Ubuntu also know as Linux.
![The Two Virtual Machines](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/4ba7e14f-1eb1-4ea2-a583-474b4887c728)

Open the first virtual machine VM1 and copy it's public IP address. Which is 20.127.184.219
![Finding The IP Address Of The 1st VM](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/baf8d482-e0ed-444a-895e-eeb12a28c152)

Connect to VM1 using remote desktop, by opening remote desktop and pasting the public IP Address of VM1.
![Connecting To The First VM](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/12ddd9b6-ede2-4359-a45c-f99b6f5736e7)

Enter the username and password for VM1 and connect to it via remote desktop.
Once connected to the virtual machine open the internet and download wireshark.

*Wireshark is a network protocol analyzer* which we will use to monitor traffic between both virtual machines.
Select WindowsX 64 installer and install onto the virtual machine. 
![Downloading Wireshark onto the VM](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/0a337839-7efe-4b21-ab9d-5afb1da3a140)

On the second virtual machine VM2 scroll down to find the private IP Address. Which is 10.0.0.5
![Private IP Address Of VM2](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/75a62686-d853-436f-aa0e-7b82dbd67f12)

Open the wireshark app from the start menu and click on the blue fin to start the analysis process.
Wireshark will begin showing all of the traffic running in the background of the virtual machine.
![Using Wireshark](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/9508d356-4643-4ff5-a655-e828a67da7cb)

In the virtual machine open Windows PowerShell. 
![Opening Powershell](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/cd567309-89de-4537-a9cd-62037bebb2cd)

Reset wireshark by clicking the green fin at the top, and then filter wireshark to only show ICMP traffic by typing ICMP on wireshark's command line.
![Filtering Traffic Using icmp](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/b9cb1598-209e-42d5-8fce-4b00eddaf50a)

On windows powershell ping the private IP address of VM2 by typing ping and it's private IP address 10.0.0.5.

There should be a successful ping between the virtual machines, and it should be visible on both Wireshark And Windows PowerShell.
![Successful Ping Between The Virtual Machines On Wireshark And PowerShell](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/76aee27f-689f-4023-bb65-c4fad219dce6)

Successful pings shows internet connectivity betweeen the virtual machine and the website.

On VM2 select network settings and select VM2's network security group or nsg for short. 
On The Network security group select inbound security rules and select add to create a new rule.
![Adding Rules In The Network Security Group](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/943e0305-eed6-4e38-b98b-2f45482e444e)

By editing the inbound and outbound rules, we can deny or allow certain types of internet traffic.
By changing the protocol to ICMP and changing the action to deny, all inbound ICMP traffic to VM2 will be denied. 
![Changing The Inbound Rules 1 (1)](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/fba3a5dd-734d-44ec-ba38-bf1ab606021d)
![Changing The Inbound Rules 1 (2)](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/0c4c0336-e840-4ed6-b628-09b5329b8af9)
Because of the inbound rules on VM2's nsg, VM1 cannot ping VM2
![Failed Ping Between VM1 To VM2](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/d2f552bd-6b9f-49fa-8b30-08e60048522a)

Changing the inbound security rules to allow ICMP traffic will once again allow VM2 to recieve ICMP traffic.

![Changing The NSG Rules To Allow ICMP](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/bced5605-6527-4666-a99c-262e53da37cf)
![Allowing ICMP Traffic Again](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/e0f43504-d788-4e37-a4c6-39b5dc160d9b)


Demonstration 

Using Remote Desktop.

To use remote desktop with Azure Virtual Machines first get the public IP address of the virtual machine you want to connect to.
![Getting The Public IP Address](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/9809f8c7-f832-4a6d-847b-b25df000b3ca)

Then open windows remote desktop and insert the public IP Address of the virtual machine and click connect. 
Enter the username and password for the virtual machine and connect to the virtual machine.

![Connecting To Remote Desktop (1)](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/0b17136d-858e-4bdd-b1fc-13c45f6eee2c)
![Connecting To Remote Desktop (2)](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/a4b172d7-63fe-4396-a7b5-4081df9b3742)

Successfully pinging websites from within the virtual machine. 

Successful ping of Youtube.com
![Successful Ping Of Youtube](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/8b8b4289-de2f-483a-986a-09f5054a3202)

Successful ping of Github
![Successful Ping Of Github](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/b9bea225-183b-422e-9050-b84180f4d500)

Successful ping of CourseCareers.com 
![Successful Ping Of CourseCareers](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/a46a0a78-548c-47a7-8e7f-027fac6fb4f6)

Denying and Allowing ICMP traffic within the virtual machines. 

By adding rules to the virtual machines network security group you can deny or allow different forms of internet traffic.
Adding a rule that prevents VM2 from recieving ICMP traffic. 
![Changing The Inbound Rules 1 (1)](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/41ae6a8a-e7e1-4ddc-b6d1-48f4b30448ef)
![Changing The Inbound Rules 1 (2)](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/300a2703-2ffc-4a9a-910c-f276090882f3)

This prevents VM2 from recieving ICMP traffic causing the ping to time out.
![Failed Ping Between VM1 To VM2](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/ead87ce9-e1c2-47f6-8e6c-7b57fb255353)

By changing the rules to allow ICMP traffic the virtual machine can once again recieve ICMP traffic. 
![Chaning Inbound Rules To Allow ICMP Traffic](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/23f4ffc8-325b-4830-9cfc-d2d65fca1f6d)
![Allowing ICMP Traffic Again](https://github.com/Ken7281/Virtual_Machines-Creation-And-Usage/assets/142465932/a1352484-c6b1-473b-8f0d-150ab86c76d3)
