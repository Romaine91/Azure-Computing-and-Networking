![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/91616666-e4d3-4499-ad2f-91968472edf3)

# Azure-Computing-and-Networking
Tutorial using Azure. 

1. Creating Resources 
2. How to Use Remote Desktop
3. Performing Activities on the Network 

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Azure Virtual Networks and Subnets
- Azure Network Machines (Windows and Linux [Ubuntu])
  Azure Network Security Groups (Firewall Resource)
- Remote Desktop
- Wireshark
- Powershell


<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Linux [Ubuntu Server 20.04]

<h2>High-Level Steps</h2>

- Step 1
- Create a Resource Group The Virtual Network and Subnet will automatically be created when making a Resource Group.
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/b6ebb16a-74df-42e7-b1c1-d715b177f3b1)
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/45b9af30-c499-4236-8eae-e031529d9ee8)




  Once the Resource Group is made it can be found under the Resource Group tab in Azure.
  
  ![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/e85ead2f-6689-4201-9fdf-40d732fe7d66)




-  Create (VM-1) Virtual Machine 1 Using Windows
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/e090f138-ca1d-4050-92c3-663d1fd0ad46)
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/756409c4-17cf-4924-8495-3315420c1633)




- The Virtual Network and Subnet were created when the Resource group was made. Also, the IP Address for your VM will be created.
  ![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/55288c3b-e2d1-4045-b35e-72438bc7f611)




Once VM-1 is created it can be found under the Virtual Machines tab in Azure. All created VMs will be listed under the VM tab.
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/3020b788-6e12-47df-abed-dee0422e4f51)



Create VM-2 Using Linux [Ubuntu} 

![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/ab3721a1-35ea-430b-a8a8-8a073c0cda60)




 Instead of using a Public Key, we`ll create VM-2 using a Password.
 ![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/07d4d7e8-bb3c-4864-aee9-14bc4ea05db9)




- Step 2 Get your Public IP address from VM-1 and log in to the remote desktop
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/aed4d50d-913a-4dc7-b7b7-6bc7c73ed92b)

![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/abe0eaa0-86b6-4a4a-9840-005387e3d7a7)



  
- Step 3 Install a program inside of VM-1 called Wireshark and use it to inspect traffic with VM-2. Installed Wire Shark from the web browser inside VM-1

- ![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/5af4e844-74e4-46b6-81ff-1f21ef4e9ed3)



- Once Wireshark is open we select to capture the traffic through the Ethernet then click the wireshark button. 
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/4a9dfc8d-b204-4687-8e65-f1452cb74f2f)




 Here`s a pic showing the live traffic running through our VM-1 machine
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/121d8608-7e3e-4f6f-89b6-9d6b42e3d043)




Then we`ll filter this traffic through prompt (ICMP) Internet Control Messenger the protocol that ping uses. Ping is used to test connectivity between different hosts on the internet or network.
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/f57da7f0-2cbc-4e10-840c-584327799cc0)




To ping to VM-2 we need to know the private IP address from VM-2. 
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/432261c7-20b1-4df8-b77e-48685f184b17)




Next, we`ll go back into our VM-1 click the start button, and open Powershell

![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/cbf7456c-6689-4b71-baaf-0e608e209e29)



Once Powershell is open using the private IP address from VM-2
Enter the prompt (ping 10.0.0.5)  under PowerShell
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/09092b9f-71aa-4bbe-9e4c-78d1b32237e7)

Next, we`ll do another prompt to ping 10.0.0.5 -t for non-stop ping. Then we`ll change the  firewall on VM-2 to NOT allow traffic through ICMP.

Go to the Azure portal go to VM-2 go to (NSG) Network Security Group change the firewall to block the ping of ICMP 
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/7e9868d0-32a3-4e31-813c-50945cd3e02a)



 Here`s a pic of the continuance ping 
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/47a5ff2c-c7d3-4fdf-908c-560124a5fe88)



Now a pic showing the firewall blocked the ping and the request to continue to ping stopped 

![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/fddf835f-f408-482a-8e84-90b8f9915229)
The rule we added to block the ping can be edited and allow the ping access to ping again.



Next, we`ll use the SSH prompt in Powershell to VM-1 to Vm-2 using SSH
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/17842d16-c26f-4ee5-90c7-a2497e228a32)


the prompt was (ssh @labuser10.0.05) asked for the password to log in. You enter the password and then will be logged in as Labuser@VM2 as u see in the pic below 

![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/5384b386-e597-42d8-934e-5ad24405ffde)

Then I`ll enter a couple of Linux prompts to show that we`re in control of VM-2 via VM-1

![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/7e6404b9-dc8e-471e-8aaa-0ea88a0d4b1c)


 DNS in Wireshark to show traffic over the command line
![image](https://github.com/Romaine91/Azure-Computing-and-Networking/assets/173863740/2cbacf2c-5b04-4f4b-8a09-21a6e6f5b715)

That concludes the lab for Azure and Prerequisites!

 
That concludes the lab for Azure Computing and Networking 
