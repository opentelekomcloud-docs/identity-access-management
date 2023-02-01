:original_name: iam_08_0008.html

.. _iam_08_0008:

Step 2: Configure Identity Conversion Rules
===========================================

As the enterprise administrator, you can manage identities and permissions of federated users in the enterprise identity provider. By configuring identity conversion rules, you can map the identities and permissions of federated users to the cloud system and control their access to specific resources.

.. note::

   -  Modifications to identity conversion rules will take effect only after the federated users log in again.
   -  To modify the permissions of a federated user, modify the permissions of the user group to which the user belongs. Then restart the identity provider system for the modifications to take effect.

Prerequisites
-------------

An identity provider has been created in the cloud system, and the login link of the identity provider is accessible. (For details about how to create and verify an identity provider, see :ref:`Step 1: Create an Identity Provider <iam_08_0009>`.)

Procedure
---------

If you configure identity conversion rules by clicking **Create Rule**, IAM converts the rule parameters to the JSON format. Alternatively, you can click **Edit Rule** to configure rules in the JSON format.

-  **Creating a Rule**

   #. Choose **Identity Providers** from the navigation pane.

   #. In the identity provider list, click **Modify** in the row containing the identity provider.

   #. In the **Identity Conversion Rules** area, click **Create Rule**. Then, configure the rule in the **Create Rule** dialog box.

      .. table:: **Table 1** Parameter description

         +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter             | Description                                                                                    | Remarks                                                                                                                                                                                                                                                                 |
         +=======================+================================================================================================+=========================================================================================================================================================================================================================================================================+
         | Username              | Username of federated users to be displayed in the cloud system                                | To distinguish federated users from users of the cloud system, it is recommended that you set the username to "**FederationUser-**\ *IdP*\ **\_**\ *XXX*". *IdP* indicates an identity provider name, for example, AD FS and Shibboleth. *XXX* indicates a custom name. |
         |                       |                                                                                                |                                                                                                                                                                                                                                                                         |
         |                       |                                                                                                | You can also set the federated username to a simple expression, for example, **FederationUser-**\ *IdP*\ **\_**\ *{email}*. After the rule is created successfully, *{email}* is automatically replaced with the email address of each federated user.                  |
         |                       |                                                                                                |                                                                                                                                                                                                                                                                         |
         |                       |                                                                                                | .. important::                                                                                                                                                                                                                                                          |
         |                       |                                                                                                |                                                                                                                                                                                                                                                                         |
         |                       |                                                                                                |    NOTICE:                                                                                                                                                                                                                                                              |
         |                       |                                                                                                |    Each federated username must be unique under your account. Identical usernames under one or more identity providers of the same account will be identified as the same federated user in the cloud system.                                                           |
         +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | User Group            | User groups to which the federated users will belong in the cloud system                       | Federated users will inherit permissions from the groups to which they belong.                                                                                                                                                                                          |
         +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Rule Conditions       | Conditions that a federated user must meet to obtain permissions from the selected user groups | Federated users who do not meet these conditions cannot access the cloud system. You can create a maximum of 10 conditions for an identity conversion rule.                                                                                                             |
         |                       |                                                                                                |                                                                                                                                                                                                                                                                         |
         |                       |                                                                                                | .. note::                                                                                                                                                                                                                                                               |
         |                       |                                                                                                |                                                                                                                                                                                                                                                                         |
         |                       |                                                                                                |    -  An identity conversion rule can have multiple conditions. It takes effect only if all of the conditions are met.                                                                                                                                                  |
         |                       |                                                                                                |    -  An identity provider can have multiple identity conversion rules. If a federated user does not meet any of the rules, the user will not be allowed to access the cloud system.                                                                                    |
         +-----------------------+------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

      For example, set an identity conversion rule for enterprise administrators.

      -  Username: **FederationUser-IdP_admin_{email}**
      -  User group: **admin**
      -  Rule condition: **\_NAMEID\_** (attribute), **any_one_of** (condition), and **ID1;ID2;ID3** (value). Only users with ID1, ID2, or ID3 inherit permissions from the **admin** user group.

   #. In the **Create Rule** area, click **OK**.

   #. On the **Modify Identity Provider** page, click **OK**.

-  **Editing a Rule**

   #. Log in to the cloud system as an administrator, and go to the IAM console. Then, choose **Identity Providers** from the navigation pane.

   #. In the identity provider list, click **Modify** in the row containing the identity provider.

   #. In the **Identity Conversion Rules** area, click **Edit Rule**. Then configure the rule in the **Edit Rule** dialog box.

   #. Edit the identity conversion rule in the JSON format. For details, see :ref:`Syntax of Identity Conversion Rules <en-us_topic_0079620340>`.

   #. Click **Validate** to verify the syntax of the rule.

   #. If the rule is correct, click **OK** in the **Edit Rule** dialog box. Then click **OK** on the **Modify Identity Provider** page.

      If a message indicating that the JSON file is incomplete is displayed, modify the statement or click **Cancel** to cancel the modifications.
