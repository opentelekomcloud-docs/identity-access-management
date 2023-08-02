:original_name: en-us_topic_0079496985.html

.. _en-us_topic_0079496985:

Assigning Permissions to an IAM User
====================================

:ref:`IAM users created <en-us_topic_0046611303>` without being added to any groups do not have permissions. You can assign permissions to these IAM users on the IAM console. After authorization, the users can use cloud resources in your account as specified by their permissions.

An IAM user obtains permissions from the user groups to which the user belongs. After you attach policies or roles to a group and add a user to the group, the user inherits the permissions defined by the policies or roles.

-  If you do not add an IAM user to any group, the user will not have permissions for accessing any cloud services. For details on how to assign permissions to an IAM user, see :ref:`Creating a User Group and Assigning Permissions <en-us_topic_0046611269>` and :ref:`Adding Users to or Removing Users from a User Group <iam_03_0002>`.
-  If you have been added to the default group **admin**, you have administrator permissions and you can perform all operations on all cloud services.
-  For the system-defined permissions of all cloud services supported by IAM, see "Permissions".
-  If you add a user to multiple user groups, the user inherits the permissions that are assigned to all the groups.

Procedure
---------

#. In the user list, click **Authorize** in the row that contains the target user.

#. On the **Authorize User** page, select an authorization mode and permissions.

   -  **Inherit permissions from user groups**: Add the IAM user to certain groups to inherit their permissions.

      If you select this option, select the user groups to which the user will belong.

   -  **Select permissions**: Directly assign specific permissions to the IAM user

      If you select this option, select the permissions to be assigned and click **Next** in the lower right corner to select the authorization scope.

   .. note::

      -  If you add an IAM user to the default group **admin**, the user becomes an administrator and can perform all operations on all cloud services.
      -  If you add a user to multiple user groups, the user inherits the permissions that are assigned to all the groups.
      -  For the system-defined permissions of all cloud services supported by IAM, see `Permissions <https://docs.otc.t-systems.com/additional/permissions.html>`__.

#. Click **OK**.

   You can go to the **Permissions** > **Authorization** page and view or modify the permissions of the IAM user.
