:original_name: vpc_faq_0059.html

.. _vpc_faq_0059:

How Do I Configure a Security Group for Multi-Channel Protocols?
================================================================

ECS Configuration
-----------------

The TFTP daemon determines whether a configuration file specifies the port range. If you use a TFTP configuration file that allows the data channel ports to be configurable, it is a good practice to configure a small range of ports that are not listened on.

Security Group Configuration
----------------------------

You can configure port 69 and configure data channel ports used by TFTP for the security group. In RFC1350, the TFTP protocol specifies that ports available to data channels range from 0 to 65535. However, not all these ports are used by the TFTP daemon processes of different applications. You can configure a smaller range of ports for the TFTP daemon.

The following figure provides an example of the security group rule configuration if the ports used by data channels range from 60001 to 60100.


.. figure:: /_static/images/en-us_image_0129473334.png
   :alt: **Figure 1** Security group rules

   **Figure 1** Security group rules
