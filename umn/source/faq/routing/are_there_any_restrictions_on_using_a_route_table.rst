:original_name: vpc_faq_0064.html

.. _vpc_faq_0064:

Are There Any Restrictions on Using a Route Table?
==================================================

-  An ECS providing SNAT must have **Unbind IP from MAC** enabled.
-  The destination of each route in a route table must be unique. The next hop must be a private IP address or a virtual IP address in the VPC. Otherwise, the route table will not take effect.
-  If a virtual IP address is set to be the next hop in a route, EIPs bound with the virtual IP address in the VPC will become invalid.
