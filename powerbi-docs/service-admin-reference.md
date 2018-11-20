---
title: PowerShell-cmdletar, REST API:er och .NET SDK för administratörer
description: Lär dig hur du kan administrera Power BI via skript och programmerings-API:er.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: overview
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: f4455fef5a2ed0e7ee23ff8ca3a0b626cd695838
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2018
ms.locfileid: "51508001"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>PowerShell-cmdletar, REST API:er och .NET SDK för Power BI-administration
Med Power BI kan administratörer skripta vanliga åtgärder med PowerShell-cmdletar. Dessutom visas REST API:er och en .NET SDK tillhandahålls för utveckling av administrativa lösningar. I det här avsnittet visas en lista över cmdletar med motsvarande SDK-metod och REST API-slutpunkt. Mer information finns i:

  - PowerShell – [nedladdning](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) och [dokumentation](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps)
  - REST API – [dokumentation](https://docs.microsoft.com/rest/api/power-bi/admin)
  - .NET SDK – [nedladdning](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) 


| **Cmdlet-namn** | **SDK-metod** | **REST API-slutpunkt** | **Beskrivning** |
| --- | --- | --- | --- |
| **Get-PowerBIDatasource** | Datasets\_GetDataSourcesAsAdmin | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Hämtar datakällor för den angivna datauppsättningen. |
| **Get-PowerBIDataset** | Datasets\_GetDatasetsAsAdmin | /v1.0/myorg/admin/datasets | Hämtar en fullständig lista över datauppsättningar i en Power BI-klientorganisation. |
| **Get-PowerBIWorkspace** | Groups\_GetGroupsAsAdmin | /v1.0/myorg/admin/groups | Hämtar en fullständig lista över arbetsytor i Power BI-klientorganisationen. |
| **Add-PowerBIWorkspaceUser** | Groups\_AddUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users | Lägger till en användare som medlem till en viss arbetsyta. |
| **Remove-PowerBIWorkspaceUser** | Groups\_DeleteUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Tar bort en användare från medlemslistan för en viss arbetsyta. |
| **Restore-PowerBIWorkspace** | Groups\_RestoreDeletedGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId}/restore | Återställer en borttagen arbetsyta. |
| **Set-PowerBIWorkspace** | Groups\_UpdateGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId} | Uppdaterar egenskaperna för en angiven arbetsyta. |
| **Get-PowerBIDataset-WorkspaceId** | Groups\_GetDatasetsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/datasets | Hämtar datauppsättningar inom en angiven arbetsyta. |
| **Export-PowerBIReport** | Reports\_ExportReportAsAdmin | Saknas | Exporterar en angiven rapport till en lokal fil. |
| **Get-PowerBIReport** | Reports\_GetReportsAsAdmin | /v1.0/myorg/admin/reports | Hämtar en fullständig lista över rapporter i Power BI-klientorganisationen. |
| **Get-PowerBIDashboard** | Dashboards\_GetDashboardsAsAdmin | /v1.0/myorg/admin/dashboards | Hämtar den fullständiga listan över instrumentpaneler i en Power BI-klientorganisation. |
| **Get-PowerBIDashboard-WorkspaceId** | Groups\_GetDashboardsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Hämtar instrumentpanelerna inom en angiven arbetsyta. |
| **Get-PowerBITile-DashboardId** | Dashboards\_GetTilesAsAdmin | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Hämtar panelerna för en angiven instrumentpanel. |
| **Get-PowerBIReport-WorkspaceId** | Groups\_GetReportsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/reports | Hämtar rapporterna inom en angiven arbetsyta. |
| **Get-PowerBIImport** | Imports\_GetImportsAsAdmin | /v1.0/myorg/admin/imports | Hämtar den fullständiga listan över importer i Power BI-klientorganisationen. |
| **Connect-PowerBIServiceAccount** | Saknas | Saknas | Logga in på Power BI och starta en session. |
| **Disconnect-PowerBIServiceAccount** | Saknas | Saknas | Logga ut från Power BI och stänga den aktuella sessionen. |
| **Invoke-PowerBIRestMethod** | Saknas | Saknas | Skicka godtyckliga REST API-anrop till Power BI. |
| **Get-PowerBIAccessToken** | Saknas | Saknas | Hämta åtkomsttoken för Power BI i en session. |
| **Resolve-PowerBIError** | Saknas | Saknas | Få detaljerad felinformation om misslyckade cmdlet-anrop. |