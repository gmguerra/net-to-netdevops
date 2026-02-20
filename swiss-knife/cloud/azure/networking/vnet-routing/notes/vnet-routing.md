# Virtual Network Routing

Route table is automatically created for each subnet within a VNet. t has the default system routes and any user defined routes. 
## System routes
Azure automatically adds system routes to each subnet, which cannot be removed. Systems routes can be overridden with custom routes. Also, adds other optional default routes to specific or every subnet when you use specific Azure capabilities. 

### Default System Routes
The default system routes for each subnet contains an address prefix and next hop types. 

The next hop is the next waypoint that the traffic is directed to. Next hop types:
- Virtual network: Routes traffic between address ranges within the VNet address space. Azure automatically provides system routes so traffic to other VNet prefixes/subnets stays inside the VNet.
- Internet: Routes the specified traffic to the internet. This would be the equivalent to the default route, specified as 0.0.0.0/0. Azure forwards all the traffic that is not explicit on the routing table towards internet, unless the destination is another Azure service, which would use the Azure backbone network. Default route can be overridden as well. 
- None: blackhole, drops the traffic. Used to avoid traffic leaking private larger subnets. 

### Optinal default sytem routes
When yoyu add any Azure capability, Azure adds default system routes for it. Depending on which is the capability, Azure adds optional default routes to either specific subnets within the VNet, or to all subnets within the VNet. 

Three of this optional routes:
- VNet peering: Azure will add a route for each address range within the address space of the peered VNets. 
- Virtual Network Gateway: once a virtual network gateway is deployed, Azure adds one or more routes with Virtual network gateway as the next hop. This means the route tells Azure to send matching traffic to the virtual network gateway. These routes show Virtual network gateway as the source because the gateway inserts the routes (for example learned by BGP) into the subnet’s effective routing table (rather than you adding them manually).
- VirtualNetworkServiceEndpoint: service endpoints can be enabled for individual subnets within a VNet. Once it's added, routes to the route table are added with the public IP addresses of the services. The route is only added to the route table of the subnet a service endpoint is enabled for. As the public IPs change periodically, Azure managed the updates to the routing table 

## User defined routes
Used to override the default routes with user-defined routes (UDR). For example, if you want to use a firewall to go to internet from a subnet, and this firewall is outside the subnet, an UDR can be configured to make sure traffic headed towards the internet is sent to the firewall first.  We need to set the next hop for that matter. The route table of the subnet must be configured. 

Other example, if I want to traverse between two subnets, I can go through a Network Virtual Appliance that can be between them, so traffic can be security analyzed. A route toward the other subnet can be set pointing to the next-hop of that NVA.

Routes can be even applied to forward the unknown traffic to your on-premise network. 

In Azure, a subnet can have zero or one associated route table. When a route table is created for that subnet, default routes are combined or overridden. 

For UDRs, these are the next hops: 
- Virtual appliance: VM that runs a network application, such as a firewall. You can specify the IP address on this next hop. 
- Virtual Network Gateway: If you want to forward the traffic to specific address prefixes reachable through a VNG (VPNs). The virtual network gateway must be created with type VPN.
- None: blackhole, dropped. 
- Virtual Network: when you want to override the default routing wihtin a VNet.
- Internet. When you want to head the traffic towards Internet. 

## Azure Route Server
Simplifies dynamic routing between a network virtual appliance and the VNet. It's a serviced that can be configured with high availability. Benefits:
- It's not necessary to update the routing table on the NVA whenever the VNet is updated.
- It's not necessary to updated the UDRs manually whenever the NVA announces or stops announcing new routes.
- Multiple instances of the NVA can be peered with Azure route server
- Peering based on BGP, so if NVA supports it, it can be peered with Azure route Server
- Azure Route Server can be deployed in any of the VNets. 
## Troubleshoot with effective routes
You can diagnose a routing problem by checking the effective routes a VM NIC has. It can be viewed for each NIC via Azure portal ![Effective routes example](var/nics.png)
