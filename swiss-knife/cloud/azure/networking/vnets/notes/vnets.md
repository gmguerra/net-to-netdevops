Virtual Networks are the fundamental building block of Azure's private network. 

A VNet exists within a certain subscription and a certain region. A VNet is not pinned to a single AZ, it spans within all the Availability Zones that are available in the region. 

A VNet is Layer 3 (Understands IP, no VLANs/L2). Dealing with TCP, UDP and ICMP. Cannot do broadcast, multicast, GRE encapsulation. All SDN. 

A VNet requires at least 1 IPv4 address, optionally you can add one or more IPv6 addresses.
## VNet Address space
VNets complies with RFC 1918, so ranges used are:
- 10/8
- 172.16/12
- 192.168/16

You can also bring your own public range if you want to, but Azure will still consider those public ranges private  (not accesible from the internet)

Azure reserves 5 IP addresses from each network:
- .0: Network address
- .1: Azure default gateway
- .2 & .3: Map the Azure DNS IPs to the VNet space 
- .255: Network broadcast

Unavailable address ranges are similar to network reserved ranges:
- 224/4 (Multicast)
- 255.255.255.255/32 (Broadcast)
- 127/8 (Loopback/Localhost)
- 169.254/16 (link-local)
- 168.64.129.16/32 (Internal DNS)

To define the IP address range, must think how many IPs are needed for the Virtual Network as a hole. Then, subnetting can be done. 

Some Azure services required a dedicated address space, such as Gateway and Azure Bastion. 

When you define a VNet, you can add address spaces as needed, even later after creation.

## Subnet capabilites
Subnets are segments of the VNet. Portion of the IP CIDR range. Subnets are regional as the VNets, so they span across the AZs for that region. 

Segmentation (subnets) allows you to control what traffic flows where. Smalles subnet is /29, while the largest is /2. IPv6 subnets must be exactly /64 in size. 

- By default, subnets can communicate between each other. 
- By Default, all resources in a VNet can communicate outbound to the internet. To communicate inbound, you'll need to assign a public IP address or a public load balancer. 
- Communication between Azure resources and subnets are allowed by default. 
- On-premise and VNets can be connected by securely extending your on-premise. Point-to-site VPN, Site-to-site VPN or Azure ExpressRoute are the services used for that. 
- Network security can be deployed to filter network traffic between subnets. NSGs (Network Security Groups)
- Azure creates by default routes to get the traffic between subnets, connected VNets, on-premises networks and internet. To override the default behavior, Route Tables and BGP can be used

IPv6 subnets always has a subnet mask of /64. 

Any resources in Azure within a Subnet will get a NIC linked (which is another resources) and will get an IP address via DHCP. Static is possible. All this is configured in the NIC. 

Subnet resizing is possible if nothing is linked. 
## Considerations for Vnets
- Ensure nonoverlapping address spaces. 
- Is any security isolation required?
- Do you need to mitigate any IP addressing limitations?
- Are there connections between Azure VNets and on-premises networks?
- Is there any isolation required for administrative purposes?
- Are you using any Azure services that create their own VNets?