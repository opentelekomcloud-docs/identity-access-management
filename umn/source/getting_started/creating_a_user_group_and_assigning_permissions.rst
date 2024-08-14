:original_name: iam_01_0030.html

.. _iam_01_0030:

Creating a User Group and Assigning Permissions
===============================================

As a security administrator, you can create user groups and grant them permissions.

Procedure
---------

#. Choose **Management & Deployment** > **Identity and Access Management**.

#. In the navigation pane, choose **User Groups**.

#. On the **User Groups** page, click **Create User Group**.

#. Enter a user group name.

#. (Optional) Enter a description for the user group.

   .. note::

      To enable users to directly view their permissions, set a description for the user group. For example, if you assign the **Security Administrator** role to a user group, you can set any description in the **Description** text box. For example: **Security Administrator: Permissions for creating, deleting, and modifying users as well as granting permissions to users.** For details about the permissions for all cloud services, see `Permission Description <https://docs.otc.t-systems.com/permissions/index.html>`__.

#. Click **OK**.

   The user group is displayed in the user group list.

#. In the row containing the user group, click **Authorize** in the **Operation** column.

#. Assign permissions for region-specific projects to the user group.

   a. Select desired permissions for project-level services and click **Next**.
   b. Set **Scope** to **Regional-specific projects**, select the regional project, and click **OK**.

#. Assign permissions for global services to the user group.

   a. Select permissions for global services, such as **OBS OperateAccess**, and click **Next**.
   b. Select **All resources** for **Scope** and click **OK**.
