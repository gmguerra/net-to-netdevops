# Azure VPN Gateway
Service used to send encrypted traffic between a VNet and on-premises network over the public internet, or VNet to VNet over Micosoft network. Uses a VNet gateway called VPN Gateway, and multiple connections can be created to the same VPN gateway. When multiple, all VPN tunnels share the available bandwidth. 

When deploying a VPN gateway, planning!!!!

Different methods of connections:
- Site2Site VPN connection: connectivity between physical connection and Azure, or between Azure environments, but peering is preferred. 
- Point2Site VPN connections: a VPN connection requiring a VPN client, either the Windows included, or any other VPN client on any device. Useful in WFH environments. 

In both types, you need a VPN gateway to land the data, a public IP address to reach from outside Azure, and something needed to traverse into the VNet itself. 

## Plan a VPN Gateway:
Factors to consider:
- Throughput
- Backbone: internet or private?
- Availability of a public static IP address
- VPN device compatibility (in case of P2S)
- Multiple client connections or a S2S link (P2S vs S2S)
- VPN Gateway type
- VPN Gateway SKU: different SKUs with different limitations in connections/tunnels, throughput, routing support, redundancy and VMs inside VNet. 

## VPN Gateway types:
Two types with specific connection requirements:
- Policy-based: previously called static routing gateways. Encrypt and direct packets through IPsec tunnels based on the IPsec policies. Policies, also called traffic selectors, are defined as an access list in the VPN device configuration. Some limitations are:
	- Policy-based VPNs supporting IKEv1 protocols can only be used with Basic Gateways SKUs
	- Only one tunnel when using a policy-based VPN.
	- Only available for site-to-site connections
- Route-based: previously called dynamic routing gateways, Uses routes in the IP forwarding or routing table to direct packets into their corresponding tunnel interfaces. The tunnel interfaces encrypt or decrypt the packets in and out of the tunnels. Most used. 

Once the Virtual Network Gateway is created, VPN type cannot be changed. 

## HA options for VPN connections:

Two options: 
- Active-standby or VPN Gateway redundancy: default type. Normally, on premises only require one active VPN gateway. In the event of a failure in Azure, the active line will be cut, and traffic will fail over to standby. There are two instances of the VPN gateway. Switching to the standby connection cases a service disruption. Planned maintenance makes connectivity to be restored in seconds, unplanned maintenance in minutes and P2S clients would need to reconnect.
- Active-Active Azure VPN Gateway: when the fail over is not acceptable or high level of uptime is needed. A couple of extra connections need to be established, as VPN tunnels to each of the active-active gateways needs to be established. Traffic is routed through both tunnels simultaneously. Whether one device goes down on-premise or in Azure itself, uptime is guaranteed. Four potential points. 