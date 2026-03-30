# Azure DDoS Protection

DoS (denial of service) is a type of cyberattack that prevents the access to services or systems by flooding the network capacities of them. DoS is for a single source, while DDoS is for multiple networks and systems as source. DDoS aims to drain APIs or application's resources, making them unavailable to legitimate users. Targets are endpoints reachable through the Internet. 

Azure DDoS Protection sits in front the VNet and protects the resources. Includes protection to VMs Public IP Addresses, load balancer and application gateways. When is paired with App Gateway WAF, it provides L3 to L7 protection and mitigation capabilities. 

## Types of DDoS attacks:

Mainly 3 types:
- Volumetric attacks: Flood the network layer with a notable amount of seemingly legitimate traffic, including UDP flood, amplification floods and other spoofed-packet floods.
- Protocol attacks: Exploiting weak areas in the layer 3 and 4 protocol stack, including SYN flood attacks, reflection attacks, and other protocol attacks.
- Resource (application) layer attacks: application (mostly web) packets used to disrupt the transmission of data between hosts. Includes HTTP protocol violation, SQL injection, cross-site scripting and other L7 attacks

## Azure DDoS Protection implementation tiers

Two tiers that provide active traffic monitoring, always-on detection and automatic mitigation: 
- DDoS Network Protection: enabled on the environment as a whole. Target the protection to a VNet and volumetric protection is enabled on the network.
- DDoS IP protection: protecting a particular IP in the environment. 

The tiers include application-based mitigation policies, metric and alerts, mitigation reports and integration with Firewall Manager. Each tier is designed for different needs and scenarios. The decision to use one flavor or another comes down to pricing. Understanding the levels of protection of each is important, but at the end the decisions needs to be done based on what's important in the environment: 
- Protecting a complete network? DMZ? Core Network?
- Protecting an application by protecting the public facing IP address of that application? 

## Standard features of Azure DDoS Protection:
- Always-on Traffic monitoring: looking for indicators of DDoS attacks.
- Adaptive real time tuning and customization: profiling and adjusting to service's traffic
- DDoS Protection Analytics, metric and alerting: Detailed reports in five-minute increments during an attack, and a complete summary after the incident. Summarized metrics from each attack through Azure Monitor. Alerts can be configured at the start and stop of an attack, and over the attack's duration, using built-in attack metrics.
- DDoS Rapid Rapid Response: team that assists customers 24x7 when they are under a DDoS attack. An actual person. This person will walk you through the mitigation process.
- Turnkey protection: Simplified configuration protection all resources immediately. 
- Multi-layered protection: When deployed with a WAF, DDoS Protection protects both at both the network and application layers.
- Extensive mitigation itself. 
