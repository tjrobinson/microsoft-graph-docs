---
description: "Automatically generated file. DO NOT MODIFY"
---

```go


import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

graphClient := msgraphsdk.NewGraphServiceClientWithCredentials(cred, scopes)


requestBody := graphmodels.NewWorkbookTableColumn()
id := "99"
requestBody.SetId(&id) 
name := "name-value"
requestBody.SetName(&name) 
index := int32(99)
requestBody.SetIndex(&index) 
values := "values-value"
requestBody.SetValues(&values) 

result, err := graphClient.Drives().ByDriveId("drive-id").Items().ByItemId("driveItem-id").Workbook().Tables().ByTableId("workbookTable-id").Columns().Post(context.Background(), requestBody, nil)


```