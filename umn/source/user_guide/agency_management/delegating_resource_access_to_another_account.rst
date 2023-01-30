:original_name: iam_01_0054.html

.. _iam_01_0054:

Delegating Resource Access to Another Account
=============================================

Agency is a trust relationship between a delegating account and a delegated account. By creating an agency, you can grant permissions to another account or cloud service for resource management.

This section uses account A and account B as an example to describe how to delegate an account to manage resources under another account.

#. Account A creates an agency to delegate resource access to account B.


   .. figure:: /_static/images/en-us_image_0274187199.png
      :alt: **Figure 1** Creating an agency

      **Figure 1** Creating an agency

#. Account B grants user Randolph permissions for managing account A's resources.

   a. Create a user group (for example, **Agency**), and grant resource management permissions to the user group.
   b. Add user Randolph to user group **Agency**.


   .. figure:: /_static/images/en-us_image_0000001089129340.png
      :alt: **Figure 2** Delegating resource access

      **Figure 2** Delegating resource access

#. User Randolph of account B manages the resources in account A.

   a. Randolph logs in to the cloud system and switches the role to account A.
   b. Job switches to project A.
   c. Job manages the resources in account A based on assigned permissions.


   .. figure:: /_static/images/en-us_image_0274187214.png
      :alt: **Figure 3** Managing resources based on agency permissions

      **Figure 3** Managing resources based on agency permissions
