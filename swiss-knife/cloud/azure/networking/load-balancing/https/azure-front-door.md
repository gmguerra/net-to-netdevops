# Azure Front Door

Is a Content Delivery Network for cloud services. Provides fast, reliable and secure access to applications' web static and dynamic web content globally. It sits in Microsoft's extensive global edge network, and provides efficient content delivery through global and local PoPs positioned close to enterprise and consumer users. 

Provides as well security features, and is content-delivery optimized. Capabilities:
- Static and dynamic content acceleration
- Support global load balancing
- Implement SSL offload
- Implement domain and certificate management
- Benefit from enhanced traffic analysis 
- Benefit from basic security capabilities

In the Azure Front Door Premium tier, security is optimized:
- WAF
- Bot protection
- Private Link support
- Integration with Microsoft Threat Intelligence and security analytics.

The user sends the request to the closer Microsoft Global Network data center. These locations are designed to cache content and deliver services with lower latency, improving the speed and responsiveness of apps for users worldwide. Once the request reaches Front Door, it determines where to direct the client request. The routing process includes the WAF, routing rules, rules engine and caching configuration. Requests can be routed depending on what the user needs, so it reaches the region that is optimized for that services. Front Door can even route the request to another cloud service or On-prem. 

The routing algorithm matches in the following order:
- HTTP protocol (HTTP or HTTPS)
- Hosts (URL hostname)
- Paths (specific path in the URL)

Front door provide response codes to clients, so they understand the purpose of the redirect. Commonly used to redirect HTTP request to HTTPS

As the rest of the load balancing solutions, it uses health probes to periodically check whether a backend is available or not. Front door uses these checks to determine the best backend resource to route the client's requests.