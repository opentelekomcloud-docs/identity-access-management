:original_name: iam_06_0001.html

.. _iam_06_0001:

Process for Account Delegation
==============================

The agency function enables you to delegate another account to implement O&M on your resources based on assigned permissions.

.. note::

   You can delegate resource access only to accounts, rather than IAM users.

The following is the procedure for delegating resource access to another account. Account A is the delegating party and account B is the delegated party.

#. Account A creates an agency in IAM to delegate resource access to account B.


   .. figure:: /_static/images/en-us_image_0000001951429117.png
      :alt: **Figure 1** (Account A) Creating an agency

      **Figure 1** (Account A) Creating an agency

#. (Optional) Account B assigns permissions to an IAM user to manage specific resources for account A.

   a. Create a user group, and grant it permissions required to manage account A's resources.
   b. Create a user and add the user to the user group.


   .. figure:: /_static/images/en-us_image_0000001924150268.png
      :alt: **Figure 2** (Account B) Authorizing an IAM user to manage delegated resources

      **Figure 2** (Account B) Authorizing an IAM user to manage delegated resources

#. Account B or the authorized user manages account A's resources.

   a. Use account B to log in and switch the role to account A.
   b. Switch to region A and manage account A's resources in this region.


   .. figure:: /_static/images/en-us_image_0000001924309660.png
      :alt: **Figure 3** (Account B) Switching the role

      **Figure 3** (Account B) Switching the role
