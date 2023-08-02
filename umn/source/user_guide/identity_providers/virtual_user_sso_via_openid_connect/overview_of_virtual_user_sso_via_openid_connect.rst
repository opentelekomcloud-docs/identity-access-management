:original_name: iam_08_0010.html

.. _iam_08_0010:

Overview of Virtual User SSO via OpenID Connect
===============================================

This section describes how to configure identity federation and how identity federation works.

Configuring Identity Federation
-------------------------------

The following describes how to configure your enterprise IdP and the cloud platform to trust each other.

#. :ref:`Create an IdP entity and establish a trust relationship <iam_08_0009>`: Create OAuth 2.0 credentials in the enterprise IdP. In the cloud platform, create an IdP entity and establish a trust relationship between the two systems.
#. :ref:`Configure identity conversion rules <iam_08_0008>`: Configure identity conversion rules in the cloud platform to the users, user groups, and permissions in the enterprise IdP to the cloud platform.
#. :ref:`Configure a login link <iam_08_0007>`: Configure a login link to allow enterprise users to be redirected to the cloud platform from your enterprise management system.

How Identity Federation Works
-----------------------------

:ref:`Figure 1 <iam_08_0010__en-us_topic_0272442730_fig185551935854>` shows the identity federation process between an enterprise management system and the cloud platform.

.. _iam_08_0010__en-us_topic_0272442730_fig185551935854:

.. figure:: /_static/images/en-us_image_0000001656576929.png
   :alt: **Figure 1** How identity federation works

   **Figure 1** How identity federation works

The process of identity federation is as follows:

#. A user opens the login link obtained from the IAM console in the browser. The browser sends an SSO request to the cloud platform.
#. The cloud platform authenticates the user against the configuration of the enterprise IdP and constructs an OpenID Connect request to the browser.
#. The browser forwards the OpenID Connect request to the enterprise IdP.
#. The user enters their username and password on the login page displayed in the enterprise IdP. After the enterprise IdP authenticates the user's identity, it constructs an ID token containing the user information, and sends the ID token to the browser as an OpenID Connect authorization response.
#. The browser responds and forwards the OpenID Connect response to the cloud platform.
#. The cloud platform parses the ID token in the OpenID Connect response, identifies the IAM user group mapping to the user based on the identity conversion rules, and issues a token to the user.
#. The user logs in to the cloud platform through SSO.
