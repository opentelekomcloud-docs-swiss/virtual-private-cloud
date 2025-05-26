:original_name: vpc_sharebandwidth_0002.html

.. _vpc_sharebandwidth_0002:

Assigning Multiple Shared Bandwidths
====================================

Function
--------

This API is used to assign multiple shared bandwidths at a time.

URI
---

POST /v2.0/{project_id}/batch-bandwidths

:ref:`Table 1 <vpc_sharebandwidth_0002__table40002310>` describes the parameters.

.. _vpc_sharebandwidth_0002__table40002310:

.. table:: **Table 1** Parameter description

   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Description                                                                                                               |
   +============+===========+===========================================================================================================================+
   | project_id | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

-  Request parameter

   .. table:: **Table 2** Request parameter

      +-----------+-----------+------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type                                                             | Description                                                                                                |
      +===========+===========+==================================================================+============================================================================================================+
      | bandwidth | Yes       | :ref:`bandwidth <vpc_sharebandwidth_0002__table11041789>` object | Specifies the bandwidth objects. For details, see :ref:`Table 3 <vpc_sharebandwidth_0002__table11041789>`. |
      +-----------+-----------+------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+

   .. _vpc_sharebandwidth_0002__table11041789:

   .. table:: **Table 3** Description of the **bandwidth** field

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                    |
      +=================+=================+=================+================================================================================================================================================================================================================+
      | name            | Yes             | String          | -  Specifies the bandwidth name.                                                                                                                                                                               |
      |                 |                 |                 | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                         |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size            | Yes             | Integer         | -  Specifies the bandwidth size. The shared bandwidth has a minimum limit, which may vary depending on sites. The default minimum value is 5 Mbit/s.                                                           |
      |                 |                 |                 | -  The value ranges from 1 Mbit/s to 2000 Mbit/s by default. (The specific range may vary depending on the configuration in each region. You can see the available bandwidth range on the management console.) |
      |                 |                 |                 | -  The minimum increment for bandwidth adjustment varies depending on the bandwidth range. The details are as follows:                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                |
      |                 |                 |                 |    -  The minimum increment is 1 Mbit/s if the allowed bandwidth ranges from 0 Mbit/s to 300 Mbit/s (with 300 Mbit/s included).                                                                                |
      |                 |                 |                 |    -  The minimum increment is 50 Mbit/s if the allowed bandwidth ranges from 300 Mbit/s to 1000 Mbit/s (with 1000 Mbit/s included).                                                                           |
      |                 |                 |                 |    -  The minimum increment is 500 Mbit/s if the allowed bandwidth is greater than 1000 Mbit/s.                                                                                                                |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | count           | Yes             | Integer         | -  Specifies the number of shared bandwidths that can be assigned at a time.                                                                                                                                   |
      |                 |                 |                 | -  The value is a positive integer.                                                                                                                                                                            |
      |                 |                 |                 | -  If a decimal fraction (for example 2.2) or a character string (for example **"2"**) is specified, the specified value will be automatically converted to an integer.                                        |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{Endpoint}/v2.0/{project_id}/batch-bandwidths

      {
          "bandwidth": {
              "name": "bandwidth123",
              "size": 10,
              "count": 2
          }
      }

Response Message
----------------

