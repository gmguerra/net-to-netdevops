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