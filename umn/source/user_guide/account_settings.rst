:original_name: en-us_topic_0046611308.html

.. _en-us_topic_0046611308:

Account Settings
================

Users with **Security Administrator** permissions can configure a login authentication policy, password policy, and ACL to keep your user information and system secure.

Procedure
---------

#. Set the login authentication policy.

   a. In the navigation pane, choose **Security Settings** > **Login Authentication Policy**.

   b. In the **Account Lockout** area, enter the idle duration, maximum number of invalid login attempts, and lockout duration.

      If the number of login attempts reaches the specified upper limit within the specified duration, the user will be locked for a period of time. For example, if a user fails to log in for 3 consecutive times within 10 minutes, the user will be locked for 15 minutes. The user can log in again after 15 minutes.

   c. In the **Account Disabling** area, select **Disable account upon login if it is not used within the validity period**, and set the user validity period. If the user does not access the cloud system through the management console or APIs within the validity period, the user will be disabled.

      The account disabling setting is for security purposes. If a user is disabled, resources in the account will not be affected and the user can contact the administrator to enable the user again.

   d. In the **Session Timeout** area, set the session timeout that will apply if you or users created using your account do not perform any operations within a specific period. The timeout ranges from 15 minutes to 24 hours, and the default value is 15 minutes. If a user does not perform any operation within the specified duration, the user needs to log in again.

   e. In the **Recent Login Information** area, select **Display last login information upon successful login**.

      Users will be able to view the login information, such as the time of the last login, on the **Login Verification** page.

   f. In the **Custom Information** area, set custom information that will be displayed upon successful login.

      Users will be able to view this custom information on the **Login Verification** page.

   g. Click **Save**.

#. Set the password policy.

   a. In the navigation pane, choose **Security Settings** > **Password Policy**.

   b. In the **Password Composition & Reuse** area, do as follows:

      -  Ensure that the password contains at least 2 to 4 of the following character types: uppercase letters, lowercase letters, digits, and special characters. By default, the password must contain at least 2 of these character types.
      -  Set **Minimum Number of Characters**.

         .. note::

            By default, a password must contain at least 6 characters.

      -  Select **Restrict consecutive identical characters** and set the maximum number of consecutive identical characters that can be contained in a password. The value ranges from 1 to 32.
      -  Select **Disallow previously used passwords** and set the number of recent passwords disallowed. The value ranges from 1 to 10.

   c. In the **Password Expiration** area, select **Prompt password change 15 days before expiration and force password change upon expiration**, and set the password validity period.

      Users must change their password when the password has expired.

      .. note::

         The password must meet the following requirements:

         -  Must contain 6 to 32 characters.
         -  Must contain at least two types of the following: uppercase letters, lowercase letters, digits, and special characters (:literal:`~`!?,.:;-_'"(`){}[]/<>@#$%^&*+|\\= and spaces).
         -  Cannot be the username or the username spelled backwards. For example, if the username is **A12345**, the password cannot be **A12345**, **a12345**, **54321A**, or **54321a**.
         -  Cannot contain the user's mobile number or email address.

   d. In the **Minimum Password Age** area, select **Allow a password to be changed only after it is used for a specified time** and set the minimum password age.

      Users can change their password only when the specified period has expired.

   e. Click **Save**.

#. Set the ACL.

   a. In the navigation pane, choose **Security Settings** > **ACL**.
   b. On the **ACL** page, enter the allowed IP address ranges or IPv4 CIDR blocks.

      -  **IP Address Ranges**: only allow users to access the system using IP addresses in specified ranges.
      -  **IPv4 CIDR Blocks**: only allow users of specified IPv4 CIDR blocks to access the system. For example: **10.10.10.10/32**.

      .. note::

         -  The ACL takes effect only for users under your account.
         -  You can click **Restore Defaults** to restore the allowed IP address ranges to the default value, **0.0.0.0**-**255.255.255.255**, and to clear **IPv4 CIDR Blocks**.
         -  If both **IP Address Ranges** and **IPv4 CIDR Blocks** are set, users are allowed to access the system if their IP address meets the conditions specified by either of the two parameters.

   c. Click **Save**.
