---
description: "Automatically generated file. DO NOT MODIFY"
---

```bash

mgc subscriptions create --body '{\
  "changeType": "created,updated",\
  "notificationUrl": "https://webhook.azurewebsites.net/api/resourceNotifications",\
  "lifecycleNotificationUrl": "https://webhook.azurewebsites.net/api/lifecycleNotifications",\
  "resource": "/users/{id}/messages",\
  "expirationDateTime": "2020-03-20T11:00:00.0000000Z",\
  "clientState": "<secretClientState>"\
}\
'

```