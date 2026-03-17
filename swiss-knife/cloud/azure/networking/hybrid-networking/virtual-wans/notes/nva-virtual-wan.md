# Network Virtual Appliance (NVA) inside a virtual WAN hub

A Virtual WAN support connections from many different technologies, including ExpressRoute, VPN Gateway, Barracuda CloudGen WAN, Cisco Cloud OnRamp for multicloud and VMware SD-WAN. This kind of devices are known as network virtual appliances (NVAs). These devices enable transitive connectivity throughout an organization's Virtual WAN

Different partners provide NVAs, which can be found in Azure Marketplace and be deployed into a virtual hub. NVAs are deployed as a managed application in Azure. 

When deploying an NVA, two resource groups are created in the subscription: 
- Customer Resource Group: Application placeholder for the managed application, used to expose any customer properties needed to be exposed.
- Managed resource group: a resource group that can't be managed by customers. 

NVA is configured as part of the deployment. 

As opposed to VPN Gateways, there is no need to create site resources in S2S or P2P connection resources ti connect branch sites to NVA in the Virtual WAN hub. There is still needed the creation of Hub-to-VNET connections to connect the Virtual WAN hub to Azure VNets.

### Deployment options: 

Different NVA partners support different deployment mechanisms, 
- Azure Marketplace Managed Application: All of the NVA partners Azure Marketplace Managed Application workflow. Easy way to deploy NVAs into Virtual WAN hub. The portal captures the critical deployment and config parameters needed to deploy and boot-strap the NVA. 
- NVA orchestrator deployments: depending on the partner, they allow the deployment of NVAs into the hub directly from the NVA orchestration or management software. When deploying via orchestration, the orchestrators need permission to interact with Azure environment. "robotic" account with permissions. Specific for NVA provider implementation. 
- Other mechanisms: NVA may offer different mechanisms, as ARM templates and Terraform. 

### Planning NVAs in Virtual WAN

Virtual WAN has a fixed subnet size, so IPs are limited. Ensure Virtual WAN hub has sufficient IP address to allow scalability and future deployment updates. 