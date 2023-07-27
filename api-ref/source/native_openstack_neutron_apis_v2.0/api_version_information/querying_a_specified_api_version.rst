:original_name: vpc_version_0002.html

.. _vpc_version_0002:

Querying a Specified API Version
================================

Function
--------

This API is used to query the version of a specified API.

URI
---

GET /{api_version}

:ref:`Table 1 <vpc_version_0002__table8488410142319>` describes the parameters.

.. _vpc_version_0002__table8488410142319:

.. table:: **Table 1** Parameter description

   =========== ====== ===================================================
   Parameter   Type   Description
   =========== ====== ===================================================
   api_version String Specifies the version number, for example **v2.0**.
   =========== ====== ===================================================

Request Parameters
------------------

None

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v2.0

Response Parameters
-------------------

.. table:: **Table 2** Response parameter

   +-----------+-------------------------------------------------------------------------+-----------------------------------------+
   | Parameter | Type                                                                    | Description                             |
   +===========+=========================================================================+=========================================+
   | resources | Array of :ref:`resource <vpc_version_0002__table1195920258372>` objects | Specifies the **resource** object list. |
   +-----------+-------------------------------------------------------------------------+-----------------------------------------+

.. _vpc_version_0002__table1195920258372:

.. table:: **Table 3** **resource** object

   +------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | Parameter  | Type                                                                | Description                                                                                      |
   +============+=====================================================================+==================================================================================================+
   | name       | String                                                              | Specifies the resource name.                                                                     |
   +------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | collection | String                                                              | Specifies the resource collection name.                                                          |
   +------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | links      | Array of :ref:`link <vpc_version_0002__table4442151110172>` objects | Specifies the link list. For details, see :ref:`Table 4 <vpc_version_0002__table4442151110172>`. |
   +------------+---------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+

.. _vpc_version_0002__table4442151110172:

.. table:: **Table 4** **link** objects

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
       "resources": [
           {
               "links": [
                   {
                       "href": "https://vpc.systems.com/v2.0/subnets",
                       "rel": "self"
                   }
               ],
               "name": "subnet",
               "collection": "subnets"
           },
           {
               "links": [
                   {
                       "href": "https://vpc.systems.com/v2.0/networks",
                       "rel": "self"
                   }
               ],
               "name": "network",
               "collection": "networks"
           },
           {
               "links": [
                   {
                       "href": "https://vpc.systems.com/v2.0/ports",
                       "rel": "self"
                   }
               ],
               "name": "port",
               "collection": "ports"
           }
       ]
   }

Status Code
-----------

See :ref:`Status Codes <vpc_api_0002>`.

Error Code
----------

See :ref:`Error Codes <vpc_api_0003>`.
