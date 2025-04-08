:original_name: vpc_vip_0002.html

.. _vpc_vip_0002:

Assigning a Virtual IP Address
==============================

Scenarios
---------

If an ECS requires a virtual IP address or if a virtual IP address needs to be reserved, you can assign a virtual IP address from the subnet.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. On the **Virtual Private Cloud** page, locate the VPC containing the subnet where a virtual IP address is to be assigned, and click the VPC name.

#. On the **Subnets** tab, click the name of the subnet where a virtual IP address is to be assigned.

#. Click the **Virtual IP Addresses** tab and click **Assign Virtual IP Address**.

#. Select a virtual IP address assignment mode.

   -  **Automatic**: The system assigns an IP address automatically.
   -  **Manual**: You can specify an IP address.

#. Select **Manual** and enter a virtual IP address.

#. Click **OK**.

You can then query the assigned virtual IP address in the IP address list.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001865663157.png
