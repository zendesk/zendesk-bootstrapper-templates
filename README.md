
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

### 2.1 Default Variables
You could use the following variables anywhere within your template code and it will automatically reference the values that you declare within the `bootstrap` object.

 1. `{{customer}}`
 2. `{{customer_name}}`
 3. `{{customer_locale}}`

### 2.2 Dependencies
Zendesk Bootstrapper helps you to resolve dependencies automatically with your templates

 1. Provide an **unique** `reference_id` on those objects that you wish to reference later on
 2. On those that objects that requires the ID to be translated from `reference_id` before it can be created, use the `{{the-unique-value-that-you-provided-in-the-reference-id}}`

#### 2.2.1 Currently Supported

`reference_id`
 1. Add Group
 2. Add Organizations
 3. Add User Fields
 4. Add Organization Fields

`{{reference_id_value}}`
 1. Add Ticket Views
 2. Add SLAs


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
 
 #### Example 2: Create 1 SLA that Reference Custom User Field and Custom Organization Field, the sample payload will be:

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

