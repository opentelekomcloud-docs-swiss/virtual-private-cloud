:original_name: vpc_vpc_0002.html

.. _vpc_vpc_0002:

Deleting a Subnet
=================

Scenarios
---------

This section describes how to delete a subnet.

Notes and Constraints
---------------------

If you want to delete a subnet that has custom routes, virtual IP addresses, or other resources, you need to delete these resources as prompted on the console first and then delete the subnet.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. On the console homepage, under , click **Virtual Private Cloud**.

#. In the navigation pane on the left, click **Subnets**.

#. In the subnet list, locate the row that contains the subnet you want to delete and click **Delete** in the **Operation** column.

   A confirmation dialog box is displayed.

#. Click **Yes**.

   .. important::

      If a VPC cannot be deleted, a message will be displayed on the console. Delete the resources that are in the VPC by referring to :ref:`Why Can't I Delete My VPCs and Subnets? <vpc_faq_0075>`

.. |image1| image:: /_static/images/en-us_image_0141273034.png
