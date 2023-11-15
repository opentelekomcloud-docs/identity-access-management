:original_name: iam_01_0607.html

.. _iam_01_0607:

Password Policy
===============

The **Password Policy** tab of the :ref:`Security Settings <iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575>` page provides the :ref:`Password Composition & Reuse <iam_01_0607__en-us_topic_0177717041_en-us_topic_0176803439_section222481512916>`, :ref:`Password Expiration <iam_01_0607__en-us_topic_0177717041_en-us_topic_0176803439_section104571219917>`, and :ref:`Minimum Password Age <iam_01_0607__en-us_topic_0177717041_en-us_topic_0176803439_section86671628898>` settings.

Only the :ref:`administrator <iam_01_0023__section1475194083513>` can configure the password policy, and IAM users can only view the configurations. If an IAM user needs to modify the configurations, the user can request the administrator to perform the modification or grant the required permissions.

You can configure the password policy to ensure that IAM users create strong passwords and rotate them periodically. In the password policy, you can define password requirements, such as minimum password length, whether to allow consecutive identical characters in a password, and whether to allow previously used passwords.

.. _iam_01_0607__en-us_topic_0177717041_en-us_topic_0176803439_section222481512916:

Password Composition & Reuse
----------------------------

-  Ensure that the password contains 2 to 4 of the following character types: uppercase letters, lowercase letters, digits, and special characters. By default, the password must contain at least 2 of these character types.
-  Set the minimum number of characters that a password must contain. The default value is 6 and the value range is from 6 to 32.
-  (Optional) Enable the **Restrict consecutive identical characters** option and set the maximum number of times that a character is allowed to be consecutively present in a password. For example, value **1** indicates that consecutive identical characters are not allowed in a password.
-  (Optional) Enable the **Disallow previously used passwords** option and set the number of previously used passwords that are not allowed. For example, value **3** indicates that the user cannot set the last three passwords that the user has previously used when setting a new password.

Changes to the password policy take effect the next time you or your IAM users change passwords. IAM users created later will also adhere to the updated password policy.

.. _iam_01_0607__en-us_topic_0177717041_en-us_topic_0176803439_section104571219917:

Password Expiration
-------------------

Set a validity period for passwords so that users need to change their passwords periodically. The users will be prompted to change their passwords 15 days before password expiration. Expired passwords cannot be used to log in to the cloud platform.

This option is disabled by default. The validity period ranges from 1 to 180 days.

The changes will take effect immediately for your account and all IAM users under your account.

.. note::

   After the password expires, users need to set a new password through the URL sent by email. The new password must be different from the old password.

.. _iam_01_0607__en-us_topic_0177717041_en-us_topic_0176803439_section86671628898:

Minimum Password Age
--------------------

To prevent password loss due to frequent password changes, you can set a minimum period after which users are allowed to make a password change.

This option is disabled by default. If you enable this option, you can set a period from 0 to 1440 minutes.

The changes will take effect immediately for your account and all IAM users under your account.
