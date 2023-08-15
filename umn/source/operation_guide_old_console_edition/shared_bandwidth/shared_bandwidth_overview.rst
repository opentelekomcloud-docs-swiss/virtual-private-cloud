:original_name: vpc_bandwidth02_0001.html

.. _vpc_bandwidth02_0001:

Shared Bandwidth Overview
=========================

A shared bandwidth can be shared by multiple EIPs and controls the data transfer rate on these EIPs in a centralized manner. All ECSs, BMSs, and load balancers that have EIPs bound in the same region can share a bandwidth.

When you host a large number of applications on the cloud, if each EIP uses a bandwidth, a lot of bandwidths are required, increasing O&M workload. If all EIPs share the same bandwidth, VPCs and the region-level bandwidth can be managed in a unified manner, simplifying O&M statistics and network operations cost settlement.

-  Easy to Manage

   Region-level bandwidth sharing and multiplexing simplify O&M statistics, management, and operations cost settlement.

-  Flexible Operations

   You can add EIPs (except for **5_gray** EIPs of dedicated load balancers) to or remove them from a shared bandwidth regardless of the type of instances that they are bound to.
