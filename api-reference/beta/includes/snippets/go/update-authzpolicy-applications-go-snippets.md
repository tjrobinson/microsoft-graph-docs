---
description: "Automatically generated file. DO NOT MODIFY"
---

```go


import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

graphClient := msgraphsdk.NewGraphServiceClientWithCredentials(cred, scopes)


requestBody := graphmodels.NewAuthorizationPolicy()
defaultUserRolePermissions := graphmodels.NewDefaultUserRolePermissions()
allowedToCreateApps := false
defaultUserRolePermissions.SetAllowedToCreateApps(&allowedToCreateApps) 
requestBody.SetDefaultUserRolePermissions(defaultUserRolePermissions)

result, err := graphClient.Policies().AuthorizationPolicy().ByAuthorizationPolicy().Id("authorizationPolicy-id").Patch(context.Background(), requestBody, nil)


```