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



graphClient.Education().Classes().ByClasseId("educationClass-id").Assignments().ByAssignmentId("educationAssignment-id").Delete(context.Background(), nil)


```