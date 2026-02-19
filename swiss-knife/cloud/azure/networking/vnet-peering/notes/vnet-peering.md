Enables you to connect separates VNets with optimal network performance, whether they are in the same azure region (VNet peering) or in different regions (Global VNet peering). 

Peering comes in a few different flavors:
- Local regional peering: when two VNets are on the same Region. Common in Hub-Spoke topology and interlink workloads in separate networks through one to another. 
- Global VNet peering: VNets can be interlinked across regional boundaries. Azure private backbone is used to traverse privately from a VNet to another. Usefil if you are interconnecting multiple sites, or you have a workload in another region. 

Regardless of the above, the creation process is nearly identical. Either via portal, CLI or template, you can configure the direction of both sides: you choose what communication should flow between one VNet to another, either if it's bidirectional or unidirection. 

**Consideration:** Any two VNets that you would like to peer cannot overlap between them. 

Network traffic between peered VNets is private, using microsoft backbone network as mentioned above.  No public internet gateways or encryption is required in communications between peered networks. 

Peered VNets appear as one, for connectivity purposes. 

**Benefits**
- Low-latency, high-bandwidth connection between resources in different VNets
- Security for VNets to block access from or to other VNets or subnets.
- Transfer data between VNets across different Azure things: Azure subscriptions, Microsoft Entra tenants, deployment models, and Azure regions.
- Azure Resource Manager can be useful to create VNets, peering can be done between VNets deployed with ARM or between a VNets deployed with ARM with VNet deployed via the classic model
- No downtime in VNets when peering or after peering is done. 
## Configure VNet peering
1. Create two VNets
2. Peer the VNets (when the peering is added in one VNet, the second VNet config is automatically added)
3. Deploye VMs in each VNet and test communication between them.

### Gateway transit and connectivity
A VPN gateway in the peered VNet can be added as a gateway transit point. With this you can achieved that a peered VNet accesses other resources through the remote gateway. A VNet can only have one gateway. This is supported for both VNet peering and Global VNet peering. 

Having this, the subnet gateway could:
- Use site-to-site VPN to connect to an on-premises network.
- Use a VNet-to-VNet connection to another VNet
- Use a point-to-site VPN to connect to a client. 

Basically, a VNet shares the gateway transit with its peered VNet and get access to remote resources. You don't need to deploy a VPN gateway for all the VNets if you have a peering already in place. 

