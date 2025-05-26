:original_name: vpc_apieg_0001.html

.. _vpc_apieg_0001:

Creating a VPC
==============

Scenarios
---------

This section describes how to call the VPC creation API to create a VPC. For details about the parameters for creating a VPC and the response message, see section :ref:`Creating a VPC <vpc_api01_0001>`.

Prerequisites
-------------

You have planned the region where you want to create the VPC and obtained the endpoint required for API calls. For details, see :ref:`Endpoints <vpc_api00_0002>`.

To use token authentication, you need to obtain a token and add **X-Auth-Token** to the request headers. Obtain the token by performing the steps provided in section :ref:`Authentication <vpc_api00_0010>`.

.. note::

   The token obtained from IAM is valid for only 24 hours. If you want to use one token for authentication, you can cache it to avoid frequently obtaining the token.

**Procedure**
-------------

#. Send **POST https://VPC endpoint/v1/{project_id}/vpcs**. Parameter **project_id** indicates the project ID.

#. Add **X-Auth-Token** to the request header.

#. Specify the following parameters in the request body:

   .. code-block::

      {
          "vpc": {
              "name": "vpc", //VPC name
              "cidr": "192.168.0.0/16" //Available subnet IP address ranges in the VPC
          }
      }

#. Check the response message.

   -  The request is successful if the following response is displayed. In the response, **id** indicates the VPC ID.

      .. code-block::

         {
             "vpc": {
                 "id": "b6684a27-b049-407d-90b4-c9551f2390e1",
                 "name": "vpc",
                 "cidr": "192.168.0.0/16",
                 "status": "CREATING",
         "routes": [].
             }
         }

   -  For details about the error codes displayed if the request fails, see section :ref:`Error Codes <vpc_api_0003>`.

#. Query the VPC details as well as update or delete the VPC based on the **vpc_id** and **project_id** values.
