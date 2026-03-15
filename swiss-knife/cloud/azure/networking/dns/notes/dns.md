By default, a VNet will use Azure DNS. That will provide name resolution for the resources in the same VNet. Custom DNS can be set, even on NIC level. 

Azure special DNS address: 168.63.1289.16 -> Azure DNS Endpoint. This DNS endpoint will only work within Azure, so on-prem would not be able to reply, unless a forwarder is created in Azure.

Two DNS services:
- Public DNS
- Private DNS

## Public DNS services
Hosting service for DNS domains. Provides name resolution using Azure infra. Hosted in Azure's global network of DNS servers. The queries are directed to the closes available server. Resolves names without needing to add a custom DNS solution. 

Entries are manually added. A, AAAA and CNAME are supported. This Public DNS zone will be authoritative for the name it belongs. Azure private DNS endpoint can resolve names against this public DNS, so internal resources can resolve those public names.  

**Considerations:**
- DNS zone must be unique within the resource group, and zone must not exist already.
- Same zone name can be reused in a different resource group or subscription. 
- Where multiple zones share the same name, each instance is assigned different name server addresses. 
- Root/parent zone is registered at the registrar and pointed to Azure NS name servers

**Delegate DNS Domains**
Azure DNS allows you to host a zone and manage the DNS records for a domain in Azure. You need to delegated the domain to Azure DNS to make sure queries reach the Azure DNS. Azure DNS isn't the domain registrar. 

You need to know the name server names for your zone in order to delegate the domain to Azure. For every zone, Azure DNS allocates name servers from a pool. Once the name servers are assigned, Azure DNS automatically creates authoritative NS records for the zone. 

You need to update the parent domain once the DNS zone is created and the NS allocated. Each egitrar has their own DNS management tools to change the name server records for a domain. It's needed to change the NS records to the ones Azure DNS created 

**Child domains**
Child domains can be delegated individually. Setting up a subdomain follows the same procedure as above, with the only difference that the NS should be changed in the parent domain (in Azure DNS) rather than in the domain registrar. 

## Private DNS services
Reliable and secure DNS service for your VNets. Manages and resolve domains in teh VNet, without a custom DNS solution. You can use own custom domains instead of the Azure-provided ones during deployment. Helps you tailor your VNet architecture to best suit you org's need. Naming resolution for VMs within a VNet and connected VNets 

Azure Private DNS Zone: certain name for the zone. It can contains different records: CNAME, TXT, PTR, MX, SRV, SOA, etc. Those can be manually added, or automatically created. When a VNet is linked to one (and only one) Azure private DNS zone for registration, it will add the resources of that VNet into the zone. A VNet can be linked to a thousand of Azure private DNS zones for resolution. 

Azure private DNS zones are global resources, for multiple zone. A single zone can hold up to 100 VNets registering to it, and up to 1000 VNets resolving from it. 

**Considerations**
- No custom DNS solutions.
- Custom DNS records, including hostnames.
- Hostname resolution between VNets
- Zones can be shared between VNetsm cross-network and service-discovery scenarios, such as VNet peering. 
- Azure DNS private zones feature is available in all Azure regions in the public cloud.

## Azure private DNS zones
Available only for internal resources. Global in scope, so if you have permissions to read the zone, they are accesible through any region, subscription, VNet or tenant. Highly resilient, replicated to regions all throughout the world. Not available to resources on internet (private only).

More flexibility than Internal DNS, own private DNS zones: 
- Specific DNS name for a zone
- Manual records when necessary
- Resolve name and IP Addresses across different zones and VNets
