:original_name: iam_08_0021.html

.. _iam_08_0021:

Overview of Virtual User SSO via SAML
=====================================

The cloud platform supports identity federation with Security Assertion Markup Language (SAML), which is an open standard that many identity providers (IdPs) use. During identity federation, the cloud platform functions as a service provider (SP) and enterprises function as IdPs. This section describes how to configure identity federation and how identity federation works.

.. caution::

   Ensure that your enterprise IdP supports SAML 2.0.

Configuring Identity Federation
-------------------------------

The following describes how to configure your enterprise IdP and the cloud platform to trust each other.


.. figure:: /_static/images/en-us_image_0000001655985477.png
   :alt: **Figure 1** Configuration of virtual user SSO via SAML

   **Figure 1** Configuration of virtual user SSO via SAML

#. :ref:`Create an IdP entity and establish a trust relationship <iam_08_0003>`: Create an IdP entity for your enterprise on the cloud platform. Then, upload the cloud platform metadata file to the enterprise IdP, and upload the metadata file of the enterprise IdP to the cloud platform.


   .. figure:: /_static/images/en-us_image_0000001607193154.png
      :alt: **Figure 2** Exchanging metadata files

      **Figure 2** Exchanging metadata files

#. :ref:`Configure the enterprise IdP <iam_08_0252>`: Configure enterprise IdP parameters to determine what information can be sent to the cloud platform.

#. :ref:`Configure identity conversion rules <iam_08_0004>`: Configure identity conversion rules to determine the IdP user identities and permissions on the cloud platform.


   .. figure:: /_static/images/en-us_image_0000001606753690.png
      :alt: **Figure 3** Mapping external identities to virtual users

      **Figure 3** Mapping external identities to virtual users

#. :ref:`Verify the federated login <iam_08_0025>`: Check whether the enterprise user can log in to the cloud platform through SSO.

#. :ref:`(Optional) Configure a login link <iam_08_0005>`: Configure a login link (see :ref:`Figure 4 <iam_08_0021__en-us_topic_0177310146_fig183392056164512>`) to allow enterprise users to be redirected to the cloud platform from your enterprise management system.

   .. _iam_08_0021__en-us_topic_0177310146_fig183392056164512:

   .. figure:: /_static/images/en-us_image_0000001655953453.png
      :alt: **Figure 4** SSO login model

      **Figure 4** SSO login model

How Identity Federation Works
-----------------------------

:ref:`Figure 5 <iam_08_0021__en-us_topic_0177310146_fig286918566460>` shows the identity federation process between an enterprise management system and the cloud platform.

.. _iam_08_0021__en-us_topic_0177310146_fig286918566460:

.. figure:: /_static/images/en-us_image_0000001656273117.png
   :alt: **Figure 5** How identity federation works

   **Figure 5** How identity federation works

.. note::

   To view interactive requests and assertions with a better experience, you are advised to use Google Chrome and install SAML Message Decoder.

As shown in :ref:`Figure 5 <iam_08_0021__en-us_topic_0177310146_fig286918566460>`, the process of identity federation is as follows:

#. A user opens the login link generated after the IdP creation in the browser. The browser sends an SSO request to the cloud platform.
#. The cloud platform authenticates the user against the metadata file of the enterprise IdP and constructs a SAML request to the browser.
#. The browser forwards the SAML request to the enterprise IdP.
#. The user enters their username and password on the login page. After the enterprise IdP authenticates the user's identity, it constructs a SAML assertion containing the user details and sends the assertion to the browser as a SAML response.
#. The browser responds and forwards the SAML response to the cloud platform.
#. The cloud platform parses the assertion in the SAML response, identifies the IAM user group mapping to the user based on the identity conversion rules, and issues a token to the user.
#. The user logs in to the cloud platform through SSO.

   .. note::

      The assertion must carry a signature; otherwise, the login will fail.
