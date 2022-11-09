:original_name: en-us_topic_0046611269.html

.. _en-us_topic_0046611269:

Creating a User Group
=====================

You can plan user groups based on user responsibilities and grant the required permissions to the user groups. Users inherit permissions from the user groups to which they belong.

Procedure
---------

#. In the navigation pane, choose **User Groups**.

#. On the **User Groups** page, click **Create User Group**.

#. Enter a user group name.

#. (Optional) Enter a description for the user group.

   .. note::

      To enable users to directly view their permissions, set a description for the user group. For example, if you assign the **Security Administrator** role to a user group, you can set any description in the **Description** text box. For example: **Security Administrator: Permissions for creating, deleting, and modifying users as well as granting permissions to users.** For details about the permissions for all cloud services, see `Permissions <https://docs.otc.t-systems.com/permissions/index.html>`__

#. Click **OK**.

   The user group is displayed in the user group list.

#. In the row containing the user group, click **Manage Permissions**.

#. On the **Permissions** tab page, click **Assign Permissions** above the permission list.

#. Specify the authorization scope. If you select **Region-specific projects**, select one or more projects in the drop-down list.

   -  **Global service project**: Services deployed without specifying physical regions are called global services, such as Object Storage Service (OBS), Content Delivery Network (CDN), and Tag Management Service (TMS). Permissions for these services must be assigned in the global service project.
   -  **Region-specific projects**: Services deployed in specific regions are called project-level services. Permissions for these services need to be assigned in region-specific projects and take effect only for the corresponding regions. If you want the permissions to take effect for all regions, grant them in all these regions.

#. Select policies and click **OK**.
