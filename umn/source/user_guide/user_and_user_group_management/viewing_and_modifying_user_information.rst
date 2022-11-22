:original_name: en-us_topic_0046661675.html

.. _en-us_topic_0046661675:

Viewing and Modifying User Information
======================================

As an administrator, you can view and modify the basic information, user groups, and logs of each user. In addition, you can change the groups to which a user belongs if the user's responsibilities have changed, or modify the login credentials of a user if the user forgets their password or access key.

Viewing User Information
------------------------

In the user list, view the detailed information about a user, including the basic information, user groups, and logs.

Modifying User Information
--------------------------

Click **Modify** in the **Operation** column of the row that contains the target user.

-  **Status**: A user is enabled by default after being created. You can change the status of a user to **Disabled** if you will no longer use it.
-  **Login Authentication**

   -  **Virtual MFA device**: Change the login authentication mode to virtual MFA device only if the user has been bound to an MFA device. The user needs to enter an MFA verification code during login.
   -  **SMS**: Change the login authentication mode to SMS only if the user has been bound to a mobile number. The user needs to enter an SMS verification code during login.
   -  **Email**: Change the login authentication mode to email only if the user has been bound to an email address. The user needs to enter an email verification code during login.

-  **Email Address**, **Mobile Number**, and **Description**
-  **Virtual MFA Device**: Bind an MFA device to or unbind an MFA device from the user.
-  **User Groups**: Add the user to or remove the user from one or more user groups.

   .. note::

      You can enter a keyword to quickly find the target user group.

Setting User Credentials
------------------------

In the user list, click **Set Credentials** in the **Operation** column of the row that contains the target user to change the password or manage access keys.

+-----------------+---------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Credential Type | Generation Method                           | Description                                                                                                                                  | Application Scenario                                                                                                                                        |
+=================+=============================================+==============================================================================================================================================+=============================================================================================================================================================+
| Password        | Set by user                                 | The user can set a password by clicking on the one-time login URL sent over email.                                                           | Resetting the password of a user who has been associated with an email address and needs to use the password to log in to the management console.           |
+-----------------+---------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                 | Automatically generated                     | The system automatically generates a 10-character password.                                                                                  | Resetting the password of a user who uses a development tool (such as APIs, CLI, and SDK) that supports password authentication to access the cloud system. |
|                 |                                             |                                                                                                                                              |                                                                                                                                                             |
|                 |                                             | .. note::                                                                                                                                    |                                                                                                                                                             |
|                 |                                             |                                                                                                                                              |                                                                                                                                                             |
|                 |                                             |    You can download the password after clicking **OK** when the user is created.                                                             |                                                                                                                                                             |
+-----------------+---------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                 | Set now                                     | Set password for the user.                                                                                                                   | Setting a password for a user.                                                                                                                              |
+-----------------+---------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Access key      | Created by a user or security administrator | Create or delete access keys in the **Access Keys** area.                                                                                    | Creating or deleting access keys of users who access the cloud system using access keys.                                                                    |
|                 |                                             |                                                                                                                                              |                                                                                                                                                             |
|                 |                                             | .. note::                                                                                                                                    |                                                                                                                                                             |
|                 |                                             |                                                                                                                                              |                                                                                                                                                             |
|                 |                                             |    Each user can have a maximum of two access keys, which are valid for 360 days. To ensure account security, keep the access keys properly. |                                                                                                                                                             |
+-----------------+---------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  **Password Reset**: If you select **Automatically generated** or **Set now**, you can choose whether to require password reset when the user logs in. For security purposes, do not deselect this option.
