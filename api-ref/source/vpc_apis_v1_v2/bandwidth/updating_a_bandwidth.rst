:original_name: vpc_bandwidth_0003.html

.. _vpc_bandwidth_0003:

Updating a Bandwidth
====================

Function
--------

This API is used to update information about a bandwidth.

URI
---

PUT /v1/{project_id}/bandwidths/{bandwidth_id}

:ref:`Table 1 <vpc_bandwidth_0003__table25281875>` describes the parameters.

.. _vpc_bandwidth_0003__table25281875:

.. table:: **Table 1** Parameter description

   +--------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Description                                                                                                               |
   +==============+===========+===========================================================================================================================+
   | project_id   | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +--------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | bandwidth_id | Yes       | Specifies the bandwidth ID, which uniquely identifies the bandwidth.                                                      |
   +--------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

-  Request parameter

   .. table:: **Table 2** Request parameter

      +-----------+-----------+-------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type                                                        | Description                                                                                           |
      +===========+===========+=============================================================+=======================================================================================================+
      | bandwidth | Yes       | :ref:`bandwidth <vpc_bandwidth_0003__table31854691>` object | Specifies the bandwidth objects. For details, see :ref:`Table 3 <vpc_bandwidth_0003__table31854691>`. |
      +-----------+-----------+-------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

   .. _vpc_bandwidth_0003__table31854691:

   .. table:: **Table 3** Description of the **bandwidth** field

      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                        |
      +=================+=================+=================+====================================================================================================================================================================================================================================================================================+
      | name            | No              | String          | -  Specifies the bandwidth name.                                                                                                                                                                                                                                                   |
      |                 |                 |                 | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.). If the value is left blank, the name of the bandwidth is not changed.                                                                                       |
      |                 |                 |                 | -  Either parameter **name** or **size** must be specified.                                                                                                                                                                                                                        |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size            | No              | Integer         | -  Specifies the bandwidth size in Mbit/s.                                                                                                                                                                                                                                         |
      |                 |                 |                 | -  The value ranges from 1 Mbit/s to 300 Mbit/s by default. (The specific range may vary depending on the configuration in each region. You can see the available bandwidth range on the management console.) If the parameter is not included, the bandwidth size is not changed. |
      |                 |                 |                 | -  Either parameter **name** or **size** must be specified.                                                                                                                                                                                                                        |
      |                 |                 |                 | -  If a decimal fraction (for example **10.2**) or a character string (for example **"10"**) is specified, the specified value will be automatically converted to an integer.                                                                                                      |
      |                 |                 |                 | -  The minimum increment for bandwidth adjustment varies depending on the bandwidth range. The details are as follows:                                                                                                                                                             |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                    |
      |                 |                 |                 |    -  The minimum increment is 1 Mbit/s if the allowed bandwidth ranges from 0 Mbit/s to 300 Mbit/s (with 300 Mbit/s included).                                                                                                                                                    |
      |                 |                 |                 |    -  The minimum increment is 50 Mbit/s if the allowed bandwidth ranges from 300 Mbit/s to 1000 Mbit/s (with 1000 Mbit/s included).                                                                                                                                               |
      |                 |                 |                 |    -  The minimum increment is 500 Mbit/s if the allowed bandwidth is greater than 1000 Mbit/s.                                                                                                                                                                                    |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      PUT https://{Endpoint}/v1/{project_id}/bandwidths/{bandwidth_id}

      {
          "bandwidth":
              {"name": "bandwidth123",
               "size": 10
              }
      }

Response Message
----------------

