:original_name: vpc_privateip_0001.html

.. _vpc_privateip_0001:

Assigning a Private IP Address
==============================

Function
--------

This API is used to assign a private IP address.

URI
---

POST /v1/{project_id}/privateips

:ref:`Table 1 <vpc_privateip_0001__table57906226>` describes the parameters.

.. _vpc_privateip_0001__table57906226:

.. table:: **Table 1** Parameter description

   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Description                                                                                                               |
   +============+===========+===========================================================================================================================+
   | project_id | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request parameter

   +------------+-----------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type                                                                  | Description                                                                                                    |
   +============+===========+=======================================================================+================================================================================================================+
   | privateips | Yes       | Array of :ref:`privateip <vpc_privateip_0001__table45335391>` objects | Specifies the private IP address objects. For details, see :ref:`Table 3 <vpc_privateip_0001__table45335391>`. |
   +------------+-----------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

.. _vpc_privateip_0001__table45335391:

.. table:: **Table 3** Description of the **privateip** field

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================+
   | subnet_id       | Yes             | String          | Specifies the ID of the subnet from which IP addresses are assigned.                                                               |
   |                 |                 |                 |                                                                                                                                    |
   |                 |                 |                 | If you use the management console, the value of this parameter is the **Network ID** value.                                        |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------+
   | ip_address      | No              | String          | -  Specifies the target IP address.                                                                                                |
   |                 |                 |                 | -  The value can be an available IP address in the subnet. If it is not specified, the system automatically assigns an IP address. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  Assign two private IP addresses from the subnet whose ID is 531dec0f-3116-411b-a21b-e612e42349fd. One IP address is automatically assigned, and the other is specified to 192.168.1.17.

   .. code-block:: text

      POST https://{Endpoint}/v1/{project_id}/privateips

      {
        "privateips":
         [
          {
              "subnet_id": "531dec0f-3116-411b-a21b-e612e42349fd"
          },
          {
              "subnet_id": "531dec0f-3116-411b-a21b-e612e42349fd",
               "ip_address": "192.168.1.17"
          }
         ]
      }

Response Parameters
-------------------

.. table:: **Table 4** Response parameter

   +------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type                                                                  | Description                                                                                                    |
   +============+=======================================================================+================================================================================================================+
   | privateips | Array of :ref:`privateip <vpc_privateip_0001__table34571880>` objects | Specifies the private IP address objects. For details, see :ref:`Table 5 <vpc_privateip_0001__table34571880>`. |
   +------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

.. _vpc_privateip_0001__table34571880:

.. table:: **Table 5** Description of the **privateip** field

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                           |
   +=======================+=======================+=======================================================================================================================================================================================+
   | status                | String                | -  Specifies the status of the private IP address.                                                                                                                                    |
   |                       |                       | -  Possible values are as follows:                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       |    -  **ACTIVE**                                                                                                                                                                      |
   |                       |                       |    -  **DOWN**                                                                                                                                                                        |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Specifies the ID of the private IP address, which uniquely identifies the private IP address.                                                                                         |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnet_id             | String                | Specifies the ID of the subnet from which IP addresses are assigned.                                                                                                                  |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       | If you use the management console, the value of this parameter is the **Network ID** value.                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                | Specifies the project ID.                                                                                                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | device_owner          | String                | -  Specifies the resource using the private IP address. The parameter is left blank if it is not used.                                                                                |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       | -  The value can be:                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       |    **network:dhcp**: DHCP service IP address                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       |    **network:router_interface_distributed**: Gateway IP address                                                                                                                       |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       |    **compute:**\ *xxx* (*xxx* indicates the AZ name. For example, **compute:aa-bb-cc** indicates that the IP address is used by an ECS in the AZ aa-bb-cc.): IP address of an ECS NIC |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       |    **neutron:VIP_PORT**: Virtual IP address                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       |    **neutron:LOADBALANCERV2**: IP address of a shared load balancer                                                                                                                   |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       |    **neutron:LOADBALANCERV3**: IP address of a dedicated load balancer                                                                                                                |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       |    **network:endpoint_interface**: IP address of a VPC endpoint                                                                                                                       |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       |    **network:nat_gateway**: IP address used by a NAT gateway                                                                                                                          |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       | -  The value range specifies only the type of private IP addresses supported by the current service.                                                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_address            | String                | Specifies the assigned private IP address.                                                                                                                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "privateips": [
           {
               "status": "DOWN",
               "id": "c60c2ce1-1e73-44bd-bf48-fd688448ff7b",
               "subnet_id": "531dec0f-3116-411b-a21b-e612e42349fd",
               "tenant_id": "8b7e35ad379141fc9df3e178bd64f55c",
               "device_owner": "",
               "ip_address": "192.168.1.10"
           },
           {
               "status": "DOWN",
               "id": "4b123c18-ae92-4dfa-92cd-d44002359aa1",
               "subnet_id": "531dec0f-3116-411b-a21b-e612e42349fd",
               "tenant_id": "8b7e35ad379141fc9df3e178bd64f55c",
               "device_owner": "",
               "ip_address": "192.168.1.17"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
