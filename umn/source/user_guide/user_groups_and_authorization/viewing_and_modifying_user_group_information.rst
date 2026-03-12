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

      In the user group list, click the target user group to view its details, including the basic information, permissions, and users.

   -  Modifying user group information

      Click **Modify** in the **Operation** column of the row that contains the target user group to go to the **Modify User Group** page.

      .. note::

         -  For the default user group, you can only manage its users and cannot modify its basic information or permissions.
         -  If the name of a user group has been configured in the identity conversion rules of an IdP, modifying the user group name will cause the identity conversion rules to fail. Exercise caution when performing this operation.

   -  Modifying user group permissions

      You can view or modify user group permissions on the **Permissions** page of the IAM console.

      .. note::

         -  Modifying the permissions of a user group changes the permissions of all users in the user group.
         -  Permissions of the default user group **admin** cannot be modified.

      a. Click a user group to go to the details page, and view the group permissions in the **Permissions** tab.

      b. Click **Delete** in the row that contains the role or policy you want to delete.


         .. figure:: /_static/images/en-us_image_0000002530633799.png
            :alt: **Figure 1** Deleting an assigned permission

            **Figure 1** Deleting an assigned permission

      c. Click **OK**.

      d. On the **Permissions** tab, click **Authorize**.


         .. figure:: /_static/images/en-us_image_0000002498759736.png
            :alt: **Figure 2** Assigning permissions to a user group

            **Figure 2** Assigning permissions to a user group

      e. Select desired permissions and a scope, and click **OK**.

      f. Go back to the **Permissions** tab to view the modified group permissions.


         .. figure:: /_static/images/en-us_image_0000002530642105.png
            :alt: **Figure 3** Permissions assigned

            **Figure 3** Permissions assigned

   -  Managing Users

      a. In the user group list, click **Manage User** in the row containing the user group you want to modify.
      b. In the **Available Users** area, select users you want to add to the user group.
      c. In the **Selected Users** area, remove users from the user group.
