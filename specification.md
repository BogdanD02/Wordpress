---
Title:    Wordpress
Proposer: David Bogdan-Nicolae
Category: Bin Packing
---


Wordpress is an open-source application frequently used in creating websites, blogs and web applications. In ..., the authors present a high-load and fault tolerant Wordpress deployment scenario. The two characteristics are ensured by load balancing. One possibility to balance the load is at the DNS level using servers like Bind. Alternatively one can use as website entry point an HTTP reverse proxy capable of load balancing such as Varnish. In both cases Worpress instances need to be configured to connect to the same database. Furthermore, having redundancy and balancing at the front-end level, one would expect to have them also at the Database Management System (DBMS) level. One way to achieve that is to use a MySQL cluster, and configure Wordpress instances with multiple entry points to it. In this deployment scenario, the following constraints must be fulfilled:
- DNSLoadBalancer requires at least 1 instance of Wordpress and can serve at most 7 such instances.
- HTTPLoadBalancer requires at least 1 instance of Wordpress and can serve at most 3 such instances.
- Wordpress requires at least 3 instances of MySQL and MySQL can serve at most 2 Wordpress instances
- Only one type of balancer must be deployed
- As Varnish exhibits load balancing features, it should not be deployed on the same virtual machine as any other balancer.
- Varnish and MySQL should not be deployed on the same virtual machine.
- If HTTPLoadBalancer is deployed, then at least 2 instances of Varnish must be deployed too.
- There must be at least 2 entry points to the MySQL cluster
- No more than 1 DNSLoadBalancer can be deployed
- Balancer components must be deployed on a single virtual machine.

In order to deploy this application in the Cloud, we need to rent virtual machines from various Cloud Providers, e.g. Amazon Web Services (https://aws.amazon.com), Microsoft Azure (https://azure.microsoft.com/en-us), Google Cloud (https://cloud.google.com), and deploy the required components so that all the constraints above are fulfilled. Our goal is to minimize the total rent price of the required virtual machines.

