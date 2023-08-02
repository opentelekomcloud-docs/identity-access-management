:original_name: iam_08_0251.html

.. _iam_08_0251:

Application Scenarios of Virtual User SSO and IAM User SSO
==========================================================

IAM supports two SSO types: virtual user SSO and IAM user SSO. This section describes the two SSO types and their differences, helping you to choose an appropriate type for your business.

Virtual User SSO
----------------

After a federated user logs in to the cloud platform, the system automatically creates a virtual user and assigns permissions to the user based on identity conversion rules. Virtual user SSO is recommended if:

-  To reduce management costs, you do not want to create and manage IAM users on the cloud platform.
-  You want to separate permissions on the cloud platform based on the user groups or attributes in your local enterprise IdP. Permission changes in the local enterprise IdP can be synchronized to the cloud platform by adjusting the user groups or attributes locally.
-  Your enterprise has branches and each branch has multiple enterprise IdPs. These IdPs need to access the same cloud account. You need to configure multiple IdPs in the cloud platform for identity federation.

IAM User SSO
------------

After a federated user logs in to the cloud platform, the system automatically maps the external identity ID to an IAM user so that the federated user has the permissions of the mapped IAM user. IAM user SSO is recommended if:

-  Your cloud products do not support virtual user SSO.
-  You do not need virtual user SSO and want to simplify the IdP configuration.

Differences Between Virtual User SSO and IAM User SSO
-----------------------------------------------------

They differences between virtual user SSO and IAM user SSO are described as follows:

1. Identity conversion mode: Virtual user SSO uses :ref:`identity conversion rules <en-us_topic_0079620340>` to convert the identities of IdP users and IAM users. IAM user SSO uses the external identity ID for identity conversion. The **IAM_SAML_Attributes_xUserId** value of the IdP user is the same as the :ref:`external identity ID <en-us_topic_0046661675__li13713193419317>` of the IAM user. The IdP user is mapped to the corresponding IAM user. When you use IAM user SSO, make sure that you have set **IAM_SAML_Attributes_xUserId** in the IdP and **External Identity ID** in the SP to the same value.

2. User identity in IAM: In virtual user SSO, the IdP user does not have a corresponding IAM user in the IAM user list. After the IdP user logs in, the system automatically creates a virtual user for it. In IAM user SSO, the IdP user has a IAM user mapped by external identity ID on the IAM console.

3. Permissions assignment in IAM: In virtual user SSO, the permissions of the IdP user are defined by the identity conversion rule. In IAM user SSO, the IdP user inherits the permissions of the user group which the mapped IAM user belongs to.
