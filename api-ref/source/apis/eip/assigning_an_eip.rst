:original_name: en-us_topic_0020090596.html

.. _en-us_topic_0020090596:

Assigning an EIP
================

Function
--------

This API is used to assign an EIP.

The EIP service provides independent public IP addresses and bandwidth for Internet access. EIPs can be bound to or unbound from ECSs, BMSs, virtual IP addresses, NAT gateways, or load balancers.

URI
---

POST /v1/{project_id}/publicips

:ref:`Table 1 <en-us_topic_0020090596__table57311924>` describes the parameters.

.. _en-us_topic_0020090596__table57311924:

.. table:: **Table 1** Parameter description

   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Name       | Mandatory | Description                                                                                                               |
   +============+===========+===========================================================================================================================+
   | project_id | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameter

   +-----------+-----------+-----------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+
   | Name      | Mandatory | Type                                                            | Description                                                                                              |
   +===========+===========+=================================================================+==========================================================================================================+
   | publicip  | Yes       | :ref:`publicip <en-us_topic_0020090596__table4491214>` object   | Specifies the EIP object. For details, see :ref:`Table 3 <en-us_topic_0020090596__table4491214>`.        |
   +-----------+-----------+-----------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+
   | bandwidth | Yes       | :ref:`bandwidth <en-us_topic_0020090596__table11041789>` object | Specifies the bandwidth object. For details, see :ref:`Table 4 <en-us_topic_0020090596__table11041789>`. |
   +-----------+-----------+-----------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020090596__table4491214:

.. table:: **Table 3** Description of the **publicip** field

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================+
   | type            | Yes             | String          | -  Specifies the EIP type.                                                                                                    |
   |                 |                 |                 | -  The value can be **5_bgp** and **5_dualStack**.                                                                            |
   |                 |                 |                 | -  Constraints:                                                                                                               |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 |    -  The configured value must be supported by the system.                                                                   |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
   | ip_version      | No              | Integer         | -  Specifies the EIP version.                                                                                                 |
   |                 |                 |                 | -  The value can be **4** and **6**, indicating IPv4 address and IPv6 address, respectively. IPv6 is not supported currently. |
   |                 |                 |                 | -  Constraints:                                                                                                               |
   |                 |                 |                 |                                                                                                                               |
   |                 |                 |                 |    -  The configured value must be supported by the system.                                                                   |
   |                 |                 |                 |    -  If this parameter is left blank or is an empty string, IPv4 address is created by default.                              |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0020090596__table11041789:

.. table:: **Table 4** Description of the **bandwidth** field

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================================================================+
   | name            | Yes             | String          | -  Specifies the bandwidth name.                                                                                                                                                                                   |
   |                 |                 |                 | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                             |
   |                 |                 |                 | -  This parameter is mandatory when **share_type** is set to **PER**. This parameter will be ignored when **share_type** is set to **WHOLE** with an ID specified.                                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size            | Yes             | Integer         | -  Specifies the bandwidth size.                                                                                                                                                                                   |
   |                 |                 |                 | -  The value ranges from 1 Mbit/s to 300 Mbit/s by default. (The specific range may vary depending on the configuration in each region. You can see the bandwidth range of each region on the management console.) |
   |                 |                 |                 | -  This parameter is mandatory when **share_type** is set to **PER**. This parameter will be ignored when **share_type** is set to **WHOLE** with an ID specified.                                                 |
   |                 |                 |                 | -  The minimum increment for bandwidth adjustment varies depending on the bandwidth range. The details are as follows:                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                    |
   |                 |                 |                 |    -  The minimum increment is 1 Mbit/s if the allowed bandwidth ranges from 0 Mbit/s to 300 Mbit/s (with 300 Mbit/s included).                                                                                    |
   |                 |                 |                 |    -  The minimum increment is 50 Mbit/s if the allowed bandwidth ranges from 300 Mbit/s to 1000 Mbit/s (with 1000 Mbit/s included).                                                                               |
   |                 |                 |                 |    -  The minimum increment is 500 Mbit/s if the allowed bandwidth is greater than 1000 Mbit/s.                                                                                                                    |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id              | No              | String          | -  Specifies the bandwidth ID. You can specify an existing shared bandwidth when assigning an EIP.                                                                                                                 |
   |                 |                 |                 | -  The value can be the ID of the shared bandwidth whose type is set to **WHOLE**.                                                                                                                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | share_type      | Yes             | String          | -  Specifies the bandwidth type.                                                                                                                                                                                   |
   |                 |                 |                 | -  The value is **PER**, indicating that the bandwidth is dedicated.                                                                                                                                               |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | charge_mode     | No              | String          | -  The value is **traffic**, indicating that the billing is based on traffic.                                                                                                                                      |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request (IPv4 EIP with dedicated bandwidth)

   .. code-block:: text

      POST https://{Endpoint}/v1/{project_id}/publicips

      {
          "publicip": {
              "type": "5_bgp",
              "ip_version": 4
          },
          "bandwidth": {
              "name": "bandwidth123",
              "size": 10,
              "share_type": "PER"
          }
      }

