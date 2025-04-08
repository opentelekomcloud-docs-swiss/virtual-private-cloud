:original_name: vpc_vpc_0011.html

.. _vpc_vpc_0011:

Viewing and Deleting Resources in a Subnet
==========================================

Scenarios
---------

VPC subnets have private IP addresses used by cloud resources. This section describes how to view resources that are using private IP addresses of subnets. If these resources are no longer required, you can delete them.

You can view resources, including ECSs, BMSs, load balancers, and NAT gateways.

.. important::

   After you delete all resources in a subnet by referring to this section, the message "Delete the resource that is using the subnet and then delete the subnet." is displayed when you delete the subnet, you can refer to :ref:`Viewing IP Addresses in a Subnet <vpc_vpc_0012>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, click **Subnets**.

   The **Subnets** page is displayed.

#. Locate the target subnet and click its name.

   The subnet details page is displayed.

#. On the **Summary** page, view the resources in the subnet.

   a. In the **VPC Resources** area, view the quantities of resources, such as ECSs, BMSs, network interfaces, and load balancers, in the subnet. Click the resource quantity with a hyperlink to view the resources in the subnet.
   b. In the **Networking Components** area on the right of the page, view the NAT gateways in the subnet.

#. Delete resources from the subnet.

   .. table:: **Table 1** Viewing and deleting resources in a subnet

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resource                          | Reference                                                                                                                                        |
      +===================================+==================================================================================================================================================+
      | ECS                               | Currently, you cannot directly switch to ECSs from the subnet details page. You need to search for the target ECS in the ECS list and delete it. |
      |                                   |                                                                                                                                                  |
      |                                   | a. In the ECS list, click the ECS name.                                                                                                          |
      |                                   |                                                                                                                                                  |
      |                                   |    The ECS details page is displayed.                                                                                                            |
      |                                   |                                                                                                                                                  |
      |                                   | b. In the **NICs** area, view the name of the subnet associated with the ECS.                                                                    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | BMS                               | Currently, you cannot directly switch to BMSs from the subnet details page. You need to search for the target BMS in the BMS list and delete it. |
      |                                   |                                                                                                                                                  |
      |                                   | a. In the BMS list, click the BMS name.                                                                                                          |
      |                                   |                                                                                                                                                  |
      |                                   |    The BMS details page is displayed.                                                                                                            |
      |                                   |                                                                                                                                                  |
      |                                   | b. In the **NICs** tab, view the subnet associated with the BMS.                                                                                 |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Load balancer                     | You can directly switch to load balancers from the subnet details page.                                                                          |
      |                                   |                                                                                                                                                  |
      |                                   | a. Click the load balancer quantity.                                                                                                             |
      |                                   |                                                                                                                                                  |
      |                                   |    The load balancer list is displayed.                                                                                                          |
      |                                   |                                                                                                                                                  |
      |                                   | b. Locate the row that contains the load balancer and click **Delete** in the **Operation** column.                                              |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | NAT gateway                       | You can directly switch to NAT gateways from the subnet details page.                                                                            |
      |                                   |                                                                                                                                                  |
      |                                   | a. Click the NAT gateway name in the **Networking Components** area.                                                                             |
      |                                   |                                                                                                                                                  |
      |                                   |    The NAT gateway details page is displayed.                                                                                                    |
      |                                   |                                                                                                                                                  |
      |                                   | b. Click |image3| to return to the NAT gateway list.                                                                                             |
      |                                   |                                                                                                                                                  |
      |                                   | c. Locate the row that contains the NAT gateway and click **Delete** in the **Operation** column.                                                |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865662745.png
.. |image3| image:: /_static/images/en-us_image_0000001818982794.png
