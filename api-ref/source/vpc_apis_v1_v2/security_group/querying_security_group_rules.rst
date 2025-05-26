:original_name: vpc_sg01_0007.html

.. _vpc_sg01_0007:

Querying Security Group Rules
=============================

Function
--------

This API is used to query security group rules using search criteria and to display the security group rules in a list.

URI
---

GET /v1/{project_id}/security-group-rules

Example:

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/security-group-rules?security_group_id=a7734e61-b545-452da3cd-0189cbd9747a&limit=10&marker=4779ab1c-7c1a-44b1-a02e-93dfc361b32d

:ref:`Table 1 <vpc_sg01_0007__table1939240195259>` describes the parameters.

.. _vpc_sg01_0007__table1939240195259:

.. table:: **Table 1** Parameter description

   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                                                                                                                        |
   +===================+=================+=================+====================================================================================================================================================================================================================================+
   | project_id        | Yes             | String          | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`.                                                                                                          |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker            | No              | String          | Specifies a resource ID for pagination query, indicating that the query starts from the next record of the specified resource ID.                                                                                                  |
   |                   |                 |                 |                                                                                                                                                                                                                                    |
   |                   |                 |                 | This parameter can work together with the parameter **limit**.                                                                                                                                                                     |
   |                   |                 |                 |                                                                                                                                                                                                                                    |
   |                   |                 |                 | -  If parameters **marker** and **limit** are not passed, resource records on the first page will be returned.                                                                                                                     |
   |                   |                 |                 | -  If the parameter **marker** is not passed and the value of parameter **limit** is set to **10**, the first 10 resource records will be returned.                                                                                |
   |                   |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the value of parameter **limit** is set to **10**, the 11th to 20th resource records will be returned.                                |
   |                   |                 |                 | -  If the value of the parameter **marker** is set to the resource ID of the 10th record and the parameter **limit** is not passed, 11th to 2,000th resource records will be returned. The default value of **limit** is **2000**. |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit             | No              | Integer         | Specifies the number of records that will be returned on each page. The value is from 0 to intmax (2^31-1). The default value is 2000.                                                                                             |
   |                   |                 |                 |                                                                                                                                                                                                                                    |
   |                   |                 |                 | **limit** can be used together with **marker**. For details, see the parameter description of **marker**.                                                                                                                          |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id | No              | String          | Specifies the security group ID.                                                                                                                                                                                                   |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_ip_prefix  | No              | String          | Specifies the remote IP address.                                                                                                                                                                                                   |
   |                   |                 |                 |                                                                                                                                                                                                                                    |
   |                   |                 |                 | The value must be in CIDR format.                                                                                                                                                                                                  |
   +-------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/security-group-rules

Response Parameters
-------------------

+----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
| Parameter            | Type                                                                           | Description                                                                                                    |
+======================+================================================================================+================================================================================================================+
| security_group_rules | Array of :ref:`security_group_rule <vpc_sg01_0007__table488727239520>` objects | Specifies the security group rule objects. For details, see :ref:`Table 2 <vpc_sg01_0007__table488727239520>`. |
+----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

.. _vpc_sg01_0007__table488727239520:

.. table:: **Table 2** **security_group_rule** objects

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                               |
   +=======================+=======================+===========================================================================================================================================================================================================================================================+
   | id                    | String                | Specifies the security group rule ID, which uniquely identifies the security group rule.                                                                                                                                                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | -  Provides supplementary information about the security group rule.                                                                                                                                                                                      |
   |                       |                       | -  The value can contain no more than 255 characters, including letters and digits.                                                                                                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id     | String                | Specifies the security group rule ID, which uniquely identifies the security group rule.                                                                                                                                                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | direction             | String                | -  Specifies the direction of access control.                                                                                                                                                                                                             |
   |                       |                       | -  Possible values are as follows:                                                                                                                                                                                                                        |
   |                       |                       |                                                                                                                                                                                                                                                           |
   |                       |                       |    -  **egress**                                                                                                                                                                                                                                          |
   |                       |                       |    -  **ingress**                                                                                                                                                                                                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ethertype             | String                | -  Specifies the IP protocol version.                                                                                                                                                                                                                     |
   |                       |                       | -  The value can be **IPv4** or **IPv6**.                                                                                                                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol              | String                | -  Specifies the protocol type.                                                                                                                                                                                                                           |
   |                       |                       | -  The value can be **icmp**, **tcp**, **udp**, **icmpv6**, or an IP protocol number (0 to 255, for example, 47 for GRE)                                                                                                                                  |
   |                       |                       | -  If the parameter is left blank, all protocols are supported.                                                                                                                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_min        | Integer               | -  Specifies the start port number.                                                                                                                                                                                                                       |
   |                       |                       | -  The value ranges from 1 to 65535.                                                                                                                                                                                                                      |
   |                       |                       | -  The value cannot be greater than the **port_range_max** value. An empty value indicates all ports. If the protocol is **icmp**, the value range is shown in :ref:`ICMP-Port Range Relationship Table <vpc_api_0009>`.                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_max        | Integer               | -  Specifies the end port number.                                                                                                                                                                                                                         |
   |                       |                       | -  The value ranges from 1 to 65535.                                                                                                                                                                                                                      |
   |                       |                       | -  If the protocol is not **icmp**, the value cannot be smaller than the **port_range_min** value. An empty value indicates all ports. If the protocol is **icmp**, the value range is shown in :ref:`ICMP-Port Range Relationship Table <vpc_api_0009>`. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_ip_prefix      | String                | -  Specifies the remote IP address. If the access control direction is set to **egress**, the parameter specifies the source IP address. If the access control direction is set to **ingress**, the parameter specifies the destination IP address.       |
   |                       |                       | -  The value can be in the CIDR format or IP addresses.                                                                                                                                                                                                   |
   |                       |                       | -  The parameter value is mutually exclusive with parameters **remote_group_id** and **remote_address_group_id**.                                                                                                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_group_id       | String                | -  Specifies the ID of the peer security group.                                                                                                                                                                                                           |
   |                       |                       | -  The parameter value is mutually exclusive with parameters **remote_ip_prefix** and **remote_address_group_id**.                                                                                                                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                | -  Specifies the ID of the project to which the security group rule belongs.                                                                                                                                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "security_group_rules": [
           {
               "direction": "egress",
               "ethertype": "IPv6",
               "id": "3c0e45ff-adaf-4124-b083-bf390e5482ff",
               "description": "",
               "port_range_max": null,
               "port_range_min": null,
               "protocol": null,
               "remote_group_id": null,
               "remote_ip_prefix": null,
               "security_group_id": "85cc3048-abc3-43cc-89b3-377341426ac5",
               "tenant_id": "e4f50856753b4dc6afee5fa6b9b6c550"
           },
           {
               "direction": "egress",
               "ethertype": "IPv4",
               "id": "93aa42e5-80db-4581-9391-3a608bd0e448",
               "description": "",
               "port_range_max": null,
               "port_range_min": null,
               "protocol": null,
               "remote_group_id": null,
               "remote_ip_prefix": null,
               "security_group_id": "85cc3048-abc3-43cc-89b3-377341426ac5",
               "tenant_id": "e4f50856753b4dc6afee5fa6b9b6c550"
           },
           {
               "direction": "ingress",
               "ethertype": "IPv6",
               "id": "c0b09f00-1d49-4e64-a0a7-8a186d928138",
               "description": "",
               "port_range_max": null,
               "port_range_min": null,
               "protocol": null,
               "remote_group_id": "85cc3048-abc3-43cc-89b3-377341426ac5",
               "remote_ip_prefix": null,
               "security_group_id": "85cc3048-abc3-43cc-89b3-377341426ac5",
               "tenant_id": "e4f50856753b4dc6afee5fa6b9b6c550"
           },
           {
               "direction": "ingress",
               "ethertype": "IPv4",
               "id": "f7d45c89-008e-4bab-88ad-d6811724c51c",
               "description": "",
               "port_range_max": null,
               "port_range_min": null,
               "protocol": null,
               "remote_group_id": "85cc3048-abc3-43cc-89b3-377341426ac5",
               "remote_ip_prefix": null,
               "security_group_id": "85cc3048-abc3-43cc-89b3-377341426ac5",
               "tenant_id": "e4f50856753b4dc6afee5fa6b9b6c550"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
