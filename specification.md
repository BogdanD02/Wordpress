---
Title:    Wordpress
Proposer: David Bogdan-Nicolae
Category: Bin Packing
---


Wordpress is an open-source application frequently used in creating websites, blogs and web applications. In ..., the authors present a high-load and fault tolerant Wordpress deployment scenario. The two characteristics are ensured by load balancing. One possibility to balance the load is at the DNS level using servers like Bind. Alternatively one can use as website entry point an HTTP reverse proxy capable of load balancing such as Varnish. In both cases Worpress instances need to be configured to connect to the same database. Furthermore, having redundancy and balancing at the front-end level, one would expect to have them alsso at the Database Management System (DBMS) level. One way to achieve that is to use a MySQL cluster, and configure Wordpress instances with multiple entry points to it. In this deployment scenario, the following constraints must be fulfilled:
- DNSLoadBalancer requires at least 1 instance of Wordpress and can serve at most 7 such instances.
- HTTPLoadBalancer requires at least 1 instance of Wordpress and can serve at most 3 such instances.
- Wordpress requires at least 3 instances of MySQL and MySQL can server at most 2 Wordpress instances
- Only one type of balancer must be deployed
- As Varnish exhibits load balancing features, it should not be deployed on the same virtual machine as any other balancer.
- Varnish and MySQL should not be deployed on the same virtual machine.
- If HTTPLoadBalancer is deployed, then at least 2 instances of Varnish must be deployed too.
- There must be at least 2 entry points to the MySQL cluster
- No more than 1 DNSLoadBalancer can be deployed
- Balancer components must be deployed on a single virtual machine.

The format of the data files is as follows:
- The first 3 lines contain the number of components, the different types of hardware requirements and the number of virtual machine offers at our disposal.
- On the next lines are the specification of each virtual machine
- Afterwards follow the hardware requirements of each component
- On the last line is the price of each virtual machine.

An example input is:
<pre>
NoComponents = 5;
HardwareReq = 3;
VMOffers = 20;

VMSpecs = [|64, 976000, 1000, 
|64, 488000, 8000, 
|64, 1952, 1000, 
|32, 244000, 2000, 
|32, 244000, 4000, 
|16, 122000, 2000, 
|16, 30000, 2000, 
|17, 117000, 24000, 
|16, 122000, 1000, 
|8, 61000, 6000, 
|8, 68400, 2000, 
|8, 68400, 2000, 
|4, 15000, 2000, 
|4, 30500, 3000, 
|4, 30500, 1000, 
|2, 7500, 1000, 
|2, 3750, 2000, 
|1, 1700, 1000, 
|1, 3750, 1000, 
|1, 3750, 1000|];
             
CompREQ = [| 2,  512, 1000,
           | 2,  512, 2000,
           | 4, 2048,  500,
           | 4, 2048,  500,
           | 4, 4000,  500 |];
           
VMPrice = [8403, 9152, 16000, 4105, 4576, 1373, 1430, 5400, 3079, 1470, 1301, 1288, 402, 827, 379, 146, 128, 58, 93, 98 ];
</pre>

For the deployment of 3 Wordpress instances,
