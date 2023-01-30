:original_name: iam_08_0010.html

.. _iam_08_0010:

OpenID Connect-based Federated Identity Authentication
======================================================

This section describes the process and configuration of OpenID Connect-based federated identity authentication between an enterprise identity provider and the cloud system.

Configuring Federated Identity Authentication
---------------------------------------------

To implement federated identity authentication between an identity provider and the cloud system, complete the following configuration:

#. :ref:`Establish a trust relationship and create an identity provider <iam_08_0009>`: Create OAuth 2.0 credentials in the enterprise identity provider, and create an identity provider in the cloud system.
#. :ref:`Configure identity conversion rules <iam_08_0008>`: Map the users, user groups, and permissions in the identity provider to the cloud system.
#. :ref:`Configure a login link <iam_08_0007>`: Configure a login link in the enterprise management system to allow users to access the cloud system through SSO.

Process of Federated Identity Authentication
--------------------------------------------

:ref:`Figure 1 <iam_08_0010__fig1898444131619>` shows the interaction between an identity provider and the cloud system after a user initiates an SSO request.

.. _iam_08_0010__fig1898444131619:

.. figure:: /_static/images/en-us_image_0274187264.png
   :alt: **Figure 1** Process of federated identity authentication

   **Figure 1** Process of federated identity authentication

As shown in the preceding figure, the process of federated identity authentication is as follows:

#. A user uses a browser to open the login link obtained from IAM, and then the browser sends an SSO request to the cloud system.
#. The cloud system searches for identity provider configurations based on the login link, and sends an OpenID Connect authorization request to the browser.
#. The browser forwards the authorization request to the enterprise identity provider.
#. The user enters their username and password on the login page displayed in the identity provider system. After the identity provider authenticates the user's identity, it constructs an ID token containing the user information, and sends the ID token to the browser as an OpenID Connect authorization response.
#. The browser responds and forwards the authorization response to the cloud system.
#. The cloud system parses the ID token in the authorization response, and issues a token to the user after identifying the group the user is mapped to, according to the configured identity conversion rules.
#. If the login is successful, the user accesses the cloud system successfully.

-  :ref:`Step 1: Create an Identity Provider <iam_08_0009>`
-  :ref:`Step 2: Configure Identity Conversion Rules <iam_08_0008>`
-  :ref:`Step 3: Configure Login Link in the Enterprise Management System <iam_08_0007>`

.. toctree::
   :maxdepth: 1
   :hidden: 

   step_1_create_an_identity_provider
   step_2_configure_identity_conversion_rules
   step_3_configure_login_link_in_the_enterprise_management_system
