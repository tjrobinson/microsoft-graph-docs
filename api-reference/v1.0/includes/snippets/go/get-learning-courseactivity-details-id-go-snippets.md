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



result, err := graphClient.EmployeeExperience().LearningCourseActivities().ByLearningCourseActivitieId("learningCourseActivity-id").Get(context.Background(), nil)


```