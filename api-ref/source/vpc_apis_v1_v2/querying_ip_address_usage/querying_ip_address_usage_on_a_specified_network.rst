:original_name: vpc_natworkip_0001.html

.. _vpc_natworkip_0001:

Querying IP Address Usage on a Specified Network
================================================

Function
--------

This API is used to query the IP address usage on a specified network.

The obtained information includes the total number of IP addresses on the network, the number of in-use IP addresses on the network, the total number of IP addresses on each subnet, and the number of in-use IP addresses on the subnet.

.. important::

   -  The first and the last two IP addresses on each subnet are reserved by the system for the gateway and DHCP service.
   -  The total number of IP addresses and the number of in-use IP addresses described in this section and the subsequent sections do not include the IP addresses reserved by the system.
   -  When assigning an IP address, you can specify the reserved IP address for the system. The reserved IP addresses will not be included in the number of in-use IP addresses and the total number of IP addresses no matter how the IP address is assigned.

URI
---

GET /v2.0/network-ip-availabilities/{network_id}

:ref:`Table 1 <vpc_natworkip_0001__table38148684>` describes the parameters.

.. _vpc_natworkip_0001__table38148684:

.. table:: **Table 1** Parameter description

   ========== ====== ========= =========================
   Parameter  Type   Mandatory Description
   ========== ====== ========= =========================
   network_id String Yes       Specifies the network ID.
   ========== ====== ========= =========================

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v2.0/network-ip-availabilities/6b50d967-779c-40c9-a157-de1df3c17043

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-------------------------+--------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Type                                                                           | Description                                                                                                                  |
   +=========================+================================================================================+==============================================================================================================================+
   | network_ip_availability | :ref:`network_ip_availability <vpc_natworkip_0001__table4952133061113>` object | Specifies the **network_ip_availability** objects. For details, see :ref:`Table 3 <vpc_natworkip_0001__table4952133061113>`. |
   +-------------------------+--------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_natworkip_0001__table4952133061113:

.. table:: **Table 3** **network_ip_availability** objects

   +------------------------+----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type                                                                                   | Description                                                                                                             |
   +========================+========================================================================================+=========================================================================================================================+
   | network_id             | String                                                                                 | Specifies the network ID.                                                                                               |
   +------------------------+----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | network_name           | String                                                                                 | Specifies the network name.                                                                                             |
   +------------------------+----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | tenant_id              | String                                                                                 | Specifies the project ID.                                                                                               |
   +------------------------+----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | total_ips              | Integer                                                                                | Specifies the total number of IP addresses on a network. (System reserved IP addresses are not included.)               |
   +------------------------+----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | used_ips               | Integer                                                                                | Specifies the number of in-use IP addresses on a network. (Reserved IP addresses are not included.)                     |
   +------------------------+----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | subnet_ip_availability | Array of :ref:`subnet_ip_availability <vpc_natworkip_0001__table110015141519>` objects | Specifies the subnet IP address usage objects. For details, see :ref:`Table 4 <vpc_natworkip_0001__table110015141519>`. |
   +------------------------+----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+

.. _vpc_natworkip_0001__table110015141519:

.. table:: **Table 4** Description of the **subnet_ip_availability** field

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                               |
   +=======================+=======================+===========================================================================================================+
   | used_ips              | Integer               | Specifies the number of in-use IP addresses on a subnet. (System reserved IP addresses are not included.) |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | subnet_id             | String                | Specifies the subnet ID.                                                                                  |
   |                       |                       |                                                                                                           |
   |                       |                       | If you use the management console, the value of this parameter is the **Network ID** value.               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | subnet_name           | String                | Specifies the subnet name.                                                                                |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | ip_version            | Integer               | Specifies the IP version of the subnet. Only IPv4 is supported.                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | cidr                  | String                | Specifies the subnet CIDR block.                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | total_ips             | Integer               | Specifies the total number of IP addresses on a subnet. (System reserved IP addresses are not included.)  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
     "network_ip_availability": {
       "used_ips": 4,
       "subnet_ip_availability": [
         {
           "used_ips": 4,
           "subnet_id": "98e343d1-3cb8-4f69-9cd1-00569819480f",
           "subnet_name": "",
           "ip_version": 4,
           "cidr": "10.0.0.0/8",
           "total_ips": 300
         }
       ],
       "network_id": "6b50d967-779c-40c9-a157-de1df3c17043",
       "tenant_id": "7c4b23cb125d481c95cbe4f91b2c11cd",
       "total_ips": 300,
       "network_name": "pch_test_003"
     }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
