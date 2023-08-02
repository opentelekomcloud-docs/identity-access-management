:original_name: en-us_topic_0046611269.html

.. _en-us_topic_0046611269:

Creating a User Group and Assigning Permissions
===============================================

You can plan user groups based on user responsibilities and grant the required permissions to the user groups. Users inherit permissions from the user groups to which they belong.

Procedure
---------

#. In the navigation pane, choose **User Groups**.

#. On the **User Groups** page, click **Create User Group**.

#. Enter a user group name.

#. (Optional) Enter a description for the user group.

   .. note::

      To enable users to directly view their permissions, set a description for the user group. For example, if you assign the **Security Administrator** role to a user group, you can set any description in the **Description** text box. For example: **Security Administrator: Permissions for creating, deleting, and modifying users as well as granting permissions to users.** For details about the permissions for all cloud services, see `Permissions <https://docs.otc.t-systems.com/additional/permissions.html>`__.

#. Click **OK**.

   The user group is displayed in the user group list.

#. In the row containing the user group, click **Authorize** in the **Operation** column.

#. On the **Authorize User Group** page, select the permissions to be assigned to the user group. You can also click **Go to Old Edition** to use the old version for authorization.

   If the system-defined policies do not meet your requirements, you can click **Create Policy** in the upper right to create custom policies for fine-grained permissions control. For details, see :ref:`Creating a Custom Policy <iam_01_0016>`.


   .. figure:: /_static/images/en-us_image_0000001656493417.png
      :alt: **Figure 1** Selecting permissions

      **Figure 1** Selecting permissions

#. Click **Next**.

#. Specify the scope. The system automatically recommends an authorization scope for the permissions you selected. :ref:`Table 1 <en-us_topic_0046611269__table13959113218281>` describes all the authorization scopes provided by IAM.

   .. _en-us_topic_0046611269__table13959113218281:

   .. table:: **Table 1** Authorization scopes

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scope                             | Description                                                                                                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================================================================================================+
      | All resources                     | IAM users can use the resources in all region-specific projects and the global services in your account based on the assigned permissions.                                                                                                                                              |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Region-specific projects          | IAM users can use the resources in the region-specific projects you select based on the assigned permissions.                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                         |
      |                                   | If some of the selected permissions belong to global services, the system automatically sets the authorization scope of these permissions to **All resources**. Selected permissions for project-level services will apply to the region-specific projects you select.                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Global services                   | IAM users can use global services based on the assigned permissions. Global services are deployed with no physical regions specified. IAM users do not need to specify a region when accessing these services, such as Object Storage Service (OBS) and Content Delivery Network (CDN). |
      |                                   |                                                                                                                                                                                                                                                                                         |
      |                                   | If some of the selected permissions belong to project-level services, the system automatically sets the authorization scope of these permissions to **All resources**. Selected permissions for global services will apply to the global services.                                      |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.
