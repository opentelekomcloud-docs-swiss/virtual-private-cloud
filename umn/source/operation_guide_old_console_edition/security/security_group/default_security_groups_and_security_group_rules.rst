:original_name: vpc_SecurityGroup02_0002.html

.. _vpc_SecurityGroup02_0002:

Default Security Groups and Security Group Rules
================================================

The system creates a default security group for each account. By default, the default security group rules:

-  Allow all outbound packets: Instances in the default security group can send requests to and receive responses from instances in other security groups.
-  Deny all inbound packets: Requests from instances in other security groups will be denied by the default security group.


.. figure:: /_static/images/en-us_image_0000001230120807.png
   :alt: **Figure 1** Default security group

   **Figure 1** Default security group

.. note::

   -  You cannot delete the default security group, but you can modify the rules for the default security group.
   -  If two ECSs are in the same security group but in different VPCs, the ECSs cannot communicate with each other. To enable communications between the ECSs, use a VPC peering connection to connect the two VPCs.

:ref:`Table 1 <vpc_securitygroup02_0002__en-us_topic_0118534003_table493045171919>` describes the default rules for the default security group.

.. _vpc_securitygroup02_0002__en-us_topic_0118534003_table493045171919:

.. table:: **Table 1** Default security group rules

   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Direction | Protocol | Port/Range | Source/Destination                                           | Description                                                                                                        |
   +===========+==========+============+==============================================================+====================================================================================================================+
   | Outbound  | All      | All        | Destination: 0.0.0.0/0                                       | Allows all outbound traffic.                                                                                       |
   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Inbound   | All      | All        | Source: the current security group (for example, sg-*xxxxx*) | Allows communications among ECSs within the security group and denies all inbound traffic (incoming data packets). |
   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
