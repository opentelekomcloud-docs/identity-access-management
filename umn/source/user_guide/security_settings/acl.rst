:original_name: iam_07_0003.html

.. _iam_07_0003:

ACL
===

The **ACL** tab of the :ref:`Security Settings <iam_07_0001__en-us_topic_0179264308_en-us_topic_0179263545_section113256158575>` page provides the :ref:`IP Address Ranges <iam_07_0003__en-us_topic_0177717042_en-us_topic_0176803440_section1659055844011>`, :ref:`CIDR Blocks <iam_07_0003__en-us_topic_0177717042_en-us_topic_0176803440_section5282253478>`, and :ref:`VPC Endpoints <iam_07_0003__en-us_topic_0177717042_en-us_topic_0176803440_section148601027258>` settings for allowing user access only from specified IP address ranges, CIDR blocks, or VPC endpoints.

Only the administrator or an entrusted identity can configure the ACL to control access of all IAM users under the account from specific IP address ranges, CIDR blocks, or VPC endpoints.

**Access type:**

-  **Console Access** (recommended): The ACL takes effect only for IAM users who are created using your account and have access to the console.
-  **API Access**: The ACL controls users' API access through API Gateway and takes effect only for your account and IAM users under your account 15 minutes after you complete the configuration.

.. note::

   -  You can configure a maximum of 200 access control items.
   -  Both IPv4 and IPv6 addresses can be used for console access, and only IPv4 addresses can be used for API access.

.. _iam_07_0003__en-us_topic_0177717042_en-us_topic_0176803440_section1659055844011:

IP Address Ranges
-----------------

You can specify the IP address range from 0.0.0.0 to 255.255.255.255 to control access to the cloud platform. The default setting is 0.0.0.0-255.255.255.255. If you do not specify a range or use the default range, your IAM users can access the cloud platform from IP addresses.

.. _iam_07_0003__en-us_topic_0177717042_en-us_topic_0176803440_section5282253478:

CIDR Blocks
-----------

Specify CIDR blocks to control access to the cloud platform. For example, set **CIDR Block** to **10.10.10.10/32**.

.. _iam_07_0003__en-us_topic_0177717042_en-us_topic_0176803440_section148601027258:

VPC Endpoints
-------------

Specify access to the cloud platform APIs only from the VPC Endpoint with the specified ID, for example, **0ccad098-b8f4-495a-9b10-613e2a5exxxx**. You can set the VPC endpoint only on the **API Access** tab. If access control is not configured, you can access APIs from all VPC endpoints by default.


.. figure:: /_static/images/en-us_image_0000001925383938.png
   :alt: **Figure 1** VPC endpoints

   **Figure 1** VPC endpoints

.. note::

   -  User access is allowed if any of **IP Address Ranges**, **CIDR Blocks**, and **VPC Endpoints** is met.
   -  To restore **IP Address Ranges** to the default settings (0.0.0.0-255.255.255.255) and clear the settings in **CIDR Blocks** and **VPC Endpoints**, click **Restore Defaults**.
