:original_name: SecurityGroup_0005.html

.. _SecurityGroup_0005:

Allowing Common Ports with a Few Clicks
=======================================

Scenarios
---------

You can configure a security group to allow common ports with a few clicks. This function is suitable for the following scenarios:

-  Remotely log in to ECSs.
-  Use the ping command to test ECS connectivity.
-  ECSs functioning as web servers provide website access services.

:ref:`Table 1 <securitygroup_0005__table117828131111>` describes the common ports that can be opened with a few clicks.

.. _securitygroup_0005__table117828131111:

.. table:: **Table 1** Common ports

   +-----------------+------------------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Direction       | Protocol & Port & Type | Source/Destination | Description                                                                                                                       |
   +=================+========================+====================+===================================================================================================================================+
   | Inbound         | TCP: 22 (IPv4)         | 0.0.0.0/0          | Allows all IPv4 addresses to access ECSs in the security group over port 22 (SSH) for remotely logging in to Linux ECSs.          |
   +-----------------+------------------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   |                 | TCP: 3389 (IPv4)       | 0.0.0.0/0          | Allows all IPv4 addresses to access ECSs in the security group over port 3389 (RDP) for remotely logging in to Windows ECSs.      |
   +-----------------+------------------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   |                 | TCP: 80 (IPv4)         | 0.0.0.0/0          | Allows all IPv4 addresses to access ECSs in the security group over port 80 (HTTP) for visiting websites.                         |
   +-----------------+------------------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   |                 | TCP: 443 (IPv4)        | 0.0.0.0/0          | Allows all IPv4 addresses to access ECSs in the security group over port 443 (HTTPS) for visiting websites.                       |
   +-----------------+------------------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   |                 | TCP: 20-21 (IPv4)      | 0.0.0.0/0          | Allows all IPv4 addresses to access ECSs in the security group over ports 20 and 21 (FTP) for uploading or downloading files.     |
   +-----------------+------------------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   |                 | ICMP: All (IPv4)       | 0.0.0.0/0          | Allows all IPv4 addresses to access ECSs in the security group over any port for using the ping command to test ECS connectivity. |
   +-----------------+------------------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Outbound        | All (IPv4)             | 0.0.0.0/0          | Allows access from ECSs in the security group to any IP address over any port.                                                    |
   |                 |                        |                    |                                                                                                                                   |
   |                 | All (IPv6)             | ::/0               |                                                                                                                                   |
   +-----------------+------------------------+--------------------+-----------------------------------------------------------------------------------------------------------------------------------+

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. In the navigation pane on the left, choose **Access Control** > **Security Groups**.

   The security group list is displayed.

#. In the security group list, click the name of the security group.

   The security group details page is displayed.

#. Click the **Inbound Rules** or **Outbound Rules** tab, and then click **Allow Common Ports**.

   The **Allow Common Ports** page is displayed.

#. Click **OK**.

   After the operation is complete, you can view the added rules in the security group rule list.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818823186.png
