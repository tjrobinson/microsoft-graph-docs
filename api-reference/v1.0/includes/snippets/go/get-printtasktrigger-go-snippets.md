---
description: "Automatically generated file. DO NOT MODIFY"
---

```go


import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)

graphClient := msgraphsdk.NewGraphServiceClientWithCredentials(cred, scopes)



result, err := graphClient.Print().Printers().ByPrinterId("printer-id").TaskTriggers().ByTaskTriggerId("printTaskTrigger-id").Get(context.Background(), nil)


```