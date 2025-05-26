:original_name: SecurityGroup_0003.html

.. _SecurityGroup_0003:

Default Security Group
======================

If you have not created any security groups yet, the system automatically creates a default security group for you and associates it with the instance when you create it. A default security group has the following rules:

-  Inbound rules control incoming traffic to instances in a security group. Only instances in the same security group can communicate with each other, and all inbound requests are denied.
-  Outbound rules allow all outbound traffic and response traffic to the outbound requests.


.. figure:: /_static/images/en-us_image_0000001865662829.png
   :alt: **Figure 1** Default security group

   **Figure 1** Default security group

.. note::

   -  You cannot delete the default security group, but you can modify existing rules or add rules to the group.
   -  The default security group denies all external requests. To log in to an instance associated with this security group, add a security group rule by referring to :ref:`Remotely Logging In to an ECS from a Local Server <en-us_topic_0081124350__section14933617154810>`.

:ref:`Table 1 <securitygroup_0003__table493045171919>` describes the default rules for the default security group.

.. _securitygroup_0003__table493045171919:

.. table:: **Table 1** Default security group rules

   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Direction | Protocol | Port/Range | Source/Destination                                           | Description                                                                                                        |
   +===========+==========+============+==============================================================+====================================================================================================================+
   | Outbound  | All      | All        | Destination: 0.0.0.0/0                                       | Allows all outbound traffic.                                                                                       |
   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Inbound   | All      | All        | Source: the current security group (for example, sg-*xxxxx*) | Allows communications among ECSs within the security group and denies all inbound traffic (incoming data packets). |
   +-----------+----------+------------+--------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
