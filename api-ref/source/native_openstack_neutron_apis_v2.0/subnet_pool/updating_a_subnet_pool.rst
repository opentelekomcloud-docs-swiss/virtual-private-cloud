:original_name: vpc_subnetpools_0004.html

.. _vpc_subnetpools_0004:

Updating a Subnet Pool
======================

Function
--------

This API is used to update a subnet pool.

URI
---

PUT /v2.0/subnetpools/{subnetpool_id}

Request Message
---------------

.. table:: **Table 1** Request parameter

   +-----------------+--------------------------------------------------------------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type                                                               | Mandatory       | Description                                                                                                  |
   +=================+====================================================================+=================+==============================================================================================================+
   | subnetpool      | :ref:`subnetpool <vpc_subnetpools_0004__table149662441462>` object | Yes             | Specifies the subnet pool list. For details, see :ref:`Table 2 <vpc_subnetpools_0004__table12211980105515>`. |
   |                 |                                                                    |                 |                                                                                                              |
   |                 |                                                                    |                 | You must specify at least one attribute when updating the subnet pool.                                       |
   +-----------------+--------------------------------------------------------------------+-----------------+--------------------------------------------------------------------------------------------------------------+

.. _vpc_subnetpools_0004__table12211980105515:

.. table:: **Table 2** **subnetpool** objects

   +-------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Attribute         | Mandatory       | Type             | Description                                                                                                                                                                                                                                         |
   +===================+=================+==================+=====================================================================================================================================================================================================================================================+
   | name              | No              | String           | Specifies the subnet pool name.                                                                                                                                                                                                                     |
   +-------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_quota     | No              | Integer          | Specifies the upper limit of the prefix space that can be allocated from the subnet pool to the subnet. For IPv4 subnet pools, **default_quota** is measured in units of /32. For IPv6 subnet pools, **default_quota** is measured in units of /64. |
   +-------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | prefixes          | No              | Array of strings | Specifies a list of subnet prefixes that are assigned to the subnet pool. The adjacent prefixes are merged and treated as a single prefix. Each subnet prefix must be unique.                                                                       |
   +-------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_prefixlen     | No              | Integer          | Specifies the minimum number for the prefix of a subnet that can be allocated from the subnet pool. The minimum number for the prefix of an IPv4 subnet is **8**, and that of an IPv6 subnet is **64**. Instructions:                               |
   |                   |                 |                  |                                                                                                                                                                                                                                                     |
   |                   |                 |                  | min_prefixlen =< default_prefixlen =< max_prefixlen                                                                                                                                                                                                 |
   +-------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_prefixlen | No              | Integer          | Specifies the default prefix to be allocated to a subnet if the **cidr** or **prefixlen** is not specified when you create the subnet. The default value is **8** for an IPv4 subnet and **64** for an IPv6 subnet.                                 |
   |                   |                 |                  |                                                                                                                                                                                                                                                     |
   |                   |                 |                  | Instructions:                                                                                                                                                                                                                                       |
   |                   |                 |                  |                                                                                                                                                                                                                                                     |
   |                   |                 |                  | min_prefixlen =< default_prefixlen =< max_prefixlen                                                                                                                                                                                                 |
   +-------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | max_prefixlen     | No              | Integer          | Specifies the maximum number for the prefix of a subnet that can be allocated from the subnet pool. The maximum number for the prefix of an IPv4 subnet is **32**, and that of an IPv6 subnet is **128**.                                           |
   |                   |                 |                  |                                                                                                                                                                                                                                                     |
   |                   |                 |                  | Instructions:                                                                                                                                                                                                                                       |
   |                   |                 |                  |                                                                                                                                                                                                                                                     |
   |                   |                 |                  | min_prefixlen =< default_prefixlen =< max_prefixlen                                                                                                                                                                                                 |
   +-------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description       | No              | String           | Provides supplementary information about the subnet pool.                                                                                                                                                                                           |
   +-------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_default        | No              | Boolean          | Specifies whether this is the default subnet pool.                                                                                                                                                                                                  |
   +-------------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Message
----------------

