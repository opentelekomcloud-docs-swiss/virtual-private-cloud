:original_name: vpc_vip02_0002.html

.. _vpc_vip02_0002:

Assigning a Virtual IP Address
==============================

Scenarios
---------

If an ECS requires a virtual IP address or if a virtual IP address needs to be reserved, you can assign a virtual IP address from the subnet.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. On the console homepage, under , click **Virtual Private Cloud**.

4.  In the navigation pane on the left, click **Virtual Private Cloud**.
5.  On the **Virtual Private Cloud** page, locate the VPC containing the subnet where a virtual IP address is to be assigned, and click the VPC name.
6.  On the **Subnets** tab, click the name of the subnet where a virtual IP address is to be assigned.
7.  Click the **Virtual IP Addresses** tab and click **Assign Virtual IP Address**.
8.  Select a virtual IP address assignment mode.

    -  **Automatic**: The system assigns an IP address automatically.
    -  **Manual**: You can specify an IP address.

9.  Select **Manual** and enter a virtual IP address.
10. Click **OK**.

You can then query the assigned virtual IP address in the IP address list.

.. |image1| image:: /_static/images/en-us_image_0226223279.png
