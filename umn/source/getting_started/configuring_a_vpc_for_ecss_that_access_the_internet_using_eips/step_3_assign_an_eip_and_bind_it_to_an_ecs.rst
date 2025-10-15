:original_name: vpc_qs_0011.html

.. _vpc_qs_0011:

Step 3: Assign an EIP and Bind It to an ECS
===========================================

Scenarios
---------

You can assign an EIP and bind it to an ECS so that the ECS can access the Internet.

Assigning an EIP
----------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Elastic IP**.

#. On the displayed page, click **Assign EIP**.

#. Set the parameters as prompted.

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                           | Example Value         |
      +=======================+=======================================================================================================================================================================================================================================================================================================================================================================+=======================+
      | Region                | Regions are geographic areas that are physically isolated from each other. The networks inside different regions are not connected to each other, so resources cannot be shared across different regions. For lower network latency and faster access to your resources, select the region nearest you. The region selected for the EIP is its geographical location. | eu-ch2                |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | EIP Type              | -  **Dynamic BGP**: Dynamic BGP provides automatic failover and chooses the optimal path when a network connection fails.                                                                                                                                                                                                                                             | Dynamic BGP           |
      |                       | -  **Mail BGP**: EIPs with port 25, 465, or 587 enabled are used for email services.                                                                                                                                                                                                                                                                                  |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                       |                       |
      |                       | The selected EIP type cannot be changed after the EIP is assigned.                                                                                                                                                                                                                                                                                                    |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Billed By             | Two options are available:                                                                                                                                                                                                                                                                                                                                            | Dedicated             |
      |                       |                                                                                                                                                                                                                                                                                                                                                                       |                       |
      |                       | -  **Dedicated**: The bandwidth can be used by only one EIP.                                                                                                                                                                                                                                                                                                          |                       |
      |                       | -  **Shared**: The bandwidth can be shared by multiple EIPs.                                                                                                                                                                                                                                                                                                          |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Bandwidth             | The bandwidth size in Mbit/s.                                                                                                                                                                                                                                                                                                                                         | 100                   |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | EIP Name              | The EIP name.                                                                                                                                                                                                                                                                                                                                                         | eip-test              |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Enterprise Project    | The enterprise project that the EIP belongs to.                                                                                                                                                                                                                                                                                                                       | default               |
      |                       |                                                                                                                                                                                                                                                                                                                                                                       |                       |
      |                       | An enterprise project facilitates project-level management and grouping of cloud resources and users. The name of the default project is **default**.                                                                                                                                                                                                                 |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Bandwidth Name        | The name of the bandwidth.                                                                                                                                                                                                                                                                                                                                            | bandwidth             |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Tag                   | The EIP tags. Each tag contains a key and value pair.                                                                                                                                                                                                                                                                                                                 | -  Key: Ipv4_key1     |
      |                       |                                                                                                                                                                                                                                                                                                                                                                       | -  Value: 3005eip     |
      |                       | The tag key and value must meet the requirements listed in :ref:`Table 2 <vpc_qs_0011__en-us_topic_0013748738_table36606052153313>`.                                                                                                                                                                                                                                  |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Quantity              | The number of EIPs you want to assign.                                                                                                                                                                                                                                                                                                                                | 1                     |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

   .. _vpc_qs_0011__en-us_topic_0013748738_table36606052153313:

   .. table:: **Table 2** EIP tag requirements

      +-----------------------+------------------------------------------------------------------------+-----------------------+
      | Parameter             | Requirement                                                            | Example Value         |
      +=======================+========================================================================+=======================+
      | Key                   | -  Cannot be left blank.                                               | Ipv4_key1             |
      |                       | -  The key value must be unique for the same EIP.                      |                       |
      |                       | -  Can contain up to 36 characters.                                    |                       |
      |                       | -  Can contain only the following character types:                     |                       |
      |                       |                                                                        |                       |
      |                       |    -  Uppercase letters                                                |                       |
      |                       |    -  Lowercase letters                                                |                       |
      |                       |    -  Digits                                                           |                       |
      |                       |    -  Only hyphens (-), underscores (_), and at signs (@) are allowed. |                       |
      +-----------------------+------------------------------------------------------------------------+-----------------------+
      | Value                 | -  Can contain up to 43 characters.                                    | 3005eip               |
      |                       | -  Can contain only the following character types:                     |                       |
      |                       |                                                                        |                       |
      |                       |    -  Uppercase letters                                                |                       |
      |                       |    -  Lowercase letters                                                |                       |
      |                       |    -  Digits                                                           |                       |
      |                       |    -  Only underscores (_), hyphens (-), and at signs (@) are allowed. |                       |
      +-----------------------+------------------------------------------------------------------------+-----------------------+

#. Click **Create Now**.

#. Click **Submit**.

Binding an EIP
--------------

#. On the **EIPs** page, locate the row that contains the target EIP, and click **Bind**.

#. Select the instance that you want to bind the EIP to.

#. Click **OK**.

Follow-Up Procedure
-------------------

After an ECS with an EIP bound is created, the system generates a reverse domain name in the format of ecs-xx-xx-xx-xx.compute.xxx.com for the EIP by default. xx-xx-xx-xx indicates the EIP, and xxx indicates the domain name of the cloud service provider. You can use the reverse domain name to access the ECS.

You can use any of the following commands to obtain the reverse domain name of an EIP:

-  nslookup -query=ptr *EIP*
-  dig -x *EIP*

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818982822.png
