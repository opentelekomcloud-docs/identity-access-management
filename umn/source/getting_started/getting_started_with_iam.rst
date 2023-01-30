:original_name: iam_01_0034.html

.. _iam_01_0034:

Getting Started with IAM
========================

Your account has full access to your resources. For security purposes, create a security administrator and perform routine management as the security administrator.

If a user needs to access resources in your account, you can create an IAM user and a user group as the security administrator, grant the required permissions to the user group, and add the user to the user group. The user inherits the permissions of the user group and has their own security credentials (username/password) to access resources in your account.

Example
-------

The following is an example of how to use IAM.

Assume that there are three user groups in your enterprise: security administrators (**admin**), developers, and testers. Each user group can contain multiple users, and a user can belong to multiple user groups.


.. figure:: /_static/images/en-us_image_0000001088564514.png
   :alt: **Figure 1** User management model

   **Figure 1** User management model

#. Create a security administrator **Franklin** and add **Franklin** to the default user group **admin**.
#. Log in as **Franklin**, create another security administrator **Lawrence**, and add **Lawrence** to the default user group **admin**.
#. Log in as **Franklin** or **Lawrence**, create user groups **Developers** and **Testers**, and grant the required permissions to each user group.
#. Log in as **Franklin** or **Lawrence**, create developers **Elizabeth** and **Randolph**, and add them to the **Developers** user group. Then create tester **Jennifer**, and add **Jennifer** and **Randolph** to the **Testers** user group.
#. Users **Elizabeth**, **Jennifer**, and **Randolph** log in using their own credentials.

   .. note::

      Security administrators and users are IAM users who have different permissions depending on the user groups to which they belong. All IAM users have their own security credentials (username and password) to log in to the system.
