# Azure Network Security Groups

Resource used to filter network traffic between Azure resources in Azure VNets. Contains security rules that allow or deny inbound network traffic to or outbound network traffic from, several types of Azure resources. Fundamental low-level piece of network control in Azure. Can be applied at a NIC level or Subnet level, simple allow or deny rules. Restrict traffic between subnets or within a subnet. 

One NSG can be applied to different resources, like generic NSGs for security posture. NSG per region at first, and then scale as per the needs. It is recommended to build NSGs at subnet level for simplicity. NSGs are not designed to sit at the edge of a network like a firewall.

NSGs contain a list of security rules that allow or deny traffic, either inbound or outbound. These rules evaluate the 5 tuple (source, dst ip and ports and protocol), CIDR and service tags. Service tag is a representation of azure services. This is a mapping of the IP CIDRs of an specific service in an specific region. For example, access to storage services in Azure Central US in an outbound direction. 

NBSG rules enable the traffic filtering. Works through a priority system. Priority can be configured from 100 and 4096 in inbound and outbound. There a default security rules in the range of priority 65000, these are low priority rules that create a default posture. These default rules allows traffic inbound from the same VNet and load balancer traffic is allowed, denying anything else inbound . In Outbound, it allows traffic towards the same VNet, and to the internet, while denying the rest of traffic. These can be overridden by creating any rule in high priority (lower number). 

Each rule can be specified with source and destination IP, ports and protocol. An NSG can contain as may rules as desired, within Azure subscription limits. NSGs and their defined rules are evaluated independently, processing the condition in each rule defined for each VM in the configuration. 

Effective security rules view is a Network Watcher feature used to view the aggregated inbound and outbound rules applied to a network interface. Provides visibility into security and admin rules applied to a network interface. 

For inbound traffic, Azure first processes NSG rules for any associated subnets and then any associated NIC, while for outbound traffic the process is reversed. 

NSGs are created within a VNet, so they need to be applied in that same region. 

An specific use case for Azure NSGs are as having as DMZ subnet accesible from the internet, but protecting the rest of your subnets. In that same manner, DMZ can speak with the other subnets. 

### Application security groups

Are tag objects that group different services to enforce security rules are equal among them. This ASGs are linked to a NIC of a resource. A rule can include an Application Security Group instead of an specific source or destination CIDR prefix. 

An ASG for web VMs and another to SQL resources, allowing communication between them just by using ASGs and NSGs. 