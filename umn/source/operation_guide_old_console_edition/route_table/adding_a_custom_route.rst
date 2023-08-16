:original_name: vpc_route02_0003.html

.. _vpc_route02_0003:

Adding a Custom Route
=====================

Scenarios
---------

If ECSs in a VPC need to access the Internet, add a custom route to enable the ECSs to access the Internet through an ECS that has an EIP bound.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. On the console homepage, under **Network**, click **Virtual Private Cloud**.
#. In the navigation pane on the left, click **Virtual Private Cloud**.
#. On the **Virtual Private Cloud** page, locate the VPC to which a route is to be added and click the VPC name.
#. On the **Route Tables** tab, click **Add Route**.
#. Set route details on the displayed page.

   -  **Destination** indicates the destination CIDR block. The default value is **0.0.0.0/0**. If the traffic originates from a VPC, the destination can be a subnet CIDR block in this VPC. If the traffic originates from outside the VPC, the destination CIDR block cannot conflict with any of the subnet CIDR blocks in this VPC. The destination of each route must be unique.
   -  **Next Hop**: indicates the IP address of the next hop. Set it to a private IP address or a virtual IP address in a VPC.

   .. note::

      If the next hop is a virtual IP address, an EIP must be bound to the virtual IP address. Otherwise, access to the Internet through this virtual IP address is not possible. (A custom route is used to forward traffic from the virtual IP address to the Internet.)

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0226820252.png
