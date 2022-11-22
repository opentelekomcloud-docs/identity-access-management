:original_name: en-us_topic_0046613147.html

.. _en-us_topic_0046613147:

Creating an Agency (by a Delegating Party)
==========================================

By creating an agency, you can share your resources with another account or a cloud service (such as ECS), or delegate an individual or team to manage your resources. You do not need to share your security credentials (the password and access keys) with the delegated party. Instead, the delegated party can log in with its own account credentials and then switches the role to your account and manage your resources.

Procedure
---------

#. In the navigation pane, choose **Agencies**.

#. On the **Agencies** page, click **Create Agency**.

#. Specify the agency name and type.

   .. table:: **Table 1** Agency types

      +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Agency Type   | Description                                                                                                                                                                        |
      +===============+====================================================================================================================================================================================+
      | Account       | Share resources with another account or delegate an individual or team to manage your resources.                                                                                   |
      +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cloud service | Delegate a specific service to access or maintain your data. For example, you can create an agency to delegate ECS to call data maintenance or monitoring APIs with an access key. |
      +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   -  If you set **Agency Type** to **Account**, enter the domain name of an account to which you want to delegate resource access in **Delegated Account**.
   -  If you set **Agency Type** to **Cloud service**, click **Select** and select a cloud service.

#. Set the validity period and enter a description about the agency.

#. In the **Permissions** area, click **Assign Permissions** above the permission list. Then attach policies to the agency and click **OK**.

   .. note::

      For details about the permissions for all cloud services, see `Permissions <https://docs.otc.t-systems.com/en-us/permissions/index.html>`__.

#. Click **OK**.

   The agency is displayed in the agency list. The delegated account can manage resources in your account by switching the role.

Follow-up Operation
-------------------

-  In the agency list, click **Modify** in the row that contains the target agency to change the agency type, delegated account, validity period, description, and permissions.
-  In the agency list, click **Delete** to delete the agency.

.. note::

   Cloud service agencies cannot be modified.
