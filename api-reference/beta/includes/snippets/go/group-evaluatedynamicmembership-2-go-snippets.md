---
description: "Automatically generated file. DO NOT MODIFY"
---

```go


import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphgroups "github.com/microsoftgraph/msgraph-beta-sdk-go/groups"
	  //other-imports
)

graphClient := msgraphsdk.NewGraphServiceClientWithCredentials(cred, scopes)


requestBody := graphgroups.NewEvaluateDynamicMembershipPostRequestBody()
memberId := "319b41e8-d9e4-42f8-bdc9-741113f48b33"
requestBody.SetMemberId(&memberId) 
membershipRule := "(user.displayName -startsWith \"EndTestUser\")"
requestBody.SetMembershipRule(&membershipRule) 

result, err := graphClient.Groups().EvaluateDynamicMembership().Post(context.Background(), requestBody, nil)


```