:original_name: vpc_api01_0001.html

.. _vpc_api01_0001:

Creating a VPC
==============

Function
--------

This API is used to create a VPC.

URI
---

POST /v1/{project_id}/vpcs

:ref:`Table 1 <vpc_api01_0001__table3672032>` describes the parameters.

.. _vpc_api01_0001__table3672032:

.. table:: **Table 1** Parameter description

   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+
   | Name       | Mandatory | Description                                                                                                               |
   +============+===========+===========================================================================================================================+
   | project_id | Yes       | Specifies the project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <vpc_api_0011>`. |
   +------------+-----------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request parameter

   +------+-----------+---------------------------------------------------+-------------------------------------------------------------------+
   | Name | Mandatory | Type                                              | Description                                                       |
   +======+===========+===================================================+===================================================================+
   | vpc  | Yes       | :ref:`vpc <vpc_api01_0001__table33750194>` object | :ref:`Specifies the VPC objects. <vpc_api01_0001__table33750194>` |
   +------+-----------+---------------------------------------------------+-------------------------------------------------------------------+

.. _vpc_api01_0001__table33750194:

.. table:: **Table 3** VPC objects

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Name            | Mandatory       | Type            | Description                                                                                                                    |
   +=================+=================+=================+================================================================================================================================+
   | name            | No              | String          | -  Specifies the VPC name.                                                                                                     |
   |                 |                 |                 | -  The value can contain no more than 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.). |
   |                 |                 |                 | -  Each VPC name of a tenant must be unique if the VPC name is not left blank.                                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | -  Provides supplementary information about the VPC.                                                                           |
   |                 |                 |                 | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                               |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
   | cidr            | No              | String          | -  Specifies the available IP address ranges for subnets in the VPC.                                                           |
   |                 |                 |                 | -  Possible values are as follows:                                                                                             |
   |                 |                 |                 |                                                                                                                                |
   |                 |                 |                 |    -  10.0.0.0/8-24                                                                                                            |
   |                 |                 |                 |    -  172.16.0.0/12-24                                                                                                         |
   |                 |                 |                 |    -  192.168.0.0/16-24                                                                                                        |
   |                 |                 |                 |                                                                                                                                |
   |                 |                 |                 | -  If **cidr** is not specified, the default value is left blank.                                                              |
   |                 |                 |                 | -  The value must be in CIDR format, for example, **192.168.0.0/16**.                                                          |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

-  Create a VPC named **vpc** and set its CIDR block to 192.168.0.0/16.

   .. code-block:: text

      POST https://{Endpoint}/v1/{project_id}/vpcs

      {
          "vpc": {
              "name": "vpc",
              "description": "test",
              "cidr": "192.168.0.0/16"
          }
      }

Response Parameters
-------------------

.. table:: **Table 4** Response parameter

   +------+---------------------------------------------------+-------------------------------------------------------------------+
   | Name | Type                                              | Description                                                       |
   +======+===================================================+===================================================================+
   | vpc  | :ref:`vpc <vpc_api01_0001__table39714111>` object | :ref:`Specifies the VPC objects. <vpc_api01_0001__table39714111>` |
   +------+---------------------------------------------------+-------------------------------------------------------------------+

.. _vpc_api01_0001__table39714111:

.. table:: **Table 5** VPC objects

   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Type                                                               | Description                                                                                                                                                                           |
   +=======================+====================================================================+=======================================================================================================================================================================================+
   | id                    | String                                                             | Specifies a resource ID in UUID format.                                                                                                                                               |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                             | -  Specifies the VPC name.                                                                                                                                                            |
   |                       |                                                                    | -  The value can contain no more than 64 characters, including letters, digits, underscores (_), hyphens (-), and periods (.).                                                        |
   |                       |                                                                    | -  Each VPC name of a tenant must be unique if the VPC name is not left blank.                                                                                                        |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                             | -  Provides supplementary information about the VPC.                                                                                                                                  |
   |                       |                                                                    | -  The value can contain no more than 255 characters and cannot contain angle brackets (< or >).                                                                                      |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cidr                  | String                                                             | -  Specifies the available IP address ranges for subnets in the VPC.                                                                                                                  |
   |                       |                                                                    | -  Possible values are as follows:                                                                                                                                                    |
   |                       |                                                                    |                                                                                                                                                                                       |
   |                       |                                                                    |    -  10.0.0.0/8-24                                                                                                                                                                   |
   |                       |                                                                    |    -  172.16.0.0/12-24                                                                                                                                                                |
   |                       |                                                                    |    -  192.168.0.0/16-24                                                                                                                                                               |
   |                       |                                                                    |                                                                                                                                                                                       |
   |                       |                                                                    | -  If **cidr** is not specified, the default value is left blank.                                                                                                                     |
   |                       |                                                                    | -  The value must be in CIDR format, for example, **192.168.0.0/16**.                                                                                                                 |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                             | -  Specifies the VPC status.                                                                                                                                                          |
   |                       |                                                                    | -  Possible values are as follows:                                                                                                                                                    |
   |                       |                                                                    |                                                                                                                                                                                       |
   |                       |                                                                    |    -  **CREATING**: The VPC is being created.                                                                                                                                         |
   |                       |                                                                    |    -  **OK**: The VPC is created successfully.                                                                                                                                        |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | routes                | Array of :ref:`route <vpc_api01_0001__table3576833291556>` objects | -  Specifies the route information.                                                                                                                                                   |
   |                       |                                                                    | -  For details, see the description of the :ref:`route objects <vpc_api01_0001__table3576833291556>`.                                                                                 |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enable_shared_snat    | Boolean                                                            | Specifies whether the shared SNAT function is enabled. The value **true** indicates that the function is enabled, and the value **false** indicates that the function is not enabled. |
   +-----------------------+--------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _vpc_api01_0001__table3576833291556:

.. table:: **Table 6** **route** objects

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Type                  | Description                                                                                                              |
   +=======================+=======================+==========================================================================================================================+
   | destination           | String                | -  Specifies the destination network segment of a route.                                                                 |
   |                       |                       | -  The value must be in the CIDR format. Currently, only the value **0.0.0.0/0** is supported.                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
   | nexthop               | String                | -  Specifies the next hop of a route.                                                                                    |
   |                       |                       | -  The value must be an IP address and must belong to the subnet in the VPC. Otherwise, this value does not take effect. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
    "vpc":
        {
        "id": "99d9d709-8478-4b46-9f3f-2206b1023fd3",
        "name": "vpc",
        "description": "test",
        "cidr": "192.168.0.0/16",
        "status": "CREATING",
        "routes": []
        }
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
