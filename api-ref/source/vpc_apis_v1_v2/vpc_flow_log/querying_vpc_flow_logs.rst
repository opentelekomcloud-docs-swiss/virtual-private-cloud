:original_name: vpc_flow_0002.html

.. _vpc_flow_0002:

Querying VPC Flow Logs
======================

Function
--------

This API is used to query all VPC flow logs of the tenant submitting the request. The VPC flow logs are filtered based on the filtering condition.

URI
---

GET /v1/{project_id}/fl/flow_logs

Example:

.. code-block:: text

   GET https://{Endpoint}/v1/b2782e6708b8475c993e6064bc456bf8/fl/flow_logs?name=flowlog

:ref:`Table 1 <vpc_flow_0002__table238711153416>` describes the parameters.

.. _vpc_flow_0002__table238711153416:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================================================================================+
   | project_id      | Yes             | String          | -  Project ID. For details, see :ref:`Obtaining a Project ID <vpc_api_0011>`.                                                                                                                                                      |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id              | No              | String          | -  Flow log ID                                                                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | -  Flow log name                                                                                                                                                                                                                   |
   |                 |                 |                 | -  The value can contain up to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id       | No              | String          | -  Project ID                                                                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | -  Flow log description                                                                                                                                                                                                            |
   |                 |                 |                 | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_type   | No              | String          | -  Type of the resource for which that the logs to be collected.                                                                                                                                                                   |
   |                 |                 |                 | -  The value can be:                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                    |
   |                 |                 |                 |    -  **port**: a single network interface.                                                                                                                                                                                        |
   |                 |                 |                 |    -  **vpc**: All network interfaces in a VPC.                                                                                                                                                                                    |
   |                 |                 |                 |    -  **network**: All network interfaces in a subnet.                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_id     | No              | String          | -  ID of the resource for which that the logs to be collected.                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | traffic_type    | No              | String          | -  Type of the traffic for which that the logs to be collected.                                                                                                                                                                    |
   |                 |                 |                 | -  The value can be:                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                    |
   |                 |                 |                 |    -  **all**: specifies that both accepted and rejected traffic of the specified resource will be logged.                                                                                                                         |
   |                 |                 |                 |    -  **accept**: specifies that only accepted inbound and outbound traffic of the specified resource will be logged.                                                                                                              |
   |                 |                 |                 |    -  **reject**: specifies that only rejected inbound and outbound traffic of the specified resource will be logged.                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | No              | String          | -  Log group ID                                                                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_topic_id    | No              | String          | -  Log topic ID                                                                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax (2^31-1). The default value is 2000.                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                                    |
   |                 |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Specifies a resource ID for pagination query, indicating that the query starts from the next record of the specified resource ID.                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                    |
   |                 |                 |                 | This parameter can work together with the parameter **limit**.                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                    |
   |                 |                 |                 | -  If parameters **marker** and **limit** are not passed, resource records on the first page will be returned.                                                                                                                     |
   |                 |                 |                 | -  If the parameter **marker** is not passed and the value of parameter **limit** is set to **10**, the first 10 resource records will be returned.                                                                                |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the value of parameter **limit** is set to **10**, the 11th to 20th resource records will be returned.                                |
   |                 |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the parameter **limit** is not passed, 11th to 2,000th resource records will be returned. The default value of **limit** is **2000**. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v1/b2782e6708b8475c993e6064bc456bf8/fl/flow_logs?name=flowlog

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------+----------------------------------------------------------------------+------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                                 | Description                                                                                    |
   +===========+======================================================================+================================================================================================+
   | flow_logs | Array of :ref:`FlowLog <vpc_flow_0002__table34811015184118>` objects | **FlowLog** object list. For details, see :ref:`Table 3 <vpc_flow_0002__table34811015184118>`. |
   +-----------+----------------------------------------------------------------------+------------------------------------------------------------------------------------------------+

.. _vpc_flow_0002__table34811015184118:

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
       "flow_logs": [
           {
               "id": "35868d55-443e-4d5c-90a4-ac618dc45c1a",
               "name": "flowlog",
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
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
