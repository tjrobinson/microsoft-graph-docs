---
description: "Automatically generated file. DO NOT MODIFY"
---

```go


import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)

graphClient := msgraphsdk.NewGraphServiceClientWithCredentials(cred, scopes)



result, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().ByMessageId("chatMessage-id").Replies().ByReplieId("chatMessage-id1").Get(context.Background(), nil)


```