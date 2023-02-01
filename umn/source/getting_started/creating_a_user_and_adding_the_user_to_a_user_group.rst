:original_name: iam_01_0031.html

.. _iam_01_0031:

Creating a User and Adding the User to a User Group
===================================================

As a security administrator, you can create a user and add the user to a user group. The user automatically inherits the permissions of the user group.

Procedure
---------

#. Choose **Management & Deployment** > **Identity and Access Management**.
#. In the navigation pane, choose **Users**. Then click **Create User**.
#. Specify the user information on the **Create User** page.

   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Description                                                                                                                                                                                                |
   +===============+============================================================================================================================================================================================================+
   | Username      | Username that will be used to log in to the cloud system. This field is required.                                                                                                                          |
   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Email Address | Email address of the user that can be used as a login credential. Users can bind an email address after they are created. This field is required if you have specified **Set by user** as the access type. |
   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mobile Number | Mobile phone number of the user that can be used as a login credential. Users can bind a mobile number after they are created. This field is optional.                                                     |
   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Description   | Additional information about the user. This field is optional.                                                                                                                                             |
   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Select an access type and click **Next**.

   +---------------------------+------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Access Type               | Configuration    |                         | Description                                                                                                                                                                                                                                     |
   +===========================+==================+=========================+=================================================================================================================================================================================================================================================+
   | Programmatic access       | --               | --                      | If you select this option, after the user is created, you can download the access key (AK/SK) generated for the user. The user can use the access key to access the cloud system through APIs. Each user can have a maximum of two access keys. |
   +---------------------------+------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Management console access | Console Password | Set by user             | If you are the administrator setting the password for the user, select this option and enter an email address and a mobile number. The user can set a password by clicking on the one-time login URL sent over email.                           |
   +---------------------------+------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                           |                  | Automatically generated | This option is available only when you create a single user.                                                                                                                                                                                    |
   +---------------------------+------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                           |                  | Set now                 | Select this option if you are the user. Then, set a password for login.                                                                                                                                                                         |
   |                           |                  |                         |                                                                                                                                                                                                                                                 |
   |                           |                  |                         | .. note::                                                                                                                                                                                                                                       |
   |                           |                  |                         |                                                                                                                                                                                                                                                 |
   |                           |                  |                         |    The password must meet the following requirements:                                                                                                                                                                                           |
   |                           |                  |                         |                                                                                                                                                                                                                                                 |
   |                           |                  |                         |    -  Must contain 6 to 32 characters.                                                                                                                                                                                                          |
   |                           |                  |                         |    -  Must contain at least two types of the following: uppercase letters, lowercase letters, digits, and special characters (:literal:`~`!?,.:;-_'"(`){}[]/<>@#$%^&*+|\\= and spaces).                                                         |
   |                           |                  |                         |    -  Cannot be the username or the username spelled backwards. For example, if the username is **A12345**, the password cannot be **A12345**, **a12345**, **54321A**, or **54321a**.                                                           |
   |                           |                  |                         |    -  Cannot contain the user's mobile number or email address.                                                                                                                                                                                 |
   +---------------------------+------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                           | Login Protection | Enable                  | If login protection is enabled, the user will need to enter a verification code in addition to the username and password during login. Enable this function for account security.                                                               |
   |                           |                  |                         |                                                                                                                                                                                                                                                 |
   |                           |                  |                         | You can choose from SMS-, email-, and :ref:`virtual MFA <iam_10_0002__section0864223164311>`-based login verification.                                                                                                                          |
   +---------------------------+------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                           |                  | Disable                 | For this example, disable login protection.                                                                                                                                                                                                     |
   +---------------------------+------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      -  For security purposes, select only one access type for each user.

         -  Programmatic access: Users can access cloud services using development tools (including APIs, CLI, and SDKs) that support key authentication. This access type is recommended for developers.
         -  Management console access: Users can log in to the management console using their own usernames and passwords.

      -  You cannot change the access type of users, but you can control their access by enabling or disabling the user accounts.

#. (Optional) Click **Next** and add the user to one or more user groups.

   -  The user will inherit the permissions assigned to the user groups to which the user belongs.
   -  You can also create new groups as required.

   .. note::

      -  If the user will be an administrator, add the user to the default group **admin**.
      -  You can add a user to multiple user groups.

#. Click **Create**. If you have specified the access type as **Programmatic access**, download the access key on the **Finish** page.
