1. Project Overview
The main goal of the project is to focus on creating and implementing a Small Office Home Office (SOHO) network where I created three departments:
•	Admin
•	Finance
•	Customer Service
The network is structured using VLAN segmentation, Inter-VLAN routing, and DHCP services for ensuring effective IP management. 
________________________________________
2. Objectives
•	To divide the network into three separate VLANs for efficient management and security.
•	To allow communication between VLANs using Inter-VLAN routing
•	To dynamically assign IP addresses using DHCP.
•	To implement subnetting for efficient IP address utilization
•	To allow Wireless Access to the departments.
________________________________________
3. Network Design Architecture
3.1 VLAN Configuration
Each department is assigned a unique VLAN:
Department	VLAN ID	 Purpose
Admin	VLAN 10	Management
Finance	VLAN 20	Financial transactions
Customer Service	VLAN 30	Client handling
Advantages:
•	Improves security by isolating traffic.
•	Reduces broadcast domains.
•	Increases the network performance.
________________________________________
3.2 Subnetting 
The entire network is divided into three subnets, one for each VLAN.
Example IP scheme:
VLAN	Department	Subnet	Gateway
10	Admin	192.168.1.0/26	192.168.1.1
20	Finance	192.168.1.64/26	192.168.1.65
30	Customer Service	192.168.1.128/26	192.168.1.129
Explanation:
•	Subnetting segments the network into smaller, operable networks.
•	Each subnet corresponds to a specific VLAN.
________________________________________
3.3 Inter-VLAN Routing
As VLANs are individual broadcast domains so communication between them is not possible by default. This can be achieved using Inter-VLAN Routing. In my case, I have used Router on a Stick method.
Implementation Method: Router-on-a-Stick
•	A router is connected to a switch via a trunk link.
•	Then I created Sub-interfaces on that particular physical interface of the router for their respective VLAN.
Example:
•	Interface G0/0.10 → VLAN 10
•	Interface G0/0.20 → VLAN 20
•	Interface G0/0.30 → VLAN 30
Here, Each sub-interface acts as the default gateway for its VLAN.
Function:
•	Allows Admin to communicate with Finance
•	Enables Customer Service to access shared resources
________________________________________
3.4 DHCP Configuration
A DHCP server is generally used to dynamically assign IP addresses to devices in each VLAN.
DHCP Pools:
•	Admin Pool → 192.168.1.0/26
•	Finance Pool → 192.168.1.64/26
•	Customer Service Pool → 192.168.1.128/26 
Each pool includes:
•	Network address
•	Default gateway
•	DNS server
•	IP range
Advantages:
•	It removes the need to manually assign the IP addresses.
•	Helps in reducing the errors and saves time.
•	Also helps to a great extent in simplifying the entire network management.
________________________________________
3.5 Wireless Network Setup
Each department has been provided with its own Separate Wireless Access Point (WAP).
Department	SSID Name	VLAN Mapping
Admin	Admin_WiFi	VLAN 10
Finance	Finance_WiFi	VLAN 20
Customer Service	CS_WiFi	VLAN 30
Important Features:
•	Each SSID is connected to its respective VLAN.
•	Ensures traffic separation even in wireless networks.
•	Augments the security and access control.
________________________________________
4. Network Devices Used
•	Router – For Inter-VLAN routing
•	Layer 3 Switch – For VLAN configuration
•	Wireless Access Points – For Wi-Fi connectivity
•	End Devices – PCs, laptops, mobile devices
________________________________________
5. Working of the Network
1.	Devices connect via wired or wireless networks
2.	DHCP assigns IP addresses based on VLAN
3.	Devices communicate within the same VLAN directly
4.	For inter-department communication:
o	Traffic is sent to the default gateway
o	Router performs routing between VLANs
5.	Response is sent back through the router
________________________________________
6. Advantages of the Design
•	Security: Departments are isolated due to which the security gets enhanced.
•	Scalability: Easy to add more VLANs as per the requirement. 
•	Efficiency: Reduces the broadcast traffic.
•	Automation: DHCP makes the IP assignment easy.
•	Flexibility: Supports both wired and wireless users.
________________________________________
7. Challenges Faced
•	Wrong VLAN configuration can restrict communication.
•	There were some Trunking difficulties	between the switch and router.
•	The IP addresses were not automatically getting allocated to the respective networks.
•	Wireless VLAN mapping complexity.
________________________________________
8. Conclusion
To conclude, this SOHO network design shows a effective and scalable which facilitates communication between the different departments using VLANs, subnetting, DHCP, and Inter-VLAN routing. This implementation ensures secure segmentation while maintaining seamless connectivity between departments, making it suitable for small to medium office environments.
________________________________________




Base Network : 192.168.1.0

No of Subnets required : 3

No of Subnets : 2*n

2*n==3=n=2

Class C= 255.255.255.0==11111111.11111111.11111111.00000000

After borrowing 2 bits

New Binary = 11111111.11111111.11111111.11000000

New Subnet Mask : 255.255.255.192

Block Size = 64

1st Subnet : 
Network ID : 192.168.1.0
Broadcast ID : 192.168.1.63
Host Range : 192.168.1.1- 192.168.1.62

2nd Subnet :
Network ID : 192.168.1.64
Broadcast ID : 192.168.1.127
Host Range : 192.168.1.65-192.168.1.126

3rd Subnet :
Network ID : 192.168.1.128
Broadcast ID : 192.168.1.191
Host Range : 192.168.1.129-192.168.1.190



# small_office_network_design