-  Response parameter

   .. table:: **Table 4** Response parameter

      +------------+----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
      | Parameter  | Type                                                                             | Description                                                                                                     |
      +============+==================================================================================+=================================================================================================================+
      | bandwidths | Array of :ref:`bandwidths <vpc_sharebandwidth_0002__table5676172817591>` objects | Specifies the bandwidth objects. For details, see :ref:`Table 5 <vpc_sharebandwidth_0002__table5676172817591>`. |
      +------------+----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+

   .. _vpc_sharebandwidth_0002__table5676172817591:

   .. table:: **Table 5** Description of the **bandwidths** field

      +-----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                                                                           | Description                                                                                                                                                                                                    |
      +=======================+================================================================================+================================================================================================================================================================================================================+
      | name                  | String                                                                         | -  Specifies the bandwidth name.                                                                                                                                                                               |
      |                       |                                                                                | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                         |
      +-----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size                  | Integer                                                                        | -  Specifies the bandwidth size.                                                                                                                                                                               |
      |                       |                                                                                | -  The value ranges from 1 Mbit/s to 2000 Mbit/s by default. (The specific range may vary depending on the configuration in each region. You can see the available bandwidth range on the management console.) |
      +-----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id                    | String                                                                         | Specifies the bandwidth ID, which uniquely identifies the bandwidth.                                                                                                                                           |
      +-----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | share_type            | String                                                                         | -  Specifies whether the bandwidth is shared or dedicated.                                                                                                                                                     |
      |                       |                                                                                | -  The value can be **PER** or **WHOLE**.                                                                                                                                                                      |
      |                       |                                                                                |                                                                                                                                                                                                                |
      |                       |                                                                                |    -  **WHOLE**: Shared bandwidth                                                                                                                                                                              |
      |                       |                                                                                |    -  **PER**: Dedicated bandwidth                                                                                                                                                                             |
      +-----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | publicip_info         | Array of :ref:`publicip_info <vpc_sharebandwidth_0002__table30936422>` objects | -  Specifies information about the EIP that uses the bandwidth. For details, see :ref:`Table 6 <vpc_sharebandwidth_0002__table30936422>`.                                                                      |
      |                       |                                                                                | -  The bandwidth, whose type is **WHOLE**, can be used by multiple EIPs. The bandwidth, whose type is **PER**, can be used by only one EIP.                                                                    |
      +-----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tenant_id             | String                                                                         | Specifies the project ID.                                                                                                                                                                                      |
      +-----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | bandwidth_type        | String                                                                         | -  Specifies the bandwidth type. The default value for the shared bandwidth is **share**.                                                                                                                      |
      +-----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | charge_mode           | String                                                                         | -  Specifies whether the bandwidth is billed by traffic or by bandwidth size.                                                                                                                                  |
      |                       |                                                                                | -  Possible values can be **bandwidth** (billed by bandwidth) and **traffic** (billed by traffic). If the value is an empty character string or no value is specified, value **bandwidth** is used.            |
      |                       |                                                                                | -  The shared bandwidth can be billed only by bandwidth.                                                                                                                                                       |
      +-----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | billing_info          | String                                                                         | Specifies the bill information.                                                                                                                                                                                |
      |                       |                                                                                |                                                                                                                                                                                                                |
      |                       |                                                                                | If **billing_info** is specified, the bandwidth is in yearly/monthly billing mode.                                                                                                                             |
      +-----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                                                                         | -  Specifies the bandwidth status.                                                                                                                                                                             |
      |                       |                                                                                | -  Possible values are as follows:                                                                                                                                                                             |
      |                       |                                                                                |                                                                                                                                                                                                                |
      |                       |                                                                                |    -  **FREEZED** (Frozen)                                                                                                                                                                                     |
      |                       |                                                                                |    -  **NORMAL** (Normal)                                                                                                                                                                                      |
      +-----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | public_border_group   | String                                                                         | Specifies whether it is in a central site or an edge site.                                                                                                                                                     |
      |                       |                                                                                |                                                                                                                                                                                                                |
      |                       |                                                                                | Values:                                                                                                                                                                                                        |
      |                       |                                                                                |                                                                                                                                                                                                                |
      |                       |                                                                                | -  **center**                                                                                                                                                                                                  |
      |                       |                                                                                | -  *Edge site name*                                                                                                                                                                                            |
      |                       |                                                                                |                                                                                                                                                                                                                |
      |                       |                                                                                | This resource can only be associated with an EIP of the same region.                                                                                                                                           |
      +-----------------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _vpc_sharebandwidth_0002__table30936422:

   .. table:: **Table 6** **publicip_info** object

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                           |
      +=======================+=======================+=======================================================================================================================+
      | publicip_id           | String                | Specifies the ID of the EIP that uses the bandwidth.                                                                  |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | publicip_address      | String                | Specifies the obtained EIP if only IPv4 EIPs are available.                                                           |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | publicipv6_address    | String                | Specifies the obtained EIP if IPv6 EIPs are available. This parameter does not exist if only IPv4 EIPs are available. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | ip_version            | Integer               | -  Specifies the IP address version.                                                                                  |
      |                       |                       | -  Possible values are as follows:                                                                                    |
      |                       |                       |                                                                                                                       |
      |                       |                       |    -  **4**: IPv4 address                                                                                             |
      |                       |                       |    -  **6**: IPv6 address                                                                                             |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
      | publicip_type         | String                | -  Specifies the EIP type.                                                                                            |
      |                       |                       | -  The value can be **5_bgp** and **5_dualStack**.                                                                    |
      |                       |                       | -  Constraints:                                                                                                       |
      |                       |                       |                                                                                                                       |
      |                       |                       |    -  The configured value must be supported by the system.                                                           |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "bandwidths": [
          {
            "id": "7e5a1a30-6e88-4ce5-b5fa-1d6c6864e084",
            "name": "bandwidth123",
            "size": 10,
            "share_type": "WHOLE",
            "publicip_info": [],
            "tenant_id": "26ae5181a416420998eb2093aaed84d9",
            "bandwidth_type": "share",
            "charge_mode": "bandwidth",
            "billing_info": "",
            "status": "NORMAL"
          },
          {
            "id": "ed2da50a-3ce9-4d86-9f17-e8f3801299a5",
            "name": "bandwidth123",
            "size": 10,
            "share_type": "WHOLE",
            "publicip_info": [],
            "tenant_id": "26ae5181a416420998eb2093aaed84d9",
            "bandwidth_type": "share",
            "charge_mode": "bandwidth",
            "billing_info": "",
            "status": "NORMAL"
          }
        ]
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
