:original_name: iam_08_0004.html

.. _iam_08_0004:

Configuring Identity Conversion Rules
=====================================

After an enterprise IdP user logs in to the cloud platform, the cloud platform authenticates the identity and assigns permissions to the user based on the identity conversion rules. You can customize identity conversion rules based on your service requirements. If you do not configure identity conversion rules, the username of the federated user on the cloud platform is **FederationUser** by default, and the federated user can only access the cloud platform by default.

You can configure the following parameters for federated users:

-  Username: Usernames of federated users in the cloud platform.
-  User permissions: Permissions assigned to federated users in the cloud platform. You need to map the federated users to IAM user groups. In this way, the federated users can obtain the permissions of the user groups to use cloud resources. Ensure that user groups have been created. For details about how to create a user group, see :ref:`Creating a User Group and Assigning Permissions <en-us_topic_0046611269>`.

.. note::

   -  Modifications to identity conversion rules will take effect the next time federated users log in.
   -  To modify the permissions of a user, modify the permissions of the user group which the user belongs to. Then restart the enterprise IdP for the modifications to take effect.

Prerequisites
-------------

-  The enterprise administrator has created an account in the cloud platform, and has created user groups and assigned permissions to the group in IAM. For details, see :ref:`Creating a User Group and Assigning Permissions <en-us_topic_0046611269>`.
-  An IdP has been created in the cloud platform. For details, see :ref:`Creating an IdP Entity <iam_08_0003>`.

Procedure
---------

If you configure identity conversion rules by clicking **Create Rule**, IAM converts your specified parameters to the JSON format. Alternatively, you can click **Edit Rule** to configure rules in JSON format. For details, see :ref:`Syntax of Identity Conversion Rules <en-us_topic_0079620340>`.

-  **Creating Rules**

   #. Log in to the IAM console as the administrator. In the navigation pane, choose **Identity Providers**.

   #. In the IdP list, click **Modify** in the row containing the IdP.

   #. In the **Identity Conversion Rules** area, click **Create Rule**. Then, configure the rules in the **Create Rule** dialog box.

      .. table:: **Table 1** Parameter description

         +-----------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter             | Description                                                                                     | Remarks                                                                                                                                                                                                                                                                                                                                                     |
         +=======================+=================================================================================================+=============================================================================================================================================================================================================================================================================================================================================================+
         | Username              | Username of federated users in the cloud platform.                                              | To distinguish federated users from users in the cloud platform, it is recommended that you set the username to **FederationUser-**\ *IdP*\ **\_**\ *XXX*. *IdP* indicates an IdP name, for example, AD FS or Shibboleth. *XXX* indicates a custom name.                                                                                                    |
         |                       |                                                                                                 |                                                                                                                                                                                                                                                                                                                                                             |
         |                       |                                                                                                 | .. important::                                                                                                                                                                                                                                                                                                                                              |
         |                       |                                                                                                 |                                                                                                                                                                                                                                                                                                                                                             |
         |                       |                                                                                                 |    NOTICE:                                                                                                                                                                                                                                                                                                                                                  |
         |                       |                                                                                                 |                                                                                                                                                                                                                                                                                                                                                             |
         |                       |                                                                                                 |    -  The username of each federated user must be unique in the same IdP. Federated users with the same usernames in the same IdP will be mapped to the same IAM user in the cloud platform.                                                                                                                                                                |
         |                       |                                                                                                 |    -  The username can be any string that does not contain <, >, {, or }, or you can use a placeholder **{0..n}**. **{0}** indicates the first attribute of the user information in **remote**, and **{1}** indicates the second attribute.                                                                                                                 |
         +-----------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | User Groups           | User groups which the federated users belong to in the cloud platform.                          | The federated users will inherit permissions from their user groups. You can select a user group that has already been created.                                                                                                                                                                                                                             |
         +-----------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Rule Conditions       | Conditions that a federated user must meet to obtain permissions from the selected user groups. | Federated users who do not meet these conditions cannot access the cloud platform. You can create a maximum of 10 conditions for an identity conversion rule.                                                                                                                                                                                               |
         |                       |                                                                                                 |                                                                                                                                                                                                                                                                                                                                                             |
         |                       |                                                                                                 | The **Attribute** and **Value** parameters are used for the enterprise IdP to transfer user information to the cloud platform through SAML assertions. The **Condition** parameter can be set to **empty**, **any_one_of**, or **not_any_of**. For details about these parameters, see :ref:`Syntax of Identity Conversion Rules <en-us_topic_0079620340>`. |
         |                       |                                                                                                 |                                                                                                                                                                                                                                                                                                                                                             |
         |                       |                                                                                                 | .. note::                                                                                                                                                                                                                                                                                                                                                   |
         |                       |                                                                                                 |                                                                                                                                                                                                                                                                                                                                                             |
         |                       |                                                                                                 |    -  An identity conversion rule can have multiple conditions. It takes effect only if all of the conditions are met.                                                                                                                                                                                                                                      |
         |                       |                                                                                                 |    -  An IdP can have multiple identity conversion rules. If none of the rules apply to a federated user, the federated user is not allowed to access the cloud platform.                                                                                                                                                                                   |
         +-----------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

      For example, set an identity conversion rule for administrators in the enterprise management system.

      -  Username: **FederationUser-IdP_admin**

      -  User group: **admin**

      -  Rule condition: **\_NAMEID\_** (attribute), **any_one_of** (condition), and **000000001** (value).

         Only the user with ID 000000001 is mapped to IAM user **FederationUser-IdP_admin** and inherits permissions from the **admin** user group.

   #. In the **Create Rule** dialog box, click **OK**.

   #. On the **Modify Identity Provider** page, click **OK**.

-  **Editing Rules**

   #. Log in to the IAM console as the administrator. In the navigation pane, choose **Identity Providers**.

   #. In the IdP list, click **Modify** in the row containing the IdP.

   #. In the **Identity Conversion Rules** area, click **Edit Rule**.

   #. Edit the identity conversion rules in JSON format. For details, see :ref:`Syntax of Identity Conversion Rules <en-us_topic_0079620340>`.

   #. Click **Validate** to verify the syntax of the rules.

   #. If the rule is correct, click **OK** in the **Edit Rule** dialog box, and click **OK** on the **Modify Identity Provider** page.

      If a message indicating that the JSON file is incomplete is displayed, modify the statements or click **Cancel** to cancel the modifications.

Related Operations
------------------

Viewing identity conversion rules: Click **View Rule** on the **Modify Identity Provider** page. The identity conversion rules are displayed in JSON format. For details about the JSON format, see :ref:`Syntax of Identity Conversion Rules <en-us_topic_0079620340>`.
