
# Private Link Service and private endpoint

Private establish private endpoints, which are NICs, in the VNet, that act as the location to access a service in Azure, a single instance of a service. Bringing a public service into a private express exclusively. 

A private endpoint is provisioned that represents a service, and private link acts like liaison between them two. It's just a NIC in a Subnet, just like the ones attached in a VM. If a VM needs to access the service, it goes through the NIC for the private endpoint. 

External connection from on-prem also benefits from this, as the connection remains private end-to-end, by going to the VNet and routing the traffic towards the private endpoint. 

Security is algo a feature, as public addressable access to the service can be turned off, so it's not exposed via the internet.  Private link removes the public part of the connection. 

The Azure resources becomes, in a sense, part of the private network, and the connections to that resource uses Azure backbone network. 

A private endpoint is the technology behind the private link, as it's a NIC attached to a subnet of a VNet that enables private and secure connection between VNet and Azure service. It's the network interface that represents the resource's IP

Private Link provides secure access to the services, while private link achieves that by replacing a resource's public endpoint with a private network interface. 

### Private endpoint vs Service endpoint

Private endpoint grant network access to specific resources without using the public exposed IP address as uses a private IP in the address space of the VLAN. A Service endpoint remains publicly routable IP address. 

### Private link between customer and provider
If both customer and its provider has resources in Azure, the provider can expose these resources via a private link by using Azure Private Link Service. This lets the provider offer connections to custom Azure services that consumers can then access privately from their own Azure VNet. 

Consumers create a private endpoint in their VNet and map it to the provider's Private link service. A Private Link service receives connection from multiple private endpoints, but one private endpoint connects to only one private link service. 