:original_name: en-us_topic_0046613148.html

.. _en-us_topic_0046613148:

Switching Roles (by a Delegated Party)
======================================

When an account establishes a trust relationship with your account, you become a delegated party. The IAM users that are granted agency permissions can switch to the delegating account and manage resources under the account based on the granted permissions.

Prerequisites
-------------

-  A trust relationship has been established between your account and another account.
-  You have obtained the delegating account name and agency name.

Procedure
---------

#. Log in to the management console using your account or log in as the IAM user created in :ref:`2 <iam_01_0063__en-us_topic_0170090700_li695863494610>`.

   .. note::

      The IAM user created in :ref:`2 <iam_01_0063__en-us_topic_0170090700_li695863494610>` can switch roles to manage resources for the delegating party.

#. Hover the mouse pointer over the username in the upper right corner and choose **Switch Role**.
#. On the **Switch Role** page, enter the domain name of the delegating party.

   .. note::

      After you enter the domain name, the agencies created under this account will be automatically displayed after you click the agency name text box. Select an authorized one from the drop-down list.

#. Click **OK** to switch to the delegating account.

Follow-Up Procedure
-------------------

To return to your own account, hover the mouse pointer over the username in the upper right corner, choose **Switch Role**, and select your account.
