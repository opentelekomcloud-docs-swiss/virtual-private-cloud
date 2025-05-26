:original_name: vpc_flow_0003.html

.. _vpc_flow_0003:

Querying a VPC Flow Log
=======================

Function
--------

This API is used to query a VPC flow log.

URI
---

GET /v1/{project_id}/fl/flow_logs/{flowlog_id}

:ref:`Table 1 <vpc_flow_0003__table152848346516>` describes the parameters.

.. _vpc_flow_0003__table152848346516:

.. table:: **Table 1** Parameter description

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                 |
   +============+===========+========+=============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | flowlog_id | Yes       | String | Flow log ID                                                                                                 |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v1/b2782e6708b8475c993e6064bc456bf8/fl/flow_logs/1e10cd9d-742a-4d36-a9fd-aee9784336ff

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | Parameter | Type                                                        | Description                                                                                |
   +===========+=============================================================+============================================================================================+
   | flow_log  | :ref:`flow_log <vpc_flow_0003__table17299234185110>` object | **FlowLog** objects. For details, see :ref:`Table 3 <vpc_flow_0003__table17299234185110>`. |
   +-----------+-------------------------------------------------------------+--------------------------------------------------------------------------------------------+

.. _vpc_flow_0003__table17299234185110:

.. table:: **Table 3** Description of the **FlowLog** field

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
           "id": "35868d55-443e-4d5c-90a4-ac618dc45c1a",
           "name": "flow",
           "description": "just a test",
           "tenant_id": "b2782e6708b8475c993e6064bc456bf8",
           "resource_type": "port",
           "resource_id": "05c4052d-8d14-488f-aa00-19fea5a25fde",
           "traffic_type": "reject",
           "log_group_id": "05c4052d-8d14-488f-aa00-19fea5a25fff",
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
