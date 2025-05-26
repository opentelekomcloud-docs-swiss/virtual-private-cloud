:original_name: vpc_peering_0005.html

.. _vpc_peering_0005:

Refusing a VPC Peering Connection
=================================

Function
--------

After tenant A requests to create a VPC peering connection with a VPC of tenant B, the VPC peering connection takes effect only after tenant B accepts the request. However, tenant can refuse the VPC peering connection request. This API is used by a tenant to refuse a VPC peering connection request initiated by another tenant.

URI
---

PUT /v2.0/vpc/peerings/{peering_id}/reject

:ref:`Table 1 <vpc_peering_0005__table18880184689>` describes the parameters.

.. _vpc_peering_0005__table18880184689:

.. table:: **Table 1** Parameter description

   +------------+-----------+--------+------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                    |
   +============+===========+========+================================================================================================+
   | peering_id | Yes       | String | Specifies the VPC peering connection ID, which uniquely identifies the VPC peering connection. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

-  Reject the VPC peering connection request from 22b76469-08e3-4937-8c1d-7aad34892be1.

   .. code-block:: text

      PUT https://{Endpoint}/v2.0/vpc/peerings/22b76469-08e3-4937-8c1d-7aad34892be1/reject

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Attribute             | Type                                                          | Description                                                                                                        |
   +=======================+===============================================================+====================================================================================================================+
   | id                    | String                                                        | Specifies the VPC peering connection ID.                                                                           |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                        | Specifies the VPC peering connection name.                                                                         |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                        | Specifies the VPC peering connection status. Possible values are as follows:                                       |
   |                       |                                                               |                                                                                                                    |
   |                       |                                                               | -  **PENDING_ACCEPTANCE**                                                                                          |
   |                       |                                                               | -  **REJECTED**                                                                                                    |
   |                       |                                                               | -  **EXPIRED**                                                                                                     |
   |                       |                                                               | -  **DELETED**                                                                                                     |
   |                       |                                                               | -  **ACTIVE**                                                                                                      |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | request_vpc_info      | :ref:`vpc_info <vpc_peering_0005__table1125991417114>` object | Specifies information about the local VPC. For details, see :ref:`Table 3 <vpc_peering_0005__table1125991417114>`. |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | accept_vpc_info       | :ref:`vpc_info <vpc_peering_0005__table1125991417114>` object | Specifies information about the peer VPC. For details, see :ref:`Table 3 <vpc_peering_0005__table1125991417114>`.  |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                        | Provides supplementary information about the VPC peering connection.                                               |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                                                        | Specifies the time (UTC) when the VPC peering connection is created.                                               |
   |                       |                                                               |                                                                                                                    |
   |                       |                                                               | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                      |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                                                        | Specifies the time (UTC) when the VPC peering connection is updated.                                               |
   |                       |                                                               |                                                                                                                    |
   |                       |                                                               | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                      |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+

.. _vpc_peering_0005__table1125991417114:

.. table:: **Table 3** **vpc_info** objects

   +-----------+--------+-----------------------------------------------------------------------------------------------+
   | Attribute | Type   | Description                                                                                   |
   +===========+========+===============================================================================================+
   | vpc_id    | String | Specifies the ID of a VPC involved in a VPC peering connection.                               |
   +-----------+--------+-----------------------------------------------------------------------------------------------+
   | tenant_id | String | Specifies the ID of the project that a VPC involved in the VPC peering connection belongs to. |
   +-----------+--------+-----------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "name": "test",
       "id": "22b76469-08e3-4937-8c1d-7aad34892be1",
       "request_vpc_info": {
          "vpc_id": "9daeac7c-a98f-430f-8e38-67f9c044e299",
          "tenant_id": "f65e9ebc-ed5d-418b-a931-9a723718ba4e"
       },
       "accept_vpc_info": {
          "vpc_id": "f583c072-0bb8-4e19-afb2-afb7c1693be5",
          "tenant_id": "f65e9ebc-ed5d-418b-a931-9a723718ba4e"
       },
       "status": "REJECTED"
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
