# Azure ExpressRoute 

ExpressRoute extends on-premises networks into Microsft Azure using a private connection, via a connectivity provider (ISPs, exchangers, etc). ExpressRoute establishes connections to various Microsoft cloud services, including Azure and MS 365. 

Connectivity can be from an IP VPN network, a point-to-point Ethernet network, or a virtual corss-connection through a connectivity provider at a colocation facility (exchange). Express routes offers reliability, faster speeds, consistent latencies and higher security. 

A basic architecture: 

![Basic architecture](var/arch.png)

### Components that make possible an ExpressRoute:

- Physical customer site: on-prem. Physical premises where a customer has its network. 
- Express route circuit: connected by a partner of some kind. Linked up in one of the co-locations where MS and the partner have presence.  secure places 
- Meet me: secure places where partner connections/circuits encounter Microsoft's. Partner needs to create a cross-connect through the meet me route in the MS routers, and directly into Microsoft secure edge. 
- Microsoft Secure Edge: Microsoft routers that enables traffic to come into the Microsoft network. 
- Microsoft services: with public IPs. M365, SQL DB, etc
- Azure: where the private address space is located.

ExpressRoute by default has high availability, and by default its resilience is being managed by a third party (partner/provider) on behalf of the customer and microsoft. You connect into ExpressRoutes with two connections by default, separate routers, independent circuits, divers fiber paths. 

Resiliency achieved with two BGP sessions (pri + sec) + redundant Microsoft secure edge routers. Provider connects you to both paths. 

The traffic that traverse the ExpressRoute is whatever you pick, as a connection against Azure via VPN gateway or Microsoft services can be estbalished, using the Azure publicly addressable IPs. 

### ExpressRoute connectivity models

2 ways:
- Service provider model:
	- CloudExchange colocation: customer needs to be colocated in a facility with a cloud exchange. Virtual cross-connection from customer to Microsoft through the colocation provider's Ethernet exchange. Either L2 or L3 cross-connections. 
	- Point-to-point Ethernet connection: on-premises to Microsoft cloud with dedicated point-to-piint Ethernet links. P2P providers offer L2 connections.
	- Any-to-any (IP VPN) connection: integration of WAN with Microsoft Azure via an IP VPN (typically MPLS VPN). Offer any-to-any connectivity between branch offices and DCs. Microsoft cloud can be interconnect to customer's WAN to make it like any other site. Managed L3 connectivity. 
- ExpressRoute Direct: connect to Microsoft cloud at a peering location which are distributed across the world. Provides dual 100-Gbps or 10-Gbps connectivity, supporting Active/Active connectivity at scale.

Choosing any of the models will depend on the customer requirements, such as performance, budget and control over the network. 

|Feature/Aspect|ExpressRoute using a Service Provider|ExpressRoute Direct|
|---|---|---|
|Usage cases|Small to medium sized business looking for a simple setup with managed services|Large enterprises with mission-critical applications requiring high-performance connectivity|
|Connectivity|Connection via a service provider's infrastructure|Direct connection to Microsoft's network through dual 10-Gbps or 100-Gbps ports|
|Circuit SKUs|Ranges from 50 Mbps to 10 Gbps|10-Gbps: 1, 2, 5, 10 Gbps; 100-Gbps: 5, 10, 40, 100 Gbps|
|Optimization|Optimized for single tenant|Optimized for a single tenant with multiple business units|
