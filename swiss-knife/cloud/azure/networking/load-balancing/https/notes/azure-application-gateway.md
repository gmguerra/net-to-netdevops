# Azure Application Gateway

Web traffic load balancer that manages traffic to Azure web applications. Works on the layer 7 and make decisions based on HTTP request attributes like URL paths and host headers. Provides SSL/TLS termination, autoscaling, zone redundancy and integration with Web Application Firewall for security by inspecting the traffic it receives. 

Processes network traffic to web apps hosted on a pool of web servers.  

Supports HTTP, HTTPS, HTTP/2 and websocket protocols. It also supports end-to-end request encryption, autoscaling to dynamically adjust capacity to the web traffic load, connection draining to remove backend pool members during planned service updates, session stickiness to ensure client requests in the same session are routed to the same backend server and path and URL based routing. 

Flow:
- Public or private frontend IP address, depending if the app should be public facing, or internal. 
- Listeners receive incoming traffic requests. Protocol, port, Hostname and IP address. 
- The application gateway routes the request to the appropriate backend based in the configured rule. 
- Traffic is routed by checking the rules that may contain specific needs for specific URL paths or request headers. 
- Application Gateway routes traffic to the server using the HTTP setting configuration specified. 
- Once HTTP setting is configured, it needs to be associated with a routing rule. 

Endpoints types:
- VM
- VM Scale set
- IP Address
- App services

Traffic is sent to the backend servers that are healthy, so the health probes are in place checking whether an endpoint is up or not. 

Azure Application Gateway components:
- Front-end IP Address: IP Address clients points to. Public, private or both. 
- Listeners: logical entity that checks for incoming connection requests. Listener task is to review the request and, if it matches protocol, port, hostname and IP address configured it accepts the requests. At least one listener is mandatory. 
- Request routing rules: determines how to route traffic on the listener. Bind the listener, backend server pool and the backend HTTP settings. When a listener accepts a request, the request routing rule forwards it to the backend or elsewhere as per the configuration. If routed to the backend, the request routing rule defines which backend server pool to forward it to. 
- Backend pools: collection of web servers or endpoints. By configuring an IP address, the App Gateway can balance between backends that are on-prem
- Health probes. determine which servers are available in a backend pool. Servers are automatically added and removed form the backend pool based on their availability. 

### How components works together

Once a user request comes in an application gateway:
1. The request reaches the listener and takes the information the user is requesting by checking the URL and header/body, and provides the relevant information so it can be reviewed by a rule. 
2.  Web Application firewall is a component that works between the listener receives the request and the traffic is routed. It's optional feature that analyzes the data of the requests to detect and prevent different threats. 
3. The rule routes the traffic based on its configuration between the available nodes: VMs, VM scale set, On-prem/External app servers and Azure App Services 

### Routing configurations: 

Two primary methods of routing client requests:
- Path-based routing: sends the request with different URL paths to different pools of back-end servers. If a server is optimized for an specific task, by using an URL that specifies it it will route the traffic to that server. 
- Multiple Site routing: Enables configure more than one web application on the same Application Gateway instance. Multiple DNS names (CNAMEs) for the frontend IP address of the application gateway, specifying in the request the name of each site. Application Gateway uses separate listeners to wait for requests for each site, and each listeners passes the request to a different rule, which can route the request to servers in a different back-end pool. 

Other routing capabilities are: 
- Redirection: redirecting requests from one protocol to another (e.g. HTTP to HTTPS) or to another site.
- Rewrite HTTP headers
- Custom error pages: Instead of displaying default error pages, own branding and layout can be used. 