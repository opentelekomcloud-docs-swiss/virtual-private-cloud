:original_name: vpc_qs_0002.html

.. _vpc_qs_0002:

Typical Application Scenarios
=============================

A VPC provides an isolated virtual network for ECSs. You can configure and manage the network as required.

-  If any of your ECSs, for example, ECSs that function as the database of server nodes for website deployment, do not need to access the Internet or need to access the Internet specific IP addresses on the default network with limited bandwidth, you can configure a VPC for the ECSs by following the instructions described in :ref:`Configuring a VPC for ECSs That Do Not Require Internet Access <vpc_qs_0003>`.
-  If your ECSs need to access the Internet, you can configure EIPs for them. For example, the ECSs functioning as the service nodes for deploying a website need to be accessed by users over the Internet. Then, you can configure a VPC for these ECSs by following the instructions provided in :ref:`Configuring a VPC for ECSs That Access the Internet Using EIPs <en-us_topic_0017816228>`.
-  When you need to access the IPv6 services on the Internet or provide services accessible from users using an IPv6 client, you need to enable the IPv6 function. After the IPv6 function is enabled, you can provide services for users using an IPv4 or IPv6 client.
