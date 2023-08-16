:original_name: vpc_firewall_0004.html

.. _vpc_firewall_0004:

Updating a Firewall Rule
========================

Function
--------

This API is used to update a firewall rule.

URI
---

PUT /v2.0/fwaas/firewall_rules/{firewall_rule_id}

Request Parameters
------------------

.. table:: **Table 1** Request parameter

   +---------------+----------------------------------------------------------------------+-----------+----------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type                                                                 | Mandatory | Description                                                                                                    |
   +===============+======================================================================+===========+================================================================================================================+
   | firewall_rule | :ref:`firewall_rule <vpc_firewall_0004__table38646929121127>` object | Yes       | Specifies the firewall rule objects. For details, see :ref:`Table 2 <vpc_firewall_0004__table38646929121127>`. |
   +---------------+----------------------------------------------------------------------+-----------+----------------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0004__table38646929121127:

.. table:: **Table 2** **Firewall Rule** objects

   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | Attribute              | Mandatory       | Type            | Description                                                                                  |
   +========================+=================+=================+==============================================================================================+
   | name                   | No              | String          | Specifies the firewall rule name.                                                            |
   |                        |                 |                 |                                                                                              |
   |                        |                 |                 | The value can contain a maximum of 255 characters.                                           |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | description            | No              | String          | Provides supplementary information about the firewall rule.                                  |
   |                        |                 |                 |                                                                                              |
   |                        |                 |                 | The value can contain a maximum of 255 characters.                                           |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | protocol               | No              | String          | Specifies the IP protocol.                                                                   |
   |                        |                 |                 |                                                                                              |
   |                        |                 |                 | The value can be **TCP**, **UDP**, **ICMPV6**, **ICMP**, or a value ranging from 0 to 255.   |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | source_port            | No              | String          | Specifies the source port number or port number range.                                       |
   |                        |                 |                 |                                                                                              |
   |                        |                 |                 | The value can be an integer from 1 to 65535 or a port number range in the format of **a:b**. |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | destination_port       | No              | String          | Specifies the destination port number or port number range.                                  |
   |                        |                 |                 |                                                                                              |
   |                        |                 |                 | The value can be an integer from 1 to 65535 or a port number range in the format of **a:b**. |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | ip_version             | No              | Integer         | Specifies the IP protocol version.                                                           |
   |                        |                 |                 |                                                                                              |
   |                        |                 |                 | The value can be **4** and **6**, indicating IPv4 address and IPv6 address, respectively.    |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | source_ip_address      | No              | String          | Specifies the source IP address or CIDR block.                                               |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | destination_ip_address | No              | String          | Specifies the destination IP address or CIDR block.                                          |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | action                 | No              | String          | Specifies action performed on traffic passing through the firewall.                          |
   |                        |                 |                 |                                                                                              |
   |                        |                 |                 | The value can be **deny** or **allow**.                                                      |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | enabled                | No              | Boolean         | Specifies whether the firewall rule is enabled.                                              |
   |                        |                 |                 |                                                                                              |
   |                        |                 |                 | The value can be **true** or **false**.                                                      |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+

Example Request
---------------

Change the **action** of the ACL rule whose ID is b94acf06-efc2-485d-ba67-a61acf2a7e28 to **deny**.

.. code-block:: text

   PUT https://{Endpoint}/v2.0/fwaas/firewall_rules/b94acf06-efc2-485d-ba67-a61acf2a7e28

   {
       "firewall_rule": {
           "action": "deny"
       }
   }

Response Parameters
-------------------

.. table:: **Table 3** Response parameter

   +---------------+-------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type                                                              | Description                                                                                                 |
   +===============+===================================================================+=============================================================================================================+
   | firewall_rule | :ref:`firewall_rule <vpc_firewall_0004__table96821221510>` object | Specifies the firewall rule objects. For details, see :ref:`Table 4 <vpc_firewall_0004__table96821221510>`. |
   +---------------+-------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+

.. _vpc_firewall_0004__table96821221510:

.. table:: **Table 4** **Firewall Rule** objects

   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | Attribute              | Type    | Description                                                                                                               |
   +========================+=========+===========================================================================================================================+
   | id                     | String  | Specifies the UUID of the firewall rule.                                                                                  |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | name                   | String  | Specifies the firewall rule name.                                                                                         |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | description            | String  | Provides supplementary information about the firewall rule.                                                               |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | tenant_id              | String  | Specifies the project ID.                                                                                                 |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | public                 | Boolean | Specifies whether the firewall rule can be shared by different tenants.                                                   |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | protocol               | String  | Specifies the IP protocol.                                                                                                |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | source_port            | String  | Specifies the source port number or port number range.                                                                    |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | destination_port       | String  | Specifies the destination port number or port number range.                                                               |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | ip_version             | Integer | Specifies the IP protocol version.                                                                                        |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | source_ip_address      | String  | Specifies the source IP address or CIDR block.                                                                            |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | destination_ip_address | String  | Specifies the destination IP address or CIDR block.                                                                       |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | action                 | String  | Specifies action performed on traffic passing through the firewall.                                                       |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | enabled                | Boolean | Specifies whether the firewall rule is enabled.                                                                           |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | project_id             | String  | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +------------------------+---------+---------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "firewall_rule": {
           "protocol": "tcp",
           "description": "",
           "source_ip_address": null,
           "destination_ip_address": null,
           "source_port": null,
           "destination_port": "80",
           "id": "b94acf06-efc2-485d-ba67-a61acf2a7e28",
           "name": "ALLOW_HTTP",
           "tenant_id": "23c8a121505047b6869edf39f3062712",
           "enabled": true,
           "action": "deny",
           "ip_version": 4,
           "public": false,
           "project_id": "23c8a121505047b6869edf39f3062712"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
