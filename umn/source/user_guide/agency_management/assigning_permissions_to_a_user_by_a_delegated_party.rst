:original_name: iam_01_0063.html

.. _iam_01_0063:

Assigning Permissions to a User (by a Delegated Party)
======================================================

When a trust relationship is established between another account and your account, you become a delegated party and you can authorize a user to manage resources for the delegating party. If another account has created multiple agencies for you, you can authorize one or more users through custom policies to manage resources specified in all or specific agencies. Each user can only switch to the agency for which the user has been granted permissions.

Prerequisites
-------------

-  A trust relationship has been established between another account and your account.
-  You have obtained the name of the delegating account and the name and ID of the created agency.

Procedure
---------

#. .. _iam_01_0063__li4527132844312:

   Create a custom policy.

   .. note::

      This step is used to create a policy containing permissions required to manage resources for a specific agency. If you want to authorize a user to manage resources for all agencies, go to :ref:`2 <iam_01_0063__li135311310144613>`.

   a. In the navigation pane, choose **Policies**.

   b. On the **Policies** page, click **Create Custom Policy**.

   c. Enter a policy name.

   d. Select **Global services** for **Scope**.

   e. Select **JSON**.

   f. In the **Policy Content** area, enter the following content:

      .. code-block::

         {
                 "Version": "1.1",
                 "Statement": [
                         {
                                 "Action": [
                                         "iam:agencies:assume"
                                 ],
                                 "Resource": {
                                         "uri": [
                                                 "/iam/agencies/b36b1258b5dc41a4aa8255508xxx..."
                                         ]
                                 },
                                 "Effect": "Allow"
                         }
                 ]
         }

      .. note::

         -  Replace *b36b1258b5dc41a4aa8255508xxx...* with the agency ID obtained from a delegating party. Do not make any other changes.
         -  For more information about fine-grained policies, see :ref:`Fine-Grained Policy Management <iam_01_0015>`.

   g. Click **OK**.

#. .. _iam_01_0063__li135311310144613:

   Create a user group and grant permissions to it.

   a. In the navigation pane, choose **User Groups**.

   b. On the **User Groups** page, click **Create User Group**.

   c. Enter a user group name.

   d. Click **OK**.

      The user group is displayed in the user group list.

   e. Click **Manage Permissions** in the **Operation** column of the row that contains the created user group.

   f. On the **Permissions** tab page, click **Assign Permissions** above the permission list.

   g. Specify the authorization scope. If you select **Region-specific projects**, select one or more projects in the drop-down list.

      -  **Global service project**: Services deployed without specifying physical regions are called global services, such as OBS, CDN, and TMS. Permissions for these services must be assigned in the global service project.
      -  **Region-specific projects**: Services deployed in specific regions are called project-level services. Permissions for these services need to be assigned in region-specific projects and take effect only for the corresponding regions. If you want the permissions to take effect for all regions, grant them in all these regions.

   h. Select the policy created in :ref:`1 <iam_01_0063__li4527132844312>` or the **Agent Operator** role, and click **OK**. The authorization is completed.

#. .. _iam_01_0063__li695863494610:

   Create a user and add the user to the user group.

   a. In the navigation pane, choose **Users**.
   b. On the **Users** page, click **Create User**.
   c. Specify the user information, select an access type, and click **Next**.
   d. In the **Available User Groups** area, select the user group created in :ref:`2 <iam_01_0063__li135311310144613>`.
   e. Click **Create**.

Follow-up Operation
-------------------

Point to the delegating account in the upper right corner of the page and choose **Switch Role** to switch back to your account.
