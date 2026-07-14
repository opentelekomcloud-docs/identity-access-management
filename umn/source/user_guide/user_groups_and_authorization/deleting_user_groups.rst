:original_name: iam_01_0430.html

.. _iam_01_0430:

Deleting User Groups
====================

You can delete a user group that is no longer needed.

.. warning::

   #. Deleting a user group modifies permissions for all associated users, invalidating their tokens. Affected users must re-obtain their tokens. Before deleting a user group, ensure that no services will be impacted and that the token acquisition logic includes a retry mechanism.
   #. If the user group has associated users, click the number in the **Users** column to review user information before proceeding.

Procedure
---------

To delete a user group, do the following:

#. Log in to the IAM console. In the navigation pane, choose **User Groups**.
#. In the user group list, click **Delete** in the row that contains the user group to be deleted.
#. In the displayed dialog box, enter **DELETE** and click **OK**.

Batch Deleting User Groups
--------------------------

To delete multiple user groups at a time, do the following:

#. Log in to the IAM console. In the navigation pane, choose **User Groups**.
#. In the user group list, select the user groups to be deleted and click **Delete** above the list.
#. In the displayed dialog box, enter **DELETE** and click **OK**.
