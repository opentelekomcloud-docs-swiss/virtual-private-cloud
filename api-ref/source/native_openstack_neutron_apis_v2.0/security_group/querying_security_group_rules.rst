:original_name: vpc_sg02_0006.html

.. _vpc_sg02_0006:

Querying Security Group Rules
=============================

Function
--------

This API is used to query all security group rules accessible to the tenant submitting the request.

URI
---

GET /v2.0/security-group-rules

Example:

.. code-block:: text

   GET https://{Endpoint}/v2.0/security-group-rules?security_group_id={security_group_id}&remote_group_id={remote_group_id}&direction={direction}&remote_ip_prefix={remote_ip_prefix}&protocol={protocol}&port_range_max={port_range_max}&port_range_min={port_range_min}&ethertype={ethertype}&tenant_id ={tenant_id}

Example of querying security group rules by page

.. code-block:: text

   GET https://{Endpoint}/v2.0/networks?limit=2&marker=07adc044-3f21-4eeb-bd57-5e5eb6024b7f&page_reverse=False

:ref:`Table 1 <vpc_sg02_0006__table15294154210275>` describes the parameters.

.. _vpc_sg02_0006__table15294154210275:

.. table:: **Table 1** Parameter description

   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name              | Mandatory       | Type            | Description                                                                                                                                                                                                            |
   +===================+=================+=================+========================================================================================================================================================================================================================+
   | id                | No              | String          | Specifies that the security group rule ID is used as the filtering condition.                                                                                                                                          |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description       | No              | String          | Specifies that the description is used as the filtering condition.                                                                                                                                                     |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_group_id   | No              | String          | Specifies the ID of the remote security group associated with the security group rule is used as the filtering condition.                                                                                              |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id | No              | String          | Specifies the ID of the corresponding security group is used as the filtering condition.                                                                                                                               |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | direction         | No              | String          | Specifies the security group rule direction is used as the filtering condition. The value can be **ingress** or **egress**.                                                                                            |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol          | No              | String          | Specifies that the IP protocol is used as the filtering condition.                                                                                                                                                     |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_ip_prefix  | No              | String          | Specifies the remote IP address range matching the security group rule is used as the filtering condition.                                                                                                             |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ethertype         | No              | String          | Specifies that the network type is used as the filtering condition.                                                                                                                                                    |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_max    | No              | Integer         | Specifies that the maximum port is used as the filtering condition.                                                                                                                                                    |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_min    | No              | Integer         | Specifies that the minimum port is used as the filtering condition.                                                                                                                                                    |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id         | No              | String          | Specifies that the project ID is used as the filtering condition.                                                                                                                                                      |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker            | No              | String          | Specifies a resource ID for pagination query, indicating that the query starts from the next record of the specified resource ID.                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                                                        |
   |                   |                 |                 | This parameter can work together with the parameter **limit**.                                                                                                                                                         |
   |                   |                 |                 |                                                                                                                                                                                                                        |
   |                   |                 |                 | -  If parameters **marker** and **limit** are not passed, resource records on the first page will be returned.                                                                                                         |
   |                   |                 |                 | -  If the parameter **marker** is not passed and the value of parameter **limit** is set to **10**, the first 10 resource records will be returned.                                                                    |
   |                   |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the value of parameter **limit** is set to **10**, the 11th to 20th resource records will be returned.                    |
   |                   |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the parameter **limit** is not passed, resource records starting from the 11th records (including 11th) will be returned. |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit             | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax (2^31-1). The default value is 2000.                                                                                 |
   |                   |                 |                 |                                                                                                                                                                                                                        |
   |                   |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                              |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v2.0/security-group-rules

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +----------------------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Type                                                                               | Description                                                                                                                                                                                                     |
   +============================+====================================================================================+=================================================================================================================================================================================================================+
   | security_group_rules       | Array of :ref:`Security Group Rule <vpc_sg02_0006__table655457801607>` objects     | Specifies the security group rule list. For details, see :ref:`Table 3 <vpc_sg02_0006__table655457801607>`.                                                                                                     |
   +----------------------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_rules_links | Array of :ref:`SecurityGroupRulesLink <vpc_sg02_0006__table1318194661915>` objects | Shows pagination information about security group rules.                                                                                                                                                        |
   |                            |                                                                                    |                                                                                                                                                                                                                 |
   |                            |                                                                                    | Only when **limit** is used for filtering and the number of resources exceeds the value of **limit** or 2000 (default value of **limit**), value **next** will be returned for **rel** and a link for **href**. |
   +----------------------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_sg02_0006__table655457801607:

