:original_name: en-us_topic_0079620340.html

.. _en-us_topic_0079620340:

Syntax of Identity Conversion Rules
===================================

An identity conversion rule is a JSON object which can be modified. The following is an example JSON object:

.. code-block::

   [
           {
               "remote": [
                   {
                      "<condition>"
                   }
                ],
               "local": [
                   {
                     "<user> or <group> or <groups>"
                   }
                ]
             }
          ]

-  **remote**: Information about a federated user in the identity provider system. This field is an expression consisting of assertion attributes and operators. The value of this field is determined by the assertion.
-  **condition**: Conditions for the identity conversion rule to take effect. The following three conditions are supported:

   -  **empty**: The rule is matched to all claims containing the attribute type. This condition does not need to be specified.
   -  **any_one_of**: The rule is matched only if any of the specified strings appear in the attribute type. The condition result is Boolean, not the argument that is passed as input.
   -  **not_any_of**: The rule is not matched if any of the specified strings appear in the attribute type. The condition result is Boolean, not the argument that is passed as input.

-  **local**: Identity information about a federated user mapped to the cloud system. The value of this field can contain placeholders, such as **{0...n}**. The attributes **{0}** and **{1}** represent the first and second remote attributes of the user information, respectively.

Examples of Identity Conversion Rule Conditions
-----------------------------------------------

The following examples illustrate how to use the **empty**, **any_one_of**, and **not_any_of** conditions in an identity conversion rule.

-  The **empty** condition returns character strings to replace the local attributes **{0..n}**.

   .. code-block::

      [
              {
                  "local": [
                      {
                          "user": {
                              "name": "{0} {1}"
                          }
                      },
                      {
                          "group": {
                              "name": "{2}"
                          }
                      }
                  ],
                  "remote": [
                      {
                          "type": "FirstName"
                      },
                      {
                          "type": "LastName"
                      },
                      {
                          "type": "Group"
                      }
                  ]
              }
          ]

   In this example, the username of a federated user will be "the value of the first remote attribute+space+the value of the second remote attribute" in the cloud system, that is, *FirstName LastName*. The group to which the user belongs is the value of the third remote attribute *Group*. This attribute has only one value.

   If the following assertion (simplified for easy understanding) is received, the username of the federated user will be **John Smith** in the cloud system and the user will only belong to the **admin** group.

   .. code-block::

      {FirstName: John}
      {LastName: Smith}
      {Groups: admin}

   If a federated user will belong to multiple user groups in the cloud system, the identity conversion rule can be configured as follows:

   .. code-block::

      [
              {
                  "local": [
                      {
                          "user": {
                              "name": "{0} {1}"
                          }
                      },
                      {
                          "groups":  "{2}"
                      }
                  ],
                  "remote": [
                      {
                          "type": "FirstName"
                      },
                      {
                          "type": "LastName"
                      },
                      {
                          "type": "Groups"
                      }
                  ]
              }
          ]

   In this example, the username of a federated user will be "the value of the first remote attribute+space+the value of the second remote attribute" in the cloud system, that is, *FirstName LastName*. The groups to which the user belongs are the value of the third remote attribute *Groups*.

   If the following assertion is received, the username of the federated user will be **John Smith** in the cloud system and the user will belong to the **admin** and **manager** groups.

   .. code-block::

      {FirstName: John}
      {LastName: Smith}
      {Groups: [admin, manager]}

