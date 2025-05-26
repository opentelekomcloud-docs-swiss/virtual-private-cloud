:original_name: faq_security_0003.html

.. _faq_security_0003:

Why Can't I Delete a Security Group?
====================================

-  The default security group is named **default** and cannot be deleted.

-  If you want to delete a security group that is associated with instances, such as cloud servers, containers, and databases, you need to remove the instances from the security group first.

-  A security group cannot be deleted if it is used as the source or destination of a rule in another security group.

   You need to delete or modify the rule first and delete the security group.

   For example, if the source of a rule in security group **sg-B** is set to **sg-A**, you need to delete or modify the rule in **sg-B** before deleting **sg-A**.
