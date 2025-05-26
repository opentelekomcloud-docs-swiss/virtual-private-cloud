:original_name: vpc_sg01_0005.html

.. _vpc_sg01_0005:

Adding a Security Group Rule
============================

Function
--------

This API is used to add a security group rule.

URI
---

POST /v1/{project_id}/security-group-rules

Request Parameters
------------------

.. table:: **Table 1** Request parameter

   +---------------------+-----------+------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory | Type                                                                   | Description                                                                                                      |
   +=====================+===========+========================================================================+==================================================================================================================+
   | security_group_rule | Yes       | :ref:`security_group_rule <vpc_sg01_0005__table40497645103533>` object | Specifies the security group rule objects. For details, see :ref:`Table 2 <vpc_sg01_0005__table40497645103533>`. |
   +---------------------+-----------+------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+

.. _vpc_sg01_0005__table40497645103533:

.. table:: **Table 2** Description of the **security_group_rule** field

   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                                                                                                                                               |
   +===================+=================+=================+===========================================================================================================================================================================================================================================================+
   | security_group_id | Yes             | String          | Specifies the security group ID.                                                                                                                                                                                                                          |
   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description       | No              | String          | -  Provides supplementary information about the security group rule.                                                                                                                                                                                      |
   |                   |                 |                 | -  The value can contain no more than 255 characters, including letters and digits.                                                                                                                                                                       |
   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | direction         | Yes             | String          | -  Access control direction specified in a security group rule.                                                                                                                                                                                           |
   |                   |                 |                 | -  The value can be:                                                                                                                                                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                                                                                           |
   |                   |                 |                 |    -  **egress**                                                                                                                                                                                                                                          |
   |                   |                 |                 |    -  **ingress**                                                                                                                                                                                                                                         |
   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ethertype         | No              | String          | -  Specifies the IP protocol version.                                                                                                                                                                                                                     |
   |                   |                 |                 | -  The value can be **IPv4** or **IPv6**.                                                                                                                                                                                                                 |
   |                   |                 |                 | -  If you do not set this parameter, **IPv4** is used by default.                                                                                                                                                                                         |
   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol          | No              | String          | -  Specifies the protocol type.                                                                                                                                                                                                                           |
   |                   |                 |                 | -  The value can be **icmp**, **tcp**, **udp**, **icmpv6**, or an IP protocol number (0 to 255, for example, 47 for GRE)                                                                                                                                  |
   |                   |                 |                 | -  If the parameter is left blank, all protocols are supported. When the protocol is **icmpv6**, IP protocol version should be **IPv6**. When the protocol is **icmp**, IP protocol version should be **IPv4**.                                           |
   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_min    | No              | Integer         | -  Specifies the start port number.                                                                                                                                                                                                                       |
   |                   |                 |                 | -  The value ranges from 1 to 65535.                                                                                                                                                                                                                      |
   |                   |                 |                 | -  The value cannot be greater than the **port_range_max** value. An empty value indicates all ports. If the protocol is **icmp**, the value range is shown in :ref:`ICMP-Port Range Relationship Table <vpc_api_0009>`.                                  |
   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port_range_max    | No              | Integer         | -  Specifies the end port number.                                                                                                                                                                                                                         |
   |                   |                 |                 | -  The value ranges from 1 to 65535.                                                                                                                                                                                                                      |
   |                   |                 |                 | -  If the protocol is not **icmp**, the value cannot be smaller than the **port_range_min** value. An empty value indicates all ports. If the protocol is **icmp**, the value range is shown in :ref:`ICMP-Port Range Relationship Table <vpc_api_0009>`. |
   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_ip_prefix  | No              | String          | -  Specifies the remote IP address. If the access control direction is set to **egress**, the parameter specifies the source IP address. If the access control direction is set to **ingress**, the parameter specifies the destination IP address.       |
   |                   |                 |                 | -  The value can be in the CIDR format or IP addresses.                                                                                                                                                                                                   |
   |                   |                 |                 | -  The parameter value is mutually exclusive with .                                                                                                                                                                                                       |
   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_group_id   | No              | String          | -  Specifies the ID of the peer security group.                                                                                                                                                                                                           |
   |                   |                 |                 | -  The parameter value is mutually exclusive with .                                                                                                                                                                                                       |
   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  Create an inbound rule in the security group whose ID is a7734e61-b545-452d-a3cd-0189cbd9747a.

   .. code-block:: text

      POST https://{Endpoint}/v1/{project_id}/security-group-rules

      {
          "security_group_rule": {
              "direction": "ingress",
              "port_range_min": "80",
              "ethertype": "IPv4",
              "port_range_max": "80",
              "protocol": "tcp",
              "remote_group_id": "85cc3048-abc3-43cc-89b3-377341426ac5",
              "security_group_id": "a7734e61-b545-452d-a3cd-0189cbd9747a"
          }
      }

   .. code-block:: text

      POST https://{Endpoint}/v1/{project_id}/security-group-rules

      {
          "security_group_rule": {
              "direction": "ingress",
              "port_range_min": "80",
              "ethertype": "IPv6",
              "port_range_max": "90",
              "protocol": "tcp",
              "security_group_id": "a7734e61-b545-452d-a3cd-0189cbd9747a"
          }
      }

Response Parameters
-------------------

.. table:: **Table 3** Response parameter

   +---------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Parameter           | Type                                                                 | Description                                                                                                    |
   +=====================+======================================================================+================================================================================================================+
   | security_group_rule | :ref:`security_group_rule <vpc_sg01_0005__table488727239520>` object | Specifies the security group rule objects. For details, see :ref:`Table 4 <vpc_sg01_0005__table488727239520>`. |
   +---------------------+----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

.. _vpc_sg01_0005__table488727239520:

.. table:: **Table 4** **security_group_rule** objects

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
       "security_group_rule": {
           "direction": "ingress",
           "ethertype": "IPv4",
           "id": "2bc0accf-312e-429a-956e-e4407625eb62",
           "description": "",
           "port_range_max": 80,
           "port_range_min": 80,
           "protocol": "tcp",
           "remote_group_id": "85cc3048-abc3-43cc-89b3-377341426ac5",
           "remote_ip_prefix": null,
           "security_group_id": "a7734e61-b545-452d-a3cd-0189cbd9747a",
           "tenant_id": "e4f50856753b4dc6afee5fa6b9b6c550"
       }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
