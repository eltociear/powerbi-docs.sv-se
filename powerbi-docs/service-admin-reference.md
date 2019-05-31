---
title: PowerShell-cmdletar, REST API:er och .NET SDK för administratörer
description: Lär dig hur du kan administrera Power BI via skript och programmerings-API:er.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: overview
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 86a90396c82a597e8b4f535b71e029bfa21328a4
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61187244"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>PowerShell-cmdletar, REST API:er och .NET SDK för Power BI-administration
Med Power BI kan administratörer skripta vanliga åtgärder med PowerShell-cmdletar. Dessutom visas REST API:er och en .NET SDK tillhandahålls för utveckling av administrativa lösningar. I det här avsnittet visas en lista över cmdletar med motsvarande SDK-metod och REST API-slutpunkt. Mer information finns i:

- PowerShell – [nedladdning](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) och [dokumentation](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps)
- REST API – [dokumentation](https://docs.microsoft.com/rest/api/power-bi/admin)
- .NET SDK – [nedladdning](https://www.nuget.org/packages/Microsoft.PowerBI.Api/)

> Cmdlet:arna nedan ska anropas med `-Scope Organization` för att fungera med klientorganisationen för administration.

| **Cmdlet-namn** | **Alias** | **SDK-metod** | **REST API-slutpunkt** | **Beskrivning** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | Saknas | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Hämtar datakällor för den angivna datauppsättningen. |
| `Get-PowerBIDataset` | Saknas | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | Hämtar en fullständig lista över datauppsättningar i en Power BI-klientorganisation. |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | Hämtar en fullständig lista över arbetsytor i Power BI-klientorganisationen. |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | Lägger till en användare som medlem till en viss arbetsyta. |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Tar bort en användare från medlemslistan för en viss arbetsyta. |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | Återställer en borttagen arbetsyta. |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | Uppdaterar egenskaperna för en angiven arbetsyta. |
| `Get-PowerBIDataset -WorkspaceId` | Saknas | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | Hämtar datauppsättningar inom en angiven arbetsyta. |
| `Get-PowerBIReport` | Saknas | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | Hämtar en fullständig lista över rapporter i Power BI-klientorganisationen. |
| `Get-PowerBIDashboard` | Saknas | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | Hämtar den fullständiga listan över instrumentpaneler i en Power BI-klientorganisation. |
| `Get-PowerBIDashboard -WorkspaceId` | Saknas | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Hämtar instrumentpanelerna inom en angiven arbetsyta. |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Hämtar panelerna för en angiven instrumentpanel. |
| `Get-PowerBIReport` | Saknas | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | Hämtar rapporterna inom en angiven arbetsyta. |
| `Get-PowerBIImport` | Saknas | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | Hämtar den fullständiga listan över importer i Power BI-klientorganisationen. |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | Saknas | Saknas | Logga in på Power BI och starta en session. |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | Saknas | Saknas | Logga ut från Power BI och stänga den aktuella sessionen. |
| `Invoke-PowerBIRestMethod`| Saknas | Saknas | Saknas | Skicka godtyckliga REST API-anrop till Power BI. |
| `Get-PowerBIAccessToken`| Saknas | Saknas | Saknas | Hämta åtkomsttoken för Power BI i en session. |
| `Resolve-PowerBIError`| Saknas | Saknas | Saknas | Få detaljerad felinformation om misslyckade cmdlet-anrop. |
