:original_name: en-us_topic_0030969462.html

.. _en-us_topic_0030969462:

Modifying a VPC
===============

Scenarios
---------

Change the VPC name and CIDR block.

If the VPC CIDR block conflicts with the CIDR block of a VPN created in the VPC, you can modify its CIDR block.

Notes and Constraints
---------------------

-  When modifying the VPC CIDR block:

   -  The VPC CIDR block to be modified must be in the supported CIDR blocks: 10.0.0.0 - 10.255.255.255, 172.16.0.0 - 172.31.255.255, and 192.168.0.0 - 192.168.255.255
   -  If the VPC has subnets, the VPC CIDR block to be modified must contain all subnet CIDR blocks.

When modifying the VPC CIDR block:

-  The VPC CIDR block to be modified must be in the supported CIDR blocks: 10.0.0.0 - 10.255.255.255, 172.16.0.0 - 172.31.255.255, and 192.168.0.0 - 192.168.255.255
-  If the VPC has subnets, the VPC CIDR block to be modified must contain all subnet CIDR blocks.

Procedure
---------

**Modifying the VPC CIDR Block**

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. On the console homepage, under , click **Virtual Private Cloud**.
#. In the navigation pane on the left, click **Virtual Private Cloud**.
#. On the **Virtual Private Cloud** page, locate the row that contains the VPC to be modified and click **Edit CIDR Block** in the **Operation** column.
#. Set a new CIDR block.
#. Click **OK**.

**Modifying a VPC**

#. Log in to the management console.
#. Click |image2| in the upper left corner and select the desired region and project.
#. On the console homepage, under , click **Virtual Private Cloud**.
#. In the navigation pane on the left, click **Virtual Private Cloud**.
#. Modify the basic information about a VPC using either of the following methods:

   -  In the VPC list, click |image3| on the right of the VPC name to change the VPC name.

   -  In the VPC list, click the VPC name.

      On the VPC details page, click |image4| next to the VPC name or description to change the VPC name or description.


      .. figure:: /_static/images/en-us_image_0000001223070074.png
         :alt: **Figure 1** Modifying VPC basic information

         **Figure 1** Modifying VPC basic information

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0141273034.png
.. |image3| image:: /_static/images/en-us_image_0000001267230305.png
.. |image4| image:: /_static/images/en-us_image_0000001267350317.png
