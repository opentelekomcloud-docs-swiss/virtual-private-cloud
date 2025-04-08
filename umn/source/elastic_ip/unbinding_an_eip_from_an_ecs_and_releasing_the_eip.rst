:original_name: vpc_eip_0001.html

.. _vpc_eip_0001:

Unbinding an EIP from an ECS and Releasing the EIP
==================================================

Scenarios
---------

If you no longer need an EIP, unbind it from the ECS and release the EIP to avoid wasting network resources.

Notes and Constraints
---------------------

-  EIPs assigned and bound to load balancers in the ELB service are displayed in the EIP list of the VPC service, but you cannot unbind these EIPs from classic load balancers.
-  Only EIPs with no instance bound can be released. If you want to release an EIP with an instance bound, you need to unbind EIP from the instance first.

Procedure
---------

**Unbinding a single EIP**

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. Click |image2| in the upper left corner, and choose > **Elastic IP**.
#. On the displayed page, locate the row that contains the EIP, and click **Unbind**.
#. Click **OK**.

**Releasing a single EIP**

#. Log in to the management console.
#. Click |image3| in the upper left corner and select the desired region and project.
#. Click |image4| in the upper left corner, and choose > **Elastic IP**.
#. On the displayed page, locate the row that contains the target EIP, click **More** and then **Release** in the **Operation** column.
#. Click **OK**.

**Unbinding multiple EIPs at once**

#. Log in to the management console.
#. Click |image5| in the upper left corner and select the desired region and project.
#. Click |image6| in the upper left corner, and choose > **Elastic IP**.
#. On the displayed page, select the EIPs to be unbound.
#. Click the **Unbind** button located above the EIP list.
#. Click **OK**.

**Releasing multiple EIPs at once**

#. Log in to the management console.
#. Click |image7| in the upper left corner and select the desired region and project.
#. Click |image8| in the upper left corner, and choose > **Elastic IP**.
#. On the displayed page, select the EIPs to be released.
#. Click the **Release** button located above the EIP list.
#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001818982734.png
.. |image2| image:: /_static/images/en-us_image_0000001818982822.png
.. |image3| image:: /_static/images/en-us_image_0000001818982734.png
.. |image4| image:: /_static/images/en-us_image_0000001818982822.png
.. |image5| image:: /_static/images/en-us_image_0000001818982734.png
.. |image6| image:: /_static/images/en-us_image_0000001818982822.png
.. |image7| image:: /_static/images/en-us_image_0000001818982734.png
.. |image8| image:: /_static/images/en-us_image_0000001818982822.png
