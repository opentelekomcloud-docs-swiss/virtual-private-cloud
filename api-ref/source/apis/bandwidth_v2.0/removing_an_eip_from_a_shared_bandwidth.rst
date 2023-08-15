:original_name: vpc_sharebandwidth_0005.html

.. _vpc_sharebandwidth_0005:

Removing an EIP from a Shared Bandwidth
=======================================

Function
--------

This API is used to remove an EIP from a shared bandwidth.

URI
---

POST /v2.0/{project_id}/bandwidths/{bandwidth_id}/remove

:ref:`Table 1 <vpc_sharebandwidth_0005__table25281875>` describes the parameters.

.. _vpc_sharebandwidth_0005__table25281875:

.. table:: **Table 1** Parameter description

   +--------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Name         | Mandatory | Description                                                                                                               |
   +==============+===========+===========================================================================================================================+
   | project_id   | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +--------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | bandwidth_id | Yes       | Specifies the bandwidth ID, which uniquely identifies the bandwidth.                                                      |
   +--------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Message
---------------

-  Request parameter

   .. table:: **Table 2** Request parameter

      +-----------+-----------+------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
      | Name      | Mandatory | Type                                                             | Description                                                                                                |
      +===========+===========+==================================================================+============================================================================================================+
      | bandwidth | Yes       | :ref:`bandwidth <vpc_sharebandwidth_0005__table31854691>` object | Specifies the bandwidth objects. For details, see :ref:`Table 3 <vpc_sharebandwidth_0005__table31854691>`. |
      +-----------+-----------+------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+

   .. _vpc_sharebandwidth_0005__table31854691:

   .. table:: **Table 3** Description of the **bandwidth** field

      +-----------------+-----------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type                                                                           | Description                                                                                                                                                                                                     |
      +=================+=================+================================================================================+=================================================================================================================================================================================================================+
      | publicip_info   | Yes             | Array of :ref:`publicip_info <vpc_sharebandwidth_0005__table30936422>` objects | -  Specifies information about the EIP to be removed from the bandwidth. For details, see :ref:`Table 4 <vpc_sharebandwidth_0005__table30936422>`.                                                              |
      |                 |                 |                                                                                | -  The bandwidth, whose type is **WHOLE**, can be used by multiple EIPs. The number of EIPs varies depending on the tenant quota. By default, a shared bandwidth can be used by up to 20 EIPs.                  |
      +-----------------+-----------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | charge_mode     | Yes             | String                                                                         | After an EIP is removed from a shared bandwidth, a dedicated bandwidth will be allocated to the EIP, and you will be billed for the dedicated bandwidth.                                                        |
      |                 |                 |                                                                                |                                                                                                                                                                                                                 |
      |                 |                 |                                                                                | Specifies whether the dedicated bandwidth used by the EIP that has been removed from a shared bandwidth is billed by traffic or by bandwidth.                                                                   |
      |                 |                 |                                                                                |                                                                                                                                                                                                                 |
      |                 |                 |                                                                                | The value can be **bandwidth** or **traffic**.                                                                                                                                                                  |
      +-----------------+-----------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | size            | Yes             | Integer                                                                        | After an EIP is removed from a shared bandwidth, a dedicated bandwidth will be allocated to the EIP, and you will be billed for the dedicated bandwidth.                                                        |
      |                 |                 |                                                                                |                                                                                                                                                                                                                 |
      |                 |                 |                                                                                | Specifies the size (Mbit/s) of the dedicated bandwidth used by the EIP that has been removed from a shared bandwidth.                                                                                           |
      |                 |                 |                                                                                |                                                                                                                                                                                                                 |
      |                 |                 |                                                                                | The value ranges from 1 Mbit/s to 300 Mbit/s by default. (The specific range may vary depending on the configuration in each region. You can see the bandwidth range of each region on the management console.) |
      +-----------------+-----------------+--------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _vpc_sharebandwidth_0005__table30936422:

   .. table:: **Table 4** **publicip_info** object

      +-------------+-----------+--------+------------------------------------------------------+
      | Name        | Mandatory | Type   | Description                                          |
      +=============+===========+========+======================================================+
      | publicip_id | Yes       | String | Specifies the ID of the EIP that uses the bandwidth. |
      +-------------+-----------+--------+------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{Endpoint}/v2.0/{project_id}/bandwidths/{bandwidth_id}/remove

      {
          "bandwidth": {
              "publicip_info": [
                  {
                      "publicip_id": "d91b0028-6f6b-4478-808a-297b75b6812a"

                  },
                  {
                      "publicip_id": "1d184b2c-4ec9-49b5-a3f9-27600a76ba3f"
                  }
              ],
              "charge_mode": "traffic",
              "size": 22
          }
      }

Response Message
----------------

-  Response parameter

   None

-  Example response

   None

   Or

   .. code-block::

      {
             "code":"xxx",
             "message":"xxxxx"
      }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
