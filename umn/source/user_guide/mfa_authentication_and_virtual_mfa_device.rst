:original_name: iam_10_0002.html

.. _iam_10_0002:

MFA Authentication and Virtual MFA Device
=========================================

What Is MFA Authentication?
---------------------------

MFA authentication provides an additional layer of protection on top of the username and password. If you enable MFA authentication, users need to enter the username and password as well as a verification code before they can perform operations.

MFA authentication can be enabled to verify a user's identity before the user is allowed to log in to the console.

MFA Authentication Methods
--------------------------

MFA authentication can be performed through SMS, email, and virtual MFA device.

.. _iam_10_0002__section0864223164311:

What Is a Virtual MFA Device?
-----------------------------

An MFA device generates 6-digit verification codes in compliance with the Time-based One-time Password Algorithm (TOTP) standard. MFA devices can be hardware- or software-based. Currently, software-based virtual MFA devices are supported. They are application programs running on smart devices such as mobile phones.

Application Scenarios
---------------------

MFA authentication verifies your identity during login. When you or an IAM user logs in to the console, you and the user need to enter a verification code in addition to the username and password.
