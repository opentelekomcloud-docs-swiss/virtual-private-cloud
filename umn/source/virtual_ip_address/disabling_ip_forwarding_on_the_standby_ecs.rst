:original_name: vpc_vip_0007.html

.. _vpc_vip_0007:

Disabling IP Forwarding on the Standby ECS
==========================================

Scenarios
---------

If a virtual IP address is used in an active/standby scenario, disable IP forwarding on the standby ECS.

Linux
-----

#. Log in to the ECS.

#. Run the following command to switch to user **root**:

   **su root**

#. Check whether IP forwarding is enabled:

   **cat /proc/sys/net/ipv4/ip_forward**

   In the command output, **1** indicates it is enabled, and **0** indicates it is disabled. The default value is **0**.

   -  If **1** is displayed, go to :ref:`4 <vpc_vip_0007__en-us_topic_0206027322_li97125518364>`.
   -  If **0** is displayed, no further action is required.

#. .. _vpc_vip_0007__en-us_topic_0206027322_li97125518364:

   Use either of the following methods to modify the configuration file:

   -  Method 1: Use the vi editor to open the **/etc/sysctl.conf** file, change the value of **net.ipv4.ip_forward** to **0**, and enter **:wq** to save the change and exit.

   -  Method 2: Use the **sed** command. An example command is as follows:

      **sed -i '/net.ipv4.ip_forward/s/1/0/g' /etc/sysctl.conf**

#. Make the modification take effect:

   **sysctl -p /etc/sysctl.conf**

Windows
-------

#. Log in to the ECS.

#. Open **Command Prompt** and run the following command:

   **ipconfig/all**

   In the command output, if the value of **IP Routing Enabled** is **No**, the IP forwarding function is disabled.

#. Press **Windows** and **R** keys together to open the **Run** box, and enter **regedit** to open the **Registry Editor**.

#. Set the value of **IPEnableRouter** under **HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\Tcpip\\Parameters** to **0**.

   -  If the value is set to **0**, IP forwarding will be disabled.
   -  If the value is set to **1**, IP forwarding will be enabled.