-  Response parameter

   .. table:: **Table 4** Response parameter

      +-----------+-------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
      | Parameter | Type                                                        | Description                                                                                           |
      +===========+=============================================================+=======================================================================================================+
      | bandwidth | :ref:`bandwidth <vpc_bandwidth_0003__table17227723>` object | Specifies the bandwidth objects. For details, see :ref:`Table 5 <vpc_bandwidth_0003__table17227723>`. |
      +-----------+-------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

   .. _vpc_bandwidth_0003__table17227723:

   .. table:: **Table 5** Description of the **bandwidth** field

      +-----------------------+---------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                                                                      | Description                                                                                                                                                                                                        |
      +=======================+===========================================================================+====================================================================================================================================================================================================================+
      | name                  | String                                                                    | -  Specifies the bandwidth name.                                                                                                                                                                                   |
      |                       |                                                                           | -  The value can contain 1 to 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                                                             |
      +-----------------------+---------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size                  | Integer                                                                   | -  Specifies the bandwidth size in Mbit/s.                                                                                                                                                                         |
      |                       |                                                                           | -  The value ranges from 1 Mbit/s to 300 Mbit/s by default. (The specific range may vary depending on the configuration in each region. You can see the bandwidth range of each region on the management console.) |
      +-----------------------+---------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id                    | String                                                                    | Specifies the bandwidth ID, which uniquely identifies the bandwidth.                                                                                                                                               |
      +-----------------------+---------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | share_type            | String                                                                    | -  The value is **PER**, indicating that the bandwidth is dedicated.                                                                                                                                               |
      +-----------------------+---------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | publicip_info         | Array of :ref:`publicip_info <vpc_bandwidth_0003__table30936422>` objects | -  Specifies the information about the EIP that uses the bandwidth. For details, see :ref:`Table 6 <vpc_bandwidth_0003__table30936422>`.                                                                           |
      +-----------------------+---------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tenant_id             | String                                                                    | Specifies the project ID.                                                                                                                                                                                          |
      +-----------------------+---------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | bandwidth_type        | String                                                                    | -  Specifies the bandwidth type.                                                                                                                                                                                   |
      |                       |                                                                           | -  The value is **bgp**.                                                                                                                                                                                           |
      +-----------------------+---------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | charge_mode           | String                                                                    | -  Specifies whether the bandwidth is billed by traffic or by bandwidth size.                                                                                                                                      |
      |                       |                                                                           | -  Possible values can be **bandwidth** (billed by bandwidth) and **traffic** (billed by traffic). If the value is an empty character string or no value is specified, value **bandwidth** is used.                |
      +-----------------------+---------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | billing_info          | String                                                                    | Specifies the bill information.                                                                                                                                                                                    |
      |                       |                                                                           |                                                                                                                                                                                                                    |
      |                       |                                                                           | If **billing_info** is specified, the bandwidth is in yearly/monthly billing mode.                                                                                                                                 |
      +-----------------------+---------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | created_at            | String                                                                    | -  Specifies the time (UTC) when the bandwidth is created.                                                                                                                                                         |
      |                       |                                                                           | -  Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                                                   |
      +-----------------------+---------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | updated_at            | String                                                                    | -  Specifies the time (UTC) when the bandwidth is updated.                                                                                                                                                         |
      |                       |                                                                           | -  Format: *yyyy-MM-ddTHH:mm:ss*                                                                                                                                                                                   |
      +-----------------------+---------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | public_border_group   | String                                                                    | Specifies whether it is in a central site or an edge site.                                                                                                                                                         |
      |                       |                                                                           |                                                                                                                                                                                                                    |
      |                       |                                                                           | The value can be:                                                                                                                                                                                                  |
      |                       |                                                                           |                                                                                                                                                                                                                    |
      |                       |                                                                           | -  center                                                                                                                                                                                                          |
      |                       |                                                                           | -  *Edge site name*                                                                                                                                                                                                |
      |                       |                                                                           |                                                                                                                                                                                                                    |
      |                       |                                                                           | An EIP can only be bound to a resource of the same region.                                                                                                                                                         |
      +-----------------------+---------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _vpc_bandwidth_0003__table30936422:

   .. table:: **Table 6** **publicip_info** objects

      +-----------------------+-----------------------+-------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                 |
      +=======================+=======================+=============================================================+
      | publicip_id           | String                | Specifies the ID of the EIP that uses the bandwidth.        |
      +-----------------------+-----------------------+-------------------------------------------------------------+
      | publicip_address      | String                | Specifies the obtained EIP if only IPv4 EIPs are available. |
      +-----------------------+-----------------------+-------------------------------------------------------------+
      | publicip_type         | String                | -  Specifies the EIP type.                                  |
      |                       |                       | -  The value can be **5_bgp** and **5_dualStack**.          |
      |                       |                       | -  Constraints:                                             |
      |                       |                       |                                                             |
      |                       |                       |    -  The configured value must be supported by the system. |
      +-----------------------+-----------------------+-------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "bandwidth": {
              "id": "3fa5b383-5a73-4dcb-a314-c6128546d855",
              "name": "bandwidth123",
              "size": 10,
              "share_type": "PER",
              "public_border_group": "center",
              "created_at": "2024-04-27T00:14:36Z",
              "updated_at": "2024-04-27T00:14:36Z",
              "publicip_info": [
                  {
                      "publicip_id": "6285e7be-fd9f-497c-bc2d-dd0bdea6efe0",
                      "publicip_address": "161.xx.xx.9",
                      "publicip_type": "5_bgp",
                      "ip_version": 4
                  }
              ],
              "tenant_id": "8b7e35ad379141fc9df3e178bd64f55c",
              "bandwidth_type": "bgp",
              "charge_mode": "bandwidth",
              "status": "NORMAL"
          }
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
