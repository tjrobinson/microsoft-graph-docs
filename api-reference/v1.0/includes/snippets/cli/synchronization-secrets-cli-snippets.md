---
description: "Automatically generated file. DO NOT MODIFY"
---

```bash

mgc service-principals synchronization secrets put --service-principal-id {servicePrincipal-id} --body '{\
    "value": [\
        {\
            "key": "BaseAddress",\
            "value": "user@domain.com"\
        },\
        {\
            "key": "SecretToken",\
            "value": "password-value"\
        },\
        {\
            "key": "SyncNotificationSettings",\
            "value": "{\"Enabled\":false,\"DeleteThresholdEnabled\":false}"\
        },\
        {\
            "key": "SyncAll",\
            "value": "false"\
        }\
    ]\
}\
'

```