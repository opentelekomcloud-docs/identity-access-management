:original_name: en-us_topic_0079620341.html

.. _en-us_topic_0079620341:

Introduction
============

The cloud platform provides identity federation based on Security Assertion Markup Language (SAML) or OpenID Connect. This function allows users in your enterprise management system to access the cloud platform through single sign-on (SSO).

Basic Concepts
--------------

.. table:: **Table 1** Basic concepts

   +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Concept                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   +=========================+====================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | Identity provider (IdP) | An IdP collects and stores user identity information, such as usernames and passwords, and authenticates users during login. For identity federation between an enterprise and the cloud platform, the identity authentication system of the enterprise is an identity provider and is also called "enterprise IdP". Popular third-party IdPs include Microsoft Active Directory Federation Services (AD FS) and Shibboleth.                                                                                                                                                                                                                                                                       |
   +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Service provider (SP)   | A service provider establishes a trust relationship with an IdP and provides services based on the user information provided by the IdP. For identity federation between an enterprise and the cloud platform, the cloud platform is a service provider.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
   +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Identity federation     | Identity federation is the process of establishing a trust relationship between an IdP and SP to implement SSO.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Single sign-on (SSO)    | SSO allows users to access a trusted SP after logging in to the enterprise IdP. For example, after a trust relationship is established between an enterprise management system and the cloud platform, users in the enterprise management system can use their existing accounts and passwords to access the cloud platform through the login link in the enterprise management system. The cloud platform supports two SSO types: virtual user SSO and IAM user SSO.                                                                                                                                                                                                                              |
   +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | SAML 2.0                | SAML 2.0 is an XML-based protocol that uses security tokens containing assertions to pass information about an end user between an IdP and an SP. It is an open standard ratified by the Organization for the Advancement of Structured Information Standards (OASIS) and is being used by many IdPs. For more information about this standard, see `SAML 2.0 Technical Overview <https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0.html>`__. The cloud platform implements identity federation in compliance with SAML 2.0. To successfully federate your enterprise users with the cloud platform, ensure that your enterprise IdP is compatible with this protocol. |
   +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OpenID Connect          | OpenID Connect is a simple identity layer on top of the Open Authorization 2.0 (OAuth 2.0) protocol. IAM implements identity federation in compliance with OpenID Connect 1.0. To successfully federate your enterprise users with the cloud platform, ensure that your enterprise IdP is compatible with this protocol.                                                                                                                                                                                                                                                                                                                                                                           |
   +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OAuth 2.0               | OAuth 2.0 is an open authorization protocol. The authorization framework of this protocol allows third-party applications to obtain access permissions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   +-------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Advantages of Identity Federation
---------------------------------

-  Easy identity management

   With an identity provider, the administrator can manage workforce identities outside of the cloud platform and give these external workforce identities permissions to use resources on the cloud platform.

-  Simplified operations

   Workforce users can use their existing accounts in the enterprise to access the cloud platform through SSO.


   .. figure:: /_static/images/en-us_image_0000001117174928.png
      :alt: **Figure 1** Advantages of identity federation

      **Figure 1** Advantages of identity federation

SSO Type
--------

IAM supports two SSO types: virtual user SSO and IAM user SSO. For details about how to choose an SSO type, see :ref:`Application Scenarios of Virtual User SSO and IAM User SSO <iam_08_0251>`.

-  Virtual user SSO

   After a federated user logs in to the cloud platform, the system automatically creates a virtual user and grants access permissions to the virtual user based on the configured identity conversion rules.

-  IAM user SSO

   After a federated user logs in to the cloud platform, the system automatically maps the :ref:`external identity ID <en-us_topic_0046661675__li13713193419317>` to an IAM user so that the federated user has the permissions of the mapped IAM user.

Currently, IAM supports two federated login methods: browser-based SSO (web SSO) and SSO via API calling.

-  Web SSO: Browsers are used as the communication media. This authentication type enables common users to access the cloud platform using browsers.
-  SSO via API calling: Enterprise employees call APIs using development tools (such as OpenStack Client and ShibbolethECP Client) to access the cloud platform.

.. table:: **Table 2** Federated logins

   +--------------+-----------------------------+-----------+-------------+---------------+--------------+---------------+
   | SSO Type     | Supported Protocols         | Web SSO   | API Calling | IdP-initiated | SP-initiated | Multiple IdPs |
   +==============+=============================+===========+=============+===============+==============+===============+
   | Virtual user | SAML 2.0 and OpenID Connect | Supported | Supported   | Supported     | Supported    | Supported     |
   +--------------+-----------------------------+-----------+-------------+---------------+--------------+---------------+
   | IAM user     | SAML 2.0                    | Supported | Supported   | Supported     | Supported    | Not supported |
   +--------------+-----------------------------+-----------+-------------+---------------+--------------+---------------+

Precautions
-----------

-  Ensure that your enterprise IdP server and the cloud platform use Greenwich Mean Time (GMT) time in the same time zone.
-  The identity information (such as email address or mobile number) of federated users is stored in the enterprise IdP. Federated users are mapped to the cloud platform as virtual identities, so their access to the cloud platform has the following restrictions:

   -  Federated users do not need to perform a 2-step verification when performing critical operations even though :ref:`critical operation protection <iam_01_0029>` (login protection or operation protection) is enabled.

   -  Federated users cannot create access keys with unlimited validity, but they can obtain temporary access credentials (access keys and security tokens) using user or agency tokens.

      If a federated user needs an access key with unlimited validity, they can contact the account administrator or an IAM user to create one. An access key contains the permissions granted to a user, so it is recommended that the federated user request an IAM user in the same group to create an access key.
