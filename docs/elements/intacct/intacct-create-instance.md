---
heading: Intacct
seo: Create Instance | Intacct | Cloud Elements API Docs
title: Create Instance
description: Create Instance
layout: sidebarelementdoc
breadcrumbs: /docs/elements.html
elementId: 921
parent: Back to Element Guides
order: 20
---

## Create Instance

When you provision an instance, your app will have access to the different functionality offered by the Intacct platform.

### Step 1. Create an Instance

To provision your Intacct Element, use the /instances API.

Below is an example of the provisioning API call.

* __HTTP Headers__: Authorization- User <user secret>, Organization <organization secret>
* __HTTP Verb__: POST
* __Request URL__: /instances
* __Request Body__: Required – see below
* __Query Parameters__: none

Description: An Element token is returned upon successful execution of this API. This token needs to be retained by the application for all subsequent requests involving this element instance.

A sample request illustrating the /instances API is shown below.

HTTP Headers:

```bash
Authorization: User <INSERT_USER_SECRET>, Organization <INSERT_ORGANIZATION_SECRET>

```
This instance.json file must be included with your instance request.  Please fill your information to provision.  The “key” into Cloud Elements Intacct is "intacct".  This will need to be entered in the “key” field below depending on which Element you wish to instantiate.

```JSON
{
  "element": {
    "key": "intacct"
  },
  "configuration": {
	"intacct.user.company.id": "<INSERT_INTACCT_COMPANY_ID>",
	"intacct.user.id": "<INSERT_INTACCT_USER_ID>",
	"intacct.user.password": "<INSERT_INTACCT_USER_PASSWORD>",
	"intacct.sender.id": "<INSERT_INTACCT_SENDER_ID>",
	"intacct.sender.password": "<INSERT_INTACCT_SENDER_PASSWORD>",
	"intacct.control.id": "<INSERT_INTACCT_CONTROL_ID>"  //unique value like myTestId
  },
  "tags": [
    "<INSERT_TAGS>"
  ],
  "name": "<INSERT_INSTANCE_NAME>"
}
```

Here is an example cURL command to create an instance using /instances API.

Example Request:

```bash
curl -X POST
-H 'Authorization: User <INSERT_USER_SECRET>, Organization <INSERT_ORGANIZATION_SECRET>'
-H 'Content-Type: application/json'
-d @instance.json
'https://api.cloud-elements.com/elements/api-v2/instances'
```

If the user does not specify a required config entry, an error will result notifying her of which entries she is missing.

Below is a successful JSON response:

```JSON
{
  "id": 1234,
  "name": "Test",
  "token": "mQuw4rrhnrMl1UeDj25v0xDU5TUx6WUw=",
  "element": {
    "id": 1666,
    "name": "Intacct. Beta",
    "hookName": "Intacct",
    "key": "intacct",
    "description": "Add a Intacct. Instance to connect your existing Intacct. account to the Finance Hub, allowing you to manage customers, employees, invoices, purchase orders, etc. across multiple Finance Elements. You will need your Intacct. account information to add an instance.",
    "image": "elements/provider_intacct.png",
    "active": true,
    "deleted": false,
    "typeOauth": false,
    "trialAccount": false,
    "resources": []
  },
  "provisionInteractions": [],
  "valid": true,
  "disabled": false,
  "maxCacheSize": 0,
  "cacheTimeToLive": 0,
  "configuration": {
    "base.url": "https://api.intacct.com/ia/xml/xmlgw.phtml",
    "bulk.add_metadata": null,
    "event.vendor.type": "polling",
    "bulk.query.date_mask": "MM/dd/yyyy HH:mm:ss",
    "bulk.attribute.created_time": "whenmodified",
    "intacct.endpoint.url": "https://api.intacct.com/ia/xml/xmlgw.phtml",
    "bulk.relations": null,
    "pagination.type": "page",
    "expires_in": "3600",
    "event.notification.enabled": "false",
    "intacct.sender.id": "SENDER_ID",
    "bulk.query.field_name": "whenmodified",
    "pagination.max": "100",
    "intacct.user.password": "********",
    "intacct.control.id": "testControlId",
    "bulk.query.operator": ">=",
    "intacct.user.company.id": "COMPANY_ID",
    "bulk.query.download_format": "JSON",
    "event.poller.refresh_interval": "15",
    "event.notification.callback.url": null,
    "intacct.user.id": "USER_ID",
    "authentication.time": "1472142721",
    "intacct.sender.password": "********",
    "intacct.session.id": "4ZaE-QJBqILBQUBdjMSQ5w..",
    "pagination.page.startindex": "0"
  },
  "eventsEnabled": false,
  "traceLoggingEnabled": false,
  "externalAuthentication": "none",
  "cachingEnabled": false
}
```

Note:  Make sure you have straight quotes in your JSON files and cURL commands.  Please use plain text formatting in your code.  Make sure you do not have spaces after the in the cURL command.

{% include common-instance-config.md %}
