:original_name: iam_08_0008.html

.. _iam_08_0008:

Step 2: Configure Identity Conversion Rules
===========================================

Federated users are named **FederationUser** by default in the cloud platform. These users can only log in to the cloud platform and they do not have any other permissions. You can configure identity conversion rules on the IAM console to achieve the following:

-  Display enterprise users with different names in the cloud platform.
-  Assign permissions to enterprise users to use the cloud platform resources by mapping these users to IAM user groups. Ensure that you have created the required user groups. For details, see :ref:`Creating a User Group and Assigning Permissions <en-us_topic_0046611269>`.

.. note::

   -  Modifications to identity conversion rules will take effect only after the federated users log in again.
   -  To modify the permissions of a user, modify the permissions of the user group to which the user belongs. Then restart the enterprise IdP for the modifications to take effect.

Prerequisites
-------------

An IdP entity has been created, and the login link of the IdP is accessible. (For details about how to create and verify an IdP entity, see :ref:`Step 1: Create an IdP Entity <iam_08_0009>`.)

Procedure
---------

If you configure identity conversion rules by clicking **Create Rule**, IAM converts the rule parameters to the JSON format. Alternatively, you can click **Edit Rule** to configure rules in JSON format. For details, see :ref:`Syntax of Identity Conversion Rules <en-us_topic_0079620340>`.

-  **Creating Rules**

   #. Log in to the IAM console as the administrator. In the navigation pane, choose **Identity Providers**.

   #. In the IdP list, click **Modify** in the row containing the IdP.

   #. In the **Identity Conversion Rules** area, click **Create Rule**. Then, configure the rules in the **Create Rule** dialog box.


      .. figure:: /_static/images/en-us_image_0289500726.png
         :alt: **Figure 1** Setting parameters

         **Figure 1** Setting parameters

      .. table:: **Table 1** Parameter description

         +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter             | Description                                                                                     | Remarks                                                                                                                                                                                                                                                  |
         +=======================+=================================================================================================+==========================================================================================================================================================================================================================================================+
         | Username              | Username of federated users in the cloud platform.                                              | To distinguish federated users from users in the cloud platform, it is recommended that you set the username to **FederationUser-**\ *IdP*\ **\_**\ *XXX*. *IdP* indicates an IdP name, for example, AD FS or Shibboleth. *XXX* indicates a custom name. |
         |                       |                                                                                                 |                                                                                                                                                                                                                                                          |
         |                       |                                                                                                 | .. important::                                                                                                                                                                                                                                           |
         |                       |                                                                                                 |                                                                                                                                                                                                                                                          |
         |                       |                                                                                                 |    NOTICE:                                                                                                                                                                                                                                               |
         |                       |                                                                                                 |                                                                                                                                                                                                                                                          |
         |                       |                                                                                                 |    -  The username of each federated user must be unique in the same IdP. Federated users with the same usernames in the same IdP will be mapped to the same IAM user in the cloud platform.                                                             |
         |                       |                                                                                                 |    -  The username can only contain letters, digits, spaces, hyphens (-), underscores (_), and periods (.). It cannot start with a digit and cannot contain the following special characters: ", \\", \\\\, \\n, \\r                                     |
         +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | User Groups           | User groups which the federated users belong to in the cloud platform.                          | The federated users will inherit permissions from their user groups. You can select a user group that has already been created.                                                                                                                          |
         +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Rule Conditions       | Conditions that a federated user must meet to obtain permissions from the selected user groups. | Federated users who do not meet these conditions cannot access the cloud platform. You can create a maximum of 10 conditions for an identity conversion rule.                                                                                            |
         |                       |                                                                                                 |                                                                                                                                                                                                                                                          |
         |                       |                                                                                                 | .. note::                                                                                                                                                                                                                                                |
         |                       |                                                                                                 |                                                                                                                                                                                                                                                          |
         |                       |                                                                                                 |    -  An identity conversion rule can have multiple conditions. It takes effect only if all of the conditions are met.                                                                                                                                   |
         |                       |                                                                                                 |    -  An IdP can have multiple identity conversion rules. If a federated user does not meet any of the conditions, the user will be denied to access the cloud platform.                                                                                 |
         +-----------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

Verifying Federated User Permissions
------------------------------------

After configuring identity conversion rules, verify the permissions of federated users.

#. Log in as a federated user.

   On the **Identity Providers** page of the IAM console, click **View** in the row containing the IdP. Click |image1| to copy the login link displayed in the **Basic Information** area, open the link using a browser, and then enter the username and password used in the enterprise management system.

#. Check that the federated user has the permissions assigned to their user group.

   For example, configure an identity conversion rule to map federated user **ID1** to the **admin** user group so that **ID1** will have full permissions for all cloud services. On the management console, select a cloud service, and check if you can access the service.

Related Operations
------------------

Viewing identity conversion rules: Click **View Rule** on the **Modify Identity Provider** page. The identity conversion rules are displayed in JSON format. For details about the JSON format, see :ref:`Syntax of Identity Conversion Rules <en-us_topic_0079620340>`.

.. |image1| image:: /_static/images/en-us_image_0000001646661553.png
