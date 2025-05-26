:original_name: vpc_network_0001.html

.. _vpc_network_0001:

Querying Networks
=================

Function
--------

Queries all networks accessible to the tenant submitting the request.

URI
---

GET /v2.0/networks

Example:

.. code-block:: text

   GET https://{Endpoint}/v2.0/networks?id={network_id}&status={network_status}&name={network_name}&admin_state_up=${admin_state_up}&tenant_id={tenant_id}&shared={is_shared}&provider:network_type={geneve}

Example of querying networks by page

.. code-block:: text

   GET https://{Endpoint}/v2.0/networks?limit=2&marker=0133cd73-34d4-4d4c-bf1f-e65b24603206&page_reverse=False

:ref:`Table 1 <vpc_network_0001__table1410155047>` describes the parameters.

.. _vpc_network_0001__table1410155047:

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                                                                                                                        |
   +=======================+=================+=================+====================================================================================================================================================================================================================================+
   | id                    | No              | String          | Specifies that the network ID is used as the filtering condition.                                                                                                                                                                  |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | No              | String          | Specifies that the network name is used as the filtering condition.                                                                                                                                                                |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up        | No              | Boolean         | Specifies that the admin state is used as the filtering condition.                                                                                                                                                                 |
   |                       |                 |                 |                                                                                                                                                                                                                                    |
   |                       |                 |                 | The value can be **true** or **false**.                                                                                                                                                                                            |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | provider:network_type | No              | String          | Specifies that the network type is used as the filtering condition.                                                                                                                                                                |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | shared                | No              | Boolean         | Specifies that whether the network can be shared by multiple tenants is used as the filtering condition.                                                                                                                           |
   |                       |                 |                 |                                                                                                                                                                                                                                    |
   |                       |                 |                 | The value can be **true** or **false**.                                                                                                                                                                                            |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | No              | String          | Specifies that the network status is used as the filtering condition.                                                                                                                                                              |
   |                       |                 |                 |                                                                                                                                                                                                                                    |
   |                       |                 |                 | The value can be **ACTIVE**, **BUILD**, or **DOWN**.                                                                                                                                                                               |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | router:external       | No              | Boolean         | Specifies whether the network is an external network is used as the filtering condition.                                                                                                                                           |
   |                       |                 |                 |                                                                                                                                                                                                                                    |
   |                       |                 |                 | The value can be **true** or **false**.                                                                                                                                                                                            |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | No              | String          | Specifies that the project ID is used as the filtering condition.                                                                                                                                                                  |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker                | No              | String          | Specifies a resource ID for pagination query, indicating that the query starts from the next record of the specified resource ID.                                                                                                  |
   |                       |                 |                 |                                                                                                                                                                                                                                    |
   |                       |                 |                 | This parameter can work together with the parameter **limit**.                                                                                                                                                                     |
   |                       |                 |                 |                                                                                                                                                                                                                                    |
   |                       |                 |                 | -  If parameters **marker** and **limit** are not passed, resource records on the first page will be returned.                                                                                                                     |
   |                       |                 |                 | -  If the parameter **marker** is not passed and the value of parameter **limit** is set to **10**, the first 10 resource records will be returned.                                                                                |
   |                       |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the value of parameter **limit** is set to **10**, the 11th to 20th resource records will be returned.                                |
   |                       |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the parameter **limit** is not passed, 11th to 2,000th resource records will be returned. The default value of **limit** is **2000**. |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit                 | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax (2^31-1). The default value is 2000.                                                                                             |
   |                       |                 |                 |                                                                                                                                                                                                                                    |
   |                       |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                                          |
   +-----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v2.0/networks?limit=1

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                         | Description                                                                                                                                                                                                     |
   +=======================+==============================================================================+=================================================================================================================================================================================================================+
   | networks              | Array of :ref:`network <vpc_network_0001__table49902238182444>` objects      | Specifies the network list. For details, see :ref:`Table 3 <vpc_network_0001__table49902238182444>`.                                                                                                            |
   +-----------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | networks_links        | Array of :ref:`networks_link <vpc_network_0001__table1296611517358>` objects | Specifies the pagination information. For details, see :ref:`Table 4 <vpc_network_0001__table1296611517358>`.                                                                                                   |
   |                       |                                                                              |                                                                                                                                                                                                                 |
   |                       |                                                                              | Only when **limit** is used for filtering and the number of resources exceeds the value of **limit** or 2000 (default value of **limit**), value **next** will be returned for **rel** and a link for **href**. |
   +-----------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_network_0001__table49902238182444:

