---
description: "Automatically generated file. DO NOT MODIFY"
---

```go


import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphchats "github.com/microsoftgraph/msgraph-sdk-go/chats"
	  //other-imports
)

graphClient := msgraphsdk.NewGraphServiceClientWithCredentials(cred, scopes)


requestParameters := &graphchats.ChatItemInstalledAppsRequestBuilderGetQueryParameters{
	Select: [] string {"consentedPermissionSet","id"},
}
configuration := &graphchats.ChatItemInstalledAppsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

result, err := graphClient.Chats().ByChatId("chat-id").InstalledApps().Get(context.Background(), configuration)


```