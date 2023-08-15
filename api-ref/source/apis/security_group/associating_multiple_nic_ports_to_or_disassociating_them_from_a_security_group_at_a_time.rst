:original_name: vpc_sg01_0009.html

.. _vpc_sg01_0009:

Associating Multiple NIC Ports to or Disassociating Them from a Security Group at a Time
========================================================================================

Function
--------

This API is used to associate multiple NIC ports to or disassociate them from a specified security group at a time.

Restrictions

-  A maximum of 20 ports can be associated to or disassociated from a security group at a time. Therefore, the **ports** can contain a maximum of 20 values.
-  No error message is displayed if a port is repeatedly associated with a security group.

URI
---

POST /v2.0/{project_id}/security-groups/{security_group_id}/instance/action

:ref:`Table 1 <vpc_sg01_0009__table7179415121614>` describes the parameters.

.. _vpc_sg01_0009__table7179415121614:

.. table:: **Table 1** Parameter description

   +-------------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Name              | Mandatory | Description                                                                                                               |
   +===================+===========+===========================================================================================================================+
   | project_id        | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +-------------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | security_group_id | Yes       | Specifies the security group ID, which uniquely identifies the security group.                                            |
   +-------------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

-  Request parameter

   .. table:: **Table 2** Request parameter

      +--------+-----------+-----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | Name   | Mandatory | Type                                                            | Description                                                                                                                       |
      +========+===========+=================================================================+===================================================================================================================================+
      | ports  | Yes       | Array of :ref:`Port <vpc_sg01_0009__table425751511619>` objects | Specifies the port list. A maximum of 20 ports are supported. For details, see :ref:`Table 3 <vpc_sg01_0009__table425751511619>`. |
      +--------+-----------+-----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | action | Yes       | String                                                          | Specifies the operation. The value can be **add** (associate) or **remove** (disassociate). The values are case-insensitive.      |
      +--------+-----------+-----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+

   .. _vpc_sg01_0009__table425751511619:

   .. table:: **Table 3** Description of field **Port**

      +------+-----------+--------+------------------------------------------------------------+
      | Name | Mandatory | Type   | Description                                                |
      +======+===========+========+============================================================+
      | id   | Yes       | String | Specifies the port ID, which uniquely identifies the port. |
      +------+-----------+--------+------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{Endpoint}/v1/{project_id}/security-groups/0c4a2336-b036-4fa2-bc3c-1a291ed4c431/instance/action

      {
          "ports": [
              {
                  "id": "b9ac5247-c4ca-4c9b-b8fa-7d19132e560a"
              },
              {
                  "id": "aa2f8625-0042-4627-a05c-61500b604cc3"
              }
          ],
          "action": "add"
      }

Response Message
----------------

-  Response parameter

   .. table:: **Table 4** Response parameter

      +-----------------------+-------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                                                  | Description                                                                                                                              |
      +=======================+=======================================================+==========================================================================================================================================+
      | fail                  | :ref:`fail <vpc_sg01_0009__table728810252119>` object | Specifies the failed ports. For details, see :ref:`Table 5 <vpc_sg01_0009__table728810252119>`.                                          |
      |                       |                                                       |                                                                                                                                          |
      |                       |                                                       | If all ports are associated with or disassociated from the security group successfully, the **fail** list in the response body is blank. |
      +-----------------------+-------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+

   .. _vpc_sg01_0009__table728810252119:

   .. table:: **Table 5** **fail** objects

      +------------+--------+--------------------------------------------------------------------------+
      | Name       | Type   | Description                                                              |
      +============+========+==========================================================================+
      | id         | String | Specifies the ID of the failed port, which uniquely identifies the port. |
      +------------+--------+--------------------------------------------------------------------------+
      | error_code | String | Specifies the error code.                                                |
      +------------+--------+--------------------------------------------------------------------------+
      | error_msg  | String | Specifies the error message.                                             |
      +------------+--------+--------------------------------------------------------------------------+

-  Example normal response 1

   Multiple NIC ports are successfully associated to or disassociated from a security group at a time.

   .. code-block::

      {
          "fail": []
      }

-  Example normal response 2

   Some NIC ports fail to be associated to or disassociated from a security group at a time.

   .. code-block::

      {
          "fail": [
              {
                  "id": "99d9d709-8478-4b46-9f3f-2206b1023fd3",
                  "error_code": "VPC.0608",
                  "error_msg": "{\"NeutronError\":{\"message\":\"Port 99d9d709-8478-4b46-9f3f-2206b1023fd3 could not be found.\",\"type\":\"PortNotFound\",\"detail\":\"\"}}"
              },
              {
                  "id": "aa2f8625-0042-4627-a05c-61500b604cc3",
                  "error_code": "VPC.0607",
                  "error_msg": "An instance must belong to at least one security group"
              }
          ]
      }

-  Example abnormal response

   .. code-block::

      {
          "code": "VPC.0606",
          "message": "Request is invalid"
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
