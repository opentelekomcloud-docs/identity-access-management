:original_name: en-us_topic_0046613147.html

.. _en-us_topic_0046613147:

Creating an Agency (by a Delegating Party)
==========================================

By creating an agency, you can share your resources with another account, or delegate an individual or team to manage your resources. You do not need to share your security credentials (the password and access keys) with the delegated party. Instead, the delegated party can log in with its own account credentials and then switches the role to your account and manage your resources.

Prerequisites
-------------

Before creating an agency, complete the following operations:

-  Understand the :ref:`basic concepts <en-us_topic_0046611276>` of permissions.
-  Determine the `permissions <https://docs.otc.t-systems.com/additional/permissions.html>`__ to be assigned to the agency, and check whether the permissions have dependencies. For more details, see :ref:`Assigning Dependency Roles <iam_01_0657>`.

Procedure
---------

#. Log in to the IAM console.

#. On the IAM console, choose **Agencies** from the navigation pane, and click **Create Agency** in the upper right corner.


   .. figure:: /_static/images/en-us_image_0000001511524692.png
      :alt: **Figure 1** Creating an agency

      **Figure 1** Creating an agency

#. Enter an agency name.


   .. figure:: /_static/images/en-us_image_0000001562564797.png
      :alt: **Figure 2** Setting the agency name

      **Figure 2** Setting the agency name

#. Specify the agency type as **Account**, and enter the name of a delegated account.

   .. note::

      -  **Account**: Share resources with another account or delegate an individual or team to manage your resources. The delegated account can only be an account, rather than an IAM user or a federated user.
      -  **Cloud service**: Delegate a specific service to access other services. For more information, see :ref:`Cloud Service Delegation <iam_06_0004>`.

#. Set the validity period and enter a description for the agency.

#. Click **Next**.

#. Select the policies or roles to be attached to the agency, click **Next**, and select the authorization scope.

   .. note::

      -  Assigning permissions to an agency is similar to assigning permissions to a user group. The two operations differ only in the number of available permissions. For details about how to assign permissions to a user group, see :ref:`Assigning Permissions to an IAM User <en-us_topic_0079496985>`.
      -  Agencies cannot be assigned the **Security Administrator** role. For account security, grant permissions required to agencies based on the principle of least privilege.

#. Click **OK**.

   .. note::

      After creating an agency, provide your domain name, agency name, agency ID, and agency permissions to the delegated party. The delegated party can then switch the role to your account and manage specific resources based on the assigned permissions.
