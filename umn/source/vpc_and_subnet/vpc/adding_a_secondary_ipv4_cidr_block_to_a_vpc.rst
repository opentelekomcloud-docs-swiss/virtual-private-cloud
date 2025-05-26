:original_name: vpc_vpc_0007.html

.. _vpc_vpc_0007:

Adding a Secondary IPv4 CIDR Block to a VPC
===========================================

Scenarios
---------

When you create a VPC, you specify a primary IPv4 CIDR block for the VPC, which cannot be changed. To extend the IP address range of your VPC, you can add a secondary CIDR block to the VPC. Five secondary CIDR blocks can be added.

Notes and Constraints
---------------------

-  You can allocate a subnet from either a primary or a secondary CIDR block of a VPC. A subnet cannot use both the primary and the secondary CIDR blocks.

   Subnets in the same VPC can communicate with each other by default, even if some subnets are allocated from the primary CIDR block and some are from the secondary CIDR block of a VPC.

-  If a subnet in a secondary CIDR block of your VPC is the same as or overlaps with the destination of an existing route in the VPC route table, the existing route does not take effect.

   If you create a subnet in a secondary CIDR block of your VPC, a route (the destination is the subnet CIDR block and the next hop is **Local**) is automatically added to your VPC route table. This route allows communications within the VPC and has a higher priority than any other routes in the VPC route table. For example, if a VPC route table has a route with the VPC peering connection as the next hop and 100.20.0.0/24 as the destination, and a route for the subnet in the secondary CIDR block has a destination of 100.20.0.0/16, 100.20.0.0/16 and 100.20.0.0/24 overlaps and traffic will be forwarded through the route of the subnet.

-  :ref:`Table 1 <vpc_vpc_0007__table1060431941314>` lists the secondary CIDR blocks that are not supported.

   .. _vpc_vpc_0007__table1060431941314:

   .. table:: **Table 1** Restricted secondary CIDR blocks

      +-----------------------------------+-----------------------------------+
      | Type                              | CIDR Block (Not Supported)        |
      +===================================+===================================+
      | Reserved system CIDR blocks       | -  100.64.0.0/10                  |
      |                                   | -  214.0.0.0/7                    |
      |                                   | -  198.18.0.0/15                  |
      |                                   | -  169.254.0.0/16                 |
      +-----------------------------------+-----------------------------------+
      | Reserved public CIDR blocks       | -  0.0.0.0/8                      |
      |                                   | -  127.0.0.0/8                    |
      |                                   | -  240.0.0.0/4                    |
      |                                   | -  255.255.255.255/32             |
      +-----------------------------------+-----------------------------------+

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the VPC list, locate the target VPC and click **Edit CIDR Block** in the **Operation** column.

   The **Edit CIDR Block** dialog box is displayed.

#. Click **Add Secondary IPv4 CIDR Block**.

#. Enter the secondary CIDR block and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818983054.png
.. |image2| image:: /_static/images/en-us_image_0000001865663001.png
