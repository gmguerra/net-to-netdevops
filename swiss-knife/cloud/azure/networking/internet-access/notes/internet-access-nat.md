# Internet Access with Azure Virtual NAT

NAT allows internal resources within a private network share a public IPv4 address to access internet. Rather than purchasing an IPv4 address for each resources that requires internet access, NAT enables mapping on ongoing requests from internal resources to an external public IP address. 

All UDP and TCP outbound flows from any VM will use NAT for internet connectivity, with no further configuration needed. It's not needed to create any UDRs, as NAT takes precedence over other outbound scenarios, replacing the default internet gateway of a subnet. 

NAT scales automatically, supporting dynamic workflows. It supports up to 16 public IP addresses,. By using port network address translation (PAT), it provides 64,000 concurrent flows for UDP and TCP per public IP, which means that around 1M concurrent flows are available with the total pool of 16 IPs.  

## NAT Gateway 
Just focused in outbound NAT connectivity. Public IPs or prefixes attached to the NAT Gateway. NAT Gateway can be linked to particular subnets within the same region. NAT Gateway performs SNAT (Source NAT). It can be Zonal or Regional, but not Zone redundant 

Kind of smart. If requests are coming from a load balancer, it will keep them going through the load balancer. But new connections towards Internet will use the NAT Gateway. It will work with the rest of services deployed.
## NAT Compatibility:
- Load balancer
- Public IP address
- Public IP prefix

## Limitations of NAT 
- IPv4 only
- NAT is per VNet, can't span multiple VNets
- IP fragmentation isn't supported. 