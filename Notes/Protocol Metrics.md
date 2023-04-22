2304211930
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Protocol Metrics



RIP Metric - Hop Count

The maximum hop count by default is 15.
Paths furthur than 15 hops are marked as 'unreachable'
Rip is used in only small and test enviornments
Less hops the better
Uses the shortest hop count , doesnt take the bandwidth of the link into account
Only the lowest metric actually make it into the routing table


OSPF Metric - Cost

Automatically derived from interface bandwidth by default
you can manually conigure the cost of links if you want to manipulate the path
Takes bandwidth into account for faster speeds


IS-IS Metric - Cost

Not automatically derived from interface bandwitdth 
you need to manually configure the bandwidth
If not configured the lowest hop count will be used

EIGRP MEtric

Uses the bandwidth and delay of links to calculate the metric
You can manually conigure the delay on links



## Choosing a routing Protocol

Rip uses hop count and has a default maxium metric of 15 it is not usually used in production netowrs because of its scalility limiattions
Eigrp is very simple to maintain, calculates changes very quickly and its metric calculation will noramlly choose the best path by deafult it is typically only supported on cisco routers 
OSPF metric calcuation will typically choose the best path by default it is an open standard which is supported by all venfodrs routes and is the most comnly deplyed IGP today
IS-IS is only ysed in service Provider networks or large organizations with their own MPLS networks who choose it because of its scalability

## ECMP - Equal Cost Multi Path

If multiple paths have an equal method, the router will enter all paths to the routing table and load balance between them

All IGP's have ECMP enabled by default.

Also works with static routes.


---
# Reference