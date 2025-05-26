:original_name: en-us_topic_0046655038.html

.. _en-us_topic_0046655038:

Creating a VPC Peering Connection with a VPC in Another Account
===============================================================

Scenarios
---------

If two VPCs from the same region cannot communicate with each other, you can use a VPC peering connection. This section describes how to create a VPC peering connection between two VPCs in different accounts.

This following describes how to create a VPC peering connection between VPC-A in account A and VPC-B in account B to enable communications between ECS-A01 and RDS-B01.

Procedure:

:ref:`Step 1: Create a VPC Peering Connection <en-us_topic_0046655038__section14616192294815>`

:ref:`Step 2: Peer Account Accepts the VPC Peering Connection Request <en-us_topic_0046655038__section497322311429>`

:ref:`Step 3: Add Routes for the VPC Peering Connection <en-us_topic_0046655038__section519111175712>`

:ref:`Step 4: Verify Network Connectivity <en-us_topic_0046655038__section920942154519>`


.. figure:: /_static/images/en-us_image_0000001818823598.png
   :alt: **Figure 1** Networking diagram of a VPC peering connection between VPCs in different accounts

   **Figure 1** Networking diagram of a VPC peering connection between VPCs in different accounts

Notes and Constraints
---------------------

-  Only one VPC peering connection can be created between two VPCs at the same time.
-  A VPC peering connection can only connect VPCs in the same region.

-  If the local and peer VPCs have overlapping CIDR blocks, the VPC peering connection may not take effect.

-  For a VPC peering connection between VPCs in different accounts:

   -  If account A initiates a request to create a VPC peering connection with a VPC in account B, the VPC peering connection takes effect only after account B accepts the request.
   -  To ensure network security, do not accept VPC peering connections from unknown accounts.

Prerequisites
-------------

You have two VPCs in the same region, but they are from different accounts. If you want to create one, see :ref:`Creating a VPC <en-us_topic_0013935842>`.

.. _en-us_topic_0046655038__section14616192294815:

Step 1: Create a VPC Peering Connection
---------------------------------------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, click **VPC Peering**.

   The VPC peering connection list is displayed.

5. In the upper right corner of the page, click **Create VPC Peering Connection**.

   The **Create VPC Peering Connection** dialog box is displayed.

6. Configure the parameters as prompted.

   For details, see :ref:`Table 1 <en-us_topic_0046655038__table13425162318260>`.

   .. _en-us_topic_0046655038__table13425162318260:

   .. table:: **Table 1** Parameters for creating a VPC peering connection

      +-----------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Parameter             | Description                                                                                                   | Example Value                    |
      +=======================+===============================================================================================================+==================================+
      | Name                  | Mandatory                                                                                                     | peering-AB                       |
      |                       |                                                                                                               |                                  |
      |                       | Enter a name for the VPC peering connection.                                                                  |                                  |
      |                       |                                                                                                               |                                  |
      |                       | The name can contain a maximum of 64 characters, including letters, digits, hyphens (-), and underscores (_). |                                  |
      +-----------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Local VPC             | Mandatory                                                                                                     | VPC-A                            |
      |                       |                                                                                                               |                                  |
      |                       | VPC at one end of the VPC peering connection. You can select one from the drop-down list.                     |                                  |
      +-----------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Local VPC CIDR Block  | CIDR block of the selected local VPC                                                                          | 172.16.0.0/16                    |
      +-----------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Account               | Mandatory                                                                                                     | Another account                  |
      |                       |                                                                                                               |                                  |
      |                       | -  Options: **My account** and **Another account**                                                            |                                  |
      |                       | -  Select **Another account**.                                                                                |                                  |
      +-----------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Peer Project ID       | This parameter is mandatory because **Account** is set to **Another account**.                                | Project ID of VPC-B in region A: |
      |                       |                                                                                                               |                                  |
      |                       |                                                                                                               | 067cf8aecf3XXX08322f13b          |
      +-----------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Peer VPC ID           | This parameter is mandatory because **Account** is set to **Another account**.                                | VPC-B ID:                        |
      |                       |                                                                                                               |                                  |
      |                       |                                                                                                               | 17cd7278-XXX-530c952dcf35        |
      +-----------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+

7. Click **OK**.

   -  If the message "Invalid VPC ID and project ID." is displayed, check whether the project ID and VPC ID are correct.

      -  Peer Project ID: The value must be the project ID of the region where the peer VPC resides.
      -  The local and peer VPCs must be in the same region.

   -  If the status of the created VPC peering connection is **Awaiting acceptance**, go to :ref:`Step 2: Peer Account Accepts the VPC Peering Connection Request <en-us_topic_0046655038__section497322311429>`.

.. _en-us_topic_0046655038__section497322311429:

Step 2: Peer Account Accepts the VPC Peering Connection Request
---------------------------------------------------------------

After you create a VPC peering connection with a VPC in another account, you need to contact the peer account to accept the VPC peering connection request. In this example, account A notifies account B to accept the request. Account B needs to:

#. Log in to the management console.

#. Click |image3| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, click **VPC Peering**.

   The VPC peering connection list is displayed.

#. In the VPC peering connection list, locate the VPC peering connection request to be accepted.

#. Locate the row that contains the target VPC peering connection and click **Accept Request** in the **Operation** column.

   After the status of the VPC peering connection changes to **Accepted**, the VPC peering connection is created.

