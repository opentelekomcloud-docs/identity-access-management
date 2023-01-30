:original_name: iam_08_0002.html

.. _iam_08_0002:

SAML-based Federated Identity Authentication
============================================

This section describes the process and configuration of SAML-based federated identity authentication between an enterprise identity provider and the cloud system.

.. caution::

   -  To implement federated identity authentication, ensure that your identity provider server and the cloud system use the same Universal Time Coordinated (UTC) time.
   -  Ensure that your identity provider system supports SAML 2.0.

Configuring Federated Identity Authentication
---------------------------------------------

To implement federated identity authentication between an identity provider and the cloud system, complete the following configuration:

#. :ref:`Establish a trust relationship and create an identity provider <iam_08_0003>`: Exchange the metadata files of the identity provider and cloud system (see :ref:`Figure 1 <iam_08_0002__fig7241863151635>`).

   .. _iam_08_0002__fig7241863151635:

   .. figure:: /_static/images/en-us_image_0274187197.png
      :alt: **Figure 1** Metadata file exchange model

      **Figure 1** Metadata file exchange model

#. :ref:`Configure identity conversion rules <iam_08_0004>`: Map the users, user groups, and permissions of the identity provider to the cloud system (see :ref:`Figure 2 <iam_08_0002__fig43579668151728>`).

   .. _iam_08_0002__fig43579668151728:

   .. figure:: /_static/images/en-us_image_0274187171.png
      :alt: **Figure 2** User identity conversion model

      **Figure 2** User identity conversion model

#. :ref:`Configure a login link <iam_08_0005>`: Configure a login link (see :ref:`Figure 3 <iam_08_0002__fig54574848151714>`) in the enterprise management system to allow users to access the cloud system through SSO.

   .. _iam_08_0002__fig54574848151714:

   .. figure:: /_static/images/en-us_image_0274187167.png
      :alt: **Figure 3** SSO login model

      **Figure 3** SSO login model

Process of Federated Identity Authentication
--------------------------------------------

:ref:`Figure 4 <iam_08_0002__fig3771174215915>` shows the interaction between an identity provider and the cloud system after a user initiates an SSO request.

.. _iam_08_0002__fig3771174215915:

.. figure:: /_static/images/en-us_image_0274187226.png
   :alt: **Figure 4** Process of federated identity authentication

   **Figure 4** Process of federated identity authentication

.. note::

   To view interactive requests and assertions with a better experience, you are advised to use the Google Chrome browser and install the SAML Message Decoder plug-in.

As shown in :ref:`Figure 4 <iam_08_0002__fig3771174215915>`, the process of federated identity authentication is as follows:

#. A user uses a browser to open the login link obtained from IAM, and then the browser sends an SSO request to the cloud system.
#. The cloud system searches for a metadata file based on the login link, and sends a SAML request to the browser.
#. The browser forwards the SAML request to the enterprise identity provider.
#. The user enters their username and password displayed in the identity provider system. After the identity provider authenticates the user's identity, it constructs a SAML assertion containing the user information, and sends the assertion to the browser as a SAML response.
#. The browser responds and forwards the SAML response to the cloud system.
#. The cloud system parses the assertion in the SAML response, and issues a token to the user after identifying the group to which the user is mapped, according to the configured identity conversion rules.
#. If the login is successful, the user accesses the cloud system successfully.

   .. note::

      The assertion must carry a signature; otherwise, the login will fail.

-  :ref:`Step 1: Create an Identity Provider <iam_08_0003>`
-  :ref:`Step 2: Configure Identity Conversion Rules <iam_08_0004>`
-  :ref:`Step 3: Configure Login Link in the Enterprise Management System <iam_08_0005>`

.. toctree::
   :maxdepth: 1
   :hidden: 

   step_1_create_an_identity_provider
   step_2_configure_identity_conversion_rules
   step_3_configure_login_link_in_the_enterprise_management_system
