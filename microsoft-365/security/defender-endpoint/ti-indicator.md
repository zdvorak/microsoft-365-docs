---
title: Indicator resource type
description: Specify the entity details and define the expiration of the indicator using Microsoft Defender for Endpoint.
keywords: apis, supported apis, get, TiIndicator, Indicator, recent
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
---

# Indicator resource type

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Applies to:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Want to experience Microsoft Defender for Endpoint? [Sign up for a free trial.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

- See the corresponding [Indicators page](https://securitycenter.windows.com/preferences2/custom_ti_indicators/files) in the portal.

Method|Return Type|Description
:---|:---|:---
[List Indicators](get-ti-indicators-collection.md)|[Indicator](ti-indicator.md) Collection|List [Indicator](ti-indicator.md) entities.
[Submit Indicator](post-ti-indicator.md)|[Indicator](ti-indicator.md)|Submit or update [Indicator](ti-indicator.md) entity.
[Import Indicators](import-ti-indicators.md)|[Indicator](ti-indicator.md) Collection|Submit or update [Indicators](ti-indicator.md) entities.
[Delete Indicator](delete-ti-indicator-by-id.md)|No Content|Deletes [Indicator](ti-indicator.md) entity.

## Properties

Property|Type|Description
:---|:---|:---
id|String|Identity of the [Indicator](ti-indicator.md) entity.
indicatorValue|String|The value of the [Indicator](ti-indicator.md).
indicatorType|Enum|Type of the indicator. Possible values are: "FileSha1", "FileSha256", "FileMd5", "CertificateThumbprint", "IpAddress", "DomainName" and "Url".
application|String|The application associated with the indicator.
action|Enum|The action that will be taken if the indicator will be discovered in the organization. Possible values are: "Warn", "Block", "Audit", "Alert", "AlertAndBlock", "BlockAndRemediate" and "Allowed".
|externalID|String|Id the customer can submit in the request for custom correlation.|
sourceType|Enum|"User" in case the Indicator created by a user (e.g. from the portal), "AadApp" in case it submitted using automated application via the API.
createdBySource|string|The name of the user/application that submitted the indicator.
createdBy|String|Unique identity of the user/application that submitted the indicator.
lastUpdatedBy|String|Identity of the user/application that last updated the indicator.
creationTimeDateTimeUtc|DateTimeOffset|The date and time when the indicator was created.
expirationTime|DateTimeOffset|The expiration time of the indicator.
lastUpdateTime|DateTimeOffset|The last time the indicator was updated.
severity|Enum|The severity of the indicator. possible values are: "Informational", "Low", "Medium" and "High".
title|String|Indicator title.
description|String|Description of the indicator.
recommendedActions|String|Recommended actions for the indicator.
rbacGroupNames|List of strings|RBAC device group names where the indicator is exposed and active. Empty list in case it exposed to all devices.
rbacGroupIds|List of strings|RBAC device group ID's where the indicator is exposed and active. Empty list in case it exposed to all devices.
## Public Preview: Indicator types

> [!IMPORTANT]
> Information in this section (**Public Preview for Automated investigation and remediation engine**) relates to prereleased product which might be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

The indicator action types supported by the API are:

- AlertAndBlock
- Allow
- Audit
- Alert
- Warn
- BlockExecution
- BlockRemdiation

The API list of action types contains the new response actions along with the prior response actions (AlertAndBlock, and Alert).

> [!Note]
>
> The prior response actions (AlertAndBlock, and Alert) will be removed when the feature has reached GAed. The estimated GA date with grace period is end of October 2021.  We advise updating any existing templates or scripts as soon as possible.

## Json representation

```json
{
    "id": "994",
    "indicatorValue": "881c0f10c75e64ec39d257a131fcd531f47dd2cff2070ae94baa347d375126fd",
    "indicatorType": "FileSha256",
    "action": "AlertAndBlock",
    "application": null,
    "source": "user@contoso.onmicrosoft.com",
    "sourceType": "User",
    "createdBy": "user@contoso.onmicrosoft.com",
    "severity": "Informational",
    "title": "Michael test",
    "description": "test",
    "recommendedActions": "nothing",
    "creationTimeDateTimeUtc": "2019-12-19T09:09:46.9139216Z",
    "expirationTime": null,
    "lastUpdateTime": "2019-12-19T09:09:47.3358111Z",
    "lastUpdatedBy": null,
    "rbacGroupNames": ["team1"]
}
```
