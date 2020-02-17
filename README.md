
# Zendesk Bootstrapper Templates

Browse here for all the available templates or build you own templates!

## 1. How to use Zendesk Bootstrapper
1. On Zendesk Slack workspace, *direct message* `@Bootstrapper`
2. Type `help` and follow through the instructions

Thats it! Its _beautifully simple_, just like Zendesk.

## 2. Don't see the Bootstrapper Template that fit your needs? Create one !
1. Browse under the folder `master-template` which contains the entire feature set that Zendesk Bootstrapper supports
2. Analyze the JSON structure
3. Formulate your own template!
4. Contact `@lechan` on Slack to get your template published for everyone to use

PS: It supports *ALL* values of the Zendesk APIs (you could refer to https://developer.zendesk.com/rest_api/docs/support/introduction for more details). So you could use values that you don't see within the `master-template` within each functionality.

### 2.1 Features List

**You can use any supported request payload that is within Zendesk's API reference specs!**

| Category       | Sub Category      | Functionality                     | API Reference (You can use any supported request payload from Zendesk !)                                                                      |
|----------------|-------------------|-----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| Settings       | Account Settings  | -                                 | https://developer.zendesk.com/rest_api/docs/support/account_settings                                                                          |
| Settings       | Security Settings | -                                 | Private API                                                                                                                                   |
| Settings       | Support Settings  | Update Default Support Email      | [Bootstrapper's unique Functionality]                                                                                                         |
| Settings       | Support Settings  | Add Recipient Addresses           | https://developer.zendesk.com/rest_api/docs/support/support_addresses#create-support-address                                                  |
| Ticket Views   | -                 | Add Ticket Views                  | https://developer.zendesk.com/rest_api/docs/support/views#create-view                                                                         |
| Users          | -                 | Add User Fields                   | https://developer.zendesk.com/rest_api/docs/support/user_fields#create-user-fields                                                            |
| Users          | -                 | Add Users                         | https://developer.zendesk.com/rest_api/docs/support/users#create-user                                                                         |
| Users          | -                 | Add Groups                        | https://developer.zendesk.com/rest_api/docs/support/groups#create-group                                                                       |
| Users          | -                 | Add Organizations                 | https://developer.zendesk.com/rest_api/docs/support/organizations#create-organization                                                         |
| Users          | -                 | Add Organization Fields           | https://developer.zendesk.com/rest_api/docs/support/organization_fields#create-organization-fields                                            |
| Business Rules | -                 | Add SLAs                          | https://developer.zendesk.com/rest_api/docs/support/sla_policies#create-sla-policy                                                            |
| Business Rules | -                 | Add Triggers                      | https://developer.zendesk.com/rest_api/docs/support/triggers#create-trigger                                                                   |
| Business Rules | -                 | Add Automations                   | https://developer.zendesk.com/rest_api/docs/support/automations#create-automation                                                             |
| Macros         | -                 | Add Macros                        | https://developer.zendesk.com/rest_api/docs/support/macros#create-macro                                                                       |
| Macros         | -                 | Disable Default Macros            | [Bootstrapper's unique Functionality] Disables: 1. Close and redirect to topics 2. Customer not responding 3. Downgrade and inform 4. Take it! |
| Apps           | -                 | Add Apps (Only Marketplace Apps)  | https://developer.zendesk.com/rest_api/docs/support/apps#create-app                                                                           |
| Tickets        | -                 | Generate Tickets                  | [Bootstrapper's unique Functionality] https://developer.zendesk.com/rest_api/docs/support/tickets#create-ticket                               |
| Tickets        | -                 | Add Ticket Fields                 | https://developer.zendesk.com/rest_api/docs/support/ticket_fields#create-ticket-field                                                         |
| Tickets        | -                 | Add Ticket Forms                  | https://developer.zendesk.com/rest_api/docs/support/ticket_forms#create-ticket-forms                                                          |
| Talk           | -                 | Add Number                        | [Bootstrapper's unique Functionality]                                                                                                         |
| Talk           | -                 | Add Talk Agents                   | [Bootstrapper's unique Functionality]                                                                                                         |
| Talk           | -                 | Add IVRs                          | https://developer.zendesk.com/rest_api/docs/voice-api/ivrs#create-ivr                                                                         |

### 2.2 Default Variables
You could use the following variables anywhere within your template code and it will automatically reference the values that you declare within the `bootstrap` object.

 1. `{{customer}}`
 2. `{{customer_name}}`
 3. `{{customer_locale}}`

### 2.3 Dependencies
Zendesk Bootstrapper helps you to resolve dependencies automatically with your templates

 1. Provide an **unique** `reference_id` on those objects that you wish to reference later on
 2. On those that objects that requires the ID or Key to be translated from `reference_id` before it can be created, use the `{{the-unique-value-that-you-provided-in-the-reference-id}}`

#### 2.3.1 Currently Supported

`reference_id`
 1. Add Group
 2. Add Organizations
 3. Add User Fields
 4. Add Organization Fields
 5. Add Ticket Fields
 6. Add Ticket Forms

`{{reference_id_value}}`
 1. Add Ticket Views
 2. Add SLAs
 3. Add Ticket Forms
 4. Add Triggers
 5. Add Automations
 6. Add Macros


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

### 2.4 Example Bootstrapper Templates
The following examples will give you a better idea how to structure a Bootstrapper template. You can easily mix and match and/or combine different examples to achieve your intended usecases.

#### 2.4.1 Enabling Zendesk Talk for Demo Instances

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


