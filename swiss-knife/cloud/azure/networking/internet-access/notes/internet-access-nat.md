# Internet Access with Azure Virtual NAT

NAT allows internal resources within a private network share a public IPv4 address to access internet. Rather than purchasing an IPv4 address for each resources that requires internet access, NAT enables mapping on ongoing requests from internal resources to an external public IP address. 

All UDP and RCP outbound flows from any VM will use NAT for internet connectivity, with no further configuration needed. It's not needed to create any UDRs, as NAT takes precedence over other outbound scenarios, replacing the default internet gateway of a subnet. 

NAT scales automatically, supporting dynamic workflows. It supports up to 16 public IP addresses,. By using port network address translation (PAT), it provides 64,000 concurrent flows for UDP and TCP per public IP, which means that around 1M concurrent flows are available with the total pool of 16 IPs.  

## NAT Compatibility:
- Load balancer
- Public IP address
- Public IP prefix

## Limitations of NAT 
- IPv4 only
- NAT is per VNet, can't span multiple VNets
- IP fragmentation isn't supported. 