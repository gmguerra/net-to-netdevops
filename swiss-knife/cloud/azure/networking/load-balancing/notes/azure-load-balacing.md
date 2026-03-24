# Load balancing in Azure

Load balancing is the technique used to even distribute incoming network traffic to a group of backend computing resources. Goal:
- Optimization in the use of resources
- Maximize throughput
- Minimize response time
- Avoid overloading any single resources

Can also improve availability by sharing a workload across redundant resources.

Load balancing solutions can be categorized in global versus regional or HTTP(S) versus non-HTTP(S)

### Global vs Regional

- Global services distribute traffic across regional backends, clouds, or hybrid on-prem services. Route end-user traffic to the closes available backend. React to changes in service reliability or performance. System that load balance between application stamps, endpoints, or scale-units hosted across different regions or geographies.
- Regional load-balancing services distribute traffic within VNets across VMs or zonal and zone-redundant service endopoints within a region in a VNet.

## HTTP(S) vs non-HTTP(S)

HTTP(S) are those services that works in the Layer 7, only accepting HTTP(S) traffic. Intended for web applications or other HTTP(S) endpoints. Include features such as SSL offload, web application firewall, path-based load balancing, and session affinity

In the other hand, non-HTTP(S) load-balancing services can handle non-HTTP(S) traffic and are recommended for nonweb workloads.

### Load balancing solutions in Azure for HTTP(S) traffic

- Azure Application Gateway: provides application delivery controller (ADC) as a service, offering L7 load balancing capabilities. Used for web farm productivity optimization by offloading CPU-intensive SSL termination to the gateway.
- Azure Front Door: application delivery network that provides gloabl load balancing and site acceleration service for web applications. L7 capabilities for applications. Front Door includes SSL offload, path-based routing, fast failover and caching

### Load balancing solutions in Azure for non-https traffic:

- Azure Load Balancer: regional workloads, one input to multiple outputs. High-performance and ultra-low latency. Works on Layer 4 for all UDP and TCP protocols. Can handle millions of requests per second. Zone redundant, high availability across availability zones.
- Traffic Manager: multiregional option. Balance between different endpoints in different regions. DNS based solution, distribute traffic optimally between Azure regions, while providing high availability and responsiveness. Load balances at the domain level, so it can't fail over as quick as other solutions (Front door)

## Choose a Load Balancing solution 

To choose the load balancing solution, the load balancer decision tree. Interactive version available in the Azure portal, or a static version in Azure architecture center. These are the conditions to consider:
- Type of traffic: web application? Public-facing or private? 
- Scope: VMs and containers within a VNet, or across regions, or both? 
- Availability: SLA for the service
- Cost: additionally to the service itself, operational cost to manage a maintain a solution built on that service.
- Feature and limitations: Load balancers have their limitations and benefites

Apart from the standard architectural models in the charts, there are several combinations of the Azure load balancing solutions. Choose based on the complete solution to deploy. 

Azure Load Balancing - help me choose page in the Azure portal guide customers to choose a load-balancing solution. Interactive wizard.

## Summary

| Service             | Global/regional | Recommended traffic |
| ------------------- | --------------- | ------------------- |
| Azure Front Door    | Global          | HTTP(S)             |
| Traffic Manager     | Global          | non-HTTP(S)         |
| Application Gateway | Regional        | HTTP(S)             |
| Azure Load Balancer | Regional        | non-HTTP(S)         |

