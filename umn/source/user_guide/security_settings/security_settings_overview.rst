:original_name: iam_07_0001.html

.. _iam_07_0001:

Security Settings Overview
==========================

You can configure the basic information, critical operation protection, login authentication policy, password policy, and access control list (ACL) on the **Security Settings** page. For details, see :ref:`Basic Information <iam_01_0703>`, :ref:`Critical Operation Protection <iam_01_0029>`, :ref:`Login Authentication Policy <iam_01_0704>`, :ref:`Password Policy <iam_01_0607>`, and :ref:`ACL <iam_07_0003>`. This chapter describes what permissions are required to and how to access the **Security Settings** page.

Permissions Required for Security Settings
------------------------------------------

:ref:`Table 1 <iam_07_0001__en-us_topic_0179264308_table107367403417>` lists the permissions required for the operations in different tabs in security settings.

.. _iam_07_0001__en-us_topic_0179264308_table107367403417:

.. table:: **Table 1** Permissions required for security settings

   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   | Function                    | Operation | Permissions                                                                    |
   +=============================+===========+================================================================================+
   | Login password              | Query     | You do not need to obtain the permissions to query your login password.        |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   |                             | Modify    | You do not need to obtain the permissions to change your login password.       |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   | Mobile number               | Query     | You do not need to obtain the permissions to query your bound mobile number.   |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   |                             | Modify    | You do not need to obtain the permissions to change your bound mobile number.  |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   | Email address               | Query     | You do not need to obtain the permissions to query your bound email address.   |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   |                             | Modify    | You do not need to obtain the permissions to change your bound email address.  |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   | Virtual MFA device          | Query     | You do not need to obtain the permissions to query your virtual MFA device.    |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   |                             | Bind      | You do not need to obtain the permissions to bind your virtual MFA device.     |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   |                             | Unbind    | You do not need to obtain the permissions to unbind your virtual MFA device.   |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   | Login protection            | Query     | You do not need to obtain the permissions to query your login protection type. |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   | Operation protection        | Query     | iam:securitypolicies:getProtectPolicy                                          |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   |                             | Modify    | iam:securitypolicies:updateProtectPolicy                                       |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   | Access key protection       | Query     | iam:securitypolicies:getProtectPolicy                                          |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   |                             | Modify    | iam:securitypolicies:updateProtectPolicy                                       |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   | Information self-management | Query     | iam:securitypolicies:getProtectPolicy                                          |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   |                             | Modify    | iam:securitypolicies:updateProtectPolicy                                       |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   | USB KEY                     | Query     | You do not need to obtain the permissions to query your USB key.               |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   | Login authentication policy | Query     | iam:securitypolicies:getLoginPolicy                                            |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   |                             | Modify    | iam:securitypolicies:updateLoginPolicy                                         |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   | Password policy             | Query     | iam:securitypolicies:getPasswordPolicy                                         |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   |                             | Modify    | iam:securitypolicies:updatePasswordPolicy                                      |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   | Console access              | Query     | iam:securitypolicies:getConsoleAclPolicy                                       |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   |                             | Modify    | iam:securitypolicies:updateConsoleAclPolicy                                    |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   | API access                  | Query     | iam:securitypolicies:getApiAclPolicy                                           |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+
   |                             | Modify    | iam:securitypolicies:updateApiAclPolicy                                        |
   +-----------------------------+-----------+--------------------------------------------------------------------------------+

.. _iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575:

Accessing the Security Settings Page
------------------------------------

#. Log in to the IAM console as an administrator or an entrusted identity.
#. In the left navigation pane, choose **Security Settings**.

-  You and all IAM users created using your account can access the **Security Settings** page from the management console.

   #. Log in to the IAM console.
   #. In the left navigation pane, choose **Security Settings**.
