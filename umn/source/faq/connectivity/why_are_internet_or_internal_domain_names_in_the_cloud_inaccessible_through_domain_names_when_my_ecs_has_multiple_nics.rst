:original_name: vpc_faq_0060.html

.. _vpc_faq_0060:

Why Are Internet or Internal Domain Names in the Cloud Inaccessible Through Domain Names When My ECS Has Multiple NICs?
=======================================================================================================================

When an ECS has more than one NIC, if different DNS server addresses are configured for the subnets used by the NICs, the ECS cannot access public websites or internal domain names in the cloud.

You can resolve this issue by configuring the same DNS server address for the subnets used by the same ECS. You can perform the following steps to modify DNS server addresses of subnets in a VPC:

#. Log in to the management console.

2. On the console homepage, under , click **Virtual Private Cloud**.

3. In the navigation pane on the left, click **Virtual Private Cloud**.

4. On the **Virtual Private Cloud** page, locate the VPC for which a subnet is to be modified and click the VPC name.

5. In the subnet list, locate the row that contains the subnet to be modified, click **Modify**. On the displayed page, change the DNS server address as prompted.

   For more information about private DNS servers, see `What Are the Private DNS Servers Provided by the DNS Service? <https://docs.sc.otc.t-systems.com/en-us/usermanual/dns/dns_faq_002.html>`__

6. Click **OK**.
