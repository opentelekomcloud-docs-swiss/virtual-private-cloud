:original_name: en-us_topic_0052003963.html

.. _en-us_topic_0052003963:

Differences Between Security Groups and Firewalls
=================================================

You can configure firewall and security group rules to protect the instances in your VPC, such as ECSs, CCI instances, and databases.

-  A security group protects the instances in it.
-  A firewall protects associated subnets and all the resources in the subnets.

For details, see :ref:`Figure 1 <en-us_topic_0052003963__fig9582182315479>`.

.. _en-us_topic_0052003963__fig9582182315479:

.. figure:: /_static/images/en-us_image_0000001818982946.png
   :alt: **Figure 1** Security groups and firewalls

   **Figure 1** Security groups and firewalls

:ref:`Table 1 <en-us_topic_0052003963__table53053071174845>` describes the differences between security groups and firewalls.

.. _en-us_topic_0052003963__table53053071174845:

.. table:: **Table 1** Differences between security groups and firewalls

   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Category              | Security Group                                                                                                                                                         | Firewall                                                                                                                                                                                                                                                  |
   +=======================+========================================================================================================================================================================+===========================================================================================================================================================================================================================================================+
   | Protection Scope      | Protects instances in a security group, such as ECSs, CCI instances, and databases.                                                                                    | Protects subnets and all the instances in the subnets.                                                                                                                                                                                                    |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Rules                 | Does not support **Allow** or **Deny** rules.                                                                                                                          | Supports both **Allow** and **Deny** rules.                                                                                                                                                                                                               |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Matching Order        | If there are conflicting rules, they are combined and applied together.                                                                                                | If rules conflict, the rule with the highest priority takes effect.                                                                                                                                                                                       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Usage                 | -  When creating an instance, such as an ECS, you must select a security group. If you do not have a security group, a default security group will be created for you. | Selecting a firewall is not allowed when you create a subnet. You must create a firewall, add inbound and outbound rules, associate subnets with it, and enable firewall. The firewall then protects the associated subnets and instances in the subnets. |
   |                       | -  After creating an instance, you can:                                                                                                                                |                                                                                                                                                                                                                                                           |
   |                       |                                                                                                                                                                        |                                                                                                                                                                                                                                                           |
   |                       |    -  Add or remove the instance to or from the security group on the security group console.                                                                          |                                                                                                                                                                                                                                                           |
   |                       |    -  Associate or disassociate a security group with or from the instance on the instance console.                                                                    |                                                                                                                                                                                                                                                           |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Packets               | Packet filtering based on the 3-tuple (protocol, port, and source/destination) is supported.                                                                           | Packet filtering based on the 5-tuple (protocol, source port, destination port, and source/destination) is supported.                                                                                                                                     |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
