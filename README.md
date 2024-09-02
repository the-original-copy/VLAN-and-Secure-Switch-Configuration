# VLAN-and-Secure-Switch-Configuration
# Table of Contents

1. [ Introduction](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#1-introduction)</br>
2. [ Part 1: Configure the Network Devices](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#2-part-1-configure-the-network-devices)</br>
  &nbsp;&nbsp;2.1[ Cable the Network](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#22-configure-router-r1)</br>
  &nbsp;&nbsp;2.2[ Configure Router R1](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#23-configure-and-verify-basic-switch-settings)</br>
 &nbsp;&nbsp;2.3[ Configure and Verify Basic Switch Settings](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#23-configure-and-verify-basic-switch-settings)</br>
3.[ Part 2: Configure VLANs on Switches](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#3-part-2-configure-vlans-on-switches)</br>
  &nbsp;&nbsp;3.1[ Configure VLAN 10](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#31-configure-vlan-10)</br>
 &nbsp;&nbsp;3.2[ Configure the SVI for VLAN 1O](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#32-configure-the-svi-for-vlan-10)</br>
  &nbsp;&nbsp;3.3[ Configure VLAN 333 with the name Native on S1 and S2](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#33-configure-vlan-333-with-the-name-native-on-s1-and-s2)</br>
4.[ Part 3: Configure Switch Security](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#4-part-3-configure-switch-security)</br>
  &nbsp;&nbsp;4.1[ Implement 802.1Q trunking](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#41-implement-8021q-trunking)</br>
  &nbsp;&nbsp;4.2[ Configure access ports](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#42-configure-access-ports)</br>
  &nbsp;&nbsp;4.3[ Secure and disable unused switchports](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#43-secure-and-disable-unused-switchports)</br>
  &nbsp;&nbsp;4.4[ Document and implement port security features](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#44-document-and-implement-port-security-features)</br>
  &nbsp;&nbsp;4.5[ Implement DHCP snooping security](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#45-implement-dhcp-snooping-security)</br>
  &nbsp;&nbsp;4.6[ Implement PortFast and BPDU guard](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#46-implement-portfast-and-bpdu-guard)</br>
  &nbsp;&nbsp;4.7[ Verify end-to-end connectivity](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#47-verify-end-to-end-connectivity)</br>
5.[ Conclusion](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#5-conclusion)</br>
# 1. Introduction

This report outlines the step-by-step procedures undertaken to configure a network
using Cisco Packet Tracer. The primary objectives are divided into three parts:
configuring network devices, setting up VLANs on switches, and implementing
switch security measures. Initially, the network devices were cabled, followed by
configuring the router (R1) and verifying basic switch settings to establish
foundational connectivity. Subsequently, VLAN configurations were executed on
switches, including the creation of VLAN10 and its corresponding Switch Virtual
Interface (SVI), as well as the setup of VLANs 333 and 999 with specific naming
conventions on switches S1 and S2. Finally, comprehensive security measures were
implemented on the switches, encompassing 802.1Q trunking, access port
configurations, securing and disabling unused switch ports, documenting and
applying port security features, implementing DHCP snooping, and configuring
PortFast and BPDU security. The ultimate goal was to ensure robust and secure
end-to-end network connectivity

# 2. Part 1: Configure the Network Devices
## 2.1 Cable the Network

In order to complete this step I cabled and initialized the devices as shown in the
picture below:

<div align="center">

![image](https://github.com/user-attachments/assets/eb5b0109-0f3f-4d29-9134-aa8aa9e3f0b6)

</div>
## 2.2 Configure Router R1
The script below sets up basic router configuration, including setting the hostname, disabling DNS lookup, and excluding specific IP address ranges from the DHCP pool
to reserve them for static use.

<div align="center">

  ![image](https://github.com/user-attachments/assets/12358ce3-88c1-4185-a2fd-156763b8cdcd)
</div>

The script below configures a DHCP pool named "Students" with specific network
settings, sets up a loopback interface with an IP address, configures a GigabitEthernet
interface with a description and trusts DHCP relay information. The sequence also
includes fixing a syntax error in the DHCP relay configuration command.

<div align="center">

![image](https://github.com/user-attachments/assets/c3bfdf0e-f4e1-4122-afa5-6d66a424f736)

  

</div>

The script below configures the GigabitEthernet0/0/1 interface with an IP address and
brings it online. Additionally, it configures the console line to synchronize logging
messages with user input and disables the EXEC timeout, preventing the console
session from timing out due to inactivity. These settings improve the user experience
during console sessions and ensure the interface is active and properly configured.

<div align="center">


![image](https://github.com/user-attachments/assets/75c5b64e-48ff-4b28-95f0-5808a7a4766c)
  

</div>

At this point I had to verify the running-configuration on R1 by running the command **show ip intrefeace brief** and below is the feedback recieved:

<div align="center">


 ![image](https://github.com/user-attachments/assets/b843bb2c-5ddb-4e77-a5e6-f2ec652eb515)


</div>

Finally I verified that the IP addressing was done correctly since all the interfaces were up and running as shown in the image below:
<div align="center">


  ![image](https://github.com/user-attachments/assets/2bf238f0-90aa-4022-8982-93b048a02c85)


</div>

## 2.3 Configure and Verify Basic Switch Settings

I first configured the hostname for switches S1 and S2 as shown in the picture below:
<div align="center">

   ![image](https://github.com/user-attachments/assets/241100f3-728f-48d7-8e4c-6b2c1bd60fb6)

</div>

Next I prevented unwanted DNS lookups on both switches as shown in the pictures
below:

<div align="center">


   ![image](https://github.com/user-attachments/assets/53fd2470-3c5e-4cb5-8018-edc5eb098b85)


</div>

Next I configured interface descriptions for the ports that are in use in S1 and S2 as
shown in the pictures below:

<div align="center">

![image](https://github.com/user-attachments/assets/c07240d0-4a01-417a-a660-15b1dff05bd3)

</div>



# 3. Part 2: Configure VLANs on Switches
## 3.1 Configure VLAN 10
To complete this step I added VLAN 10 to S1 and S2 and called the VLAN
Management as shown below:

<div align="center">


![image](https://github.com/user-attachments/assets/88bec368-b249-4d4a-98dd-325b2c757024)


</div>

I also set the default-gateway for the Management VLAN as 192.168.10.1 on both
switches as shown below:

<div align="center">

![image](https://github.com/user-attachments/assets/1a0e2b22-a434-4ad1-8e58-c256562a925e)


</div>


## 3.2 Configure the SVI for VLAN 10
## 3.3 Configure VLAN 333 with the name Native on S1 and S2
# 4. Part 3: Configure Switch Security
## 4.1 Implement 802.1Q trunking
## 4.2 Configure access ports
## 4.3 Secure and disable unused switchports
## 4.4 Document and implement port security features
## 4.5 Implement DHCP snooping security
## 4.6 Implement PortFast and BPDU guard
## 4.7 Verify end-to-end connectivity
# 5. Conclusion
