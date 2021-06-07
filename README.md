# Zendesk Bootstrapper Templates

Browse here for all the available templates or build you own templates!

## 1. How to use Zendesk Bootstrapper

1. On Zendesk Slack workspace, _direct message_ `@Bootstrapper`
2. Type `help` and follow through the instructions

Thats it! Its _beautifully simple_, just like Zendesk.

## 2. Don't see the Bootstrapper Template that fit your needs? Create one !

1. Browse under the folder `master-template` which contains the entire feature set that Zendesk Bootstrapper supports
2. Analyze the JSON structure
3. Formulate your own template!
4. Contact `@lechan` on Slack to get your template published for everyone to use

PS: It supports _ALL_ values of the Zendesk APIs (you could refer to https://developer.zendesk.com/rest_api/docs/support/introduction for more details). So you could use values that you don't see within the `master-template` within each functionality.

### 2.1 Features List

**You can use any supported request payload that is within Zendesk's API reference specs!**

| Category        | Sub Category      | Functionality                    | API Reference (You can use any supported request payload from Zendesk !)                                                                       |
| --------------- | ----------------- | -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Settings        | Account Settings  | -                                | https://developer.zendesk.com/rest_api/docs/support/account_settings                                                                           |
| Settings        | Security Settings | -                                | Private API                                                                                                                                    |
| Settings        | Support Settings  | Update Default Support Email     | [Bootstrapper's unique Functionality]                                                                                                          |
| Settings        | Support Settings  | Add Recipient Addresses          | https://developer.zendesk.com/rest_api/docs/support/support_addresses#create-support-address                                                   |
| Ticket Views    | -                 | Add Ticket Views                 | https://developer.zendesk.com/rest_api/docs/support/views#create-view                                                                          |
| Users           | -                 | Add User Fields                  | https://developer.zendesk.com/rest_api/docs/support/user_fields#create-user-fields                                                             |
| Users           | -                 | Add Users                        | https://developer.zendesk.com/rest_api/docs/support/users#create-user                                                                          |
| Users           | -                 | Add Groups                       | https://developer.zendesk.com/rest_api/docs/support/groups#create-group                                                                        |
| Users           | -                 | Add Group Memberships            | https://developer.zendesk.com/rest_api/docs/support/group_memberships#create-membership                                                        |
| Users           | -                 | Add Organizations                | https://developer.zendesk.com/rest_api/docs/support/organizations#create-organization                                                          |
| Users           | -                 | Add Organization Fields          | https://developer.zendesk.com/rest_api/docs/support/organization_fields#create-organization-fields                                             |
| Business Rules  | -                 | Add SLAs                         | https://developer.zendesk.com/rest_api/docs/support/sla_policies#create-sla-policy                                                             |
| Business Rules  | -                 | Add Triggers                     | https://developer.zendesk.com/rest_api/docs/support/triggers#create-trigger                                                                    |
| Business Rules  | -                 | Add Automations                  | https://developer.zendesk.com/rest_api/docs/support/automations#create-automation                                                              |
| Macros          | -                 | Add Macros                       | https://developer.zendesk.com/rest_api/docs/support/macros#create-macro                                                                        |
| Macros          | -                 | Disable Default Macros           | [Bootstrapper's unique Functionality] Disables: 1. Close and redirect to topics 2. Customer not responding 3. Downgrade and inform 4. Take it! |
| Apps            | -                 | Add Apps (Only Marketplace Apps) | https://developer.zendesk.com/rest_api/docs/support/apps#create-app                                                                            |
| Tickets         | -                 | Generate Tickets                 | [Bootstrapper's unique Functionality] https://developer.zendesk.com/rest_api/docs/support/tickets#create-ticket                                |
| Tickets         | -                 | Add Ticket Fields                | https://developer.zendesk.com/rest_api/docs/support/ticket_fields#create-ticket-field                                                          |
| Tickets         | -                 | Add Ticket Forms                 | https://developer.zendesk.com/rest_api/docs/support/ticket_forms#create-ticket-forms                                                           |
| Dynamic Content | -                 | Add Dynamic Content Items        | https://developer.zendesk.com/rest_api/docs/support/dynamic_content#create-item                                                                |
| Talk            | -                 | Add Number                       | [Bootstrapper's unique Functionality]                                                                                                          |
| Talk            | -                 | Add Talk Agents                  | [Bootstrapper's unique Functionality]                                                                                                          |
| Talk            | -                 | Add IVRs                         | https://developer.zendesk.com/rest_api/docs/voice-api/ivrs#create-ivr                                                                          |
| Guide           | -                 | Activate Guide                   | [Bootstrapper's unique Functionality] Value has to be "{{bootstrapper-guide-default-brand-id}}"                                                |
| Guide           | -                 | Publish Theme                    | [Bootstrapper's unique Functionality] Set theme as live                                                                                        |
| Guide           | -                 | Import Themes                    | Value will be based on a repository of themes that Bootstrapper has. Contact Leroy Chan to add your own HC theme.                              |
| Guide           | -                 | Add Categories                   | https://developer.zendesk.com/rest_api/docs/help_center/categories#create-category                                                             |
| Guide           | -                 | Add Sections                     | https://developer.zendesk.com/rest_api/docs/help_center/sections#create-section                                                                |
| Guide           | -                 | Add Articles                     | https://developer.zendesk.com/rest_api/docs/help_center/articles#create-article                                                                |
| Sunshine        | -                 | Add Custom Object Types          | https://developer.zendesk.com/rest_api/docs/sunshine/resource_types#create-object-type                                                         |
| Sunshine        | -                 | Add Relationship Types           | https://developer.zendesk.com/rest_api/docs/sunshine/relationship_types#create-relationship-type                                               |
| Sunshine        | -                 | Add Custom Object Records        | https://developer.zendesk.com/rest_api/docs/sunshine/resources#create-object-record                                                            |
| Sunshine        | -                 | Add Relationship Records         | https://developer.zendesk.com/rest_api/docs/sunshine/relationships#create-relationship-record                                                  |
| Sunshine        | -                 | Add Profiles                     | https://developer.zendesk.com/rest_api/docs/sunshine/profiles_api#create-or-update-profile-by-identifier                                       |
| Sunshine        | -                 | Add Events                       | https://developer.zendesk.com/rest_api/docs/sunshine/events_api#track-event-against-a-sunshine-profile                                         |

### 2.2 Default Variables

You could use the following variables anywhere within your template code and it will automatically reference the values that you declare within the `bootstrap` object.

1.  `{{customer}}`
2.  `{{customer_name}}`
3.  `{{customer_locale}}`
4.  `{{bootstrapper-default-ticket-field-priority}}`: Return default system ticket field - Priority's ID
5.  `{{bootstrapper-default-ticket-field-tickettype}}`: Return default system ticket field - Ticket Type's ID
6.  `{{bootstrapper-default-ticket-field-subject}}`: Return default system ticket field - Subject's ID
7.  `{{bootstrapper-default-ticket-field-description}}`: Return default system ticket field - Description's ID
8.  `{{bootstrapper-default-ticket-field-status}}`: Return default system ticket field - Status's ID
9.  `{{bootstrapper-default-ticket-field-group}}`: Return default system ticket field - Group's ID
10. `{{bootstrapper-default-ticket-field-assignee}}`: Return default system ticket field - Assignee's ID
11. `{{bootstrapper-default-group-support}}`: Return default Agent's group (Support)'s ID
12. `{{bootstrapper-default-brand}}`: Return default brand's ID

For Guide's Categories, Sections and Articles, there is a special key-value pair that is called `bootstrapper_delay` that allows you to insert delay (in milliseconds) to individual objects in order to prevent database collission error that is returned by Guide's API.

### 2.3 Dependencies

Zendesk Bootstrapper helps you to resolve dependencies automatically with your templates

1.  Provide an **unique** `reference_id` on those objects that you wish to reference later on
2.  On those that objects that requires the ID or Key to be translated from `reference_id` before it can be created, use the `{{the-unique-value-that-you-provided-in-the-reference-id}}`

#### 2.3.1 Currently Supported

`reference_id`

1.  [Support] Add Users
2.  [Support] Add Groups
3.  [Support] Add Organizations
4.  [Support] Add User Fields
5.  [Support] Add Organization Fields
6.  [Support] Add Ticket Fields
7.  [Support] Add Ticket Forms
8.  [Support] Add Targets
9.  [Sunshine] Add Custom Object Types
10. [Sunshine] Add Custom Object Records
11. [Sunshine] Add Relationship Types
12. [Sunshine] Add Relationship Records
13. [Sunshine] Add Profiles
14. [Guide] Import Themes
15. [Guide] Add Sections
16. [Guide] Add Articles

`{{reference_id_value}}`

1.  [Support] Add Organizations
2.  [Support] Add Ticket Views
3.  [Support] Add SLAs
4.  [Support] Add Ticket Forms
5.  [Support] Add Triggers
6.  [Support] Add Automations
7.  [Support] Add Macros
8.  [Support] Add Group Memberships
9.  [Sunshine] Add Custom Object Records
10. [Sunshine] Add Relationship Types
11. [Sunshine] Add Relationship Records
12. [Sunshine] Add Events
13. [Guide] Publish Theme
14. [Guide] Import Themes
15. [Guide] Add Categories
16. [Guide] Add Sections
17. [Guide] Add Articles

#### Example 1: Create 2 Views that Reference 2 Groups, the sample payload will be:

    {
      "bootstrap": {
          "subdomain": "z3n-leroychan",
          "auth": {
              "username": "lechan@zendesk.com",
              "password": "XXXXX"
          },
          "customer": {
              "name": "Kaws",
              "locale": "en"
          }
      },
      "users": {
          "add_groups": [
              {
                  "name": "Tier 1 Support",
                  "reference_id": "group-tier1-support-id"
              },
              {
                  "name": "Tier 2 Support",
                  "reference_id": "group-tier2-support-id"
              }
          ]
      },
      "ticket_views": {
          "add_ticket_views": {
              "views": [
                  {
                      "title": "Bootstrapper - Depend on Group Tier 1",
                      "active": true,
                      "output": {
                          "group_by": "status",
                          "group_order": "desc",
                          "sort_by": "nice_id",
                          "sort_order": "desc",
                          "columns": [
                              "satisfaction_score",
                              "subject",
                              "requester",
                              "created",
                              "assignee"
                          ]
                      },
                      "all": [
                          {
                              "field": "status",
                              "operator": "less_than",
                              "value": "solved"
                          },
                          {
                              "field": "group_id",
                              "operator": "is",
                              "value": "{{group-tier1-support-id}}"
                          }
                      ]
                  },
                  {
                      "title": "Bootstrapper - Depend on Group Tier 2",
                      "active": true,
                      "output": {
                          "group_by": "status",
                          "group_order": "desc",
                          "sort_by": "nice_id",
                          "sort_order": "desc",
                          "columns": [
                              "satisfaction_score",
                              "subject",
                              "requester",
                              "created",
                              "assignee"
                          ]
                      },
                      "all": [
                          {
                              "field": "status",
                              "operator": "less_than",
                              "value": "solved"
                          },
                          {
                              "field": "group_id",
                              "operator": "is",
                              "value": "{{group-tier2-support-id}}"
                          }
                      ]
                  }
              ]
          }
      }
    }

#### Example 2: Create 1 SLA that references Custom User Field and Custom Organization Field, the sample payload will be:

    {
      "bootstrap": {
          "subdomain": "z3n-leroychan",
          "auth": {
              "username": "lechan@zendesk.com",
              "password": "XXXXX"
          },
          "customer": {
              "name": "Kaws",
              "locale": "en"
          }
      },
      "users": {
        "add_user_fields": [
            {
                "title": "Custom User Field 1",
                "type": "checkbox",
                "key": "custom_user_field_1",
                "reference_id": "userfield-1"
            }
        ],
        "add_organization_fields": [
            {
                "title": "Custom Org Field 1",
                "type": "checkbox",
                "key": "custom_org_field_1",
                "reference_id": "orgfield-1"
            }
        ]
      },
      "business_rules": {
        "add_slas": [
            {
                "title": "Bootstrapper - Dependency SLA",
                "description": "For VIP request, we will respond to tickets in 10 minutes",
                "position": 2,
                "filter": {
                    "all": [
                        {
                            "field": "requester.custom_fields.{{userfield-1}}",
                            "operator": "is",
                            "value": "true"
                        },
                        {
                            "field": "organization.custom_fields.{{orgfield-1}}",
                            "operator": "is",
                            "value": "true"
                        }
                    ],
                    "any": []
                },
                "policy_metrics": [
                    {
                        "priority": "normal",
                        "metric": "first_reply_time",
                        "target": 30,
                        "business_hours": false
                    },
                    {
                        "priority": "urgent",
                        "metric": "first_reply_time",
                        "target": 10,
                        "business_hours": false
                    },
                    {
                        "priority": "low",
                        "metric": "requester_wait_time",
                        "target": 180,
                        "business_hours": false
                    },
                    {
                        "priority": "normal",
                        "metric": "requester_wait_time",
                        "target": 160,
                        "business_hours": false
                    },
                    {
                        "priority": "high",
                        "metric": "requester_wait_time",
                        "target": 140,
                        "business_hours": false
                    },
                    {
                        "priority": "urgent",
                        "metric": "requester_wait_time",
                        "target": 120,
                        "business_hours": false
                    }
                ]
            }
        ]
      }
    }

#### Example 3: Create 1 Ticket Form that references 2 Ticket Fields, the sample payload will be:

    {
      "bootstrap": {
          "subdomain": "z3n-leroychan",
          "auth": {
              "username": "lechan@zendesk.com",
              "password": "XXXXX"
          },
          "customer": {
              "name": "Kaws",
              "locale": "en"
          }
      },
      "tickets": {
        "add_ticket_fields": [
            {
                "type": "text",
                "title": "Age",
                "reference_id": "ticket-field-age"
            },
            {
                "type": "text",
                "title": "Device",
                "reference_id": "ticket-field-device"
            }
        ],
        "add_ticket_forms": [
            {
                "name": "Test Bootstrapper Form",
                "end_user_visible": true,
                "active": true,
                "in_all_brands": true,
                "position": 9999,
                "ticket_field_ids": [
                    "{{ticket-field-age}}",
                    "{{ticket-field-device}}"
                ]
            }
        ]
      }
    }

#### Example 4: Create 1 Trigger that depends on a Ticket Form that depends on Ticket Fields [Nested Dependency]

    {
      "bootstrap": {
          "subdomain": "z3n-leroychan",
          "auth": {
              "username": "lechan@zendesk.com",
              "password": "XXXXX"
          },
          "customer": {
              "name": "Kaws",
              "locale": "en"
          }
      },
      "business_rules": {
        "add_triggers": [
            {
                "title": "Test Bootstrapper Trigger",
                "all": [
                    {
                        "field": "ticket_form_id",
                        "operator": "is",
                        "value": "{{form-test-bootstrapper}}"
                    }
                ],
                "actions": [
                  {
                    "field": "status",
                    "value": "solved"
                  }
                ]
            }
        ]
      },
      "tickets": {
          "add_ticket_fields": [
              {
                  "type": "text",
                  "title": "Age",
                  "reference_id": "ticket-field-age"
              },
              {
                  "type": "text",
                  "title": "Device",
                  "reference_id": "ticket-field-device"
              }
          ],
          "add_ticket_forms": [
              {
                  "name": "Test Bootstrapper Form",
                  "end_user_visible": true,
                  "active": true,
                  "in_all_brands": true,
                  "position": 9999,
                  "ticket_field_ids": [
                      "{{ticket-field-age}}",
                      "{{ticket-field-device}}"
                  ],
                  "reference_id": "form-test-bootstrapper"
              }
          ]
      }
    }

#### Example 5: Create 1 Macro that depends on a Ticket Field (Dropdown)

    {
      "bootstrap": {
          "subdomain": "z3n-leroychan",
          "auth": {
              "username": "lechan@zendesk.com",
              "password": "XXXXX"
          },
          "customer": {
              "name": "Kaws",
              "locale": "en"
          }
      },
      "macros": {
        "add_macros": [
            {
                "title": "Test Macro 2",
                "actions": [
                    {
                        "field": "status",
                        "value": "solved"
                    },
                    {
                        "field": "custom_fields_{{piesmacro1}}",
                        "value": "pecanmacro1"
                    }
                ]
            }
        ]
      },
      "tickets": {
        "add_ticket_fields": [
            {
                "type": "tagger",
                "title": "Pies macro 1",
                "custom_field_options": [
                    {
                        "name": "Apple Pie",
                        "value": "applemacro1"
                    },
                    {
                        "name": "Pecan Pie",
                        "value": "pecanmacro1"
                    }
                ],
                "reference_id": "piesmacro1"
            }
        ],
        "add_ticket_forms": [
            {
                "name": "Dropdow Macro 1",
                "end_user_visible": true,
                "active": true,
                "in_all_brands": true,
                "position": 9999,
                "ticket_field_ids": [
                    "{{piesmacro1}}"
                ]
            }
        ]
      }
    }

#### Example 5: Create Agents, Groups and Adding Agents to a Group

    {
      "bootstrap": {
          "subdomain": "z3n-leroychan",
          "auth": {
              "username": "lechan@zendesk.com",
              "password": "XXXXX"
          },
          "customer": {
              "name": "Kaws",
              "locale": "en"
          }
      },
      "users": {
        "add_users": [
            {
                "name": "Test Agent 7",
                "email": "testagent7@zendesk.com",
                "role": "agent",
                "reference_id": "user-agent-7"
            },
            {
                "name": "Test Agent 8",
                "email": "testagent8@zendesk.com",
                "role": "agent",
                "reference_id": "user-agent-8"
            }
        ],
        "add_groups": [
            {
                "name": "Test Group 7",
                "reference_id": "group-test-7"
            },
            {
                "name": "Test Group 8",
                "reference_id": "group-test-8"
            }
        ],
        "add_group_memberships": [
            {
                "user_id": "{{user-agent-7}}",
                "group_id": "{{group-test-7}}"
            },
            {
                "user_id": "{{user-agent-8}}",
                "group_id": "{{group-test-8}}"
            }
        ]
      }
    }

### 2.4 Example Bootstrapper Templates

The following examples will give you a better idea how to structure a Bootstrapper template. You can easily mix and match and/or combine different examples to achieve your intended usecases.

#### 2.4.1 Support - Add Private Apps - Configurable Customer 360 App

Note: `app-name` must be one of the following values: `configurable-customer-360-v1`, `related-objects-with-settings-v1`
If you would like your private apps to be included in Bootstrapper, please contact #ask-bootstrapper

    {
      "bootstrap": {
          "subdomain": "z3n-leroychan",
          "auth": {
              "username": "lechan@zendesk.com",
              "password": "XXXXX"
          },
          "customer": {
              "name": "Kaws",
              "locale": "en"
          }
      },
      "apps": {
        "add_private_apps": [
          {
            "app_name": "configurable-customer-360-v1",
            "name": "Customer 360",
            "short_description": "Configurable Customer 360 App with Management Pane to configure static data"
          }
        ]
      }
    }

#### 2.4.2 Sunshine - Add 1 Product (Custom Object), Add 1 Order (Custom Object) and Create 1 Relationship (order_contains_products)

    {
      "bootstrap": {
          "subdomain": "z3n-leroychan",
          "auth": {
              "username": "lechan@zendesk.com",
              "password": "XXXXX"
          },
          "customer": {
              "name": "Kaws",
              "locale": "en"
          }
      },
      "sunshine": {
        "add_custom_object_types": [
            {
                "key": "product",
                "schema": {
                    "properties": {
                        "id": {
                            "type": "string",
                            "description": "product id"
                        },
                        "name": {
                            "type": "string",
                            "description": "product name"
                        }
                    },
                    "required": [
                        "id",
                        "name"
                    ]
                },
                "reference_id": "co-product"
            },
            {
                "key": "order",
                "schema": {
                    "properties": {
                        "id": {
                            "type": "string",
                            "description": "order id"
                        },
                        "name": {
                            "type": "string",
                            "description": "order name"
                        }
                    },
                    "required": [
                        "id",
                        "name"
                    ]
                },
                "reference_id": "co-order"
            }
        ],
        "add_relationship_types": [
          {
            "key": "user_has_orders",
            "source": "zen:user",
            "target": "{{co-order}}",
            "reference_id": "rs-order"
          },
          {
            "key": "order_contains_products",
            "source": "{{co-order}}",
            "target": "{{co-product}}",
            "reference_id": "rs-product"
          }
        ],
        "add_custom_object_records": [
          {
            "type": "{{co-product}}",
            "external_id": "1717",
            "attributes": {
              "id": "1717",
              "name": "Test Bootstrapper Product 1"
            },
            "reference_id": "co-record-1"

          },
          {
            "type": "{{co-order}}",
            "external_id": "order-1717",
            "attributes": {
              "id": "order-1717",
              "name": "Test Bootstrapper Order 1"
            },
            "reference_id": "co-record-2"
          }
        ],
        "add_relationship_records": [
          {
            "relationship_type": "{{rs-product}}",
            "source": "{{co-record-2}}",
            "destination": "{{co-record-1}}"
          }
        ]
    }
    }

#### 2.4.3 Enabling Zendesk Talk for Demo Instances

    {
      "bootstrap": {
          "subdomain": "z3n-leroychan",
          "auth": {
              "username": "lechan@zendesk.com",
              "password": "XXXXX"
          },
          "customer": {
              "name": "Kaws",
              "locale": "en"
          }
      },
      "talk": {
        "add_number": {
            "country_code": "US",
            "purchase_first_available_number": true
        },
        "add_talk_agents": {
          "enable_first_admin": true
        },
        "add_ivrs": [
          {
            "name": "Bootstrapper Sample IVR"
          }
        ]
      }
    }

#### 2.4.4 Guide - Activate Guide + Import Custom Theme + Publish Theme + Add 2 Categories + Add 2 Sections + Add 2 Articles

Note: Value for `activate_guide` MUST be `{{bootstrapper-guide-default-brand-id}}`

    {
      "bootstrap": {
          "subdomain": "z3n-leroychan",
          "auth": {
              "username": "lechan@zendesk.com",
              "password": "XXXXX"
          },
          "customer": {
              "name": "Kaws",
              "locale": "en"
          }
      },
      "guide": {
        "activate_guide": "{{bootstrapper-guide-default-brand-id}}",
        "publish_theme": "{{generic-template}}",
        "import_themes": [
          {
            "theme_name": "generic-template",
            "reference_id": "generic-template"
          }
        ],
        "add_categories": [
          {
            "locale": "en-us",
            "name": "Refunds",
            "description": "Decided to refund? We are here to help.",
            "reference_id": "category-1"
          },
          {
            "locale": "en-us",
            "name": "Promotions",
            "description": "Latest promotions to help save your wallet!",
            "reference_id": "category-2"
          }
        ],
        "add_sections": [
          {
            "locale": "en-us",
            "category_id": "{{category-1}}",
            "name": "Required Refund Documents",
            "description": "Documents that are required to facilitate the refund",
            "reference_id": "section-1"
          },
          {
            "locale": "en-us",
            "category_id": "{{category-2}}",
            "name": "New Joiner Promotion",
            "description": "For all newbies",
            "reference_id": "section-2"
          }
        ],
        "add_articles": [
          {
            "section_id": "{{section-1}}",
            "title": "Proof of Purchase",
            "body": "Your Proof of Purchase must be dated within 14 days of the refund date"
          },
          {
            "section_id": "{{section-2}}",
            "title": "1 for 1 Deal",
            "body": "Buy 2 at the price of 1!"
          }
        ]
      }
    }
