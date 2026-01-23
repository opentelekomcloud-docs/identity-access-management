:original_name: iam_01_0657.html

.. _iam_01_0657:

Assigning Dependency Roles
==========================

Cloud services interwork with each other. Therefore, the administrator needs to assign both the required roles and their dependent roles for the authorization to take effect. Policies, however, do not require dependencies.

Procedure
---------

#. Log in to the as the administrator.

#. In the user group list, click **Authorize** in the row that contains the created user group.

#. On the displayed page, search for a role in the search box in the upper right corner.

#. Select the target role. The system automatically selects the dependency roles.

#. Click |image1| next to the role to view the dependencies.

   For example, the **DNS Administrator** role contains the **Depends** parameter which specifies the dependency roles. When you assign the **DNS Administrator** role to a user group, you also need to assign the **Tenant Guest** and **VPC Administrator** roles to the group for the same project.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001162246460.png