.. table:: **Table 3** **network** object

   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Attribute               | Type                  | Description                                                                                                                                                                                                                                              |
   +=========================+=======================+==========================================================================================================================================================================================================================================================+
   | status                  | String                | Specifies the network status. The value can be **ACTIVE**, **BUILD**, **DOWN**, or **ERROR**.                                                                                                                                                            |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnets                 | Array of strings      | Specifies ID of the subnet associated with this network.                                                                                                                                                                                                 |
   |                         |                       |                                                                                                                                                                                                                                                          |
   |                         |                       | Only one subnet can be associated with each network.                                                                                                                                                                                                     |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                    | String                | Specifies the network name.                                                                                                                                                                                                                              |
   |                         |                       |                                                                                                                                                                                                                                                          |
   |                         |                       | The name cannot be the same as the **admin_external_net** value (preset network name and cannot be used).                                                                                                                                                |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | router:external         | Boolean               | Specifies whether the network is an external network. The default value is **false**. This is an extended attribute.                                                                                                                                     |
   |                         |                       |                                                                                                                                                                                                                                                          |
   |                         |                       | If the value of this parameter is set to **true**, the **port_security_enable** parameter is not returned.                                                                                                                                               |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up          | Boolean               | Specifies the administrative status.                                                                                                                                                                                                                     |
   |                         |                       |                                                                                                                                                                                                                                                          |
   |                         |                       | The value can only be **true**.                                                                                                                                                                                                                          |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id               | String                | Specifies the project ID.                                                                                                                                                                                                                                |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | shared                  | Boolean               | Specifies whether the network can be shared by different tenants.                                                                                                                                                                                        |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                      | String                | Specifies the network ID.                                                                                                                                                                                                                                |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | provider:network_type   | String                | Specifies the network type.                                                                                                                                                                                                                              |
   |                         |                       |                                                                                                                                                                                                                                                          |
   |                         |                       | Only the VXLAN and GENEVE networks are supported.                                                                                                                                                                                                        |
   |                         |                       |                                                                                                                                                                                                                                                          |
   |                         |                       | Tenants can only set this parameter to **geneve**. If this parameter is not specified, the network type is automatically set to VXLAN. If the network is preset as **admin_external_net**, this parameter is fixed at **vlan** and cannot be configured. |
   |                         |                       |                                                                                                                                                                                                                                                          |
   |                         |                       | Note:                                                                                                                                                                                                                                                    |
   |                         |                       |                                                                                                                                                                                                                                                          |
   |                         |                       | -  Set this parameter to **geneve** if you want to create GENEVE networks.                                                                                                                                                                               |
   |                         |                       | -  Do not specify this parameter if you want to create VXLAN networks.                                                                                                                                                                                   |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone_hints | Array of strings      | Specifies the availability zones available to this network. The current version does not support cross-availability-zone network scheduling.                                                                                                             |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zones      | Array of strings      | Specifies the availability zone of this network.                                                                                                                                                                                                         |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_security_enabled   | Boolean               | Specifies whether the security option is enabled for the port. If the option is not enabled, the security group and DHCP snooping settings of all VMs in the network do not take effect.                                                                 |
   |                         |                       |                                                                                                                                                                                                                                                          |
   |                         |                       | This parameter is not displayed when an external network is called and the value of **router:external** is **true**. This parameter is visible when the value of **router:external** is **false**.                                                       |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dns_domain              | String                | Specifies the default private network DNS domain address. The system automatically sets this parameter, and you are not allowed to configure or change the parameter value.                                                                              |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id              | String                | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`.                                                                                                                                |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at              | String                | Specifies the time (UTC) when the network is created.                                                                                                                                                                                                    |
   |                         |                       |                                                                                                                                                                                                                                                          |
   |                         |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                                                                                            |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at              | String                | Specifies the time (UTC) when the network is updated.                                                                                                                                                                                                    |
   |                         |                       |                                                                                                                                                                                                                                                          |
   |                         |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                                                                                            |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_network_0001__table1296611517358:

.. table:: **Table 4** **networks_link** object

   +-----------+--------+----------------------------------------------------------------------+
   | Parameter | Type   | Description                                                          |
   +===========+========+======================================================================+
   | href      | String | Specifies the API link.                                              |
   +-----------+--------+----------------------------------------------------------------------+
   | rel       | String | Specifies the relationship between the API link and the API version. |
   +-----------+--------+----------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "networks": [
           {
               "id": "0133cd73-34d4-4d4c-bf1f-e65b24603206",
               "name": "3804f26c-7862-43b6-ad3c-48445f42de89",
               "status": "ACTIVE",
               "shared": false,
               "subnets": [
                   "423796f5-e02f-476f-bf02-2b88c8ddac8b"
               ],
               "availability_zone_hints": [],
               "availability_zones": [
                   "az2.dc2",
                   "az5.dc5"
               ],
               "admin_state_up": true,
               "tenant_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
               "project_id": "bbfe8c41dd034a07bebd592bf03b4b0c",
               "provider:network_type": "vxlan",
               "router:external": false,
               "port_security_enabled": true,
               "created_at": "2018-03-23T03:51:58",
               "updated_at": "2018-03-23T03:51:58"
           }
       ],
       "networks_links": [
          {
               "rel": "next",
               "href": "https://{Endpoint}/v2.0/networks?limit=1&marker=0133cd73-34d4-4d4c-bf1f-e65b24603206"
           },
          {    "rel": "previous",
               "href": "https://{Endpoint}/v2.0/subnets?limit=1&marker=0133cd73-34d4-4d4c-bf1f-e65b24603206&page_reverse=True"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
