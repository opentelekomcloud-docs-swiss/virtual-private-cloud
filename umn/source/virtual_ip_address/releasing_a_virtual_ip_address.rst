:original_name: vpc_vip_0009.html

.. _vpc_vip_0009:

Releasing a Virtual IP Address
==============================

Scenarios
---------

If you no longer need a virtual IP address or a reserved virtual IP address, you can release it to avoid wasting resources.

Notes and Constraints
---------------------

If you want to release a virtual IP address that is being used by a resource, refer to :ref:`Table 1 <vpc_vip_0009__table85161971410>`.

.. _vpc_vip_0009__table85161971410:

.. table:: **Table 1** Releasing a virtual IP address that is being used by a resource

   +-----------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Prompts                                                                                                                           | Cause Analysis and Solution                                                                                                         |
   +===================================================================================================================================+=====================================================================================================================================+
   | This operation cannot be performed because the IP address is bound to an instance or an EIP. Unbind the IP address and try again. | This virtual IP address is being used by an EIP or an ECS.                                                                          |
   |                                                                                                                                   |                                                                                                                                     |
   |                                                                                                                                   | Release the virtual IP address.                                                                                                     |
   +-----------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | This operation cannot be performed because the IP address is being used by a system component.                                    | The virtual IP address is being used by an RDS DB instance. Delete the DB instance, which will also release its virtual IP address. |
   +-----------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose > **Virtual Private Cloud**.

   The **Virtual Private Cloud** page is displayed.

#. On the **Virtual Private Cloud** page, locate the VPC containing the subnet from which a virtual IP address is to be released, and click the VPC name.

#. On the **Subnets** tab, click the name of the subnet from which a virtual IP address is to be released.

#. Click the **Virtual IP Addresses** tab, locate the row that contains the virtual IP address to be released, click **More** in the **Operation** column, and select **Release**.

#. In the navigation pane on the left, click **Subnets**.

#. Confirm the information and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818983414.png
