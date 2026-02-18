Two DNS services:
- Public DNS
- Private DNS

## Public DNS services
Hosting service for DNS domains. Provides name resolution using Azure infra. Hosted in Azure's global network of DNS servers. The queries are directed to the closes available server. Resolves names without needing to add a custom DNS solution. 

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