Response Message
----------------

-  Response parameter

   .. table:: **Table 5** Response parameter

      +----------+----------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
      | Name     | Type                                                           | Description                                                                                        |
      +==========+================================================================+====================================================================================================+
      | publicip | :ref:`publicip <en-us_topic_0020090596__table44471219>` object | Specifies the EIP object. For details, see :ref:`Table 6 <en-us_topic_0020090596__table44471219>`. |
      +----------+----------------------------------------------------------------+----------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0020090596__table44471219:

   .. table:: **Table 6** Description of the **publicip** field

      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                        |
      +=======================+=======================+====================================================================+
      | id                    | String                | Specifies the unique identifier of an EIP.                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | status                | String                | -  Specifies the EIP status.                                       |
      |                       |                       | -  Possible values are as follows:                                 |
      |                       |                       |                                                                    |
      |                       |                       |    -  **FREEZED** (Frozen)                                         |
      |                       |                       |    -  **BIND_ERROR** (Binding failed)                              |
      |                       |                       |    -  **BINDING** (Binding)                                        |
      |                       |                       |    -  **PENDING_DELETE** (Releasing)                               |
      |                       |                       |    -  **PENDING_CREATE** (Assigning)                               |
      |                       |                       |    -  **PENDING_UPDATE** (Updating)                                |
      |                       |                       |    -  **NOTIFYING** (Assigning)                                    |
      |                       |                       |    -  **NOTIFY_DELETE** (Release)                                  |
      |                       |                       |    -  **DOWN** (Unbound)                                           |
      |                       |                       |    -  **ACTIVE** (Bound)                                           |
      |                       |                       |    -  **ELB** (Bound to a load balancer)                           |
      |                       |                       |    -  **VPN** (Bound to a VPN)                                     |
      |                       |                       |    -  **ERROR** (Exceptions)                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | type                  | String                | -  Specifies the EIP type.                                         |
      |                       |                       | -  The value can be **5_bgp** and **5_dualStack**.                 |
      |                       |                       | -  Constraints:                                                    |
      |                       |                       |                                                                    |
      |                       |                       |    -  The configured value must be supported by the system.        |
      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | public_ip_address     | String                | Specifies the obtained EIP if only IPv4 EIPs are available.        |
      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | ip_version            | Integer               | Specifies the IP address version. The value can be **4** or **6**. |
      |                       |                       |                                                                    |
      |                       |                       | -  **4**: IPv4                                                     |
      |                       |                       | -  **6**: IPv6 (IPv6 is not supported currently.)                  |
      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | tenant_id             | String                | Specifies the project ID.                                          |
      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | create_time           | String                | Specifies the time (UTC) when the EIP is assigned.                 |
      +-----------------------+-----------------------+--------------------------------------------------------------------+
      | bandwidth_size        | Integer               | Specifies the bandwidth (Mbit/s).                                  |
      +-----------------------+-----------------------+--------------------------------------------------------------------+

-  Example response (IPv4 EIP with dedicated bandwidth)

   .. code-block::

      {
          "publicip": {
              "id": "f588ccfa-8750-4d7c-bf5d-2ede24414706",
              "status": "PENDING_CREATE",
              "type": "5_bgp",
              "public_ip_address": "161.xx.xx.7",
              "tenant_id": "8b7e35ad379141fc9df3e178bd64f55c",
              "ip_version": 4,
              "create_time": "2015-07-16 04:10:52",
              "bandwidth_size": 0,

          }
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
