---
title: "List alerts"
description: "Get a list of the unifiedRoleManagementAlert objects and their properties."
author: "rkarim-ms"
ms.localizationpriority: medium
ms.prod: "governance"
doc_type: apiPageType
---

# List alerts
Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of the [unifiedRoleManagementAlert](../resources/unifiedrolemanagementalert.md) objects and their properties.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type|Permissions (from least to most privileged)|
|:---|:---|
|Delegated (work or school account)|RoleManagementAlert.Read.Directory, RoleManagementAlert.ReadWrite.Directory|
|Delegated (personal Microsoft account)|Not supported|
|Application|RoleManagementAlert.Read.Directory, RoleManagementAlert.ReadWrite.Directory|

[!INCLUDE [rbac-pim-alerts-apis-read](../includes/rbac-for-apis/rbac-pim-alerts-apis-read.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /identityGovernance/roleManagementAlerts/alerts?$filter=scopeId eq 'scopeId' and scopeType eq 'scopeType'
```

## Optional query parameters
This method supports the `$select`, `$filter`, and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers
|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|

## Request body
Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [unifiedRoleManagementAlert](../resources/unifiedrolemanagementalert.md) objects in the response body.

## Examples

### Request
The following is an example of a request.
# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "list_unifiedrolemanagementalert"
}
-->
``` http
GET https://graph.microsoft.com/beta/identityGovernance/roleManagementAlerts/alerts?$filter=scopeId eq '/' and scopeType eq 'DirectoryRole'&$expand=alertDefinition,alertConfiguration,alertIncidents
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/list-unifiedrolemanagementalert-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/list-unifiedrolemanagementalert-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/list-unifiedrolemanagementalert-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/list-unifiedrolemanagementalert-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/list-unifiedrolemanagementalert-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/list-unifiedrolemanagementalert-powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/list-unifiedrolemanagementalert-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

### Response
The following is an example of the response
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.unifiedRoleManagementAlert)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/roleManagementAlerts/alerts(alertDefinition(),alertConfiguration(),alertIncidents())",
    "value": [
        {
            "id": "DirectoryRole_19356be4-7e93-4ed6-a7c6-0ae28454d125_TooManyGlobalAdminsAssignedToTenantAlert",
            "alertDefinitionId": "DirectoryRole_19356be4-7e93-4ed6-a7c6-0ae28454d125_TooManyGlobalAdminsAssignedToTenantAlert",
            "scopeId": "/",
            "scopeType": "DirectoryRole",
            "incidentCount": 2,
            "isActive": true,
            "lastModifiedDateTime": "2023-05-27T19:16:09.643Z",
            "lastScannedDateTime": "2023-06-11T23:01:35.21Z",
            "alertDefinition": {
                "id": "DirectoryRole_19356be4-7e93-4ed6-a7c6-0ae28454d125_TooManyGlobalAdminsAssignedToTenantAlert",
                "displayName": "There are too many global administrators",
                "scopeType": "DirectoryRole",
                "scopeId": "/",
                "description": "The percentage of global administrators is high, relative to other privileged roles. It is recommended to use least privileged roles, with just enough privileges to perform the required tasks.",
                "severityLevel": "low",
                "securityImpact": "Global administrator is the highest privileged role. If a Global Administrator is compromised, the attacker gains access to all of their permissions, which puts your whole system at risk.",
                "mitigationSteps": "·Review the users in the list and remove any that do not absolutely need the Global Administrator role.·Assign lower privileged roles to these users instead.",
                "howToPrevent": "Assign users the least privileged role they need.",
                "isRemediatable": true,
                "isConfigurable": true
            },
            "alertConfiguration": {
                "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertConfiguration",
                "id": "DirectoryRole_19356be4-7e93-4ed6-a7c6-0ae28454d125_TooManyGlobalAdminsAssignedToTenantAlert",
                "alertDefinitionId": "DirectoryRole_19356be4-7e93-4ed6-a7c6-0ae28454d125_TooManyGlobalAdminsAssignedToTenantAlert",
                "scopeType": "DirectoryRole",
                "scopeId": "/",
                "isEnabled": true,
                "globalAdminCountThreshold": 2,
                "percentageOfGlobalAdminsOutOfRolesThreshold": 4
            },
            "alertIncidents@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/roleManagementAlerts/alerts('DirectoryRole_19356be4-7e93-4ed6-a7c6-0ae28454d125_TooManyGlobalAdminsAssignedToTenantAlert')/alertIncidents",
            "alertIncidents": [
                {
                    "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
                    "id": "f5417b06-cdae-417f-9589-a334104206cf",
                    "assigneeId": "f5417b06-cdae-417f-9589-a334104206cf",
                    "assigneeDisplayName": "testUser1",
                    "assigneeUserPrincipalName": "testuser1@anujcoffice.onmicrosoft.com"
                },
                {
                    "@odata.type": "#microsoft.graph.tooManyGlobalAdminsAssignedToTenantAlertIncident",
                    "id": "861e0b20-1e9f-4ca9-bcd1-ddc22c5d7320",
                    "assigneeId": "861e0b20-1e9f-4ca9-bcd1-ddc22c5d7320",
                    "assigneeDisplayName": "testUser2",
                    "assigneeUserPrincipalName": "testuser2@anujcoffice.onmicrosoft.com"
                }
            ]
        }
    ]
}
```

