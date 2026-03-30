# Azure Firewall

Cloud-native, intelligent network firewall security service used to protect Azure Virtual Network resources. Has a built-in high availability and unrestricted cloud scalability. Works for Internet and internal traffic. Internal traffic includes spoke-to-spoke and hybrid cloud traffic between on-prem network and Azure VNet. 

It can be deployed in a subnet of a VNet or, more commonly, deployed in a hub and spoke architecture, with FW living in the hub. Shield for VNet, allowing legitimate traffic and denying the rest. 

Threat intelligence based filtering, can alert and deny traffic from or to known malicious IPs or domains. Microsoft thread intelligence service identifies and updates these malicious IPs or domains. Azure FW is stateful, so it differentiates between legitimate packet and malicious packets.

Customer would like to use Azure firewall in different scenarios: 
- Protect network against infiltration
- Protect network against user error
- When e-commerce or credit cards are used in the apps inside Azure
- In Spoke-to-Spoke connectivity
- Monitor incoming and outgoing traffic

## Azure Firewall SKUs:

Azure Firewall has 3 SKUs: Basic, Standard and Premium: 
- Basic: Up to 250 Mbps, designed for small and medium business environments, threat intelligence in alert mode only
- Standard: Up to 30Gbps, designed for enterprise environments, L3-L7 filtering, DNS proxy, web categories, full threat intelligence.
- Premium: Up to 100Gbps, designed for regulated/sensitive environments (healthcare/payment), TLS inspection, IDPS, full URL filtering, PCI DSS compliance

## Azure Firewall rules

Azure Firewall denies all the traffic by default, until rules are manually configured to allow traffic. Rules are organized inside rules collections, which are contained in Rule Collection Groups. In Azure Firewall, there are different types of rules:
- NAT rules: translate and filter inbound internet traffic based on Firewall's public IP and a specified port number. Used to enable remote desktop connection to a VM, allowing connections and translating firewall's public IP address and port 3389 to the private IP address of the VM
- Application: Filter traffic based on an FQDN. Used e.g. to allow outbound traffic to access Azure SQL Database instance using the FQDN.
- Network: Filters traffic based on one or more of the three network parameters: IP address (src or dst), port and protocol. Used to allow traffic flows.

Rules are applied in priority order. Rules based on threat intelligence are given the highest priority and are processed first. After that, rules are applied by type: NAT rules, then network rules and finally application rules. Within each type, rules are processed according to the priority values assigned when the rule is created, from lowest value to highest value.