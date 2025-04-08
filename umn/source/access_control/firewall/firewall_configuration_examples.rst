:original_name: acl_0002.html

.. _acl_0002:

Firewall Configuration Examples
===============================

This section provides examples for configuring firewalls.

-  :ref:`Denying Access from a Specific Port <acl_0002__section11312173319432>`
-  :ref:`Allowing Access from Specific Ports and Protocols <acl_0002__section61291659102216>`

.. _acl_0002__section11312173319432:

Denying Access from a Specific Port
-----------------------------------

You might want to block TCP port 445 to protect against the WannaCry ransomware attacks. You can add a firewall rule to deny all incoming traffic from TCP port 445.

Firewall Configuration

:ref:`Table 1 <acl_0002__table553618145582>` lists the inbound rules required.

.. _acl_0002__table553618145582:

.. table:: **Table 1** Firewall rules

   +-----------+--------+----------+-----------+-------------------+-------------+------------------------+------------------------------------------------------------------+
   | Direction | Action | Protocol | Source    | Source Port Range | Destination | Destination Port Range | Description                                                      |
   +===========+========+==========+===========+===================+=============+========================+==================================================================+
   | Inbound   | Deny   | TCP      | 0.0.0.0/0 | 1-65535           | 0.0.0.0/0   | 445                    | Denies inbound traffic from any IP address through TCP port 445. |
   +-----------+--------+----------+-----------+-------------------+-------------+------------------------+------------------------------------------------------------------+
   | Inbound   | Allow  | All      | 0.0.0.0/0 | 1-65535           | 0.0.0.0/0   | All                    | Allows all inbound traffic.                                      |
   +-----------+--------+----------+-----------+-------------------+-------------+------------------------+------------------------------------------------------------------+

.. note::

   -  By default, a firewall denies all inbound traffic. You can add a rule to allow all inbound traffic if necessary.
   -  If you want a deny rule to be matched first, insert the deny rule above the allow rule. For details, see :ref:`Changing the Sequence of a Firewall Rule <vpc_acl_0004>`.

.. _acl_0002__section61291659102216:

Allowing Access from Specific Ports and Protocols
-------------------------------------------------

In this example, an ECS in a subnet is used as the web server, and you need to allow inbound traffic from HTTP port 80 and HTTPS port 443 and allow all outbound traffic. You need to configure both the firewall rules and security group rules to allow the traffic.

Firewall Configuration

:ref:`Table 2 <acl_0002__table195634095313>` lists the inbound and outbound rules required.

.. _acl_0002__table195634095313:

.. table:: **Table 2** Firewall rules

   +-----------+--------+----------+-----------+-------------------+-------------+------------------------+------------------------------------------------------------------------------------------+
   | Direction | Action | Protocol | Source    | Source Port Range | Destination | Destination Port Range | Description                                                                              |
   +===========+========+==========+===========+===================+=============+========================+==========================================================================================+
   | Inbound   | Allow  | TCP      | 0.0.0.0/0 | 1-65535           | 0.0.0.0/0   | 80                     | Allows inbound HTTP traffic from any IP address to ECSs in the subnet through port 80.   |
   +-----------+--------+----------+-----------+-------------------+-------------+------------------------+------------------------------------------------------------------------------------------+
   | Inbound   | Allow  | TCP      | 0.0.0.0/0 | 1-65535           | 0.0.0.0/0   | 443                    | Allows inbound HTTPS traffic from any IP address to ECSs in the subnet through port 443. |
   +-----------+--------+----------+-----------+-------------------+-------------+------------------------+------------------------------------------------------------------------------------------+
   | Outbound  | Allow  | All      | 0.0.0.0/0 | All               | 0.0.0.0/0   | All                    | Allows all outbound traffic from the subnet.                                             |
   +-----------+--------+----------+-----------+-------------------+-------------+------------------------+------------------------------------------------------------------------------------------+

**Security group configuration**

:ref:`Table 3 <acl_0002__table30323767195135>` lists the inbound and outbound security group rules required.

.. _acl_0002__table30323767195135:

.. table:: **Table 3** Security group rules

   +-----------+----------------------+------+------------------------+---------------------------------------------------------------------------------------------------------------+
   | Direction | Protocol/Application | Port | Source/Destination     | Description                                                                                                   |
   +===========+======================+======+========================+===============================================================================================================+
   | Inbound   | TCP                  | 80   | Source: 0.0.0.0/0      | Allows inbound HTTP traffic from any IP address to ECSs associated with the security group through port 80.   |
   +-----------+----------------------+------+------------------------+---------------------------------------------------------------------------------------------------------------+
   | Inbound   | TCP                  | 443  | Source: 0.0.0.0/0      | Allows inbound HTTPS traffic from any IP address to ECSs associated with the security group through port 443. |
   +-----------+----------------------+------+------------------------+---------------------------------------------------------------------------------------------------------------+
   | Outbound  | All                  | All  | Destination: 0.0.0.0/0 | Allows all outbound traffic from the security group.                                                          |
   +-----------+----------------------+------+------------------------+---------------------------------------------------------------------------------------------------------------+

A firewall adds an additional layer of security. Even if the security group rules allow more traffic than that actually required, the firewall rules allow only access from HTTP port 80 and HTTPS port 443 and deny other inbound traffic.
