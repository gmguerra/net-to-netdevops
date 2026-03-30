# Azure Firewall Manager

When there are multiple firewalls, is difficult to keep the firewall rules in sync. Also, for IT teams is important to define base firewall policies and enforce them across multiple business units. 

For this reasons Azure Firewall Manager was created. This is a security management service that provides central security policy and route management for cloud-based security perimeters, suuch as multiple Azure Firewall instances. Can provide security management for two network architecture types:
- Secured virtual hub: When Security and routing policies are associated with a Virtual WAN hub, this is called a secured virtual hub. Underlying resource is a virtual WAN hub.
- Hub virtual network: when the security policies are associated with a Hub VNet. Azure Firewall Policy is support and can peer spoke virtual networks that contain the workload servers and services, so the firewalls in the VNet ensure security in those connections. Underlying resource is a VNet. 

Firewall policies are created in Azure Firewall Manager and applied rapidly to multiple firewalls.

### Features

Centralizing firewall configuration among multiple Azure Firewall instances. Firewall manager enables: 
- Span multiple Azure subscriptions
- Span different Azure regions
- Implement hub and spoke architectures to provide for traffic governance and protection. 

The factors that might help an administrator to decide whether his organization needs a Firewall Manager:
- Complexity: Depending on the complexity of the organization's firewall and security requirements. 
- Need for centralized management: Depending if managing the Firewalls centrally is beneficial to the organization
- Number of Virtua Networks: Depending on the manageability of the current virtual network infrastructure. If several VNets with many different Firewalls exists in the cloud, the organization might benefit. 