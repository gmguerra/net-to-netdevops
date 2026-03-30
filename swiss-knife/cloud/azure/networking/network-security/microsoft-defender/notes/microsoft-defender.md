# Network Security

It covers different technologies, devices and processes. All of them needs to have a level of network security. Security provides a set of rules and configurations designed to protect the integrity, confidentiality and accessibility of computer networks and data. Security needs to be everywhere, and Azure provide solutions to protect organizations from the ever-growing risks of attacks. 

Network Security is an specific path of security, covering securing Virtual Networks, establishing private connections, preventing and mitigating external attacks, and securing DNS. 

Microsoft Azure applies different Network Security Controls, from Microsoft Security Benchmarks. These benchmarks are frameworks that includes Microsoft's own insights, external insights on Azure and a combination of other cloud provider framework, ensuring consistency between environments. Security Controls applicable to network:
- NS-1: Establish network segmentation boundaries
- NS-2: Secure cloud services with network controls
- NS-3: Deploy firewall at the edge of enterprise network
- NS-4: Deploy intrusion detection/prevention systems (IDS/IPS)
- NS-5: Deploy DDOS protection: There's always a chance that an attacker tries to DDoS the network. Explicit recommendations for this point.
- NS-6: Deploy WAF
- NS-7: Simplify network security configuration
- NS-8: Detect and disable insecure services and protocols
- NS-9: connect on-premises or cloud network privately
- NS-10: Ensure DNS security

This recommendations can be used by customers to help secure their cloud services. 
Two types: 
- Services baselines: apply the controls to individual cloud services to provide recommendations on that service's security configuration. Implementation of the security control to an specific Azure service
- Security controls: Generally applicable across cloud workloads. Each recommendation identifies a list of stakeholders that are involved in planning, approving or implementing the benchmark. High level description, not specific to a technology.
## Microsoft Defender for Cloud

Cloud Native Application Protection Platform, combines multiple cloud security tools to protect apps across their lifecycle. Helps streamline the process for meeting network regulatory compliance requirements. 

It provides a regulatory compliance dashboard that shows the status of all the assessments within the Azure environment for the chosen standard and regulations. Compliance posture improves when reducing risks and following recommendations. Provides the passing vs failing assessments associated with each standard. 

For each security control (the security controls mentioned above), the Microsoft Defender for Cloud will provide the failing items and the resources where it needs to be addressed:

- Subscriptions the standard is applied on.
- List of all controls for that standard.
- View the details of passing and failing assessments associated with that control.
- Number of affected resources.
- Severity of the alert.