#. Go to :ref:`Step 3: Add Routes for the VPC Peering Connection <en-us_topic_0046655038__section519111175712>`.

.. _en-us_topic_0046655038__section519111175712:

Step 3: Add Routes for the VPC Peering Connection
-------------------------------------------------

To enable communications between VPCs connected by a VPC peering connection, you need to add forward and return routes to the route tables of the VPCs. For details, see :ref:`VPC Peering Connection Usage Examples <en-us_topic_0046809840>`.

Both accounts need to add a route to the route table of their VPC. In this example, account A adds a route to the route table of VPC-A, and account B adds a route to the route table of VPC-B.

#. Add routes to the route table of the local VPC:

   a. In the VPC peering connection list of the local account, click the name of the target VPC peering connection.

      The **Basic Information** tab of the VPC peering connection is displayed.

   b. On the **Local Routes** tab of the VPC peering connection, click the **Route Tables** hyperlink.

      The **Summary** tab of the default route table for the local VPC is displayed.

   c. Click **Add Route**.

      :ref:`Table 2 <en-us_topic_0046655038__en-us_topic_0118498960_table97163496270>` describes the parameters.

      .. _en-us_topic_0046655038__en-us_topic_0118498960_table97163496270:

      .. table:: **Table 2** Parameter descriptions

         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Parameter             | Description                                                                                                                                            | Example Value                   |
         +=======================+========================================================================================================================================================+=================================+
         | Destination           | The peer VPC CIDR block, subnet CIDR block, or ECS IP address. For details, see :ref:`VPC Peering Connection Usage Examples <en-us_topic_0046809840>`. | VPC-B CIDR block: 172.17.0.0/16 |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Next Hop Type         | The next hop type. Select **VPC peering connection**.                                                                                                  | VPC peering                     |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Next Hop              | The next hop address. Select the name of the current VPC peering connection.                                                                           | peering-AB                      |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Description           | Supplementary information about the route. This parameter is optional.                                                                                 | ``-``                           |
         |                       |                                                                                                                                                        |                                 |
         |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                    |                                 |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+

   d. Click **OK**.

      You can view the routes in the route list.

#. Add routes to the route table of the peer VPC:

   a. In the VPC peering connection list of the peer account, click the name of the target VPC peering connection.

      The **Basic Information** tab of the VPC peering connection is displayed.

   b. On the **Local Routes** tab of the VPC peering connection, click the **Route Tables** hyperlink.

      The **Summary** tab of the default route table for the peer VPC is displayed.

   c. Click **Add Route**.

      :ref:`Table 3 <en-us_topic_0046655038__en-us_topic_0118498960_table13697163914393>` describes the parameters.

      .. _en-us_topic_0046655038__en-us_topic_0118498960_table13697163914393:

      .. table:: **Table 3** Parameter descriptions

         +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Parameter             | Description                                                                                                                                             | Example Value                   |
         +=======================+=========================================================================================================================================================+=================================+
         | Destination           | The local VPC CIDR block, subnet CIDR block, or ECS IP address. For details, see :ref:`VPC Peering Connection Usage Examples <en-us_topic_0046809840>`. | VPC-A CIDR block: 172.16.0.0/16 |
         +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Next Hop Type         | The next hop type. Select **VPC peering connection**.                                                                                                   | VPC peering                     |
         +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Next Hop              | The next hop address. Select the name of the current VPC peering connection.                                                                            | peering-AB                      |
         +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Description           | Supplementary information about the route. This parameter is optional.                                                                                  | ``-``                           |
         |                       |                                                                                                                                                         |                                 |
         |                       | The description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                     |                                 |
         +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+

   d. Click **OK**.

      You can view the routes in the route list.

.. _en-us_topic_0046655038__section920942154519:

Step 4: Verify Network Connectivity
-----------------------------------

After you add routes for the VPC peering connection, verify the communication between the local and peer VPCs.

#. Log in to ECS-A01 in the local VPC.

#. Check whether ECS-A01 can communicate with RDS-B01.

   **ping** *IP address of RDS-B01*

   Run the following commands:

   **ping 172.17.0.21**

   If information similar to the following is displayed, ECS-A01 and RDS-B01 can communicate with each other, and the VPC peering connection between VPC-A and VPC-B is successfully created.

   .. code-block:: console

      [root@ecs-A02 ~]# ping 172.17.0.21
      PING 172.17.0.21 (172.17.0.21) 56(84) bytes of data.
      64 bytes from 172.17.0.21: icmp_seq=1 ttl=64 time=0.849 ms
      64 bytes from 172.17.0.21: icmp_seq=2 ttl=64 time=0.455 ms
      64 bytes from 172.17.0.21: icmp_seq=3 ttl=64 time=0.385 ms
      64 bytes from 172.17.0.21: icmp_seq=4 ttl=64 time=0.372 ms
      ...
      --- 172.17.0.21 ping statistics ---

   .. important::

      -  In this example, ECS-A01 and RDS-B01 are in the same security group. If the instances in different security groups, you need to add inbound rules to allow access from the peer security group. For details, see :ref:`Enabling ECSs In Different Security Groups to Communicate Through an Internal Network <en-us_topic_0081124350__section094514632817>`.
      -  If VPCs connected by a VPC peering connection cannot communicate with each other, refer to :ref:`Why Did Communication Fail Between VPCs That Were Connected by a VPC Peering Connection? <vpc_faq_0069>`.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865583133.png
.. |image3| image:: /_static/images/en-us_image_0000001818983374.png
