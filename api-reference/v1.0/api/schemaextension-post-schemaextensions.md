---
title: "Create schemaExtension"
description: "Create a new schemaExtension definition to extend a supporting resource type."
ms.localizationpriority: high
author: "dkershaw10"
ms.prod: "extensions"
doc_type: apiPageType
---

# Create schemaExtension

Namespace: microsoft.graph

Create a new [schemaExtension](../resources/schemaextension.md) definition and its associated schema extension property to extend a [supporting resource type](/graph/extensibility-overview#supported-resources).

Schema extensions let you add strongly-typed custom data to a resource. The app that creates a schema extension is the owner app. Depending on the 
[state](/graph/api/resources/schemaextension#schema-extensions-lifecycle) of the extension, the owner app, and only the owner app, may update or delete the extension. 

See examples of how to [define a schema extension that describes a training course](/graph/extensibility-schema-groups#2-register-a-schema-extension-definition-that-describes-a-training-course), 
use the schema extension definition to [create a new group with training course data](/graph/extensibility-schema-groups#3-create-a-new-group-with-extended-data), and 
[add training course data to an existing group](/graph/extensibility-schema-groups#4-add-update-or-remove-custom-data-in-an-existing-group).

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).


<!-- { "blockType": "ignored"  } // Note: Removing this line will result in the permissions autogeneration tool overwriting the table. -->
|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Application.ReadWrite.All    |
|Delegated (personal Microsoft account) | Not supported.    |
|Application | Application.ReadWrite.All and Directory.ReadWrite.All |

> [!NOTE]
> Additionally for the delegated flow, the signed-in user must be the owner of the calling application OR the owner of the (application with the) **appId** used to set the **owner** property.

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
POST /schemaExtensions
```

## Request headers
| Name       | Description|
|:---------------|:----------|
| Authorization  | Bearer {token}. Required. |
| Content-Type  | application/json  |

## Request body
In the request body, supply a JSON representation of [schemaExtension](../resources/schemaextension.md) object.

The following table shows the properties that are required when you create a schema extension.

| Parameter | Type | Description|
|:---------------|:--------|:----------|
|description|String|Description for the schema extension.|
|id|String|The unique identifier for the schema extension definition. <br>You can assign a value in one of two ways: <ul><li>Concatenate the name of one of your verified domains with a name for the schema extension to form a unique string in this format, \{_&#65279;domainName_\}\_\{_&#65279;schemaName_\}. As an example, `contoso_mySchema`. NOTE: Only verified domains under the following top-level domains are supported: `.com`,`.net`, `.gov`, `.edu` or `.org`. </li><li>Provide a schema name, and let Microsoft Graph use that schema name to complete the **id** assignment in this format: ext\{_&#65279;8-random-alphanumeric-chars_\}\_\{_&#65279;schema-name_\}. An example would be `extkvbmkofy_mySchema`.</li></ul>This property cannot be changed after creation. |
|owner|String|(Optional) The `appId` of the application that is the owner of the schema extension. By default, the calling application's `appId` will be set as the owner. However, the property may be supplied on creation, to set the owner appId to something different from the calling app. In all cases, in the delegated flow, the signed-in user **must** be the owner of the application being set as the schema extension's owner. So, for example, if creating a new schema extension definition using Graph Explorer, you **must** supply the owner property, for an appId you own. Once set, this property is read-only and cannot be changed.|
|properties|[extensionSchemaProperty](../resources/extensionschemaproperty.md) collection|The collection of property names and types that make up the schema extension definition.|
|targetTypes|String collection|Set of Microsoft Graph resource types (that support schema extensions) that this schema extension definition can be applied to.|

## Response

If successful, this method returns `201 Created` response code and [schemaExtension](../resources/schemaextension.md) object in the response body.

## Example

### Example 1: Creating a schema extension using a verified domain

#### Request

This example shows using a verified domain name, `graphlearn`, and a schema name, `courses`, to form a unique string for the **id** property of the schema extension definition. The unique string is based on this format, \{_&#65279;domainName_\}\_\{_&#65279;schemaName_\}.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "create_schemaextension_from_schemaextensions_1"
}-->
```http
POST https://graph.microsoft.com/v1.0/schemaExtensions
Content-type: application/json

{
    "id":"graphlearn_courses",
    "description": "Graph Learn training courses extensions",
    "targetTypes": [
        "Group"
    ],
    "properties": [
        {
            "name": "courseId",
            "type": "Integer"
        },
        {
            "name": "courseName",
            "type": "String"
        },
        {
            "name": "courseType",
            "type": "String"
        }
    ]
}
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/create-schemaextension-from-schemaextensions-1-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/create-schemaextension-from-schemaextensions-1-cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/create-schemaextension-from-schemaextensions-1-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/create-schemaextension-from-schemaextensions-1-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/create-schemaextension-from-schemaextensions-1-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/create-schemaextension-from-schemaextensions-1-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/create-schemaextension-from-schemaextensions-1-powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/create-schemaextension-from-schemaextensions-1-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response

The following is an example of the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.schemaExtension"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "graphlearn_courses",
    "description": "Graph Learn training courses extensions",
    "targetTypes": [
        "Group"
    ],
    "status": "InDevelopment",
    "owner": "24d3b144-21ae-4080-943f-7067b395b913",
    "properties": [
        {
            "name": "courseId",
            "type": "String"
        },
        {
            "name": "courseName",
            "type": "String"
        },
        {
            "name": "courseType",
            "type": "String"
        }
    ]
}
```

### Example 2: Creating a schema extension using just a name

#### Request

The following example shows specifying just a schema name, `courses`, in the **id** property in the request, together with the JSON representation of the rest of the properties in the [schemaExtension](../resources/schemaextension.md) object. Microsoft Graph will assign and return a unique string value in the response.


# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "create_schemaextension_from_schemaextensions_2"
}-->
```http
POST https://graph.microsoft.com/v1.0/schemaExtensions
Content-type: application/json

{
    "id":"courses",
    "description": "Graph Learn training courses extensions",
    "targetTypes": [
        "Group"
    ],
    "properties": [
        {
            "name": "courseId",
            "type": "Integer"
        },
        {
            "name": "courseName",
            "type": "String"
        },
        {
            "name": "courseType",
            "type": "String"
        }
    ]
}
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/create-schemaextension-from-schemaextensions-2-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/create-schemaextension-from-schemaextensions-2-cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/create-schemaextension-from-schemaextensions-2-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/create-schemaextension-from-schemaextensions-2-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/create-schemaextension-from-schemaextensions-2-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/create-schemaextension-from-schemaextensions-2-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/create-schemaextension-from-schemaextensions-2-powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/create-schemaextension-from-schemaextensions-2-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response

The response includes a unique string in the **id** property that is based on the schema name provided in the request, together with the rest of the newly created schema definition. 
The value in **id** in the response is based on the format, ext\{_&#65279;8-random-alphanumeric-chars_\}\_\{_&#65279;schema-name_\}. 
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.schemaExtension"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "extk9eruy7c_courses",
    "description": "Graph Learn training courses extensions",
    "targetTypes": [
        "Group"
    ],
    "status": "InDevelopment",
    "owner": "24d3b144-21ae-4080-943f-7067b395b913",
    "properties": [
        {
            "name": "courseId",
            "type": "String"
        },
        {
            "name": "courseName",
            "type": "String"
        },
        {
            "name": "courseType",
            "type": "String"
        }
    ]
}
```

### Example 3: Creating a schema extension setting the owner

#### Request

The following example shows how to create a schema extension setting the **owner**.  In this scenario, the user of the application might not be the owner of the application (for example if you are using Microsoft Graph Explorer).  In this case you should set the **owner** property to the **appId** of an application you own, otherwise you won't be authorized to create a schema extension. Set the **owner** property in the request, together with the JSON representation of the rest of the properties in the [schemaExtension](../resources/schemaextension.md) object.


# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "create_schemaextension_from_schemaextensions_3"
}-->

```http
POST https://graph.microsoft.com/v1.0/schemaExtensions
Content-type: application/json

{
    "id":"courses",
    "description": "Graph Learn training courses extensions",
    "targetTypes": [
        "Group"
    ],
    "owner": "50897f70-a455-4adf-87bc-4cf17091d5ac",
    "properties": [
        {
            "name": "courseId",
            "type": "Integer"
        },
        {
            "name": "courseName",
            "type": "String"
        },
        {
            "name": "courseType",
            "type": "String"
        }
    ]
}
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/create-schemaextension-from-schemaextensions-3-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/create-schemaextension-from-schemaextensions-3-cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/create-schemaextension-from-schemaextensions-3-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/create-schemaextension-from-schemaextensions-3-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/create-schemaextension-from-schemaextensions-3-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/create-schemaextension-from-schemaextensions-3-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/create-schemaextension-from-schemaextensions-3-powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/create-schemaextension-from-schemaextensions-3-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response

The response includes the **owner** set to the value supplied in the request. 
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.schemaExtension"
} -->

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "extk9eruy7c_courses",
    "description": "Graph Learn training courses extensions",
    "targetTypes": [
        "Group"
    ],
    "status": "InDevelopment",
    "owner": "50897f70-a455-4adf-87bc-4cf17091d5ac",
    "properties": [
        {
            "name": "courseId",
            "type": "String"
        },
        {
            "name": "courseName",
            "type": "String"
        },
        {
            "name": "courseType",
            "type": "String"
        }
    ]
}
```

## See also

- [Add custom data to resources using extensions](/graph/extensibility-overview)
- [Add custom data to groups using schema extensions](/graph/extensibility-schema-groups)


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create schemaExtension",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
  ]
}-->

