# Public IP services

Public IP addresses enable Internet resources to communicate with Azure and enable the resources to communicate outbound with Internet. Your own public addressment cannot be imported into Azure to use it as an Internet facing public IP, as Azure already has public addresses. 

A public IP address in Azure is dedicated to a specific resource. If the resources isn't allocated with a public IP, it can communicated outbound internet with a NAT service, which assigns dynamically an available IP address. 

NAT is done by the Fabric itself, so resources don't know that they have a public IP. 

A public IP is bounded to a region, you can move a resources to another region but public IP would need to change. 

In Azure Resources MAnager, a public IP address is a resource that has its own properties. Resources that can be associated with a public IP address:
- Virtual machine network interfaces
- Virtual machine scale sets
- Public Load Balancers
- Virtual Network Gateways (VPN/ER)
- NAT gateways
- Application Gateways
- Azure Firewall
- Bastion Host
- Route Server

Public IPs can be static or dynamic:
- Dynamic is allocated when a VM is created or started, and released when it's stopped or deleted. In each region, public IP addresses are assigned from a unique pool of addresses. 
- Static is allocated over the lifespan of the azure resource. Once the allocation method is explicitly set to static, the IP is assigned immediately. The IP is released when the resources is deleted or the IP allocation method is changed to dynamic. 

Standard SKU (Stock Keeping Unit) for public IP addresses: 
- Static only
- Locked down by default: standard needs NSG to allow inbound traffic.
- AZ support 

You need to use the same type of public IP than the resource you want it to be linked (Standard load balancer needs standard public IP) 

Public IPs usage examples:
- VPN Gateways
- Firewall solutions
- Load balancers

### Public IP Prefix: 
Contiguos block of public IP addresses. 