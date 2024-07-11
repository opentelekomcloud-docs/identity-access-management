:original_name: iam_02_0008.html

.. _iam_02_0008:

Making an API Request
=====================

This section describes the structure of a REST API request, and uses the IAM API for obtaining a user token (see :ref:`Obtaining a User Token <en-us_topic_0057845583>`) as an example to demonstrate how to call an API. The obtained token can then be used to authenticate the calling of other APIs.

Request URI
-----------

A request URI is in the following format:

**{URI-scheme} :// {Endpoint} / {resource-path} ? {query-string}**

.. table:: **Table 1** Parameter description

   +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Description                                                                                                                                                                                                                                                              |
   +===============+==========================================================================================================================================================================================================================================================================+
   | URI-scheme    | Protocol used to transmit requests. All APIs use HTTPS.                                                                                                                                                                                                                  |
   +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Endpoint      | Domain name or IP address of the server bearing the REST service. The endpoint varies between services in different regions.                                                                                                                                             |
   +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource-path | Access path of an API for performing a specified operation. Obtain the path from the URI of an API. For example, the **resource-path** of the API used to obtain a user token is **/v3/auth/tokens**.                                                                    |
   +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query-string  | Query parameter, which is optional. Ensure that a question mark (?) is included before each query parameter that is in the format of "*Parameter name*\ =\ *Parameter value*". For example, **?limit=10** indicates that a maximum of 10 data records will be displayed. |
   +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. code-block::


   https://www.example.com/v3/auth/tokens

.. note::

   To simplify the URI display in this document, each API is provided only with a **resource-path** and a request method. The **URI-scheme** of all APIs is **HTTPS**, and the endpoints of all APIs in the same region are identical.

Request Methods
---------------

The HTTP protocol defines the following request methods that can be used to send a request to the server:

-  **GET**: requests a server to return specified resources.
-  **PUT**: requests the server to update specified resources.
-  **POST**: requests the server to add resources or perform special operations.
-  **DELETE**: requests the server to delete specified resources, for example, an object.
-  **HEAD**: same as GET except that the server must return only the response header.
-  **PATCH**: requests the server to update partial content of a specified resource. If the resource does not exist, a new resource will be created.

For example, in the case of the API used to obtain a user token (:ref:`Obtaining a User Token <en-us_topic_0057845583>`), the request method is POST. The request is as follows:

.. code-block::


   POST https://www.example.com/v3/auth/tokens

Request Header
--------------

You can also add additional header fields to a request, such as the fields required by a specified URI or HTTP method. For example, to request for the authentication information, add **Content-Type**, which specifies the request body type.

Common request header fields are as follows:

-  **Content-Type**: specifies the request body type or format. This field is mandatory and its default value is **application/json**.
-  **X-Auth-Token**: specifies a user token only for token-based API authentication. **X-Auth-Token** is a response to the API used to obtain a user token (:ref:`Obtaining a User Token <en-us_topic_0057845583>`). This API is the only one that does not require authentication.

   .. note::

      In addition to supporting token-based authentication, APIs also support authentication using access key ID/secret access key (AK/SK). During AK/SK-based authentication, an SDK is used to sign the request, and the **Authorization** (signature information) and **X-Sdk-Date** (time when the request is sent) header fields are automatically added to the request.

      For details, see "AK/SK-based Authentication" in :ref:`Authentication <iam_02_0510>`.

The API used to obtain a user token (:ref:`Obtaining a User Token <en-us_topic_0057845583>`) does not require authentication. Only the **Content-Type** field needs to be added to requests for calling the API. An example of such requests is as follows:

.. code-block::


   POST https://www.example.com/v3/auth/tokens
   Content-Type: application/json

(Optional) Request Body
-----------------------

The body of a request is often sent in a structured format as specified in the **Content-Type** header field. The request body transfers content except the request header.

The request body varies between APIs. Some APIs do not require the request body, such as the APIs requested using the GET and DELETE methods.

In the case of the API used to obtain a user token (:ref:`Obtaining a User Token <en-us_topic_0057845583>`), the request parameters and parameter description can be obtained from the API request. The following provides an example request with a body included. Replace *username*, *domainname*, ``********`` (login password), and *xxxxxxxxxxxxxxxxxx* (project ID) with the actual values. If you obtain a token using an account, ensure that you set *username* and *domainname* to the same value.

.. note::

   The **scope** parameter specifies where a token takes effect. You can set **scope** to an account or a project under the account. In the following example, the token takes effect only for the resources in a specified project. For more information about this API, see :ref:`Obtaining a User Token <en-us_topic_0057845583>`.

.. code-block::


   POST https://www.example.com/v3/auth/tokens
   Content-Type: application/json

   {
       "auth": {
           "identity": {
               "methods": [
                   "password"
               ],
               "password": {
                   "user": {
                       "name": "username",
                       "password": "********",
                       "domain": {
                           "name": "domainname"
                       }
                   }
               }
           },
           "scope": {
               "project": {
                   "id": "xxxxxxxxxxxxxxxxxx"
               }
           }
       }
   }

If all data required for the API request is available, you can send the request to call the API through `curl <https://curl.haxx.se/>`__, `Postman <https://www.getpostman.com/>`__, or coding. In the response to the API used to obtain a user token (:ref:`Obtaining a User Token <en-us_topic_0057845583>`), **x-subject-token** is the desired user token. This token can then be used to authenticate the calling of other APIs.
