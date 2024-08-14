:original_name: iam_01_0063.html

.. _iam_01_0063:

(Optional) Assigning Permissions to an IAM User (by a Delegated Party)
======================================================================

When a trust relationship is established between your account and another account, you become a delegated party. By default, only your account and the members of the **admin** group can manage resources for the delegating party. To authorize IAM users to manage these resources, assign permissions to the users.

You can authorize an IAM user to manage resources for all delegating parties, or authorize the user to manage resources for a specific delegating party.

Prerequisites
-------------

-  A trust relationship has been established between your account and another account.
-  You have obtained the name of the delegating account and the name and ID of the created agency.

Procedure
---------

#. .. _iam_01_0063__en-us_topic_0170090700_li135311310144613:

   Create a user group and grant permissions to it.

   a. On the **User Groups** page, click **Create User Group**.

   b. Enter a user group name.

   c. Click **OK**.

   d. In the row containing the user group, click **Authorize**.

   e. Create a custom policy.

      .. note::

         This step is used to create a policy containing permissions required to manage resources for a specific agency. If you want to authorize an IAM user to manage resources for all agencies, go to :ref:`1.f <iam_01_0063__en-us_topic_0170090700_li027318403345>`.

      #. On the **Select Policy/Role** page, click **Create Policy** in the upper right corner of the permission list.

      #. Enter a policy name.

      #. Select **JSON** for **Policy View**.

      #. In the **Policy Content** area, enter the following content:

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
            -  For more information about permissions, see :ref:`Permissions <iam_01_0015>`.

      #. Click **Next**.

   f. .. _iam_01_0063__en-us_topic_0170090700_li027318403345:

      Select the policy created in the previous step or the **Agent Operator** role and click **Next**.

      -  Custom policy: Allows a user to manage resources only for an agency identified by a specific ID.
      -  **Agent Operator** role: Allows a user to manage resources for all agencies.

   g. Specify the authorization scope.

   h. Click **OK**.

#. .. _iam_01_0063__en-us_topic_0170090700_li695863494610:

   Create an IAM user and add the user to the user group.

   a. On the **Users** page, click **Create User**.
   b. On the **Create User** page, enter a username.
   c. Select **Management console access** for **Access Type** and then select **Set by user** for **Credential Type**.
   d. Enable login protection and click **Next**.
   e. Select the user group created in :ref:`1 <iam_01_0063__en-us_topic_0170090700_li135311310144613>` and click **Create**.

      .. note::

         After the authorization is complete, the IAM user can switch to the account of the delegating party and manage specific resources under the account.

Related Operations
------------------

The delegated account or the authorized IAM users can :ref:`switch their roles <en-us_topic_0046613148>` to the delegating account to view and use its resources.
