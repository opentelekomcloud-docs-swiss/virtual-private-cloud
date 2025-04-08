:original_name: vpc_qs_0004.html

.. _vpc_qs_0004:

Overview
========

If your ECSs do not require Internet access or need to access the Internet using IP addresses on the default network (100.64.0.0/11) with limited bandwidth (for example, the ECSs functioning as the database nodes or server nodes for deploying a website), you can follow the procedure shown in :ref:`Figure 1 <vpc_qs_0004__fd87108563a6848bba1a0f0295fef3515>` to configure a VPC for the ECSs.

.. _vpc_qs_0004__fd87108563a6848bba1a0f0295fef3515:

.. figure:: /_static/images/en-us_image_0000001818823762.png
   :alt: **Figure 1** Configuring the network

   **Figure 1** Configuring the network

:ref:`Table 1 <vpc_qs_0004__t1b39acc5d1d449eabbea2aab68bfab25>` describes the different tasks in the procedure for configuring the network.

.. _vpc_qs_0004__t1b39acc5d1d449eabbea2aab68bfab25:

.. table:: **Table 1** Configuration process description

   +------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Task                               | Description                                                                                                              |
   +====================================+==========================================================================================================================+
   | Create a VPC.                      | This task is mandatory.                                                                                                  |
   |                                    |                                                                                                                          |
   |                                    | After the VPC is created, you can create other required network resources in the VPC based on your service requirements. |
   +------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Create another subnet for the VPC. | This task is optional.                                                                                                   |
   |                                    |                                                                                                                          |
   |                                    | If the default subnet cannot meet your requirements, you can create one.                                                 |
   |                                    |                                                                                                                          |
   |                                    | The new subnet is used to assign IP addresses to NICs added to the ECS.                                                  |
   +------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Create a security group.           | This task is mandatory.                                                                                                  |
   |                                    |                                                                                                                          |
   |                                    | You can create a security group and add ECSs in the VPC to the security group to improve ECS access security.            |
   |                                    |                                                                                                                          |
   |                                    | After a security group is created, it has default rules.                                                                 |
   +------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Add a security group rule.         | This task is optional.                                                                                                   |
   |                                    |                                                                                                                          |
   |                                    | If the default rule meets your service requirements, you do not need to add rules to the security group.                 |
   +------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
