---
description: "Automatically generated file. DO NOT MODIFY"
---

```bash

mgc users events create --user-id {user-id} --body '{\
  "subject": "Let's go for lunch",\
  "body": {\
    "contentType": "HTML",\
    "content": "Does noon work for you?"\
  },\
  "start": {\
      "dateTime": "2017-04-15T12:00:00",\
      "timeZone": "Pacific Standard Time"\
  },\
  "end": {\
      "dateTime": "2017-04-15T14:00:00",\
      "timeZone": "Pacific Standard Time"\
  },\
  "location":{\
      "displayName":"Harry's Bar"\
  },\
  "attendees": [\
    {\
      "emailAddress": {\
        "address":"samanthab@contoso.onmicrosoft.com",\
        "name": "Samantha Booth"\
      },\
      "type": "required"\
    }\
  ],\
  "allowNewTimeProposals": true,\
  "isOnlineMeeting": true,\
  "onlineMeetingProvider": "teamsForBusiness"\
}\
'

```