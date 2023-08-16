:original_name: vpc_network_0002.html

.. _vpc_network_0002:

Querying Network Details
========================

Function
--------

This API is used to query details about a network.

URI
---

GET /v2.0/networks/{network_id}

:ref:`Table 1 <vpc_network_0002__table1710134691014>` describes the parameters.

.. _vpc_network_0002__table1710134691014:

.. table:: **Table 1** Parameter description

   ========== ========= =========================
   Name       Mandatory Description
   ========== ========= =========================
   network_id Yes       Specifies the network ID.
   ========== ========= =========================

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v2.0/networks/0133cd73-34d4-4d4c-bf1f-e65b24603206

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                          | Description                                                                                     |
   +===========+===============================================================+=================================================================================================+
   | network   | :ref:`network <vpc_network_0002__table49902238182444>` object | Specifies the network. For details, see :ref:`Table 3 <vpc_network_0002__table49902238182444>`. |
   +-----------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------+

.. _vpc_network_0002__table49902238182444:

.. table:: **Table 3** **network** objects

   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Attribute               | Type                  | Description                                                                                                                                                                                        |
   +=========================+=======================+====================================================================================================================================================================================================+
   | status                  | String                | Specifies the network status. The value can be **ACTIVE**, **BUILD**, **DOWN**, or **ERROR**.                                                                                                      |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnets                 | Array of strings      | Specifies IDs of the subnets associated with this network. The IDs are in a list.                                                                                                                  |
   |                         |                       |                                                                                                                                                                                                    |
   |                         |                       | Only one subnet can be associated with each network.                                                                                                                                               |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                    | String                | Specifies the network name.                                                                                                                                                                        |
   |                         |                       |                                                                                                                                                                                                    |
   |                         |                       | The name cannot be the same as the **admin_external_net** value (preset network name and cannot be used).                                                                                          |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | router:external         | Boolean               | Specifies whether the network is an external network. The default value is **false**. This is an extended attribute.                                                                               |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | admin_state_up          | Boolean               | Specifies the administrative status.                                                                                                                                                               |
   |                         |                       |                                                                                                                                                                                                    |
   |                         |                       | The value can only be **true**.                                                                                                                                                                    |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id               | String                | Specifies the project ID.                                                                                                                                                                          |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | shared                  | Boolean               | Specifies whether the network can be shared by different tenants.                                                                                                                                  |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                      | String                | Specifies the network ID.                                                                                                                                                                          |
   |                         |                       |                                                                                                                                                                                                    |
   |                         |                       | This parameter is not mandatory when you query networks.                                                                                                                                           |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | provider:network_type   | String                | Specifies the network type. Only the VXLAN and GENEVE networks are supported. This is an extended attribute.                                                                                       |
   |                         |                       |                                                                                                                                                                                                    |
   |                         |                       | Tenants can only set this parameter to **geneve**. If this parameter is not specified, the network type is automatically set to VXLAN.                                                             |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone_hints | Array of strings      | Specifies the availability zones available to this network. The current version does not support cross-availability-zone network scheduling.                                                       |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zones      | Array of strings      | Specifies the availability zone of this network.                                                                                                                                                   |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_security_enabled   | Boolean               | Specifies whether the security option is enabled for the port. If the option is not enabled, the security group and DHCP snooping settings of all VMs in the network do not take effect.           |
   |                         |                       |                                                                                                                                                                                                    |
   |                         |                       | This parameter is not displayed when an external network is called and the value of **router:external** is **true**. This parameter is visible when the value of **router:external** is **false**. |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dns_domain              | String                | Specifies the default private network DNS domain address. The system automatically sets this parameter, and you are not allowed to configure or change the parameter value.                        |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id              | String                | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`.                                                                          |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at              | String                | Specifies the time (UTC) when the network is created.                                                                                                                                              |
   |                         |                       |                                                                                                                                                                                                    |
   |                         |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                                      |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at              | String                | Specifies the time (UTC) when the network is updated.                                                                                                                                              |
   |                         |                       |                                                                                                                                                                                                    |
   |                         |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                                      |
   +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "network": {
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
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
