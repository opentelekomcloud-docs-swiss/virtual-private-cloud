:original_name: SecurityGroup_0003.html

.. _SecurityGroup_0003:

Default Security Group and Its Rules
====================================

If you have not created any security groups yet, the system automatically creates a default security group for you and associates it with the instance when you create it. A default security group has the following rules:

-  Inbound rules control incoming traffic to instances in a security group. Only instances in the same security group can communicate with each other, and all inbound requests are denied.
-  Outbound rules allow all outbound traffic and response traffic to the outbound requests.


.. figure:: /_static/images/en-us_image_0000001865662829.png
   :alt: **Figure 1** Default security group

   **Figure 1** Default security group

.. note::

   -  You cannot delete the default security group, but you can modify existing rules or add rules to the group.
   -  The default security group denies all external requests. To log in to an instance associated with this security group, add a security group rule by referring to :ref:`Remotely Logging In to an ECS from a Local Server <en-us_topic_0081124350__section14933617154810>`.

:ref:`Table 1 <securitygroup_0003__table694213763818>` describes the default rules for the default security group.

.. _securitygroup_0003__table694213763818:

.. table:: **Table 1** Rules in the default security group

   +-----------+------+-----------------+------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Direction | Type | Protocol & Port | Source/Destination                       | Description                                                                                                                   |
   +===========+======+=================+==========================================+===============================================================================================================================+
   | Inbound   | IPv4 | TCP: 22         | Source: 0.0.0.0/0                        | Allows IPv4 traffic to reach instances in the security group over SSH port 22 for remotely logging in to Linux instances.     |
   +-----------+------+-----------------+------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | TCP: 3389       | Source: 0.0.0.0/0                        | Allows IPv4 traffic to reach instances in the security group over RDP port 3389 for remotely logging in to Windows instances. |
   +-----------+------+-----------------+------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | TCP: 80         | Source: 0.0.0.0/0                        | Allows IPv4 traffic to reach the websites deployed on the instances in the security group over HTTP port 80.                  |
   +-----------+------+-----------------+------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | TCP: 443        | Source: 0.0.0.0/0                        | Allows IPv4 traffic to reach the websites deployed on the instances in the security group over HTTPS port 443.                |
   +-----------+------+-----------------+------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | ICMP: all       | Source: 0.0.0.0/0                        | Allows external IPv4 servers to ping the instances in the security group to verify the network connectivity.                  |
   +-----------+------+-----------------+------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv4 | All             | Source: Default security group (default) | Allows IPv4 instances in the security group to communicate with each other using any protocol over any port.                  |
   +-----------+------+-----------------+------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Inbound   | IPv6 | All             | Source: Default security group (default) | Allows IPv6 instances in the security group to communicate with each other using any protocol over any port.                  |
   +-----------+------+-----------------+------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Outbound  | IPv4 | All             | Destination: 0.0.0.0/0                   | Allows all traffic from the instances in the security group to any IPv4 address over any port.                                |
   +-----------+------+-----------------+------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Outbound  | IPv6 | All             | Destination: ::/0                        | Allows all traffic from the instances in the security group to any IPv6 address over any port.                                |
   +-----------+------+-----------------+------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
