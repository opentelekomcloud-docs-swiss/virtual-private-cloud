:original_name: vpc_privateip_0003.html

.. _vpc_privateip_0003:

Querying Private IP Addresses
=============================

Function
--------

This API is used to query private IP addresses using search criteria and to display the private IP addresses in a list.

URI
---

GET /v1/{project_id}/subnets/{subnet_id}/privateips

Example:

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/subnets/{subnet_id}/privateips?limit=10&marker=4779ab1c-7c1a-44b1-a02e-93dfc361b32d

:ref:`Table 1 <vpc_privateip_0003__table12098568>` describes the parameters.

.. _vpc_privateip_0003__table12098568:

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================================================================================+
   | project_id      | Yes             | String          | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`.                                                                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnet_id       | Yes             | String          | Specifies the unique ID of the subnet to which the private IP address belongs.                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                    |
   |                 |                 |                 | If you use the management console, the value of this parameter is the **Network ID** value.                                                                                                                                        |
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
   | limit           | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax (2^31-1). The default value is 2000.                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                                    |
   |                 |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/subnets/{subnet_id}/privateips

Response Parameters
-------------------

.. table:: **Table 2** Request parameter

   +------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type                                                                  | Description                                                                                                    |
   +============+=======================================================================+================================================================================================================+
   | privateips | Array of :ref:`privateip <vpc_privateip_0003__table21538022>` objects | Specifies the private IP address objects. For details, see :ref:`Table 3 <vpc_privateip_0003__table21538022>`. |
   +------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

.. _vpc_privateip_0003__table21538022:

.. table:: **Table 3** Description of the **privateip** field

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
               "id": "d600542a-b231-45ed-af05-e9930cb14f78",
               "subnet_id": "531dec0f-3116-411b-a21b-e612e42349fd",
               "tenant_id": "8b7e35ad379141fc9df3e178bd64f55c",
               "device_owner": "",
               "ip_address": "192.168.1.11"
           },
           {
               "status": "DOWN",
               "id": "d600542a-b231-45ed-af05-e9930cb14f79",
               "subnet_id": "531dec0f-3116-411b-a21b-e612e42349fd",
               "tenant_id": "8b7e35ad379141fc9df3e178bd64f55c",
               "device_owner": "",
               "ip_address": "192.168.1.12"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
