:original_name: en-us_topic_0046613148.html

.. _en-us_topic_0046613148:

Managing Delegated Resources
============================

When an account establishes a trust relationship with your account, you become a delegated party. The IAM users granted agency permissions can switch to the delegating domain name and manage resources under the account based on the granted permissions.

Prerequisites
-------------

-  A trust relationship has been established between another account and your account.
-  You have obtained the name of the delegating account and the agency name.

Procedure
---------

#. Log in to the management console using your account, or log in as the IAM user created in "Assigning Permissions to an IAM User (by a Delegated Party)".

   .. note::

      The IAM user created in "Assigning Permissions to an IAM User (by a Delegated Party)" has permission to manage agencies and switch roles.

#. Move the cursor to the username in the upper right corner and choose **Switch Role**.
#. On the **Switch Role** page, enter the domain name of the delegating party.

   .. note::

      After you enter the domain name, the agencies created under this account will be automatically displayed after you click the agency name text box. Select an authorized one from the drop-down list.

#. Click **OK** to switch to the delegating Domain name.

Follow-Up Procedure
-------------------

Move the cursor to the username in the upper right corner and choose **Switch Role**.
