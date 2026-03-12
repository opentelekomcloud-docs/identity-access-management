:original_name: en-us_topic_0046661675.html

.. _en-us_topic_0046661675:

Viewing and Modifying User Information
======================================

You can click the user to view user details. The administrator can change the user status, access method, description, external identity ID, and groups to which the user belongs.

If the job responsibilities of a user are changed, you can change the permissions assigned for that user by changing the groups which the user belongs to. You can also change the virtual MFA device and access keys of the user by choosing **More** > **Security Settings** in the row containing the target user. If a user forgot their password or access keys, you can modify the login credentials of the user.

As an administrator, you can modify the basic information about an IAM user, change the security settings of the user and the groups to which the user belongs, and view or delete the assigned permissions. To view or modify user information, click **Security Settings** in the row containing the IAM user.

To adjust the item columns displayed on the list, click |image1|. The **Username** and **Operation** columns are displayed by default, and the **Status** column cannot be removed. Optional columns include: User ID, **External Identity ID**, **Description**, **Last Login**, **Created**, **Access Type**, **MFA Type**, **Password Age**, and **Access Key (Status, Age, and AK)**.

.. _en-us_topic_0046661675__section1916211354916:

Basic Information
-----------------

You can modify the basic information of IAM users, but cannot modify the basic information of your account. The username, user ID, and creation time can be viewed but cannot be modified.

-  **Status**: New IAM users are enabled by default. You can set **Status** to **Disabled** to disable an IAM user. A disabled user is no longer able to log in to the cloud platform through the management console or programmatic access.

-  **Access Type**: You can change the access type of the IAM user.

   .. note::

      -  Pay attention to the following when you set the access type for an IAM user:

         -  If you intend to enable the user to access cloud services only by using the management console, select **Management console access**.
         -  If you intend to enable the user to access cloud services only by using programmatic access, select **Programmatic access**.
         -  If the user needs to use a password as the credential for programmatic access to certain APIs, select **Programmatic access**.
         -  If the user needs to perform access key verification when using certain services in the console, select both **Programmatic access** and **Management console access**.

      -  If the access type of the user is **Programmatic access** or both **Programmatic access** and **Management console access**, deselecting **Programmatic access** will restrict the user's access to cloud services. Exercise caution when performing this operation.

-  **Description**: You can modify the description of the IAM user.

-  .. _en-us_topic_0046661675__li13713193419317:

   **External Identity ID**: Identifies an enterprise user in federated login using SSO.

User Groups
-----------

An IAM user inherits permissions from the groups to which the user belongs. You can change the permissions assigned for an IAM user by changing the groups to which the user belongs. To modify the permissions of a user group, see :ref:`Viewing and Modifying User Group Information <en-us_topic_0085605493>`.

Your account belongs to the default group **admin**, which cannot be changed.

-  Click **Add to User Group**, and select one or more groups to which the user will belong. The user then inherits permissions of these groups.
-  Click **Remove** on the right of a user group and click **Yes**. The user no longer has the permissions assigned to the group.

.. |image1| image:: /_static/images/en-us_image_0000001524684833.png