.. table:: **Table 3** Response parameter

   +------------+--------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type                                                               | Description                                                                                                |
   +============+====================================================================+============================================================================================================+
   | subnetpool | :ref:`subnetpool <vpc_subnetpools_0004__table149662441462>` object | Specifies the subnet pool list. For details, see :ref:`Table 4 <vpc_subnetpools_0004__table149662441462>`. |
   +------------+--------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+

.. _vpc_subnetpools_0004__table149662441462:

.. table:: **Table 4** **subnetpool** objects

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Attribute             | Type                  | Description                                                                                                                                                                                                                                 |
   +=======================+=======================+=============================================================================================================================================================================================================================================+
   | id                    | String                | Specifies the subnet pool ID.                                                                                                                                                                                                               |
   |                       |                       |                                                                                                                                                                                                                                             |
   |                       |                       | This parameter is not mandatory when you query subnet pools.                                                                                                                                                                                |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the subnet pool name.                                                                                                                                                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_version            | Integer               | Specifies the IP address version.                                                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                             |
   |                       |                       | The value can be **4** (IPv4) or **6** (IPv6).                                                                                                                                                                                              |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_quota         | Integer               | Specifies the upper limit of the prefix space that can be allocated from the subnet pool to the subnet. For IPv4 subnet pools, default_quota is measured in units of /32. For IPv6 subnet pools, default_quota is measured in units of /64. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`.                                                                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                | Specifies the time (UTC) when the subnet pool is created.                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                             |
   |                       |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                | Specifies the time (UTC) when the subnet pool rule is updated.                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                             |
   |                       |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | prefixes              | Array of strings      | Specifies a list of subnet prefixes that are assigned to the subnet pool. The adjacent prefixes are merged and treated as a single prefix. Each subnet prefix must be unique.                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_prefixlen         | Integer               | Specifies the minimum number for the prefix of a subnet that can be allocated from the subnet pool. The minimum number for the prefix of an IPv4 subnet is **8**, and that of an IPv6 subnet is **64**.                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | address_scope_id      | String                | Specifies the ID of the address range allocated to the subnet pool.                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                                                             |
   |                       |                       | Only the administrator can specify this attribute.                                                                                                                                                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | shared                | Boolean               | Specifies whether the network can be shared to all projects.                                                                                                                                                                                |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                | Specifies the project ID.                                                                                                                                                                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_prefixlen     | Integer               | Specifies the default prefix to be allocated to a subnet if the **cidr** or **prefixlen** is not specified when you create the subnet. The default value is **8** for an IPv4 subnet and **64** for an IPv6 subnet.                         |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | max_prefixlen         | Integer               | Specifies the maximum number for the prefix of a subnet that can be allocated from the subnet pool. The maximum number for the prefix of an IPv4 subnet is **32**, and that of an IPv6 subnet is **128**.                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Provides supplementary information about the subnet pool.                                                                                                                                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_default            | Boolean               | Specifies whether this is the default subnet pool.                                                                                                                                                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                  | Array of strings      | Specifies the tags.                                                                                                                                                                                                                         |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example:
--------

Example request

.. code-block:: text

   PUT https://{Endpoint}/v2.0/subnetpools/03f761e6-eee0-43fc-a921-8acf64c14988

   {
       "subnetpool": {
           "name": "my-new-subnetpool-name",
           "prefixes": [
               "2001:db8::/64",
               "2001:db8:0:1::/64",
               "2001:db8:0:2::/64"
           ],
           "min_prefixlen": 64,
           "default_prefixlen": 64,
           "max_prefixlen": 64
       }
   }

Example response

.. code-block::

   {
       "subnetpool": {
           "name": "my-new-subnetpool-name",
           "default_quota": null,
           "is_default": false,
           "project_id": "9fadcee8aa7c40cdb2114fff7d569c08",
           "tenant_id": "9fadcee8aa7c40cdb2114fff7d569c08",
           "prefixes": [
               "2001:db8::/63",
               "2001:db8:0:2::/64"
           ],
           "min_prefixlen": 64,
           "address_scope_id": null,
           "ip_version": 6,
           "shared": false,
           "default_prefixlen": 64,
           "id": "03f761e6-eee0-43fc-a921-8acf64c14988",
           "max_prefixlen": 64,
           "description": "",
           "created_at": "2018-09-20T02:15:34",
           "updated_at": "2018-09-20T02:15:34",
           "tags": []
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
