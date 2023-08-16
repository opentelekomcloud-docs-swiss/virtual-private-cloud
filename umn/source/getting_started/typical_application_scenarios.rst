:original_name: vpc_qs_0002.html

.. _vpc_qs_0002:

Typical Application Scenarios
=============================

A VPC provides an isolated virtual network for ECSs. You can configure and manage the network as required.

-  If your ECSs, for example, ECSs that function as databases, do not need to access the Internet or need to access the Internet using specific IP addresses with limited bandwidth, you can configure a VPC for the ECSs by following the instructions described in :ref:`Configuring a VPC for ECSs That Do Not Require Internet Access <vpc_qs_0003>`.
-  If your ECSs, for example, ECSs where websites are deployed, need to communicate with the Internet, you can bind EIPs to them. To configure a VPC for these ECSs, follow the instructions provided in :ref:`Configuring a VPC for ECSs That Access the Internet Using EIPs <en-us_topic_0017816228>`.

.. note::

   Click |image1| in the lower right corner of the console to switch between the new and the old consoles. The old edition does not have the function of associating a subnet with a route table.

   This document provides two sets of operation guides. The "Getting Started" chapter uses the new console edition as an example.

   -  If you use the new console edition, see :ref:`Operation Guide (New Console Edition) <vpc_newui_0000>`.
   -  If you use the old console edition, see :ref:`Operation Guide (Old Console Edition) <vpc_oldui_0000>`.

.. |image1| image:: /_static/images/en-us_image_0000001207253746.png
