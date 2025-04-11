# SOHO

## Scenario
The company requires the following during the implementation:
- One router and one switch are to be used.
- 3 departments for Administration, Operation, Finance Department.
- Each department is required to be in a different VLANs.
- Devices in all the departments are required to communicate with each other.
- Each department is required to have a wireless network for the users.
- Host devices in the network are required to obtain IPv4 address automatically.

The ISP gave out a base network of 192.168.1.0 to work around.

## Final output

![image](https://github.com/user-attachments/assets/75c298c4-6f4a-4c15-8346-e746c770c9d9)

**Addressing Table:**

## Configuring VLANs in Switch
For Administration Department

![image](https://github.com/user-attachments/assets/ae4e3760-7190-489c-accf-2abe441e97ad)

For Operation Department

![image](https://github.com/user-attachments/assets/2d0615c5-b384-4a74-a337-5c06bd8b174a)

For Finance Department

![image](https://github.com/user-attachments/assets/ae925a35-067d-44da-9d7b-6ca43b31c2dd)

Overall command:

![image](https://github.com/user-attachments/assets/eccc1404-a25f-4db6-ab8d-f5c868cc10d1)

To view the changes, I used the command "_do show start_" in the configuration terminal.

![image](https://github.com/user-attachments/assets/1d9069b1-6d41-4c67-88c0-bfbacd83377e)

## Enabling trunk port in Switch
Why do we need to enable trunk port? VLANs segment a physical network into multiple logical networks. Without trunk ports, traffic from one VLAN would typically not be able to reach another VLAN. 

To enable trunk port

![image](https://github.com/user-attachments/assets/119d60d1-794e-4d8b-a1ca-e49cd794318c)

To view the changes, I used the command "_do show start_" in the configuration terminal.

![image](https://github.com/user-attachments/assets/a17350ed-4d05-4ee4-84dc-fa11e2f399d0)

## Configuring Access Points
For Administration Department

![image](https://github.com/user-attachments/assets/6166c44a-fce1-4c0d-a2b2-a5117b832a93)

For Operation Department

![image](https://github.com/user-attachments/assets/48edceaa-ff9f-408a-887c-17d9a44dea11)

For Finance Department

![image](https://github.com/user-attachments/assets/f3d17d76-cccc-4196-8852-70e499767c94)

## Enabling Router

![image](https://github.com/user-attachments/assets/fd43481f-7f6c-41f0-bb75-d0f3e25d2dc5)

## Creating sub interface in Router

**This is crucial for scenarios where a single router port needs to serve as the default gateway for multiple VLANs connected to a switch via a trunk link.**

For Admin

![image](https://github.com/user-attachments/assets/47c70908-9924-49a5-896d-efda6af4a3b2)

The IP address shown in the configuration is considered the default gateway for the subnet admin, and the same goes for the following departments.

For Operation

![image](https://github.com/user-attachments/assets/94c321d1-0083-4bdb-a732-8d5fc9bf48d2)

For Finance

![image](https://github.com/user-attachments/assets/df7bcaeb-51d4-4c7d-b5aa-e5883f5b73e5)

To view the changes, I used the command "_do show start_" in the configuration terminal.

![image](https://github.com/user-attachments/assets/3cb4f93d-34ff-4589-b892-aea954507d50)

I created a sub-interface for the 3 subnet Administration, Operation, and Finance Department

The encapsulation dot1Q or IEEE 802.1Q is a standard protocol that adds a 4-byte tag to Ethernet frames to identify the VLAN to which the frame belongs, enabling VLAN trunking and routing between VLANs. 

Each subnet has its default gateway address seen in the configuration.

## Configuring DHCP & DNS Server in Router

For Administration

![image](https://github.com/user-attachments/assets/26a6e7b3-fac0-4d9f-b2ca-3f3528501b8b)

For Operation

![image](https://github.com/user-attachments/assets/d1030519-66a4-4f85-8a06-dc98cb15e30a)

For Finance

![image](https://github.com/user-attachments/assets/99434a3e-19ec-4c17-9bdc-4d6b802d8968)

Overall commands

![image](https://github.com/user-attachments/assets/f96fec84-17ce-4251-97d5-e20f5db4b9a8)

To view the changes, I used the command "_do show start_" in the configuration terminal.

![image](https://github.com/user-attachments/assets/458d4fff-a94b-4a3a-a8e6-8efa38b5d7d4)

## Testing if the configured DHCP server worked

**Lastly, we configure the end devices by switching from static to dhcp.**

For Administration

![image](https://github.com/user-attachments/assets/898f762f-2143-48d4-8045-46fc79082199)

PC:

![image](https://github.com/user-attachments/assets/95191b3d-f1d7-4f28-9415-c6d7800ba586)

Printer:

![image](https://github.com/user-attachments/assets/69c35716-7402-4e14-92ff-21c71fd05337)

Mobile Device connected to Access Point

SSID: Admin AP

Password: AdminR@cks

![image](https://github.com/user-attachments/assets/cdbe23c2-74cc-4c2b-965a-4781eaebad7c) ![image](https://github.com/user-attachments/assets/da7bb5a5-23b8-4754-9102-b95a6edc8ed1)

For Operation

![image](https://github.com/user-attachments/assets/df7a5f10-f5be-4209-a1b2-3e92ca2fada3)

PC:

![image](https://github.com/user-attachments/assets/d6cf0e17-7321-4384-9afb-3fa804e57907)

Printer:

![image](https://github.com/user-attachments/assets/fb7ff568-a136-4c24-998c-af4b57bc919f)

Mobile Device connected to Access Point

SSID: Operation AP

Password: 0peration!

![image](https://github.com/user-attachments/assets/1d922e64-907b-4249-a768-a4c0fc004324) ![image](https://github.com/user-attachments/assets/9f3e697c-db0e-4d06-85f0-373693bb9a1d)

For Finance

![image](https://github.com/user-attachments/assets/65ad5e65-eb33-43df-87d4-62893c7a9375)

PC:

![image](https://github.com/user-attachments/assets/ce3b3244-9575-4ad0-be4c-6b6a74f1374c)

Printer:

![image](https://github.com/user-attachments/assets/dab5555a-a814-4d09-8377-039823b36aed)

Mobile Device connected to Access Point

SSID: Finance AP

Password: Finance!

![image](https://github.com/user-attachments/assets/1cf379e0-ef76-425a-bb27-3ade700a9dab) ![image](https://github.com/user-attachments/assets/bed60c31-0ba3-4146-b201-64ed1597e4b8)



## Testing
_ping_ command is used to test network connectivity between devices. It sends an ICMP echo request to a specified IP address and waits for a reply. This helps determine if the destination device is reachable and if the network path between the devices is functioning correctly. 
