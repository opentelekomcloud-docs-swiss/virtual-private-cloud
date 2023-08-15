:original_name: vpc_vip02_0003.html

.. _vpc_vip02_0003:

Binding a Virtual IP Address to an EIP or ECS
=============================================

Scenarios
---------

You can bind a virtual IP address to an EIP so that you can access the ECSs bound with the same virtual IP address from the Internet. These ECSs can work in the active/standby mode to improve fault tolerance.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select the desired region and project.
#. On the console homepage, under , click **Virtual Private Cloud**.
#. In the navigation pane on the left, click **Virtual Private Cloud**.

5.  On the **Virtual Private Cloud** page, locate the VPC containing the virtual IP address and click the VPC name.

6.  On the **Subnets** tab, click the name of the subnet that the virtual IP address belongs to.

7.  Click the **Virtual IP Addresses** tab.

    -  To bind a virtual IP address to an EIP, locate the row that contains the virtual IP address and click **Bind to EIP** in the **Operation** column.
    -  To bind a virtual IP address to an ECS, locate the row that contains the virtual IP address and click **More** > **Bind to Server** in the **Operation** column.

8.  Select the desired EIP, or ECS and its NIC.

    .. note::

       -  If the ECS has multiple NICs, bind the virtual IP address to the primary NIC.
       -  Multiple virtual IP addresses can be bound to an ECS NIC.

9.  Click **OK**.

10. Manually configure the virtual IP address bound to an ECS.

    After a virtual IP address is bound to an ECS NIC, you need to manually configure the virtual IP address on the ECS.

    **Linux OS** (CentOS 7.2 64bit is used as an example.)

    a. .. _vpc_vip02_0003__en-us_topic_0118499077_li528316578916:

       Run the following command to obtain the NIC to which the virtual IP address is to be bound and the connection of the NIC:

       **nmcli connection**

       Information similar to the following is displayed:

       |image2|

       The command output in this example is described as follows:

       -  **eth0** in the **DEVICE** column indicates the NIC to which the virtual IP address is to be bound.
       -  **Wired connection 1** in the **NAME** column indicates the connection of the NIC.

    b. Run the following command to add the virtual IP address for the target connection:

       **nmcli connection modify "**\ *CONNECTION*\ **" ipv4.addresses** *VIP*

       Configure the parameters as follows:

       -  CONNECTION: connection of the NIC obtained in :ref:`10.a <vpc_vip02_0003__en-us_topic_0118499077_li528316578916>`.
       -  VIP: virtual IP address to be added.

          -  If you add multiple virtual IP addresses at a time, separate them with commas (,).
          -  If a virtual IP address already exists and you need to add a new one, the command must contain both the new and original virtual IP addresses.

       Example commands:

       -  Adding a single virtual IP address: **nmcli connection modify "Wired connection 1" ipv4.addresses** **172.16.0.125**
       -  Adding multiple virtual IP addresses: **nmcli connection modify "Wired connection 1" ipv4.addresses** **172.16.0.125,172.16.0.126**

    c. Run the following command to make the configuration take effect:

       **nmcli connection up "**\ *CONNECTION*\ **"**

       In this example, run the following command:

       **nmcli connection up "Wired connection 1"**

       Information similar to the following is displayed:

       |image3|

    d. Run the following command to check whether the virtual IP address has been bound:

       **ip a**

       Information similar to the following is displayed. In the command output, the virtual IP address 172.16.0.125 is bound to NIC eth0.

       |image4|

    **Windows OS** (Windows Server is used as an example here.)

    a. In **Control Panel**, click **Network and Sharing Center**, and click the corresponding local connection.

    b. On the displayed page, click **Properties**.

    c. On the **Network** tab page, select **Internet Protocol Version 4 (TCP/IPv4)**.

    d. Click **Properties**.

    e. Select **Use the following IP address** and set **IP address** to the private IP address of the ECS, for example, 10.0.0.101.


       .. figure:: /_static/images/en-us_image_0000001179761510.png
          :alt: **Figure 1** Configuring private IP address

          **Figure 1** Configuring private IP address

    f. Click **Advanced**.

    g. On the **IP Settings** tab, click **Add** in the **IP addresses** area.

       Add the virtual IP address. For example, 10.0.0.154.


       .. figure:: /_static/images/en-us_image_0000001225081545.png
          :alt: **Figure 2** Configuring virtual IP address

          **Figure 2** Configuring virtual IP address

    h. Click **OK**.

    i. In the **Start** menu, open the Windows command line window and run the following command to check whether the virtual IP address has been configured:

       **ipconfig /all**

       In the command output, **IPv4 Address** is the virtual IP address 10.0.0.154, indicating that the virtual IP address of the ECS NIC has been correctly configured.

.. |image1| image:: /_static/images/en-us_image_0226223279.png
.. |image2| image:: /_static/images/en-us_image_0000001281210233.png
.. |image3| image:: /_static/images/en-us_image_0000001237328110.png
.. |image4| image:: /_static/images/en-us_image_0000001237013856.png
