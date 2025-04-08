:original_name: overview_0004.html

.. _overview_0004:

Product Advantages
==================

Flexible Configuration
----------------------

You can create VPCs, add subnets, specify IP address ranges, and configure DHCP and route tables. You can configure the same VPC for ECSs that are in different availability zones (AZs).

Secure and Reliable
-------------------

VPCs are logically isolated through tunneling technologies. By default, different VPCs cannot communicate with each other. You can use firewalls to protect subnets and use security groups to protect ECSs. They add additional layers of security to your VPCs, so your network is secure.


.. figure:: /_static/images/en-us_image_0000001818983218.png
   :alt: **Figure 1** Secure and Reliable

   **Figure 1** Secure and Reliable

Seamless Interconnectivity
--------------------------

By default, instances in a VPC cannot access the Internet. You can use EIPs, load balancers, NAT gateways, VPN connections, and Direct Connect connections to enable access to or from the Internet.

By default, instances in different VPCs cannot communicate with each other. You can create a VPC peering connection to enable the instances in the two VPCs in the same region to communicate with each other using private IP addresses.

Multiple connectivity options are available to meet diverse service requirements for the cloud, enabling you to deploy enterprise applications with ease and lower enterprise IT operation and maintenance (O&M) costs.

High-Speed Access
-----------------

Dynamic BGP is used to provide access to various carrier networks. You can establish over 20 dynamic BGP connections to different carriers. Dynamic BGP connections enable real-time failovers based on preset routing protocols, ensuring high network stability, low network latency, and smooth access to services on the cloud.

Advantage Comparison
--------------------

:ref:`Table 1 <overview_0004__table1617718259238>` lists the advantages of a VPC over a traditional IDC.

.. _overview_0004__table1617718259238:

.. table:: **Table 1** Comparison between a VPC and a traditional IDC

   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Item                  | VPC                                                                                                                                                                                                             | Traditional IDC                                                                                                                                                                                                                               |
   +=======================+=================================================================================================================================================================================================================+===============================================================================================================================================================================================================================================+
   | Deployment cycle      | -  You do not need to perform complex engineering deployment, including engineering planning and cabling.                                                                                                       | You need to set up networks and perform tests. The entire process takes a long time and requires professional technical support.                                                                                                              |
   |                       | -  You can determine your networks, subnets, and routes on based on service requirements.                                                                                                                       |                                                                                                                                                                                                                                               |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Total cost            | provides flexible billing modes for network services. You can select whichever one best fits your business needs. There are no upfront costs and network O&M costs, reducing the total cost of ownership (TCO). | You need to invest heavily in equipment rooms, power supply, construction, and hardware materials. You also need professional O&M teams to ensure network security. Asset management costs increase with any change in business requirements. |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Flexibility           | provides a variety of network services for you to choose from. If you need more network resources (for instance, if you need more bandwidth), you can expand resources on the fly.                              | You have to strictly comply with the network plan to complete the service deployment. If there are changes in your service requirements, it is difficult to dynamically adjust the network.                                                   |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Security              | VPCs are logically isolated from each other. You can use security features such as firewalls and security groups, and even security services like Advanced Anti-DDoS (AAD) to protect your cloud resources.     | The network is insecure and difficult to maintain. You need professional technical personnel to ensure network security.                                                                                                                      |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
