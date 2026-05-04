# Virtual Network Service Endpoints 

A Virtual Network Service Endpoint provide secure and direct connectivity to Azure services over an optimized route through Azure backbone network. By default, Azure resources have public IP addresses, including PaaS services such as Azure SQL Database and Azure Storage. In a lot of cases, this is a liability. VNet Service Endpoint address this by allowing customers to secure the critical Azure service resources to only customer's virtual networks. Service endpoints enable private IP addresses in the VNet to reach the endpoint of an Azure service. 

Use cases:
- Connecting services to peered or multiple virtual networks.
- Securing Azure resources to services deployed directly into virtual networks.
- Filtering outbound traffic from a virtual network to Azure services.
- Managing disk traffic from an Azure virtual machine.

Azure Service Endpoints are available for many services, including storage, databases, key vault, service bus or data lake. 

## Service Endpoint optimization and security features

### Optimization

The default behavior when resources within a VNet try to access a resource outside the VNet is practically go to Azure edge and then come back to Azure. Service endpoint is an optimization mechanism that is attached to the vnet, that while creating this service endpoints all services of the same kind in the same region of the VNet will be available to be accessed through the improved path.  

Server can still be accessed normally by external users and on-prem. 

### Security 
Service endpoints can add restrictions of who can access it by restricting certain IP ranges. Also, it can filter the connection based in if it's coming from Azure VNet subnet specified or not. Simple firewall rules attached to the service endpoint.  

## Service endpoint policies
Enable to filter virtual network traffic to spefic Azure resources, over service endpoints. Granual access control for VNet traffic to Azure Storage as an example. 