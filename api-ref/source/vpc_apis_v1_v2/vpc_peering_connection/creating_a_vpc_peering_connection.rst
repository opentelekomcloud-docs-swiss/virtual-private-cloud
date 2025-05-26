:original_name: vpc_peering_0003.html

.. _vpc_peering_0003:

Creating a VPC Peering Connection
=================================

Function
--------

This API is used to create a VPC peering connection.

If you create a VPC peering connection with another VPC of your own, the connection is created without the need for you to accept the connection.

If you create a VPC peering connection with a VPC of another tenant, the peer tenant must accept the connection so that the connection can be created. If the peer tenant refuses the connection, it cannot be created.

URI
---

POST /v2.0/vpc/peerings

Request Parameters
------------------

.. table:: **Table 1** Request parameter

   +-----------+-----------+--------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                         | Description                                                                                                   |
   +===========+===========+==============================================================+===============================================================================================================+
   | peering   | Yes       | :ref:`peering <vpc_peering_0003__table1026243410414>` object | Specifies the VPC peering connection. For details, see :ref:`Table 2 <vpc_peering_0003__table1026243410414>`. |
   +-----------+-----------+--------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+

.. _vpc_peering_0003__table1026243410414:

.. table:: **Table 2** Description of the **peering** field

   +------------------+-----------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Attribute        | Mandatory       | Type                                                          | Description                                                                                                        |
   +==================+=================+===============================================================+====================================================================================================================+
   | name             | Yes             | String                                                        | Specifies the name of the VPC peering connection. The value can contain 1 to 64 characters.                        |
   +------------------+-----------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | description      | No              | String                                                        | Provides supplementary information about the VPC peering connection.                                               |
   |                  |                 |                                                               |                                                                                                                    |
   |                  |                 |                                                               | The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                      |
   +------------------+-----------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | request_vpc_info | Yes             | :ref:`vpc_info <vpc_peering_0003__table1132310347417>` object | Specifies information about the local VPC. For details, see :ref:`Table 3 <vpc_peering_0003__table1132310347417>`. |
   +------------------+-----------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | accept_vpc_info  | Yes             | :ref:`vpc_info <vpc_peering_0003__table1132310347417>` object | Specifies information about the peer VPC. For details, see :ref:`Table 3 <vpc_peering_0003__table1132310347417>`.  |
   +------------------+-----------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+

.. _vpc_peering_0003__table1132310347417:

.. table:: **Table 3** Description of the **vpc_info** field

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | Attribute       | Mandatory       | Type            | Description                                                                                              |
   +=================+=================+=================+==========================================================================================================+
   | vpc_id          | Yes             | String          | Specifies the ID of a VPC involved in a VPC peering connection.                                          |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | tenant_id       | No              | String          | Specifies the ID of the project to which a VPC involved in the VPC peering connection belongs.           |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 | This parameter is mandatory if the VPC peering connection is created between VPCs in different accounts. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  Create a VPC peering connection. The VPC ID of the requester is 9daeac7c-a98f-430f-8e38-67f9c044e299, the VPC ID of the receiver is f583c072-0bb8-4e19-afb2-afb7c1693be5, and the VPC peering connection is named **test**.

   .. code-block:: text

      POST https://{Endpoint}/v2.0/vpc/peerings

      {
          "peering": {
              "name": "test",
              "request_vpc_info": {
                 "vpc_id": "9daeac7c-a98f-430f-8e38-67f9c044e299"
              },
              "accept_vpc_info": {
                 "vpc_id": "f583c072-0bb8-4e19-afb2-afb7c1693be5"
              }
          }
      }

Response Parameters
-------------------

.. table:: **Table 4** Response parameter

   +-----------+---------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                          | Description                                                                                                    |
   +===========+===============================================================+================================================================================================================+
   | peering   | :ref:`peering <vpc_peering_0003__table14258131481112>` object | Specifies the VPC peering connection. For details, see :ref:`Table 5 <vpc_peering_0003__table14258131481112>`. |
   +-----------+---------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

.. _vpc_peering_0003__table14258131481112:

.. table:: **Table 5** **peering** objects

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
   | request_vpc_info      | :ref:`vpc_info <vpc_peering_0003__table1125991417114>` object | Specifies information about the local VPC. For details, see :ref:`Table 6 <vpc_peering_0003__table1125991417114>`. |
   +-----------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | accept_vpc_info       | :ref:`vpc_info <vpc_peering_0003__table1125991417114>` object | Specifies information about the peer VPC. For details, see :ref:`Table 6 <vpc_peering_0003__table1125991417114>`.  |
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

.. _vpc_peering_0003__table1125991417114:

.. table:: **Table 6** **vpc_info** objects

   +-----------+--------+------------------------------------------------------------------------------------------------+
   | Attribute | Type   | Description                                                                                    |
   +===========+========+================================================================================================+
   | vpc_id    | String | Specifies the ID of a VPC involved in a VPC peering connection.                                |
   +-----------+--------+------------------------------------------------------------------------------------------------+
   | tenant_id | String | Specifies the ID of the project to which a VPC involved in the VPC peering connection belongs. |
   +-----------+--------+------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "peering": {
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
           "status": "ACTIVE"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
