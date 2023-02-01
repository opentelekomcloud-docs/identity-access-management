:original_name: en-us_topic_0085605493.html

.. _en-us_topic_0085605493:

Viewing and Modifying User Group Information
============================================

As a security administrator, you can view and modify the basic information, permissions, and users of a user group. You can modify users' permissions by changing the groups to which the users belong.

Procedure
---------

#. In the navigation pane, choose **User Groups**.
#. In the user group list, view or modify user group information.

   -  Viewing user group information

      In the user group list, click |image1| next to the target user group to view its details, including the basic information, permissions, and users.

   -  Modifying user group information

      Click **Modify** in the **Operation** column of the row that contains the target user group to go to the **Modify User Group** page.

      .. note::

         -  For the default user group, you can only manage its users and cannot modify its basic information or permissions.
         -  If the name of a user group has been configured in the identity conversion rules of an identity provider, modifying the user group name will cause the identity conversion rules to fail. Exercise caution when performing this operation.

   -  Modifying user group permissions

      You can assign new permissions to or cancel the existing permissions of a user group in the policy view or project view.

      -  Changing the authorization scope in the policy view

         a. Choose **User Groups** in the navigation pane, and click **Manage Permissions** in the row containing the user group you want to modify. On the **Permissions** tab page, select **Policy View**.
         b. Click **Change Project** on the right of a policy.
         c. On the **Change Project** page, select or deselect desired projects.
         d. Click **OK**.

      -  Modifying permissions for certain projects in the project view

         a. Choose **User Groups** in the navigation pane, and click **Manage Permissions** on the right of a user group. On the **Permissions** tab page, select **Project View**.
         b. Click **Modify Permissions** on the right of a project.
         c. Select or deselect desire policies, and click **OK**.

   -  Managing Users

      a. In the user group list, click **Manage User** in the row containing the user group you want to modify.
      b. In the **Available Users** area, select users you want to add to the user group.
      c. In the **Selected Users** area, remove users from the user group.

.. |image1| image:: /_static/images/en-us_image_0291358588.png
