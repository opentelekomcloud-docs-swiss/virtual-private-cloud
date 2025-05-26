:original_name: en-us_topic_0046655037.html

.. _en-us_topic_0046655037:

Creating a VPC Peering Connection with Another VPC in Your Account
==================================================================

Scenarios
---------

If two VPCs from the same region cannot communicate with each other, you can use a VPC peering connection. This section describes how to create a VPC peering connection between two VPCs in the same account.

This following describes how to create a VPC peering connection between VPC-A and VPC-B in account A to enable communications between ECS-A01 and RDS-B01.

Procedure:

:ref:`Step 1: Create a VPC Peering Connection <en-us_topic_0046655037__section143383585438>`

:ref:`Step 2: Add Routes for the VPC Peering Connection <en-us_topic_0046655037__section19655123018712>`

:ref:`Step 3: Verify Network Connectivity <en-us_topic_0046655037__section026312306414>`


.. figure:: /_static/images/en-us_image_0000001865663449.png
   :alt: **Figure 1** Networking diagram of a VPC peering connection between VPCs in the same account

   **Figure 1** Networking diagram of a VPC peering connection between VPCs in the same account

Notes and Constraints
---------------------

-  Only one VPC peering connection can be created between two VPCs at the same time.
-  A VPC peering connection can only connect VPCs in the same region.
-  If the local and peer VPCs have overlapping CIDR blocks, the VPC peering connection may not take effect.

Prerequisites
-------------

You have two VPCs from the same account in the same region. If you want to create one, see :ref:`Creating a VPC <en-us_topic_0013935842>`.

.. _en-us_topic_0046655037__section143383585438:

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

   For details, see :ref:`Table 1 <en-us_topic_0046655037__table348414246354>`.

   .. _en-us_topic_0046655037__table348414246354:

   .. table:: **Table 1** Parameters for creating a VPC peering connection

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                      | Example Value         |
      +=======================+==================================================================================================================================================================================================+=======================+
      | Name                  | Mandatory                                                                                                                                                                                        | peering-AB            |
      |                       |                                                                                                                                                                                                  |                       |
      |                       | Enter a name for the VPC peering connection.                                                                                                                                                     |                       |
      |                       |                                                                                                                                                                                                  |                       |
      |                       | The name can contain a maximum of 64 characters, including letters, digits, hyphens (-), and underscores (_).                                                                                    |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Local VPC             | Mandatory                                                                                                                                                                                        | VPC-A                 |
      |                       |                                                                                                                                                                                                  |                       |
      |                       | VPC at one end of the VPC peering connection. You can select one from the drop-down list.                                                                                                        |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Local VPC CIDR Block  | CIDR block of the selected local VPC                                                                                                                                                             | 172.16.0.0/16         |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Account               | Mandatory                                                                                                                                                                                        | My account            |
      |                       |                                                                                                                                                                                                  |                       |
      |                       | -  Options: **My account** and **Another account**                                                                                                                                               |                       |
      |                       | -  Select **My account**.                                                                                                                                                                        |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Peer Project          | The system fills in the corresponding project by default because **My account** is set to **Account**.                                                                                           | ab-cdef-1             |
      |                       |                                                                                                                                                                                                  |                       |
      |                       | For example, if VPC-A and VPC-B are in account A and region A, the system fills in the correspond project of account A in region A by default.                                                   |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Peer VPC              | This parameter is mandatory if **Account** is set to **My account**.                                                                                                                             | VPC-B                 |
      |                       |                                                                                                                                                                                                  |                       |
      |                       | VPC at the other end of the VPC peering connection. You can select one from the drop-down list.                                                                                                  |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Peer VPC CIDR Block   | CIDR block of the selected peer VPC                                                                                                                                                              | 172.17.0.0/16         |
      |                       |                                                                                                                                                                                                  |                       |
      |                       | If the local and peer VPCs have overlapping CIDR blocks, the VPC peering connection may not take effect. For details, see :ref:`VPC Peering Connection Usage Examples <en-us_topic_0046809840>`. |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7. Click **OK**.

.. _en-us_topic_0046655037__section19655123018712:

Step 2: Add Routes for the VPC Peering Connection
-------------------------------------------------

To enable communications between VPCs connected by a VPC peering connection, you need to add forward and return routes to the route tables of the VPCs. For details, see :ref:`VPC Peering Connection Usage Examples <en-us_topic_0046809840>`.

#. Add routes to the route table of the local VPC:

   a. On the **Local Routes** tab of the VPC peering connection, click the **Route Tables** hyperlink.

      The **Summary** tab of the default route table for the local VPC is displayed.

   b. Click **Add Route**.

      :ref:`Table 2 <en-us_topic_0046655037__table97163496270>` describes the route parameters.

      .. _en-us_topic_0046655037__table97163496270:

      .. table:: **Table 2** Parameter description

         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Parameter             | Description                                                                                                                                            | Example Value                   |
         +=======================+========================================================================================================================================================+=================================+
         | Destination           | The peer VPC CIDR block, subnet CIDR block, or ECS IP address. For details, see :ref:`VPC Peering Connection Usage Examples <en-us_topic_0046809840>`. | VPC-B CIDR block: 172.17.0.0/16 |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Next Hop Type         | The next hop type. Select **VPC peering connection**.                                                                                                  | VPC peering connection          |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Next Hop              | The next hop address. Select the name of the current VPC peering connection.                                                                           | peering-AB                      |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Description           | Supplementary information about the route. This parameter is optional.                                                                                 | ``-``                           |
         |                       |                                                                                                                                                        |                                 |
         |                       | The route description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                              |                                 |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+

   c. Click **OK**.

      You can view the route in the route list.

2. Add routes to the route table of the peer VPC:

   a. On the **Peer Routes** tab of the VPC peering connection, click the **Route Tables** hyperlink.

      The **Summary** tab of the default route table for the peer VPC is displayed.

   b. Click **Add Route**.

      :ref:`Table 3 <en-us_topic_0046655037__table13697163914393>` describes the route parameters.

      .. _en-us_topic_0046655037__table13697163914393:

      .. table:: **Table 3** Parameter description

         +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Parameter             | Description                                                                                                                                             | Example Value                   |
         +=======================+=========================================================================================================================================================+=================================+
         | Destination           | The local VPC CIDR block, subnet CIDR block, or ECS IP address. For details, see :ref:`VPC Peering Connection Usage Examples <en-us_topic_0046809840>`. | VPC-A CIDR block: 172.16.0.0/16 |
         +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Next Hop Type         | The next hop type. Select **VPC peering connection**.                                                                                                   | VPC peering connection          |
         +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Next Hop              | The next hop address. Select the name of the current VPC peering connection.                                                                            | peering-AB                      |
         +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
         | Description           | Supplementary information about the route. This parameter is optional.                                                                                  | ``-``                           |
         |                       |                                                                                                                                                         |                                 |
         |                       | The route description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                               |                                 |
         +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+

   c. Click **OK**.

      You can view the route in the route list.

.. _en-us_topic_0046655037__section026312306414:

Step 3: Verify Network Connectivity
-----------------------------------

After you add routes for the VPC peering connection, verify the communication between the local and peer VPCs.

#. Log in to ECS-A01 in the local VPC.

#. Check whether ECS-A01 can communicate with RDS-B01.

   **ping** *IP address of RDS-B01*

   Example command:

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
.. |image2| image:: /_static/images/en-us_image_0000001818983506.png
