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
-  You can only release EIPs that are not bound to any resources.

Procedure
---------

**Unbinding a single EIP**

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. On the console homepage, under , click **Elastic IP**.
#. On the displayed page, locate the row that contains the target EIP, and click **Unbind**.
#. Click **Yes** in the displayed dialog box.

**Releasing a single EIP**

#. Log in to the management console.
#. Click |image2| in the upper left corner and select the desired region and project.
#. On the console homepage, under , click **Elastic IP**.
#. On the displayed page, locate the row that contains the target EIP, click **More** and then **Release** in the **Operation** column.
#. Click **Yes** in the displayed dialog box.

**Unbinding multiple EIPs at once**

#. Log in to the management console.
#. Click |image3| in the upper left corner and select the desired region and project.
#. On the console homepage, under , click **Elastic IP**.
#. On the displayed page, select the EIPs to be unbound.
#. Click the **Unbind** button located above the EIP list.
#. Click **Yes** in the displayed dialog box.

**Releasing multiple EIPs at once**

#. Log in to the management console.
#. Click |image4| in the upper left corner and select the desired region and project.
#. On the console homepage, under , click **Elastic IP**.
#. On the displayed page, select the EIPs to be released.
#. Click the **Release** button located above the EIP list.
#. Click **Yes** in the displayed dialog box.

.. |image1| image:: /_static/images/en-us_image_0141273034.png
.. |image2| image:: /_static/images/en-us_image_0141273034.png
.. |image3| image:: /_static/images/en-us_image_0141273034.png
.. |image4| image:: /_static/images/en-us_image_0141273034.png
