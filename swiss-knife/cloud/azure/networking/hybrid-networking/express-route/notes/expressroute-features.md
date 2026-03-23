# ExpressRoute global reach to connect geographically dispersed networks

ExpressRoute GlobalReach is a capability where a link between ExpressRoute circuits is created to enable a private network between the on-premises networks. This communication flows over Microsoft's global network. This is a complementary service to ISP's WAN implementation, connecting branch offices worldwide. Useful when the ISP operates regionally but not globally. A way to integrate remote sites into your ISP's WAN. Effectively bypasses Azure cloud environment. 

It's useful to leverage connectivity in sites that already have an ExpressRoute connection. Data is transmitted securely across Microsoft's private network, reducing exposure to potential threats compared to internet-based connections. Also, Microsoft's network offers high speeds that can significantly reduce latency, faster and more efficient data transfers between sites. Can be easily scaled to accommodate growing network demands with a centralized managed by Azure, which simplifies configuration and monitoring of network connections. 

# ExpressRoute improved data path with ExpressRoute FastPath

Feature to enhance data path performance between on-premises networks and VNets. When enabled, Microsoft will route customer traffic from the MSEE to directly to the virtual machines, bypassing the ER Virtual Network Gateway. Available on all ExpressRoute circuits. 

Useful for enterprises that need consisten and high performance connectivity to Azure for mission-critical applications. 

Benefits:
- Improved performance reduces latency and increases throughput by allowing data to bypass the Azure WAN, providing a more direct path to the VNet. Latency is reduced due to the fewer number of hops. Higher throughput is achieved by supporting higher data transfer rates, making it suitable for bandwidth intensive applications and workloads.  
- Optimized routing: enhance overall efficiency of network operations
- Reliability: more direct connection makes less chance of network congestion or packet loss. 
- Security: ensures data travels through fewer intermediary points, potentially reducing exposure to security risks. 

Some limitations:
- As gateway is bypassed, UDRs on the gateway subnet has no impact. 
- The traffic from on-prem to VNets that are peered to the VNet of the gateway will continue to go through the GW.  
- If there is a basic load balancer, the traffic destined to the devices behind that load balancer will use the gateway. 
- If you connect to a private endpoint in the virtual network from the on-prem, the connection will go through the virtual network gateway

# Other features

## BFD 
If any ExpressRoute circuit fails, BGP would switch the traffic over. But BGP is not fast to converge. Bidirectional Forwarding Detection enables much faster link failover (sub-second). 

## MACsec

Used to encrypt traffic in the ExpressRoute direct method, encrypting the traffic between the customer edge router in the meet me, and the MSEE router. Not end-to-end encryption, just between routers.

## VPN

A S2S or P2S VPN can be created, with VPN gateways in both ends making that connection. The gateways must sit behind the Azure virtual network Gateway for the case in the cloud, and for on-prem behind the CEs (or maybe the CEs)  