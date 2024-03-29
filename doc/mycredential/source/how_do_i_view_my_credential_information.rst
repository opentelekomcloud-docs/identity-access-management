How Do I View My Credential Information?
========================================

You need to use your security credentials when you access the public cloud system through the management console or APIs, or perform service interconnection in
the public cloud system. You can view security credentials on the **My Credential** page.

Procedure
^^^^^^^^^

1. On the console page, click the username in the upper right corner and select **My Credential** from the drop-down list.

   .. figure:: /_static/images/en-us_image_0111879390.jpg

2. On the **My Credential** page, view basic account information.

.. table:: **Table 1** Basic account information

   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | **Basic Information**                                                         | **Description**                                                               |
   +===============================================================================+===============================================================================+
   | Username                                                                      | Username used for logging in to the public cloud system.                      |
   |                                                                               |                                                                               |
   |                                                                               | -  The username created in MyWorkplace is in the following format: ICU        |
   |                                                                               |       *userid* *Contract instance number*.                                    |
   |                                                                               |                                                                               |
   |                                                                               | -  The username created in Open Telekom Cloud is user-defined.                |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | User ID                                                                       | Unique identifier for a user in the public cloud system. It is automatically  |
   |                                                                               | generated by the system.                                                      |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Domain Name                                                                   | **Domain Name** is the same as the username created in MyWorkplace, that is,  |
   |                                                                               | ICU userid *Contract instance name*. The name is required when you log in to  |
   |                                                                               | the public cloud system.                                                      |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Domain ID                                                                     | Unique identifier for a domain in the public cloud system. The domain ID is   |
   |                                                                               | automatically generated by the system.                                        |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Verified Email Address                                                        | Email address bound to a user. Users can use their email address to log in to |
   |                                                                               | the public cloud system, reset their passwords, and receive verification      |
   |                                                                               | codes and other push notifications.                                           |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Mobile Number                                                                 | Mobile number bound to a user. Users can use their mobile number to log in to |
   |                                                                               | the public cloud system, reset their passwords, and receive verification      |
   |                                                                               | codes and other push notifications.                                           |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Password                                                                      | Login password configured in the public cloud system.                         |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Verify Login by SMS Message                                                   | Whether SMS message-based login authentication is enabled. If it is enabled,  |
   |                                                                               | a user needs to enter an SMS verification code when attempting to log in.     |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Project                                                                       | Projects are used to group and isolate OpenStack resources, including         |
   |                                                                               | computing, storage, and network resources. Resources owned by users must be   |
   |                                                                               | mounted under projects. A project can be a department or a project team. You  |
   |                                                                               | can create projects in a region to perform isolated management of resources.  |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Project List                                                                  | List of projects an account can access. The project parameter needs to be     |
   |                                                                               | specified when the user accesses native OpenStack APIs.                       |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Access Keys                                                                   | AK/SK. A maximum of two pairs can be created. The AK/SK is used to encrypt    |
   |                                                                               | the signature when accessing the public cloud system through APIs.            |
   +-------------------------------------------------------------------------------+-------------------------------------------------------------------------------+

Related Information
^^^^^^^^^^^^^^^^^^^

API Key

To allow MyWorkplace users to access OpenStack APIs, you can enable the public cloud system to generate an API key in earlier versions and use the API key as
the value of the **password** field to call APIs or log in to the public cloud system.

.. note::

   An API key is a 32-character string consisting of random digits and letters.

The current version of the public cloud system supports user creation. You can directly log in to the public cloud system as well as create a user in IAM and
set a password. The password can replace the API key. Therefore, the API key information has been deleted from the related GUI.

For security purposes, a user who uses an API key is advised to use the following method to set a login password for replacing the API key:

-  Log in to the public cloud system using the API key and set a password.

-  Use the password retrieval function on the login page of the public cloud system to set a new password.

-  Contact users with **Security Administrator** permissions to set a password by setting credentials.

After the password is set successfully, the API key becomes invalid. The user can use the new password to call APIs or log in to the public cloud system.
