# VLAN-and-Secure-Switch-Configuration
# Table of Contents

1. [ Introduction](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#1-introduction)</br>
2. [ Part 1: Configure the Network Devices](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#2-part-1-configure-the-network-devices)</br>
  &nbsp;&nbsp;2.1[ Cable the Network](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#22-configure-router-r1)</br>
  &nbsp;&nbsp;2.2[ Configure Router R1](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#22-configure-router-r1)</br>
 &nbsp;&nbsp;2.3[ Configure and Verify Basic Switch Settings](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#23-configure-and-verify-basic-switch-settings)</br>
3.[ Part 2: Configure VLANs on Switches](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#3-part-2-configure-vlans-on-switches)</br>
  &nbsp;&nbsp;3.1[ Configure VLAN 10](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#31-configure-vlan-10)</br>
 &nbsp;&nbsp;3.2[ Configure the SVI for VLAN 10](https://github.com/the-original-copy/VLAN-and-Secure-Switch-Configuration/blob/main/README.md#32-configure-the-svi-for-vlan-10)</br>
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

![image](https://github.com/user-attachments/assets/2f50bd7d-0303-436c-a85f-73eb3d20d270)



</div>



## 3.2 Configure the SVI for VLAN 10
Here I configured the IP address according to the Addressing Table for SVI for
VLAN 10 on S1 and S2. I enabled the SVI interfaces as shown below:

<div align="center">

![image](https://github.com/user-attachments/assets/a6b3b8aa-c482-456f-8ccf-143da8e4366e)

</div>



## 3.3 Configure VLAN 333 with the name Native on S1 and S2

Here I created vlan 333 with the name Native on VLAN 333 on S2 and S1 and
another VLAN 999 called ParkingLot on both switch S1 and S2 as shown in the
picture below:

<div align="center">

![image](https://github.com/user-attachments/assets/adc8e824-ff80-40bf-b0d0-faf248d646ca)

</div>


# 4. Part 3: Configure Switch Security
## 4.1 Implement 802.1Q trunking

On both switches I configured trunking on F0/1 to use VLAN 333 as the native as
shown in the pictures below:

<div align="center">

![image](https://github.com/user-attachments/assets/fb1ebf3b-7bed-4570-a7bc-7f1a71175a92)
<br/>Image: 802.1Q trunking on S1

![image](https://github.com/user-attachments/assets/b0d7e4f4-c875-47c5-9cea-34d31a59b91b)
<br/>Image: 802.1Q trunking on S2


</div>

Next I verified that trunking has been configured on both switches as shown below:

<div align="center">

![image](https://github.com/user-attachments/assets/85b8da8e-a818-4f28-877c-50bf54dff911)


</div>

Next I disabled DTP negotiation on F0/1 on both switch S1 and S2 as shown below:

<div align="center">


![image](https://github.com/user-attachments/assets/f0e9599b-2dfc-401e-ab9c-b3ab6635d4e7)


</div>

I verified that DTP negotiation was disabled as confirmed by the picture below:

<div align="center">


![image](https://github.com/user-attachments/assets/dd8edf56-5051-4898-a073-b887c1f2b0cc)



</div>

## 4.2 Configure access ports

On S1 I configured F0/5 and F0/6 as access ports associated with VLAN 10 while on
S2 I configured F0/18 as the access port that is associated with VLAN 10 as shown
below:

<div align="center">

![image](https://github.com/user-attachments/assets/ced5aca3-5199-435b-b612-df16ba61a24c)

</div>



## 4.3 Secure and disable unused switchports

On both S1 and S2 I moved the unused ports from VLAN 1 to VLAN 999 and
disabled the unused ports as shown below:

<div align="center">

![image](https://github.com/user-attachments/assets/f492878c-bc7c-4a7a-88f1-4e0b99f629ad)

</div>

Next I verified that the unused ports are disabled and associated with VLAN 999 as
confirmed by the picture below:

<div align="center">

![image](https://github.com/user-attachments/assets/cbf6a659-14f6-4b0f-927f-360cc4065bff)

</div>



## 4.4 Document and implement port security features

In S1 I issued the **show port-security interface f0/6** in order to display the default
port security settings as confirmed by the picture below:

<div align="center">

![image](https://github.com/user-attachments/assets/3b9fd0aa-ef76-47b9-bf15-9fcfcbf68b5a)


</div>

Next on S1 I enabled port security on f0/6 with the following settings:
* Maximum number of MAC addresses : **3**
* Violation type: **Restrict**
* Aging time: **60min**
The picture below confirms that the listed port security settings were loaded:

<div align="center">

![image](https://github.com/user-attachments/assets/37a8366c-73d5-49bc-8893-ee0ab256fc41)

</div>

The port security aging type: **inactivity** was not loaded since the command was not
supported as shown below:

<div align="center">

![image](https://github.com/user-attachments/assets/89ea7383-0b53-4d86-b087-74019de98bfc)

</div>

I verified port security by checking the interface f0/6 and the port security address as
confirmed by the pictures below:

<div align="center">

![image](https://github.com/user-attachments/assets/aa45621c-fbda-46b7-af85-0f38e415f82a)
<br/> Image: port-security on interface f0/6

![image](https://github.com/user-attachments/assets/3297f551-a2ae-4697-ae34-3909c3f15819)
<br/> Image: port-security address

</div>

Next I enabled port security on interface f0/18 in S2 by configuring the port to add
MAC addresses learned on the port automatically to the running configuration as
shown in the picture below:

<div align="center">

![image](https://github.com/user-attachments/assets/9e50aa30-5bb2-4b93-9af2-8966b5239535)


</div>

Next I configured the below port security settings on S2 F0/18:
* Maximum number of MAC addresses: **2**
* Violation type: **protect**
* Aging time: **60min**
As confirmed by the picture below:

<div align="center">

![image](https://github.com/user-attachments/assets/21ccb0f5-f3d9-4825-8f60-fa04ecd61c5a)


</div>

Next I verified port security on S2 F0/18 by checking the port-security interface and
port-security address as shown below:

<div align="center">

![image](https://github.com/user-attachments/assets/bab93ded-cd3d-489f-879a-36944ad6bef5)
<br/> Image: port-security interface F0/18

![image](https://github.com/user-attachments/assets/19cef5db-cf5e-4068-98d5-1ddcbad9df4b)
<br/> Image: port-security address

</div>

## 4.5 Implement DHCP snooping security

On S2, I enabled DHCP snooping and configured DHCP snooping on VLAN 10 as
confirmed by the picture below:

<div align="center">

![image](https://github.com/user-attachments/assets/cc91f01d-7810-4ad0-9880-7b9445317494)

</div>

Next I configured the trunk port on S2 as a trusted port as confirmed by the picture
below:

<div align="center">

![image](https://github.com/user-attachments/assets/051bb12a-9d25-4d90-8d23-1f6150632c4d)

</div>

Next I limited the untrusted port F0/18 to five DHCP packets per second as confirmed
by the picture below:

<div align="center">

![image](https://github.com/user-attachments/assets/655a44bc-0815-4143-a957-efc119510ea5)

</div>

Finally I confirmed the DHCP Snooping on S2 matched the security settings set as
confirmed by the picture below:

<div align="center">

![image](https://github.com/user-attachments/assets/56d5ac42-9be0-464f-bce6-f80d486ff052)


</div>

## 4.6 Implement PortFast and BPDU guard

### PortFast

PortFast is a Cisco feature that can be configured on switch ports connected to end
devices like workstations or servers, rather than other switches. When PortFast is
enabled on a port, the port bypasses the usual Spanning Tree Protocol (STP) states
(Listening, Learning) and moves directly to the Forwarding state. This immediate
transition minimizes the delay for end devices to start communicating on the
network.

### BPDU Guard

PDU Guard is a security feature used in conjunction with PortFast. It protects the
network from potential Spanning Tree Protocol (STP) topology changes caused by an
unintended or malicious connection of a switch or another device that sends Bridge
Protocol Data Units (BPDUs) into a PortFast-enabled port. When BPDU Guard is
enabled, if any BPDU is received on that port, the port is immediately put into an
error-disabled state, effectively shutting it down.<br/>

First I configured PortFast on all the access ports that are in use on both switches as
confirmed in the pictures below:

<div align="center">


![image](https://github.com/user-attachments/assets/598b6787-8e0f-431b-b323-9f147d257228)
<br/> Image: PortFast on S1 from interface f0/5 - 6

![image](https://github.com/user-attachments/assets/67c2fbae-a331-457a-9321-0f57528952d9)
<br/> Image: PortFast on S2 from interface f0/18

</div>

Next I configured BPDU guard on S1 and S2 VLAN10 access ports connected to
PC-A and PC-B as confirmed by the pictures below:

<div align="center">

![image](https://github.com/user-attachments/assets/e894804c-39cc-4b97-84c4-c6a93ca5a583)
<br/> Image: BPDU guard on S1

![image](https://github.com/user-attachments/assets/4f6817f4-f73b-4774-b36c-0413e59ce82b)
<br/> Image: BPDU guard on S2

</div>

Finally I verified that BPDU guard and PortFast are enabled on the appropriate ports as shown by the pictures below:

<div align="center">

![image](https://github.com/user-attachments/assets/3678e797-609f-4661-b602-07d0cc2f7e6c)
<br/> Image: BPDU guard and PortFast on S1 interface f0/6

![image](https://github.com/user-attachments/assets/f3b97e2f-222e-4406-a7fc-83bd68aef58f)

<br/> Image: BPDU guard on S2

</div>

## 4.7 Verify end-to-end connectivity

I verified connectivity from PC-A by pinging the listed devices as shown below:

<div align="center">

![image](https://github.com/user-attachments/assets/c4b942e3-3a86-4c24-85fa-4e7b146ec3da)
<br/> Image: Ping from PC-A to R1 interface G0/0/1


![image](https://github.com/user-attachments/assets/937c6693-648c-4ad3-bc5e-f883b2c7179d)
<br/> Image: Ping from PC-A ro R1 interface 10.10.1.1


![image](https://github.com/user-attachments/assets/6fea1ddd-4cc6-466c-8233-0e8640ef7577)
<br/> Image: Ping from PC-A to S1

</div>



# 5. Conclusion

In conclusion, the network configuration process successfully addressed each objective, resulting in a fully operational and secure network environment. By cabling the network and configuring essential devices, a solid groundwork was laid. The detailed VLAN configurations on the switches facilitated organized network segmentation and improved traffic management. Moreover, the rigorous implementation of switch security protocols, including trunking, port security, and DHCP snooping, fortified the network against potential threats and vulnerabilities.Verifying end-to-end connectivity confirmed the efficacy of these configurations.This systematic approach not only achieved the desired outcomes but also enhanced the overall security and performance of the network, demonstrating the effectiveness ofmeticulous planning and execution in network management.
