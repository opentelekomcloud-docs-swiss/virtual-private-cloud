:original_name: vpc_vpc_0012.html

.. _vpc_vpc_0012:

Viewing IP Addresses in a Subnet
================================

Scenarios
---------

A subnet is an IP address range in a VPC. This section describes how to view the used IP addresses in a subnet.

-  Virtual IP addresses
-  Private IP addresses

   -  Used by the subnet itself, such as the gateway, system interface, and DHCP.
   -  Used by cloud resources, such as ECSs, load balancers, and RDS instances.

Notes and Constraints
---------------------

-  A subnet cannot be deleted if its IP addresses are used by cloud resources.
-  A subnet can be deleted if its IP addresses are used by itself.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Virtual Private Cloud** > **Subnets**.

   The **Subnets** page is displayed.

#. Locate the target subnet and click its name.

   The subnet details page is displayed.

#. Click the **IP Addresses** tab to view the IP addresses in the subnet.

   a. In the virtual IP address list, you can view the virtual IP addresses assigned from the subnet.
   b. In the private IP address list in the lower part of the page, you can view the private IP addresses used by the subnet (gateway, system interface, and DHCP).

Follow-up Operations
--------------------

If you want to view and delete the resources in the subnet, refer to :ref:`Why Can't I Delete My VPCs and Subnets? <vpc_faq_0075>`

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818983610.png
