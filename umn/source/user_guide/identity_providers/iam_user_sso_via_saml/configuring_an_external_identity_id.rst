:original_name: iam_08_0257.html

.. _iam_08_0257:

Configuring an External Identity ID
===================================

For the IAM user SSO type, you must configure an external identity ID for the IAM user which the federated user maps to on the cloud platform. The external identity ID must be the same as the **IAM_SAML_Attributes_xUserId** value of the enterprise IdP user (federated user). You can create an IAM user and configure an external identity ID for it, or change the external identity ID of an existing IAM user.

-  :ref:`Creating an IAM User and Configuring an External Identity ID <iam_08_0257__en-us_topic_0000001646272761_en-us_topic_0000001378359130_section193611361710>`
-  :ref:`Changing the External Identity ID of an Existing IAM User <iam_08_0257__en-us_topic_0000001646272761_en-us_topic_0000001378359130_section1633315112717>`

.. _iam_08_0257__en-us_topic_0000001646272761_en-us_topic_0000001378359130_section193611361710:

Creating an IAM User and Configuring an External Identity ID
------------------------------------------------------------

#. Log in to the as the administrator.

#. On the IAM console, choose **Users** from the navigation pane, and click **Create User** in the upper right corner.

#. In the **User Details** area, configure an external identity ID. For details about other settings, see :ref:`Creating a User <en-us_topic_0046611303>`.


   .. figure:: /_static/images/en-us_image_0000001606781944.png
      :alt: **Figure 1** Configuring an external identity ID

      **Figure 1** Configuring an external identity ID

.. _iam_08_0257__en-us_topic_0000001646272761_en-us_topic_0000001378359130_section1633315112717:

Changing the External Identity ID of an Existing IAM User
---------------------------------------------------------

In the IAM user list, click a username or choose **More** > **Security Settings** in the row containing the user and change the external identity ID.


.. figure:: /_static/images/en-us_image_0000001606942104.png
   :alt: **Figure 2** Changing the external identity ID of an existing IAM user

   **Figure 2** Changing the external identity ID of an existing IAM user
