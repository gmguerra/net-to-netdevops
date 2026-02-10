Public IP addresses enable Internet resources to communicate with Azure and enable the resources to communicate outbound with Internet.

A public IP address in Azure is dedicated to a specific resource. If the resources isn't allocated with a public IP, it can communicated outbound internet with a NAT service, which assigns dynamically an available IP address. 

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

Standard SKU (Stock Keeping Unit) for public IP addresses. 