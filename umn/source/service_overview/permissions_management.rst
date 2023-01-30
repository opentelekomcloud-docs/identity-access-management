:original_name: iam_01_0024.html

.. _iam_01_0024:

Permissions Management
======================

You can grant users permissions to access different resources.

Granting Permissions to Users
-----------------------------


.. figure:: /_static/images/en-us_image_0274187188.png
   :alt: **Figure 1** Authorization model

   **Figure 1** Authorization model

#. Plan user groups and grant permissions to each user group.
#. Add a user to a specific user group so that the user can inherit the permissions of the group.

When personnel changes occur, you only need to change the user groups to which the users belong.

Granting Permissions to Other Accounts
--------------------------------------

You (account A) can grant permissions to another account (account B) by creating an agency. Account B can then grant the **Agent Operator** permissions to a user so that the user can manage resources in your account (account A).

Granting Permissions to Federated Users
---------------------------------------

You can federate external users to IAM and grant permissions to the users to access cloud resources by creating an identity provider and identity conversion rules.


.. figure:: /_static/images/en-us_image_0274186856.png
   :alt: **Figure 2** Identity conversion of federated users

   **Figure 2** Identity conversion of federated users
