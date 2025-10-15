:original_name: vpc_vpc_0003.html

.. _vpc_vpc_0003:

Deleting a VPC
==============

Scenarios
---------

This section describes how to delete a VPC.

Notes and Constraints
---------------------

If you want to delete a VPC that has subnets, custom routes, or other resources, you need to delete these resources as prompted on the console first and then delete the VPC.

You can refer to :ref:`Why Can't I Delete My VPCs and Subnets? <vpc_faq_0075>`

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Network** > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. On the **Virtual Private Cloud** page, locate the row that contains the VPC to be deleted and click **Delete** in the **Operation** column.

   A confirmation dialog box is displayed.

#. Confirm the information and click **OK**.

   .. important::

      If a VPC cannot be deleted, a message will be displayed on the console. Delete the resources that are in the VPC by referring to :ref:`Why Can't I Delete My VPCs and Subnets? <vpc_faq_0075>`

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865663509.png
