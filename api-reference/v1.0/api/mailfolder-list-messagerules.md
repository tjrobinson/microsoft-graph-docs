---
title: "List rules"
description: "Get all the messageRule objects defined for the user's inbox."
ms.localizationpriority: medium
author: "abheek-das"
ms.prod: "outlook"
doc_type: apiPageType
---

# List rules

Namespace: microsoft.graph

Get all the [messageRule](../resources/messagerule.md) objects defined for the user's inbox.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | MailboxSettings.Read    |
|Delegated (personal Microsoft account) | MailboxSettings.Read    |
|Application | MailboxSettings.Read |

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
GET /me/mailFolders/inbox/messageRules
GET /users/{id | userPrincipalName}/mailFolders/inbox/messageRules
```

## Optional query parameters
This method supports the [OData Query Parameters](/graph/query-parameters) to help customize the response.

## Request headers
| Name       | Type | Description|
|:-----------|:------|:----------|
| Authorization  | string  | Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a `200 OK` response code and a collection of [messageRule](../resources/messagerule.md) objects in the response body.

## Example
### Request
The following is an example of a request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "sampleKeys": ["inbox"],
  "name": "get_messagerules"
}-->
```msgraph-interactive
GET https://graph.microsoft.com/v1.0/me/mailFolders/inbox/messageRules
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/get-messagerules-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/get-messagerules-cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/get-messagerules-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/get-messagerules-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/get-messagerules-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/get-messagerules-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/get-messagerules-powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/get-messagerules-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

### Response
The following is an example of the response. 
>**Note**: The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.messageRule",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#Me/mailFolders('inbox')/messageRules",
  "value":[
    {
      "id":"AQAAAJ5dZp8=",
      "displayName":"Remove spam",
      "sequence":1,
      "isEnabled":true,
      "hasError":false,
      "isReadOnly":false,
      "conditions":{
        "subjectContains":[
          "enter to win"
        ]
      },
      "actions":{
        "delete":true,
        "stopProcessingRules":true
      }
    },
    {
      "id":"AQAAAJ5dZqA=",
      "displayName":"From partner",
      "sequence":2,
      "isEnabled":true,
      "hasError":false,
      "isReadOnly":false,
      "conditions":{
        "senderContains":[
          "ADELE"
        ]
      },
      "actions":{
        "stopProcessingRules":true,
        "forwardTo":[
          {
            "emailAddress":{
              "name":"Alex Wilbur",
              "address":"AlexW@contoso.onmicrosoft.com"
            }
          }
        ]
      }
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List rules",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
  ]
}-->
