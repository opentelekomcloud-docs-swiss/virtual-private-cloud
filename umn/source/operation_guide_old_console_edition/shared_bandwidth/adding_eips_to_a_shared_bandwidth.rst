:original_name: vpc_bandwidth02_0003.html

.. _vpc_bandwidth02_0003:

Adding EIPs to a Shared Bandwidth
=================================

Scenarios
---------

Add EIPs to a shared bandwidth and the EIPs can then share that bandwidth. You can add multiple EIPs to a shared bandwidth at the same time.

Notes and Constraints
---------------------

-  After an EIP is added to a shared bandwidth, the original bandwidth used by the EIP will become invalid and the EIP will start to use the shared bandwidth.
-  The EIP's original dedicated bandwidth will be deleted.
-  If it is a standard shared bandwidth, you can add dynamic BGP EIPs and IPv6 NICs to it. If it is a premium shared bandwidth, you can add premium BGP EIPs and IPv6 NICs to it.

Procedure
---------

#. Log in to the management console.

2. Click |image1| in the upper left corner and select the desired region and project.
3. On the console homepage, under , click **Elastic IP**.
4. In the navigation pane on the left, choose **Elastic IP and Bandwidth** > **Shared Bandwidths**.
5. In the shared bandwidth list, locate the row that contains the shared bandwidth that you want to add EIPs to. In the **Operation** column, choose **More** > **Add EIP**, and select the EIPs to be added.
6. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
