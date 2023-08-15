:original_name: vpc_peering02_0004.html

.. _vpc_peering02_0004:

Creating a VPC Peering Connection with a VPC in Another Account
===============================================================

Scenarios
---------

The VPC service also allows you to create a VPC peering connection with a VPC in another account. The two VPCs must be in the same region. If you request a VPC peering connection with a VPC in another account in the same region, the owner of the peer account must accept the request to activate the connection.

Creating a VPC Peering Connection
---------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, under **Network**, click **Virtual Private Cloud**.

#. In the navigation pane on the left, click **VPC Peering**.

#. In the right pane displayed, click **Create VPC Peering Connection**.

#. Configure parameters as prompted. You must select **Another account** for **Account**.


   .. figure:: /_static/images/en-us_image_0226829595.png
      :alt: **Figure 1** Create VPC Peering Connection

      **Figure 1** Create VPC Peering Connection

   .. table:: **Table 1** Parameter description

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Parameter             | Description                                                                                                                           | Example Value                        |
      +=======================+=======================================================================================================================================+======================================+
      | Name                  | Specifies the name of the VPC peering connection.                                                                                     | peering-001                          |
      |                       |                                                                                                                                       |                                      |
      |                       | The name contains a maximum of 64 characters, which consist of letters, digits, hyphens (-), and underscores (_).                     |                                      |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Local VPC             | Specifies the local VPC. You can select one from the drop-down list.                                                                  | vpc_002                              |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Account               | Specifies the account that the VPC to peer with belongs to.                                                                           | Another account                      |
      |                       |                                                                                                                                       |                                      |
      |                       | -  **My account**: The VPC peering connection will be created between two VPCs, in the same region, in your account.                  |                                      |
      |                       | -  **Another account**: The VPC peering connection will be created between your VPC and a VPC in another account, in the same region. |                                      |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Peer Project ID       | This parameter is available only when **Another account** is selected.                                                                | ``-``                                |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Peer VPC ID           | This parameter is available only when **Another account** is selected.                                                                | 65d062b3-40fa-4204-8181-3538f527d2ab |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+

#. Click **OK**.

Accepting a VPC Peering Connection Request
------------------------------------------

To request a VPC peering connection with a VPC in another account, the owner of the peer account must accept the request to activate the connection.

#. The owner of the peer account logs in to the management console.
#. On the console homepage, under **Network**, click **Virtual Private Cloud**.
#. In the navigation pane on the left, click **VPC Peering**.
#. In the VPC peering connection list, locate the row that contains the target VPC peering connection and click **Accept Request** in the **Operation** column.
#. Click **Yes** in the displayed dialog box.

Rejecting a VPC Peering Connection Request
------------------------------------------

The owner of the peer account can reject any VPC peering connection request that they receive. If a VPC peering connection request is rejected, the connection will not be established. You must delete the rejected VPC peering connection request before creating a VPC peering connection between the same VPCs as those in the rejected request.

#. The owner of the peer account logs in to the management console.
#. On the console homepage, under **Network**, click **Virtual Private Cloud**.
#. In the navigation pane on the left, click **VPC Peering**.
#. In the VPC peering connection list, locate the row that contains the target VPC peering connection and click **Accept Request** in the **Operation** column.
#. Click **Yes** in the displayed dialog box.

Adding Routes for the VPC Peering Connection
--------------------------------------------

If you request a VPC peering connection with a VPC in another account, the owner of the peer account must accept the request. To enable communication between the two VPCs, you need to add routes for the VPC peering connection. The owner of the local account can add only the local route because the owner does not have the required permission to perform operations on the peer VPC. The owner of the peer account must add the peer route. The procedure for adding a local route and a peer route is the same.

#. Log in to the management console.

#. On the console homepage, under **Network**, click **Virtual Private Cloud**.

#. In the navigation pane on the left, click **VPC Peering**.

#. Locate the target VPC peering connection in the connection list.

#. Click the name of the VPC peering connection to switch to the page showing details about the connection.

#. On the displayed page, click the **Local Routes** tab.

#. In the displayed **Local Routes** area, click **Add Local Route**. In the displayed dialog box, add a local route. :ref:`Table 2 <vpc_peering02_0004__en-us_topic_0118498933_en-us_topic_0118498960_table1626072032518>` lists the parameters to be configured.

   .. _vpc_peering02_0004__en-us_topic_0118498933_en-us_topic_0118498960_table1626072032518:

   .. table:: **Table 2** Route parameter description

      +-------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Parameter   | Description                                                                                                 | Example Value                        |
      +=============+=============================================================================================================+======================================+
      | Destination | Specifies the destination address. Set it to the peer VPC or subnet CIDR block.                             | 192.168.2.0/24                       |
      +-------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Next Hop    | Specifies the next hop address. The default value is the VPC peering connection ID. Keep the default value. | d1a7863b-9d5e-4d27-8eaf-ab14d2a9148b |
      +-------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------+

#. Click **OK**.

After the VPC peering connection is created, the two VPCs can communicate with each other through private IP addresses. You can run the **ping** command to check whether the two VPCs can communicate with each other.

If two VPCs cannot communicate with each other, check the configuration by following the instructions provided in :ref:`Why Did Communication Fail Between VPCs That Were Connected by a VPC Peering Connection? <vpc_faq_0069>`

.. |image1| image:: /_static/images/en-us_image_0226829583.png
