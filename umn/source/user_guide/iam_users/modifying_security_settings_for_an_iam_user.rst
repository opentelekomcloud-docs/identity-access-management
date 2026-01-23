:original_name: iam_01_0653.html

.. _iam_01_0653:

Modifying Security Settings for an IAM User
===========================================

As an administrator, you can modify the password, MFA device, login protection, and access keys of an IAM user.

Constraints
-----------

-  IAM users can change their passwords on the :ref:`Basic Information <iam_01_0703>` tab.
-  By default, only the IAM user's MFA device can be changed on the **Security Settings** tab. The MFA device of the account cannot be changed. To change the MFA device of the account, grant the permissions needed to add and unbind the MFA device.
-  The mobile number and email address of the IAM user cannot be the same as those of the account or other IAM users.

Changing the Password of an IAM User
------------------------------------

As an administrator, you can reset the password of an IAM user if the user has forgotten the password and no email address or mobile number has been bound to the user.

#. Log in to the IAM console as the administrator.
#. In the user list, click a username or click **Security Settings** in the **Operation** column to access the user details page.
#. Click the **Security Settings** tab. In the **Login Credentials** area, click |image1| in the **Login Password** row to reset the login password for the IAM user.

   -  **Set by user**: A one-time login URL will be emailed to the user. The user can then click the link to set a password.
   -  **Automatically generated**: A password will be automatically generated and then sent to the user by email.
   -  **Set now**: You set a new password and send the new password to the user.

Changing the MFA Device for an IAM User
---------------------------------------

You can only change the MFA device for an IAM user, but not for the account.

#. Log in to the IAM console as the administrator.
#. In the user list, click a username or click **Security Settings** in the **Operation** column to access the user details page.
#. Click the **Security Settings** tab and change the MFA device of the IAM user.

   -  Change the mobile number or email address of the user.

      .. note::

         The mobile number and email address of the IAM user cannot be the same as those of the account or other IAM users.

   -  Reset the MFA device for a user. For more information about MFA and virtual MFA device, see :ref:`MFA Authentication and Virtual MFA Device <iam_10_0002>`.

Modifying the Login Protection Configuration for an IAM User
------------------------------------------------------------

Login protection is disabled by default. If you enable this option, the user will need to enter a verification code in addition to the username and password when logging in to the console.

#. Log in to the IAM console as the administrator.
#. In the user list, click a username or click **Security Settings** in the **Operation** column to access the user details page.
#. Click the **Security Settings** tab and modify the login protection configuration of the IAM user. This option is disabled by default. You can choose from the following methods for secondary verification:

   -  SMS
   -  Email address
   -  Virtual MFA device

Related Operations
------------------

-  If you are an IAM user and need to change your mobile number, email address, or virtual MFA device, see :ref:`Security Settings Overview <iam_07_0001>`.
-  To manage access keys of IAM users, see :ref:`Modifying User Permissions <en-us_topic_0080335069>`.

.. |image1| image:: /_static/images/en-us_image_0000002162336158.png