.. table:: **Table 3** **Security Group Rule** objects

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Attribute             | Type                  | Description                                                                                                                                                                                 |
   +=======================+=======================+=============================================================================================================================================================================================+
   | id                    | String                | Specifies the security group rule ID.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | This parameter is not mandatory when you query security group rules.                                                                                                                        |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Provides supplementary information about the security group rule.                                                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id     | String                | Specifies the ID of the belonged security group.                                                                                                                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_group_id       | String                | Specifies the peer ID of the belonged security group.                                                                                                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | direction             | String                | Specifies the direction of the traffic for which the security group rule takes effect.                                                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_ip_prefix      | String                | Specifies the peer IP address segment.                                                                                                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol              | String                | Specifies the protocol type or the IP protocol number.                                                                                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_max        | Integer               | Specifies the maximum port number. When ICMP is used, the value is the ICMP code.                                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_min        | Integer               | Specifies the minimum port number. If the ICMP protocol is used, this parameter indicates the ICMP type.                                                                                    |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | When the TCP or UDP protocol is used, both **port_range_max** and **port_range_min** must be specified, and the **port_range_max** value must be greater than the **port_range_min** value. |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | When the ICMP protocol is used, if you specify the ICMP code (**port_range_max**), you must also specify the ICMP type (**port_range_min**).                                                |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ethertype             | String                | Specifies the network type.                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | IPv4 and IPv6 are supported.                                                                                                                                                                |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                | Specifies the project ID.                                                                                                                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`.                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                | Specifies the time (UTC) when the security group rule is created.                                                                                                                           |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                | Specifies the time (UTC) when the security group rule is updated.                                                                                                                           |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_sg02_0006__table1318194661915:

.. table:: **Table 4** **SecurityGroupRulesLink** objects

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
       "security_group_rules": [
           {
               "remote_group_id": "1d8b19c7-7c56-48f7-a99b-4b40eb390967",
               "direction": "ingress",
               "remote_ip_prefix": null,
               "protocol": null,
               "tenant_id": "6c9298ec8c874f7f99688489ab65f90e",
               "port_range_max": null,
               "security_group_id": "1d8b19c7-7c56-48f7-a99b-4b40eb390967",
               "port_range_min": null,
               "ethertype": "IPv6",
               "description": null,
               "id": "07adc044-3f21-4eeb-bd57-5e5eb6024b7f",
               "project_id": "6c9298ec8c874f7f99688489ab65f90e",
               "created_at": "2018-09-20T02:15:34",
               "updated_at": "2018-09-20T02:15:34"
           },
           {
               "remote_group_id": null,
               "direction": "egress",
               "remote_ip_prefix": null,
               "protocol": null,
               "tenant_id": "6c9298ec8c874f7f99688489ab65f90e",
               "port_range_max": null,
               "security_group_id": "328fb454-a2ee-4a11-bdb1-ee19bbdfde43",
               "port_range_min": null,
               "ethertype": "IPv6",
               "description": null,
               "id": "09358f83-f4a5-4386-9563-a1e3c373d655",
               "project_id": "6c9298ec8c874f7f99688489ab65f90e",
               "created_at": "2018-09-20T02:15:34",
               "updated_at": "2018-09-20T02:15:34"
           },
           {
               "remote_group_id": "4c763030-366e-428c-be2b-d48f6baf5297",
               "direction": "ingress",
               "remote_ip_prefix": null,
               "protocol": null,
               "tenant_id": "6c9298ec8c874f7f99688489ab65f90e",
               "port_range_max": null,
               "security_group_id": "4c763030-366e-428c-be2b-d48f6baf5297",
               "port_range_min": null,
               "ethertype": "IPv6",
               "description": null,
               "id": "219a6f56-1069-458b-bec0-df9270e7a074",
               "project_id": "6c9298ec8c874f7f99688489ab65f90e",
               "created_at": "2018-09-20T02:15:34",
               "updated_at": "2018-09-20T02:15:34"
           }
       ],
       "security_group_rules_links": [
          {    "rel": "previous",
               "href": "https://{Endpoint}/v2.0/
   security-group-rules?marker=07adc044-3f21-4eeb-bd57-5e5eb6024b7f&page_reverse=True"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
