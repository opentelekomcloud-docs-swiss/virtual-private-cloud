:original_name: vpc_Concepts_0010.html

.. _vpc_Concepts_0010:

Shared SNAT
===========

The VPC service provides free SNAT function, which allows ECSs to use a limited number of public IP addresses to gain one-way access to the Internet for operations, such as updating software. However, Internet users cannot directly access the ECSs.

:ref:`Figure 1 <vpc_concepts_0010__f04fc5d5739d142e5b38d73f3746f6cad>` shows how shared SNAT works. The SNAT device forwards traffic from ECSs to the Internet and the response traffic from the Internet to the ECSs. When forwarding ECS traffic to the Internet, the SNAT device converts the source IP addresses (ECS private IP addresses) in the data packets into the public IP addresses set on the SNAT device. When processing the response packets from the Internet to the ECSs, the SNAT device changes the public IP addresses in the response data packets to the private IP addresses of the ECSs.

.. _vpc_concepts_0010__f04fc5d5739d142e5b38d73f3746f6cad:

.. figure:: /_static/images/en-us_image_0000001818983170.png
   :alt: **Figure 1** SNAT function

   **Figure 1** SNAT function

-  To enable shared SNAT using the API, refer to `Updating a Router <https://docs.sc.otc.t-systems.com/virtual-private-cloud/api-ref/native_openstack_neutron_apis_v2.0/router/updating_a_router.html#vpc-router-0004>`__ and set **enable_snat** to **true**.
-  To enable shared SNAT on the management console:

   #. Log in to the management console.

   #. Click |image1| in the upper left corner and choose > **Virtual Private Cloud**.

      The **Virtual Private Cloud** page is displayed.

   #. On the **Virtual Private Cloud** page, locate the VPC for which shared SNAT is to be enabled, and click **Modify**.

   #. In the displayed dialog box, enable **Shared SNAT**.

   #. Click **OK**.

After being configured for a VPC, shared SNAT takes effect for the whole VPC. If EIPs are bound to ECSs in a VPC for which shared SNAT is configured, Internet traffic is preferentially forwarded using the EIPs. If you want to prevent an ECS from connecting to the Internet, you can configure an outbound rule for the security group associated with the ECS.

For example:

To prevent an ECS from connecting to the Internet but allow the ECS to access 192.168.10.0/24, configure the following rule for the security group associated with the ECS:

#. Delete the default outbound rule that allows all outgoing data packets from the security group.

   After this rule is deleted, ECSs associated with this security group are not allowed to access any network, including the internal networks in the VPC of the ECSs.

#. Add the required outbound rule.

   The following shows the added outbound rule that allows the ECS to access the 192.168.10.0/24 CIDR block.

   The differences between shared SNAT and custom routes are as follows:

   -  Shared SNAT provides the SNAT function for a specified VPC through an API or the management console and enables all ECSs in the VPC to gain one-way access to the Internet.
   -  A custom route enables ECSs to access the Internet through an SNAT server that has an EIP bound. The ECSs' access requests are routed to the SNAT server based on the route table.
   -  Shared SNAT takes effect for the whole VPC by default, while a custom route takes effect for the VPC or subnet for which routes have been configured.
   -  A custom route has a higher priority than a shared SNAT.

.. |image1| image:: /_static/images/en-us_image_0000001865582917.png