-  Unlike the **empty** condition, the **any one of** and **not any of** conditions return Boolean values. These values will not be used to replace the local attributes. In the following example, only **{0}** will be replaced by the returned value of the first **empty** condition in the **remote** block. The value of **group** is fixed as **admin**.

   .. code-block::

      [
              {
                  "local": [
                      {
                          "user": {
                              "name": "{0}"
                          }
                      },
                      {
                          "group": {
                              "name": "admin"
                          }
                      }
                  ],
                  "remote": [
                      {
                      "type": "UserName"
                      },
                      {
                          "type": "Groups",
                          "any_one_of": [
                              "idp_admin"
                          ]
                      }
                  ]
              }
          ]

   The username of the federated user in the cloud system is the value of the first remote attribute, that is, *UserName*. The federated user belongs to the **admin** group. This rule takes effect only for users who are members of the **idp_admin** group in the identity provider system.

   If a federated user will belong to multiple user groups in the cloud system, the identity conversion rule can be configured as follows:

   .. code-block::

      [
              {
                  "local": [
                      {
                          "user": {
                              "name": "{0}"
                          }
                      },
                      {
                          "groups": "[\"admin\",\"manager\"]"
                      }
                  ],
                  "remote": [
                      {
                      "type": "UserName"
                      },
                      {
                          "type": "Groups",
                          "any_one_of": [
                              "idp_admin"
                          ]
                      }
                  ]
              }
          ]

   The username of the federated user in the cloud system is the value of the first remote attribute, that is, *UserName*. The federated user belongs to the **admin** and **manager** groups. This rule takes effect only for users who are members of the **idp_admin** group in the identity provider system.

   -  The following assertion indicates that the federated user John Smith is a member of the **idp_admin** group. Therefore, the user can access the cloud system.

      .. code-block::

         {UserName: John Smith}
         {Groups: [idp_user, idp_admin, idp_agency]}

   -  The following assertion indicates that the federated user John Smith is not a member of the **idp_admin** group. Therefore, the rule does not take effect for the user and the user cannot access the cloud system.

      .. code-block::

         {UserName: John Smith}
         {Groups: [idp_user, idp_agency]}

-  Example condition containing a regular expression: You can add **"regex": true** to a condition to calculate results using a regular expression.

   .. code-block::

      [
              {
                  "local": [
                      {
                          "user": {
                              "name": "{0}"
                          }
                      },
                      {
                          "group": {
                              "name": "admin"
                          }
                      }
                  ],
                  "remote": [
                      {
                      "type": "UserName"
                      },
                      {
                          "type": "Groups",
                          "any_one_of": [
                              ".*@mail.com$"
                          ],
                          "regex": true
                      }
                  ]
              }
          ]

   This rule takes effect for any user whose username ends with **@mail.com**. The username of each applicable federated user is *UserName* in the cloud system and the user belongs to the **admin** group.

-  Examples of combined conditions: Multiple conditions can be combined using the logical operator AND.

   .. code-block::

      [
              {
                  "local": [
                      {
                          "user": {
                              "name": "{0}"
                          }
                      },
                      {
                          "group": {
                              "name": "admin"
                          }
                      }
                  ],
                  "remote": [
                      {
                      "type": "UserName"
                      },
                      {
                          "type": "Groups",
                          "not_any_of": [
                              "idp_user"
                          ]
                      },
                      {
                          "type": "Groups",
                          "not_any_of": [
                              "idp_agent"
                          ]
                      }
                  ]
              }
          ]

   This rule takes effect only for the federated users who do not belong to the **idp_user** or **idp_agent** user group in the identity provider system. The username of each applicable federated user is *UserName* in the cloud system and the user belongs to the **admin** group. The preceding rule is equivalent to the following:

   .. code-block::

      [
              {
                  "local": [
                      {
                          "user": {
                              "name": "{0}"
                          }
                      },
                      {
                          "group": {
                              "name": "admin"
                          }
                      }
                  ],
                  "remote": [
                      {
                      "type": "UserName"
                      },
                      {
                          "type": "Groups",
                          "not_any_of": [
                              "idp_user",
                              "idp_agent"
                          ]
                      }
                  ]
              }
          ]

-  Examples of combined rules

   If multiple rules are combined, the methods for matching usernames and user groups are different.

   The name of a federated user will be the username matched in the first rule that takes effect, and the user will belong to all groups matched in all rules that take effect. A federated user can log in only if at least one rule takes effect to match the username.

   For easy understanding, username and user group rules can be configured separately.

   .. code-block::

      [
          {
              "local": [
                  {
                      "user": {
                          "name": "{0}"
                      }
                  }
              ],
              "remote": [
                  {
                      "type": "UserName"
                  }
              ]
          },
          {
              "local": [
                  {
                      "group": {
                          "name": "admin"
                      }
                  }
              ],
              "remote": [
                  {
                      "type": "Groups",
                      "any_one_of": [
                          "idp_admin"
                      ]
                  }
              ]
          }
      ]

   In this example, the rules take effect for users in the **idp_admin** group. The username of each applicable federated user is *UserName* in the cloud system and the user belongs to the **admin** group.

   The following assertion indicates that user John Smith is a member of the **idp_admin** group in the identity provider system and therefore meets the rules. The username of this user will be **John Smith** in the cloud system, and the user will belong to the **admin** group.

   .. code-block::

      {UserName: John Smith}
      {Groups: [idp_user, idp_admin, idp_agency]}
