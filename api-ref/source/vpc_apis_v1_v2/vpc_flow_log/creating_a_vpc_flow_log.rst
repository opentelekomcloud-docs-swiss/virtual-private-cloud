:original_name: vpc_flow_0001.html

.. _vpc_flow_0001:

Creating a VPC Flow Log
=======================

Function
--------

This API is used to create a VPC flow log.

A VPC flow log captures information about the traffic going to and from your VPC. You can use flow logs to monitor network traffic, analyze network attacks, and to determine whether security group and firewall rules need to be modified.

VPC flow logs must be used together with the Log Tank Service (LTS). You need to create a log group and a log topic in LTS, and then create a VPC flow log.

URI
---

POST /v1/{project_id}/fl/flow_logs

:ref:`Table 1 <vpc_flow_0001__table1851575853914>` describes the parameters.

.. _vpc_flow_0001__table1851575853914:

.. table:: **Table 1** Parameter description

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                 |
   +============+===========+========+=============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request parameter

   +-----------+-----------+-----------------------------------------------------------+------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                      | Description                                                                              |
   +===========+===========+===========================================================+==========================================================================================+
   | flow_log  | Yes       | :ref:`flow_log <vpc_flow_0001__table656165873916>` object | **FlowLog** objects. For details, see :ref:`Table 3 <vpc_flow_0001__table656165873916>`. |
   +-----------+-----------+-----------------------------------------------------------+------------------------------------------------------------------------------------------+

.. _vpc_flow_0001__table656165873916:

.. table:: **Table 3** Description of the **FlowLog** field

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                             |
   +=================+=================+=================+=========================================================================================================================+
   | name            | No              | String          | -  Flow log name.                                                                                                       |
   |                 |                 |                 | -  The value can contain up to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.). |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | -  Flow log description                                                                                                 |
   |                 |                 |                 | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | resource_type   | Yes             | String          | -  Type of the resource for which that the logs to be collected.                                                        |
   |                 |                 |                 | -  The value can be:                                                                                                    |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 |    -  **port**: a single network interface.                                                                             |
   |                 |                 |                 |    -  **vpc**: All network interfaces in a VPC.                                                                         |
   |                 |                 |                 |    -  **network**: All network interfaces in a subnet.                                                                  |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | resource_id     | Yes             | String          | -  ID of the resource for which that the logs to be collected.                                                          |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | traffic_type    | Yes             | String          | -  Type of the traffic for which that the logs to be collected.                                                         |
   |                 |                 |                 | -  The value can be:                                                                                                    |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 |    -  **all**: specifies that both accepted and rejected traffic of the specified resource will be logged.              |
   |                 |                 |                 |    -  **accept**: specifies that only accepted inbound and outbound traffic of the specified resource will be logged.   |
   |                 |                 |                 |    -  **reject**: specifies that only rejected inbound and outbound traffic of the specified resource will be logged.   |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | Yes             | String          | -  Log group ID                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | log_topic_id    | Yes             | String          | -  Log topic ID                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  Create a VPC flow log. Set the resource type to port, resource ID to 05c4052d-8d14-488f-aa00-19fea5a25fde, traffic type to reject, log group ID to 05c4052d-8d14-488f-aa00-19fea5a25fdd, and log topic ID to a9d7dee7-37d2-4cba-a208-a016252aaa63.

   .. code-block:: text

      POST https://{Endpoint}/v1/b2782e6708b8475c993e6064bc456bf8/fl/flow_logs

      {
          "flow_log": {
              "name": "flowlog",
              "description": "just a test",
              "resource_type": "port",
              "resource_id": "05c4052d-8d14-488f-aa00-19fea5a25fde",
              "traffic_type": "reject",
              "log_group_id": "05c4052d-8d14-488f-aa00-19fea5a25fdd",
              "log_topic_id": "a9d7dee7-37d2-4cba-a208-a016252aaa63"
          }
      }

Response Parameters
-------------------

.. table:: **Table 4** Response parameter

   +-----------+-----------------------------------------------------------+------------------------------------------------------------------------------------------+
   | Parameter | Type                                                      | Description                                                                              |
   +===========+===========================================================+==========================================================================================+
   | flow_log  | :ref:`flow_log <vpc_flow_0001__table763920584395>` object | **FlowLog** objects. For details, see :ref:`Table 5 <vpc_flow_0001__table763920584395>`. |
   +-----------+-----------------------------------------------------------+------------------------------------------------------------------------------------------+

.. _vpc_flow_0001__table763920584395:

.. table:: **Table 5** Description of the **FlowLog** field

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                             |
   +=======================+=======================+=========================================================================================================================+
   | id                    | String                | -  Flow log ID                                                                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | -  Flow log name                                                                                                        |
   |                       |                       | -  The value can contain up to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.). |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                | -  Project ID                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | -  Flow log description                                                                                                 |
   |                       |                       | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | resource_type         | String                | -  Type of the resource for which that the logs to be collected.                                                        |
   |                       |                       | -  The value can be:                                                                                                    |
   |                       |                       |                                                                                                                         |
   |                       |                       |    -  **port**: a single network interface.                                                                             |
   |                       |                       |    -  **vpc**: All network interfaces in a VPC.                                                                         |
   |                       |                       |    -  **network**: All network interfaces in a subnet.                                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | resource_id           | String                | -  ID of the resource for which that the logs to be collected.                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | traffic_type          | String                | -  Type of the traffic for which that the logs to be collected.                                                         |
   |                       |                       | -  The value can be:                                                                                                    |
   |                       |                       |                                                                                                                         |
   |                       |                       |    -  **all**: specifies that both accepted and rejected traffic of the specified resource will be logged.              |
   |                       |                       |    -  **accept**: specifies that only accepted inbound and outbound traffic of the specified resource will be logged.   |
   |                       |                       |    -  **reject**: specifies that only rejected inbound and outbound traffic of the specified resource will be logged.   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | log_group_id          | String                | -  Log group ID                                                                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | log_topic_id          | String                | -  Log topic ID                                                                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                | -  Time when the flow log is created                                                                                    |
   |                       |                       | -  UTC time in the format of yyyy-MM-ddTHH:mm:ss                                                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                | -  Time when the flow log is updated                                                                                    |
   |                       |                       | -  UTC time in the format of yyyy-MM-ddTHH:mm:ss                                                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "flow_log": {
           "id": "f49f00f1-0f15-470a-a8c5-4e879e461c8d",
           "name": "flowlog",
           "description": "just a test",
           "tenant_id": "b2782e6708b8475c993e6064bc456bf8",
           "resource_type": "port",
           "resource_id": "05c4052d-8d14-488f-aa00-19fea5a25fde",
           "traffic_type": "reject",
           "log_group_id": "05c4052d-8d14-488f-aa00-19fea5a25fdd",
           "log_topic_id": "a9d7dee7-37d2-4cba-a208-a016252aaa63",
           "created_at": "2019-01-14T11:03:02",
           "updated_at": "2019-01-14T11:03:02"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
