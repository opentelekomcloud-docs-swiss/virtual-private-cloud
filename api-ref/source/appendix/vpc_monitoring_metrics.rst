:original_name: vpc_api_0010.html

.. _vpc_api_0010:

VPC Monitoring Metrics
======================

Description
-----------

This section describes monitoring metrics reported by VPC to Cloud Eye as well as their namespaces and dimensions. You can use APIs provided by Cloud Eye to query the monitoring metrics of the monitored object and alarms generated for VPC.

Namespace
---------

SYS.VPC

Metrics
-------

.. table:: **Table 1** EIP and bandwidth metrics

   +----------------------+--------------------+-------------------------------------------------------------+-------------+-------+-----------------+------------------------------+--------------------------------+
   | ID                   | Name               | Description                                                 | Value Range | Unit  | Conversion Rule | Monitored Object (Dimension) | Monitoring Interval (Raw Data) |
   +======================+====================+=============================================================+=============+=======+=================+==============================+================================+
   | upstream_bandwidth   | Outbound Bandwidth | Network rate of outbound traffic                            | >= 0        | bit/s | 1000 (SI)       | Bandwidth or EIP             | 1 minute                       |
   +----------------------+--------------------+-------------------------------------------------------------+-------------+-------+-----------------+------------------------------+--------------------------------+
   | downstream_bandwidth | Inbound Bandwidth  | Network rate of inbound traffic                             | >= 0        | bit/s | 1000 (SI)       | Bandwidth or EIP             | 1 minute                       |
   +----------------------+--------------------+-------------------------------------------------------------+-------------+-------+-----------------+------------------------------+--------------------------------+
   | up_stream            | Outbound Traffic   | Network traffic going out of the cloud platform in a minute | >= 0        | Byte  | 1000 (SI)       | Bandwidth or EIP             | 1 minute                       |
   +----------------------+--------------------+-------------------------------------------------------------+-------------+-------+-----------------+------------------------------+--------------------------------+
   | down_stream          | Inbound Traffic    | Network traffic going into the cloud platform in a minute   | >= 0        | Byte  | 1000 (SI)       | Bandwidth or EIP             | 1 minute                       |
   +----------------------+--------------------+-------------------------------------------------------------+-------------+-------+-----------------+------------------------------+--------------------------------+

Dimension
---------

============ ============
Key          Value
============ ============
publicip_id  EIP ID
bandwidth_id Bandwidth ID
============ ============
