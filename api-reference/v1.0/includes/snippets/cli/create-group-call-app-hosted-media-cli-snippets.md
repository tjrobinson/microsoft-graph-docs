---
description: "Automatically generated file. DO NOT MODIFY"
---

```bash

mgc communications calls create --body '{\
  "@odata.type": "#microsoft.graph.call",\
  "direction": "outgoing",\
  "subject": "Create a group call with application hosted media",\
  "callbackUri": "https://bot.contoso.com/callback",\
  "source": {\
    "@odata.type": "#microsoft.graph.participantInfo",\
    "identity": {\
      "@odata.type": "#microsoft.graph.identitySet",\
      "application": {\
        "@odata.type": "#microsoft.graph.identity",\
        "displayName": "TestBot",\
        "id": "dd3885da-f9ab-486b-bfae-85de3d445555"\
      }\
    }\
  },\
  "targets": [\
    {\
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",\
      "identity": {\
        "@odata.type": "#microsoft.graph.identitySet",\
        "user": {\
          "@odata.type": "#microsoft.graph.identity",\
          "displayName": "user1",\
          "id": "98da8a1a-1b87-452c-a713-65d3f10b5555"\
        }\
      }\
    },\
    {\
      "@odata.type": "#microsoft.graph.invitationParticipantInfo",\
      "identity": {\
        "@odata.type": "#microsoft.graph.identitySet",\
        "user": {\
          "@odata.type": "#microsoft.graph.identity",\
          "displayName": "user2",\
          "id": "bf5aae9a-d11d-47a8-93b1-782504c95555"\
        }\
      }\
    }\
  ],\
  "requestedModalities": [\
    "audio"\
  ],\
  "mediaConfig": {\
    "@odata.type": "#microsoft.graph.appHostedMediaConfig",\
    "removeFromDefaultAudioGroup": false\
  }\
}\
'

```