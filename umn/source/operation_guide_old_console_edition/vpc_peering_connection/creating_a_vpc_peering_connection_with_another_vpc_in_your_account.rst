:original_name: vpc_peering02_0003.html

.. _vpc_peering02_0003:

Creating a VPC Peering Connection with Another VPC in Your Account
==================================================================

Scenarios
---------

To create a VPC peering connection, first create a request to peer with another VPC. You can request a VPC peering connection with another VPC in your account, but the two VPCs must be in the same region. The system automatically accepts the request.

Prerequisites
-------------

There are two VPCs in the same region.

Step 1: Create a VPC Peering Connection
---------------------------------------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. On the console homepage, under , click **Virtual Private Cloud**.

4. In the navigation pane on the left, click **VPC Peering**.

   The VPC peering connection list is displayed.

5. In the upper right corner of the page, click **Create VPC Peering Connection**.

   The **Create VPC Peering Connection** dialog box is displayed.

6. Configure the parameters as prompted.

   For details, see :ref:`Table 1 <vpc_peering02_0003__en-us_topic_0118498960_table348414246354>`.

   .. _vpc_peering02_0003__en-us_topic_0118498960_table348414246354:

   .. table:: **Table 1** Parameters for creating a VPC peering connection

      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                    | Example Value         |
      +=======================+================================================================================================================================================+=======================+
      | Name                  | Mandatory                                                                                                                                      | peering-AB            |
      |                       |                                                                                                                                                |                       |
      |                       | Enter a name for the VPC peering connection.                                                                                                   |                       |
      |                       |                                                                                                                                                |                       |
      |                       | The name can contain a maximum of 64 characters, including letters, digits, hyphens (-), and underscores (_).                                  |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Local VPC             | Mandatory                                                                                                                                      | VPC-A                 |
      |                       |                                                                                                                                                |                       |
      |                       | VPC at one end of the VPC peering connection. You can select one from the drop-down list.                                                      |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Local VPC CIDR Block  | CIDR block of the selected local VPC                                                                                                           | 172.16.0.0/16         |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Account               | Mandatory                                                                                                                                      | My account            |
      |                       |                                                                                                                                                |                       |
      |                       | -  Options: **My account** and **Another account**                                                                                             |                       |
      |                       | -  Select **My account**.                                                                                                                      |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Peer Project          | The system fills in the corresponding project by default because **My account** is set to **Account**.                                         | ab-cdef-1             |
      |                       |                                                                                                                                                |                       |
      |                       | For example, if VPC-A and VPC-B are in account A and region A, the system fills in the correspond project of account A in region A by default. |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Peer VPC              | This parameter is mandatory if **Account** is set to **My account**.                                                                           | VPC-B                 |
      |                       |                                                                                                                                                |                       |
      |                       | VPC at the other end of the VPC peering connection. You can select one from the drop-down list.                                                |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Peer VPC CIDR Block   | CIDR block of the selected peer VPC                                                                                                            | 172.17.0.0/16         |
      |                       |                                                                                                                                                |                       |
      |                       | If the local and peer VPCs have overlapping CIDR blocks, the VPC peering connection may not take effect.                                       |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7. Click **OK**.

Adding Routes for the VPC Peering Connection
--------------------------------------------

If you request a VPC peering connection with another VPC in your own account, the system automatically accepts the request. To enable communication between the two VPCs, you need to add local and peer routes for the VPC peering connection.

#. On the console homepage, under **Network**, click **Virtual Private Cloud**.

#. In the navigation pane on the left, click **VPC Peering**.

#. Locate the target VPC peering connection in the connection list.

#. Click the name of the VPC peering connection to switch to the page showing details about the connection.

#. In the displayed **Local Routes** area, click **Add Local Route**. In the displayed dialog box, add a local route. :ref:`Table 2 <vpc_peering02_0003__en-us_topic_0118498960_table1626072032518>` lists the parameters to be configured.

   .. _vpc_peering02_0003__en-us_topic_0118498960_table1626072032518:

   .. table:: **Table 2** Route parameter description

      +-------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Parameter   | Description                                                                                                 | Example Value                        |
      +=============+=============================================================================================================+======================================+
      | Destination | Specifies the destination address. Set it to the peer VPC or subnet CIDR block.                             | 192.168.2.0/24                       |
      +-------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Next Hop    | Specifies the next hop address. The default value is the VPC peering connection ID. Keep the default value. | d1a7863b-9d5e-4d27-8eaf-ab14d2a9148b |
      +-------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------+

#. Click **OK** to switch to the page showing the VPC peering connection details.

#. On the displayed page, click the **Peer Routes** tab.

#. In the displayed **Peer Routes** area, click **Add Peer Route** and add a route.

#. Click **OK**.

After a VPC peering connection is created, the two VPCs can communicate with each other through private IP addresses. You can run the **ping** command to check whether the two VPCs can communicate with each other.

If two VPCs cannot communicate with each other, check the configuration by following the instructions provided in :ref:`Why Did Communication Fail Between VPCs That Were Connected by a VPC Peering Connection? <vpc_faq_0069>`

.. |image1| image:: /_static/images/en-us_image_0141273034.png
