:original_name: vpc_privateip_0002.html

.. _vpc_privateip_0002:

Querying Private IP Address Details
===================================

Function
--------

This API is used to query details about a private IP address using the specified ID.

URI
---

GET /v1/{project_id}/privateips/{privateip_id}

:ref:`Table 1 <vpc_privateip_0002__table4378562>` describes the parameters.

.. _vpc_privateip_0002__table4378562:

.. table:: **Table 1** Parameter description

   +--------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Name         | Mandatory | Description                                                                                                               |
   +==============+===========+===========================================================================================================================+
   | project_id   | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +--------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | privateip_id | Yes       | Specifies the ID of the private IP address, which uniquely identifies the private IP address.                             |
   +--------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/privateips/d600542a-b231-45ed-af05-e9930cb14f78

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------+-------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Name      | Type                                                        | Description                                                                                                    |
   +===========+=============================================================+================================================================================================================+
   | privateip | :ref:`privateip <vpc_privateip_0002__table23250319>` object | Specifies the private IP address objects. For details, see :ref:`Table 3 <vpc_privateip_0002__table23250319>`. |
   +-----------+-------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

.. _vpc_privateip_0002__table23250319:

.. table:: **Table 3** Description of the **privateip** field

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Type                  | Description                                                                                                                                                                           |
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
   |                       |                       |    **compute:subeni**: IP address of a supplementary network interface                                                                                                                |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       |    **neutron:LOADBALANCERV2**: IP address of a shared load balancer                                                                                                                   |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       |    **neutron:LOADBALANCERV3**: IP address of a dedicated load balancer                                                                                                                |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       |    **network:endpoint_interface**: IP address of a VPC endpoint                                                                                                                       |
   |                       |                       |                                                                                                                                                                                       |
   |                       |                       | -  The value range specifies only the type of private IP addresses supported by the current service.                                                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_address            | String                | Specifies the assigned private IP address.                                                                                                                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "privateip":
           {
               "status": "DOWN",
               "id": "d600542a-b231-45ed-af05-e9930cb14f78",
               "subnet_id": "531dec0f-3116-411b-a21b-e612e42349fd",
               "tenant_id": "8b7e35ad379141fc9df3e178bd64f55c",
               "device_owner": "",
               "ip_address": "192.168.1.11"
           }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
