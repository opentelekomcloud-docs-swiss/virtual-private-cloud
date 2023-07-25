:original_name: vpc_eip02_0001.html

.. _vpc_eip02_0001:

Assigning an EIP and Binding It to an ECS
=========================================

Scenarios
---------

You can assign an EIP and bind it to an ECS so that the ECS can access the Internet.

Assigning an EIP
----------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, under , click **Elastic IP**.

#. On the displayed page, click **Assign EIP**.

#. Set the parameters as prompted.

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                           | Example Value         |
      +=======================+=======================================================================================================================================================================================================================================================================================================================================================================+=======================+
      | Region                | Regions are geographic areas that are physically isolated from each other. The networks inside different regions are not connected to each other, so resources cannot be shared across different regions. For lower network latency and faster access to your resources, select the region nearest you. The region selected for the EIP is its geographical location. | eu-ch2                |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | EIP Type              | **Dynamic BGP**: Dynamic BGP provides automatic failover and chooses the optimal path when a network connection fails.                                                                                                                                                                                                                                                | Dynamic BGP           |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Billed By             | The following bandwidth types are available:                                                                                                                                                                                                                                                                                                                          | Dedicated             |
      |                       |                                                                                                                                                                                                                                                                                                                                                                       |                       |
      |                       | -  **Dedicated**: The bandwidth can be used by only one EIP.                                                                                                                                                                                                                                                                                                          |                       |
      |                       | -  **Shared**: The bandwidth can be shared by multiple EIPs.                                                                                                                                                                                                                                                                                                          |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Bandwidth             | The bandwidth size in Mbit/s.                                                                                                                                                                                                                                                                                                                                         | 100                   |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Bandwidth Name        | The name of the bandwidth.                                                                                                                                                                                                                                                                                                                                            | bandwidth             |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Tag                   | The EIP tags. Each tag contains a key and value pair.                                                                                                                                                                                                                                                                                                                 | -  Key: Ipv4_key1     |
      |                       |                                                                                                                                                                                                                                                                                                                                                                       | -  Value: 3005eip     |
      |                       | The tag key and value must meet the requirements listed in :ref:`Table 2 <vpc_eip02_0001__en-us_topic_0118498850_table36606052153313>`.                                                                                                                                                                                                                               |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Quantity              | The number of EIPs you want to purchase.                                                                                                                                                                                                                                                                                                                              | 1                     |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

   .. _vpc_eip02_0001__en-us_topic_0118498850_table36606052153313:

   .. table:: **Table 2** EIP tag requirements

      +-----------------------+---------------------------------------------------------------------+-----------------------+
      | Parameter             | Requirement                                                         | Example Value         |
      +=======================+=====================================================================+=======================+
      | Key                   | -  Cannot be left blank.                                            | Ipv4_key1             |
      |                       | -  Must be unique for each EIP.                                     |                       |
      |                       | -  Can contain a maximum of 36 characters.                          |                       |
      |                       | -  Can contain only the following character types:                  |                       |
      |                       |                                                                     |                       |
      |                       |    -  Uppercase letters                                             |                       |
      |                       |    -  Lowercase letters                                             |                       |
      |                       |    -  Digits                                                        |                       |
      |                       |    -  Special characters, including hyphens (-) and underscores (_) |                       |
      +-----------------------+---------------------------------------------------------------------+-----------------------+
      | Value                 | -  Can contain a maximum of 43 characters.                          | 3005eip               |
      |                       | -  Can contain only the following character types:                  |                       |
      |                       |                                                                     |                       |
      |                       |    -  Uppercase letters                                             |                       |
      |                       |    -  Lowercase letters                                             |                       |
      |                       |    -  Digits                                                        |                       |
      |                       |    -  Special characters, including hyphens (-) and underscores (_) |                       |
      +-----------------------+---------------------------------------------------------------------+-----------------------+

#. Click **Create Now**.

#. Click **Submit**.

Binding an EIP
--------------

#. On the **EIPs** page, locate the row that contains the target EIP, and click **Bind**.
#. Select the instance that you want to bind the EIP to.
#. Click **OK**.

Follow-Up Procedure
-------------------

After an ECS with an EIP bound is created, the system generates a domain name in the format of **ecs-**\ *xx-xx-xx-xx*\ **.compute.**\ *xxx*\ **.com** for the EIP by default. *xx-xx-xx-xx* indicates the EIP, and xxx indicates the domain name of the cloud service provider. You can use the domain name to access the ECS.

You can use any of the following commands to obtain the domain name of an EIP:

-  ping -a *EIP*
-  nslookup [-qt=ptr] *EIP*
-  dig -x *EIP*

.. |image1| image:: /_static/images/en-us_image_0141273034.png
