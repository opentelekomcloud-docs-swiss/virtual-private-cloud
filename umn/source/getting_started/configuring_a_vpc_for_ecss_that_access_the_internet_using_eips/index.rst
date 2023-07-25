:original_name: en-us_topic_0017816228.html

.. _en-us_topic_0017816228:

Configuring a VPC for ECSs That Access the Internet Using EIPs
==============================================================

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, under , click **Virtual Private Cloud**.

#. Click **Create VPC**.

#. On the **Create VPC** page, set parameters as prompted.

   A default subnet will be created together with a VPC and you can also click **Add Subnet** to create more subnets for the VPC.

   .. table:: **Table 1** VPC parameter descriptions

      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Category                            | Parameter              | Description                                                                                                                                                                                                                                                                                             | Example Value       |
      +=====================================+========================+=========================================================================================================================================================================================================================================================================================================+=====================+
      | Basic Information                   | Region                 | Regions are geographic areas that are physically isolated from each other. The networks inside different regions are not connected to each other, so resources cannot be shared across different regions. For lower network latency and faster access to your resources, select the region nearest you. | eu-ch2              |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Basic Information                   | Name                   | The VPC name.                                                                                                                                                                                                                                                                                           | VPC-001             |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         |                     |
      |                                     |                        | The name can contain a maximum of 64 characters, which may consist of letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot contain spaces.                                                                                                                                   |                     |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Basic Information                   | IPv4 CIDR Block        | The CIDR block of the VPC. The CIDR block of a subnet can be the same as the CIDR block for the VPC (for a single subnet in the VPC) or a subset of the CIDR block for the VPC (for multiple subnets in the VPC).                                                                                       | 192.168.0.0/16      |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         |                     |
      |                                     |                        | The following CIDR blocks are supported:                                                                                                                                                                                                                                                                |                     |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         |                     |
      |                                     |                        | 10.0.0.0/8-24                                                                                                                                                                                                                                                                                           |                     |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         |                     |
      |                                     |                        | 172.16.0.0/12-24                                                                                                                                                                                                                                                                                        |                     |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         |                     |
      |                                     |                        | 192.168.0.0/16-24                                                                                                                                                                                                                                                                                       |                     |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Basic Information/Advanced Settings | Tag                    | The VPC tag, which consists of a key and value pair. You can add a maximum of 20 tags to each VPC.                                                                                                                                                                                                      | -  Key: vpc_key1    |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         | -  Value: vpc-01    |
      |                                     |                        | The tag key and value must meet the requirements listed in :ref:`Table 2 <en-us_topic_0017816228__en-us_topic_0118498860_en-us_topic_0118498861_table248245914136>`.                                                                                                                                    |                     |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Basic Information/Advanced Settings | Description            | Supplementary information about the VPC. This parameter is optional.                                                                                                                                                                                                                                    | N/A                 |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         |                     |
      |                                     |                        | The VPC description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                                                                                                                                                 |                     |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Default Subnet                      | Name                   | The subnet name.                                                                                                                                                                                                                                                                                        | Subnet              |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         |                     |
      |                                     |                        | The name can contain a maximum of 64 characters, which may consist of letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot contain spaces.                                                                                                                                   |                     |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Default Subnet                      | IPv4 CIDR Block        | The CIDR block for the subnet. This value must be within the VPC CIDR block.                                                                                                                                                                                                                            | 192.168.0.0/24      |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Default Subnet                      | IPv6 CIDR Block        | Specifies whether to set **IPv6 CIDR Block** to **Enable**.                                                                                                                                                                                                                                             | ``-``               |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         |                     |
      |                                     |                        | After the IPv6 function is enabled, the system automatically assigns an IPv6 CIDR block to the created subnet. Currently, the IPv6 CIDR block cannot be customized. IPv6 cannot be disabled after the subnet is created.                                                                                |                     |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Default Subnet                      | Associated Route Table | The default route table to which the subnet will be associated. You can change the route table to a custom route table on the **Subnets** page.                                                                                                                                                         | Default             |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Default Subnet/Advanced Settings    | Gateway                | The gateway address of the subnet.                                                                                                                                                                                                                                                                      | 192.168.0.1         |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Default Subnet/Advanced Settings    | DNS Server Address     | By default, two DNS server addresses are configured. You can change them as required. A maximum of five DNS server addresses can be configured. Multiple IP addresses must be separated using commas (,).                                                                                               | 100.125.x.x         |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         |                     |
      |                                     |                        | For more information about private DNS servers, see `What Are the Private DNS Servers Provided by the DNS Service? <https://docs.sc.otc.t-systems.com/en-us/usermanual/dns/dns_faq_002.html>`__                                                                                                         |                     |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Default Subnet/Advanced Settings    | NTP Server Address     | The IP address of the NTP server. This parameter is optional.                                                                                                                                                                                                                                           | 192.168.2.1         |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         |                     |
      |                                     |                        | You can configure the NTP server IP addresses to be added to the subnet as required. The IP addresses are added in addition to the default NTP server addresses. If this parameter is left empty, no IP address of the NTP server is added.                                                             |                     |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         |                     |
      |                                     |                        | A maximum of four IP addresses can be configured. Multiple IP addresses must be separated using commas (,).                                                                                                                                                                                             |                     |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Default Subnet/Advanced Settings    | Tag                    | The subnet tag, which consists of a key and value pair. You can add a maximum of 20 tags to each subnet.                                                                                                                                                                                                | -  Key: subnet_key1 |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         | -  Value: subnet-01 |
      |                                     |                        | The tag key and value must meet the requirements listed in :ref:`Table 3 <en-us_topic_0017816228__en-us_topic_0118498860_en-us_topic_0118498861_table6536185812515>`.                                                                                                                                   |                     |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+
      | Default Subnet/Advanced Settings    | Description            | Supplementary information about the subnet. This parameter is optional.                                                                                                                                                                                                                                 | N/A                 |
      |                                     |                        |                                                                                                                                                                                                                                                                                                         |                     |
      |                                     |                        | The subnet description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                                                                                                                                              |                     |
      +-------------------------------------+------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------+

   .. _en-us_topic_0017816228__en-us_topic_0118498860_en-us_topic_0118498861_table248245914136:

   .. table:: **Table 2** VPC tag key and value requirements

      +-----------------------+------------------------------------------------------------------------+-----------------------+
      | Parameter             | Requirements                                                           | Example Value         |
      +=======================+========================================================================+=======================+
      | Key                   | -  Cannot be left blank.                                               | vpc_key1              |
      |                       | -  Must be unique for each VPC and can be the same for different VPCs. |                       |
      |                       | -  Can contain a maximum of 36 characters.                             |                       |
      |                       | -  Can contain only the following character types:                     |                       |
      |                       |                                                                        |                       |
      |                       |    -  Uppercase letters                                                |                       |
      |                       |    -  Lowercase letters                                                |                       |
      |                       |    -  Digits                                                           |                       |
      |                       |    -  Special characters, including hyphens (-) and underscores (_)    |                       |
      +-----------------------+------------------------------------------------------------------------+-----------------------+
      | Value                 | -  Can contain a maximum of 43 characters.                             | vpc-01                |
      |                       | -  Can contain only the following character types:                     |                       |
      |                       |                                                                        |                       |
      |                       |    -  Uppercase letters                                                |                       |
      |                       |    -  Lowercase letters                                                |                       |
      |                       |    -  Digits                                                           |                       |
      |                       |    -  Special characters, including hyphens (-) and underscores (_)    |                       |
      +-----------------------+------------------------------------------------------------------------+-----------------------+

   .. _en-us_topic_0017816228__en-us_topic_0118498860_en-us_topic_0118498861_table6536185812515:

   .. table:: **Table 3** Subnet tag key and value requirements

      +-----------------------+---------------------------------------------------------------------+-----------------------+
      | Parameter             | Requirements                                                        | Example Value         |
      +=======================+=====================================================================+=======================+
      | Key                   | -  Cannot be left blank.                                            | subnet_key1           |
      |                       | -  Must be unique for each subnet.                                  |                       |
      |                       | -  Can contain a maximum of 36 characters.                          |                       |
      |                       | -  Can contain only the following character types:                  |                       |
      |                       |                                                                     |                       |
      |                       |    -  Uppercase letters                                             |                       |
      |                       |    -  Lowercase letters                                             |                       |
      |                       |    -  Digits                                                        |                       |
      |                       |    -  Special characters, including hyphens (-) and underscores (_) |                       |
      +-----------------------+---------------------------------------------------------------------+-----------------------+
      | Value                 | -  Can contain a maximum of 43 characters.                          | subnet-01             |
      |                       | -  Can contain only the following character types:                  |                       |
      |                       |                                                                     |                       |
      |                       |    -  Uppercase letters                                             |                       |
      |                       |    -  Lowercase letters                                             |                       |
      |                       |    -  Digits                                                        |                       |
      |                       |    -  Special characters, including hyphens (-) and underscores (_) |                       |
      +-----------------------+---------------------------------------------------------------------+-----------------------+

#. Click **Create Now**.

-  :ref:`Overview <vpc_qs_0022>`
-  :ref:`Step 1: Create a VPC <vpc_qs_0009>`
-  :ref:`Step 2: Create a Subnet for the VPC <vpc_qs_0010>`
-  :ref:`Step 3: Assign an EIP and Bind It to an ECS <vpc_qs_0011>`
-  :ref:`Step 4: Create a Security Group <vpc_qs_0012>`
-  :ref:`Step 5: Add a Security Group Rule <vpc_qs_0013>`

.. |image1| image:: /_static/images/en-us_image_0141273034.png

.. toctree::
   :maxdepth: 1
   :hidden: 

   overview
   step_1_create_a_vpc
   step_2_create_a_subnet_for_the_vpc
   step_3_assign_an_eip_and_bind_it_to_an_ecs
   step_4_create_a_security_group
   step_5_add_a_security_group_rule
