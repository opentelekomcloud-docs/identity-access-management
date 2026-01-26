:original_name: iam_01_0016.html

.. _iam_01_0016:

Creating a Custom Policy
========================

You can create custom policies to supplement system-defined policies and implement more refined access control.

Creating a Custom Policy in the Visual Editor
---------------------------------------------

#. On the IAM console, choose **Policies** in the navigation pane, and click **Create Custom Policy**.
#. Enter a policy name.
#. Select **Visual editor**.
#. Set the policy content.

   a. Select **Allow** or **Deny**.
   b. Select a cloud service.

      .. note::

         Only one cloud service can be selected for each permission block. To configure permissions for multiple cloud services, click **Add Permissions** or switch to the JSON view.

   c. Select actions.
   d. Select all resources, or select specific resources by specifying their paths.
   e. (Optional) Add request conditions by specifying condition keys, operators, and values.

      .. table:: **Table 1** Condition parameters

         +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Name          | Description                                                                                                                                                                                                                                                                                                                                                            |
         +===============+========================================================================================================================================================================================================================================================================================================================================================================+
         | Condition Key | A key in the **Condition** element of a statement. There are global and service-specific condition keys. Global condition keys (starting with **g:**) are available for operations of all services, while service-specific condition keys (starting with a service abbreviation name such as **obs:**) are available only for operations of the corresponding service. |
         +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Operator      | Used together with a condition key to form a complete condition statement.                                                                                                                                                                                                                                                                                             |
         +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Value         | Used together with a condition key and an operator that requires a keyword, to form a complete condition statement.                                                                                                                                                                                                                                                    |
         +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. (Optional) Switch to the JSON view and modify the policy content in the JSON format.

   .. note::

      If the policy content is incorrect after modification, check and modify the content, or click **Reset** to cancel the modifications.

#. (Optional) To add another permission block for the policy, click **Add Permissions**. Alternatively, click the plus (+) icon on the right of an existing permission block to clone its permissions.
#. (Optional) Enter a brief description for the policy.
#. Click **OK**.
#. Attach the policy to a user group. Users in the group then inherit the permissions defined in the policy.

Creating a Custom Policy in JSON View
-------------------------------------

#. On the IAM console, choose **Policies** in the navigation pane, and click **Create Custom Policy**.
#. Enter a policy name.
#. Select **JSON**.
#. (Optional) Click **Select Existing Policy**, and select a policy to use it as a template, such as **VPC Admin**.
#. Click **OK**.
#. Modify the statement in the template.

   -  **Effect**: Set it to **Allow** or **Deny**.
   -  **Action**: Enter the actions provided in the API actions table of the EVS service, for example, **evs:volumes:create**.

      .. note::

         -  The version of each custom policy is fixed at **1.1**.

#. (Optional) Enter a brief description for the policy.
#. Click **OK**. If the policy list is displayed, the policy is created successfully.
#. Attach the policy to a user group. Users in the group then inherit the permissions defined in the policy.
