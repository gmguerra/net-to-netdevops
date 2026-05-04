# Integrating Azure DNS and private link

Azure provides a private DNS zone, which domains start with privatelink.* 

In Azure, resources can use this DNS resolver to resolve the domain names of the services they'd like to access. DNS Forwarders can have conditional forwarders configured for each private endpoint public DNS zone, pointing to the DNS private resolver. DNS Forwarder zones must be linked to the private DNS zone names for Azure Serivces, those FQDN starting with privatelink. 

Azure DNS Private resolver is a service that enables secure and seamless DNS resolution between Azure VNets and on-premises environment, without need to deploy, manage or patch custom DNS servers. This service resolves DNS queries for private DNS zones from anuwhere. Facilitates hybrid network connectivity and simplifies network management. 