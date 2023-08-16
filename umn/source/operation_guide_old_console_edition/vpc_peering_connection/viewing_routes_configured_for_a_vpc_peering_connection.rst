:original_name: vpc_peering02_0008.html

.. _vpc_peering02_0008:

Viewing Routes Configured for a VPC Peering Connection
======================================================

Scenarios
---------

This section describes how to view the routes added to the route tables of local and peer VPCs of a VPC peering connection.

-  :ref:`Viewing Routes of a VPC Peering Connection Between VPCs in the Same Account <vpc_peering02_0008__en-us_topic_0118499033_section1865779319727>`
-  :ref:`Viewing Routes of a VPC Peering Connection Between VPCs in Different Accounts <vpc_peering02_0008__en-us_topic_0118499033_section92403501475>`

If two VPCs cannot communicate through a VPC peering connection, you can check the routes added for the local and peer VPCs by following the instructions provided in this section.

.. _vpc_peering02_0008__en-us_topic_0118499033_section1865779319727:

Viewing Routes of a VPC Peering Connection Between VPCs in the Same Account
---------------------------------------------------------------------------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. On the console homepage, under , click **Virtual Private Cloud**.

4. In the navigation pane on the left, click **VPC Peering**.

   The VPC peering connection list is displayed.

5. In the VPC peering connection list, click the name of the target VPC peering connection.

   The page showing the VPC peering connection details is displayed.

6. View the routes added for the VPC peering connection:

   a. Click the **Local Routes** tab to view the local route added for the VPC peering connection.
   b. Click the **Peer Routes** tab to view the peer route added for the VPC peering connection.

.. _vpc_peering02_0008__en-us_topic_0118499033_section92403501475:

Viewing Routes of a VPC Peering Connection Between VPCs in Different Accounts
-----------------------------------------------------------------------------

Only the account owner of a VPC in a VPC peering connection can view the routes added for the connection.

#. .. _vpc_peering02_0008__en-us_topic_0118499033_li4105938135810:

   Log in to the management console using the account of the local VPC and view the route of the local VPC:

   a. Click |image2| in the upper left corner and select the desired region and project.

   b. On the console homepage, under , click **Virtual Private Cloud**.

   c. In the navigation pane on the left, click **VPC Peering**.

      The VPC peering connection list is displayed.

   d. In the VPC peering connection list, click the name of the target VPC peering connection.

      The page showing the VPC peering connection details is displayed.

   e. Click the **Local Routes** tab to view the local route added for the VPC peering connection.

#. Log in to the management console using the account of the peer VPC and view the route of the peer VPC by referring to :ref:`1 <vpc_peering02_0008__en-us_topic_0118499033_li4105938135810>`.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0141273034.png
