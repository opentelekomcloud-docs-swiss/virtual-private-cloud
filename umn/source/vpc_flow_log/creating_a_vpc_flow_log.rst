:original_name: FlowLog_0003.html

.. _FlowLog_0003:

Creating a VPC Flow Log
=======================

Scenarios
---------

A VPC flow log records information about the traffic going to and from a VPC.

Prerequisites
-------------

Ensure that the following operations have been performed on the LTS console:

-  Create a log group.
-  Create a log topic.

For more information about the LTS service, see the *Log Tank Service User Guide*.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.

3. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

4. In the navigation pane on the left, choose **VPC Flow Logs**.
5. In the upper right corner, click **Create VPC Flow Log**. On the displayed page, configure parameters as prompted.

   .. table:: **Table 1** Parameter descriptions

      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                | Example Value         |
      +=======================+============================================================================================================================================================================================================================================================+=======================+
      | Name                  | The VPC flow log name.                                                                                                                                                                                                                                     | flowlog-495d          |
      |                       |                                                                                                                                                                                                                                                            |                       |
      |                       | The name can contain a maximum of 64 characters, which may consist of letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot contain spaces.                                                                                      |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Resource Type         | The type of resources whose traffic is to be logged. You can select **NIC**, **Subnet**, or **VPC**.                                                                                                                                                       | NIC                   |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Resource              | The specific NIC whose traffic is to be logged.                                                                                                                                                                                                            | N/A                   |
      |                       |                                                                                                                                                                                                                                                            |                       |
      |                       | .. note::                                                                                                                                                                                                                                                  |                       |
      |                       |                                                                                                                                                                                                                                                            |                       |
      |                       |    We recommend that you select an ECS that is in the running state. If an ECS in the stopped state is selected, restart the ECS after creating the VPC flow log for accurately recording the information about the traffic going to and from the ECS NIC. |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Filter                | -  **All traffic**: specifies that both accepted and rejected traffic of the specified resource will be logged.                                                                                                                                            | All                   |
      |                       | -  **Accepted traffic**: specifies that only accepted traffic of the specified resource will be logged. Accepted traffic refers to the traffic permitted by the security group or firewall.                                                                |                       |
      |                       | -  **Rejected traffic**: specifies that only rejected traffic of the specified resource will be logged. Rejected traffic refers to the traffic denied by the firewall.                                                                                     |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Log Group             | The log group created in LTS.                                                                                                                                                                                                                              | lts-group-abc         |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Log Topic             | The log topic created in LTS.                                                                                                                                                                                                                              | LogTopic1             |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Supplementary information about the VPC flow log. This parameter is optional.                                                                                                                                                                              | N/A                   |
      |                       |                                                                                                                                                                                                                                                            |                       |
      |                       | The VPC flow log description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                                                                                           |                       |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

   .. note::

      Only two flow logs, each with a different filter, can be created for a single resource under the same log group and log topic. Each VPC flow log must be unique.

6. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865663109.png
