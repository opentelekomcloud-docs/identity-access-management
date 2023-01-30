:original_name: iam_01_0029.html

.. _iam_01_0029:

Creating a Security Administrator
=================================

For security purposes, create a security administrator and manage users in your account as the security administrator.

Procedure
---------

#. Choose **Management & Deployment** > **Identity and Access Management**.
#. In the navigation pane, choose **Users**.
#. On the **Users** page, click **Create User**.
#. Specify the user information on the **Create User** page.

   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Description                                                                                                                                                                                                |
   +===============+============================================================================================================================================================================================================+
   | Username      | Username that will be used to log in to the cloud system, for example, **Franklin**. This field is required.                                                                                               |
   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Email Address | Email address of the user that can be used as a login credential. Users can bind an email address after they are created. This field is required if you have specified **Set by user** as the access type. |
   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Mobile Number | Mobile phone number of the user that can be used as a login credential. Users can bind a mobile number after they are created. This field is optional.                                                     |
   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Description   | Additional information about the user. This field is optional.                                                                                                                                             |
   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Specify the access type as **Management console access** and click **Next**.

   +---------------------------+------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Access Type               | Configuration    |                         | Description                                                                                                                                                                                                                               |
   +===========================+==================+=========================+===========================================================================================================================================================================================================================================+
   | Management console access | Console Password | Set by user             | If you are the administrator setting the password for user **Franklin**, select this option and enter an email address and a mobile number. User **Franklin** can then set a password by clicking the one-time login URL sent over email. |
   +---------------------------+------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                           |                  | Automatically generated | This option is available only when you create a single user.                                                                                                                                                                              |
   +---------------------------+------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                           |                  | Set now                 | Select this option if you are user **Franklin**. Then, set a password for login.                                                                                                                                                          |
   +---------------------------+------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                           | Login Protection | Enable                  | If login protection is enabled, user **Bob** will need to enter a verification code in addition to the username and password during login. Enable this function for account security.                                                     |
   |                           |                  |                         |                                                                                                                                                                                                                                           |
   |                           |                  |                         | You can choose from SMS-, email-, and :ref:`virtual MFA <iam_10_0002__section0864223164311>`-based login verification.                                                                                                                    |
   +---------------------------+------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                           |                  | Disable                 | For this example, disable login protection.                                                                                                                                                                                               |
   +---------------------------+------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      Programmatic access: Users can access cloud services using development tools (including APIs, CLI, and SDKs) that support key authentication. This access type is recommended for developers.

#. Click **Next** to add the user to the **admin** user group.
#. Click **Create**.
