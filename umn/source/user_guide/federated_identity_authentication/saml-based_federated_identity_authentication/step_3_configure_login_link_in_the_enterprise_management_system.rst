:original_name: iam_08_0005.html

.. _iam_08_0005:

Step 3: Configure Login Link in the Enterprise Management System
================================================================

Configure the login link of the identity provider in the enterprise management system so that enterprise users can use this link to access the cloud system.

Prerequisites
-------------

-  An identity provider has been created in the cloud system, and the login link of the identity provider is accessible. (For details about how to create and verify an identity provider, see :ref:`Step 1: Create an Identity Provider <iam_08_0003>`.)
-  A login link to the cloud system has already been configured in the enterprise management system.

Procedure
---------

#. Log in to the IAM console, and choose **Identity Providers** from the navigation pane.

#. Click **View** in the row containing the identity provider.

#. Click **Copy** next to the login link.

#. Add the following statement to the page file of the enterprise management system:

   .. code-block::

      <a href="<Login link>"> Login </a>

#. Log in to the enterprise management system, and then click the configured login link to access the cloud system.
