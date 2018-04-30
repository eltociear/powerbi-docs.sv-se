---
title: Använda granskning i din organisation
description: Lär dig hur du kan övervaka och undersöka åtgärder genom att använda granskning med Power BI. Du kan använda säkerhets- och efterlevnadscentret eller PowerShell.
services: powerbi
documentationcenter: ''
author: mgblythe
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/10/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 23fa4ea28631e7545a1d68cd1f631eb087c56b98
ms.sourcegitcommit: 312390f18b99de1123bf7a7674c6dffa8088529f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="using-auditing-within-your-organization"></a>Använda granskning i din organisation

Lär dig hur du kan övervaka och undersöka åtgärder genom att använda granskning med Power BI. Du kan använda säkerhets- och efterlevnadscentret eller PowerShell.

Att veta vem som vidtagit en viss åtgärd för ett visst objekt i din Power BI-klient kan vara av avgörande betydelse när det gäller att hjälpa organisationen att uppfylla olika krav, t.ex regelefterlevnad och posthantering.

Du kan filtrera granskningsdata efter datumintervall, användare, instrumentpanel, rapport, datamängd eller aktivitetstyp. Du kan också hämta aktiviteterna till en CSV-fil att analysera dem offline.

## <a name="requirements"></a>Krav
Du måste uppfylla följande krav för att komma åt granskningsloggar:

- Du måste ha en Exchange Online-licens (ingår i Office 365 Enterprise E3 och E5-prenumerationer) för att komma åt granskningsavsnittet i säkerhet- och efterlevnadscentrumet för Office 365.
- Du måste antingen vara global administratör eller ha en Exchange-administratörsroll som ger åtkomst till granskningsloggen. 

  Exchange-administratörsrollerna styrs via administrationscentret för Exchange. Mer information finns i [Behörigheter i Exchange Online](https://technet.microsoft.com/library/jj200692(v=exchg.150).aspx).

- Om du har åtkomst till granskningsloggen men inte är global administratör eller administratör för Power BI-tjänsten, får du inte åtkomst till Power BI-administratörsportalen. I det här fallet måste du hämta en direktlänk till säkerhet- och efterlevnadscentrumet för Office 365.

> [!NOTE]
> Om du vill visa granskningsloggar för Power BI i din klient, så måste du ha minst en Exchange-postlådelicens i din klient.

## <a name="accessing-your-audit-logs"></a>Öppna dina granskningsloggar

Om du vill granska dina Power BI-loggar måste du gå till säkerhets- och efterlevnadscentret i O365.

1. Välj **kugghjulsikonen** i det övre högra hörnet.

2. Välj **Administratörsportalen**.
   
   ![](media/service-admin-auditing/powerbi-admin.png)

3. Välj **Granskningsloggar**.
 
4. Välj **Gå till administrationscentret för O365**.
   
   ![](media/service-admin-auditing/audit-log-o365-admin-center.png)

Du kan också bläddra till [Office 365 | Säkerhet och efterlevnad](https://protection.office.com/#/unifiedauditlog).

> [!NOTE]
> Om du vill ge åtkomst till granskningsloggen för icke-administratörskonton, så måste du tilldela behörigheter i administrationscentret för Exchange Online. Du skulle t.ex. kunna tilldela en befintlig rollgrupp, som Organisationens ledning, en användare, eller så skulle du kunna skapa en ny rollgrupp med rollen Granskningsloggar. Mer information finns i [Behörigheter i Exchange Online](https://technet.microsoft.com/library/jj200692\(v=exchg.150\).aspx).

## <a name="search-only-power-bi-activities"></a>Sök endast efter Power BI-aktiviteter

Du kan begränsa resultaten till enbart Power BI-aktiviteter genom att göra följande.

1. Välj den nedrullningsbara listrutan för **Aktiviteter** under **Sök** på sidan **Sök i granskningslogg**.

2. Välj **PowerBI-aktiviteter**.
   
   ![](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Stäng markeringsrutan genom att klicka någonstans utanför den.

Dina sökningar filtreras nu enbart efter Power BI-aktiviteter.

## <a name="search-the-audit-logs-by-date"></a>Sök efter datum i granskningsloggarna

Du kan söka i loggarna efter datumintervall med hjälp av fälten Startdatum och Slutdatum. De senaste sju dagarna markeras som standard. Datum och tid som visas i UTC-format (Coordinated Universal Time). Det maximala datumintervall som du kan ange är 90 dagar. Ett felmeddelande visas om det valda datumintervallet är längre än 90 dagar.

> [!NOTE]
> Om du använder det maximala datumintervallet 90 dagar, så välj den aktuella tiden som startdatum. I annat fall får du ett felmeddelande som säger att startdatumet är senare än slutdatumet. Om du har aktiverat granskning under de senaste 90 dagarna, kan det maximala datumintervallet inte starta före det datum då granskningen aktiverades.

![](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Sök i granskningsloggarna efter användare

Du kan söka efter granskningsloggposter för aktiviteter som utförts av specifika användare. Om du vill göra detta, så ange ett eller flera användarnamn i fältet Användare.  Det handlar om de användarnamn som användarna använder när de loggar in på Power BI. Det ser ut som en e-postadress.
Om du lämnar den här rutan tom returneras poster för alla användare (och tjänstkonton) i organisationen.

![](media/service-admin-auditing/search-audit-log-by-user.png)

## <a name="viewing-search-results"></a>Visa sökresultat

När du klickar på sökknappen läses sökresultaten in och strax därpå visas de under Resultat. När sökningen är klar visas antalet funna träffar. 

> [!NOTE]
> Högst 1000 händelser visas. Om fler än 1000 händelser uppfyller sökvillkoren visas de 1000 senaste händelserna.

Resultaten innehåller följande information om varje händelse som returneras av sökningen.

| **Kolumn** | **Definition** |
| --- | --- |
| Datum |Datum och tid (i UTC-format) när händelsen inträffade. |
| IP-adress |IP-adressen för den enhet som användes när aktiviteten loggades. IP-adressen visas i IPv4- eller IPv6-adressformat. |
| Användare |Den användare (eller det tjänstkonto) som utförde den åtgärd som utlöste händelsen. |
| Aktivitet |Den aktivitet som utfördes av användaren. Det här värdet motsvarar de aktiviteter som du har markerat i listrutan Aktiviteter. Värdet i den här kolumnen är en Exchange-cmdlet för en händelse från Exchange-administratörens granskningslogg. |
| Objekt |Det objekt som skapades eller ändrades till följd av motsvarande aktivitet. Det kan t.ex. vara den fil som visades eller ändrades, eller det användarkonto som uppdaterades. Alla aktiviteter har inte något värde i den här kolumnen. |
| Information |Ytterligare information om en aktivitet. Som redan nämnts har inte alla aktiviteter något värde. |

> [!NOTE]
> Sortera resultaten genom att välja en kolumnrubrik under Resultat. Du kan sortera resultaten från A till Ö eller Ö till A. Klicka på rubriken Datum om du vill sortera resultaten från tidigast till senast eller senast till tidigast.

## <a name="view-the-details-for-an-event"></a>Visa information om en händelse

Du kan visa mer information om en händelse genom att markera händelseposten i listan med sökresultat. En sida med information visas med detaljerade egenskaper från händelseposten. Vilka egenskaper som visas beror på i vilken Office 365-tjänst som händelsen inträffar. Om du vill visa ytterligare information väljer du **Mer information**.

Följande tabell innehåller information om vad som kan visas.

| **Parameter eller händelse** | **Beskrivning** | **Ytterligare information** |
| --- | --- | --- |
| Power BI-rapport hämtades |Den här aktiviteten loggas varje gång en rapport hämtas |Rapportnamn, namn på datauppsättning |
| Skapa rapport |Den här aktiviteten loggas varje gång en ny rapport skapas. |Rapportnamn, namn på datauppsättning |
| Redigera rapporten |Den här aktiviteten loggas varje gång som en rapport redigeras. |Rapportnamn, namn på datauppsättning |
| Skapa datauppsättning |Den här aktiviteten loggas varje gång en datauppsättning skapas. |Namn på datauppsättning, DataConnectivityMode |
| Ta bort datauppsättning |Den här aktiviteten loggas varje gång en datauppsättning raderas. |Namn på datauppsättning, DataConnectivityMode |
| Skapa Power BI-app |Den här aktiviteten loggas varje gång en Power BI-app skapas |Appnamn, behörigheter, namn på arbetsyta |
| Installera Power BI-app |Den här aktiviteten loggas varje gång en Power BI-app installeras |Appnamn |
| Uppdatera Power BI-app |Den här aktiviteten loggas varje gång en Power BI-app uppdateras |Appnamn, behörigheter, namn på arbetsyta |
| En utökad utvärderingsversion av Power BI har startats |Den här aktiviteten loggas varje gång en användare accepterar den utökade Pro-utvärderingsversionen som körs fram till den 31 maj 2018 | |
| Power BI-datauppsättning analyserades |Den här aktiviteten loggas varje gång en Power BI-datauppsättning analyseras i Excel. | |
| Power BI-gateway skapades |Den här aktiviteten loggas varje gång en ny gateway skapas. |Gatewaynamn, gatewaytyp |
| Power BI-gateway togs bort |Den här aktiviteten loggas varje gång en gateway tas bort. |Gatewaynamn, gatewaytyp |
| En datakälla lades till i Power BI-gatewayen |Den här aktiviteten loggas varje gång en datakälla läggs till i gatewayen |Gatewaynamn, gatewaytyp, namn på datakälla, typ av datakälla |
| En datakälla togs bort från Power BI-gatewayen |Den här aktiviteten loggas varje gång en datakälla tas bort från en gateway |Gatewaynamn, gatewaytyp, namn på datakälla, typ av datakälla |
| Power BI gateway-administratörer ändrades |Den här aktiviteten loggas varje gång administratörer för en gateway ändras (läggs till eller tas bort) |Gatewaynamn, tillagda användare, borttagna användare |
| Användare av Power IB-gatewayens datakälla ändrades |Den här aktiviteten loggas varje gång användare för en gateway ändras (läggs till eller tas bort) |Gatewaynamn, tillagda användare, borttagna användare |
| SetScheduledRefresh |Den här aktiviteten loggas varje gång en ny uppdatering schemaläggs för en datauppsättning |Namn på datauppsättning, uppdateringsfrekvens (i minuter) |

## <a name="using-powershell-to-search"></a>Söka med PowerShell

Du kan använda PowerShell för att få åtkomst till granskningsloggarna utifrån din inloggning. Detta gör du genom att öppna Exchange Online. Här följer ett exempel på ett kommando som används för att hämta poster till Power BI-granskningsloggen.

> [!NOTE]
> Om ditt konto ska kunna använda kommandot New-PSSession måste det ha tilldelats en Exchange Online-licens och du måste ha åtkomst till din klients granskningslogg.

```
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2016 -EndDate 9/15/2016 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

Mer information om hur du ansluter till Exchange Online finns i [Anslut till Exchange Online PowerShell](https://technet.microsoft.com/library/jj984289\(v=exchg.160\).aspx).

Mer information om parametrar och om hur man använder kommandot Search-UnifiedAuditLog finns i [Search-UnifiedAuditLog](https://technet.microsoft.com/library/mt238501\(v=exchg.160\).aspx).

Om du vill se ett exempel på hur man kan använda PowerShell för att söka i granskningsloggen och sedan tilldela Power BI Pro-licenser utifrån poster finns i [Använda Power BI-granskningsloggen och PowerShell för att tilldela Power BI Pro-licenser](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/).

## <a name="export-the-power-bi-audit-log"></a>Exportera Power BI-granskningsloggen

Du kan exportera Power BI-granskningsloggen till en csv-fil.

1. Välj **Exportera resultat**.

2. Välj **Spara inlästa resultat** eller **Hämta alla resultat**.
   
   ![](media/service-admin-auditing/export-auditing-results.png)

## <a name="record-and-user-types"></a>Post- och användartyper

Granskningsloggsposterna innehåller RecordType och UserType som en del av informationen om varje post. Alla Power BI-poster har en RecordType på 20.

En fullständig lista finns i [Detaljerade egenskaper i Office 365-granskningsloggen](https://support.office.com/article/Detailed-properties-in-the-Office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3)

## <a name="list-of-activities-audited-by-power-bi"></a>Lista med aktiviteter som granskas av Power BI

| Aktivitet | Beskrivning | Ytterligare information |
| --- | --- | --- |
| CreateDashboard |Den här aktiviteten loggas varje gång som en ny instrumentpanel skapas. |– Namn på instrumentpanel. |
| EditDashboard |Den här aktiviteten loggas varje gång som en instrumentpanel byter namn. |– Namn på instrumentpanel. |
| DeleteDashboard |Den här aktiviteten loggas varje gång som en instrumentpanel tas bort. |– Namn på instrumentpanel. |
| PrintDashboard |Den här aktiviteten loggas varje gång som en instrumentpanel skrivs ut. |– Namn på instrumentpanel.<br/>– Namn på datauppsättning |
| ShareDashboard |Den här aktiviteten loggas varje gång som en instrumentpanel delas. |– Namn på instrumentpanel.<br/>– Mottagarens e-postadress.<br/>– Namn på datauppsättning.<br>– Dela behörigheter igen. |
| ViewDashboard |Den här aktiviteten loggas varje gång som en instrumentpanel visas. |– Namn på instrumentpanel. |
| ExportTile |Den här händelsen loggas varje gång som data exporteras från en panel på instrumentpanelen. |– Panelnamn.<br/>– Namn på datauppsättning. |
| DeleteReport |Den här aktiviteten loggas varje gång som en rapport tas bort. |– Rapportnamn. |
| ExportReport |Den här händelsen loggas varje gång som data exporteras från en rapportpanel. |– Rapportnamn.<br/>– Namn på datauppsättning. |
| PrintReport |Den här aktiviteten loggas varje gång som en rapport skrivs ut. |– Rapportnamn.<br/>– Namn på datauppsättning. |
| PublishToWebReport |Den här aktiviteten loggas varje gång som en rapport publiceras på webben. |– Rapportnamn.<br/>– Namn på datauppsättning. |
| ViewReport |Den här aktiviteten loggas varje gång som en rapport visas. |– Rapportnamn. |
| ExploreDataset |Den här händelsen loggas varje gång som du utforskar en datauppsättning genom att välja den. |– Namn på datauppsättning |
| DeleteDataset |Den här händelsen loggas varje gång en datauppsättning tas bort. |– Namn på datauppsättning. |
| CreateOrgApp |Den här aktiviteten loggas varje gång en organisations innehållspaket skapas. |– Namn på organisationens innehållspaket.<br/>– Instrumentpanelsnamn.<br/>– Rapportnamn.<br/>– Namn på datauppsättningar. |
| CreateGroup |Den här aktiviteten utlöses varje gång en grupp skapas. |– Gruppnamn. |
| AddGroupMembers |Den här aktiviteten loggas varje gång en medlem läggs till i en arbetsyta för en Power BI-grupp. |– Gruppnamn.<br/>– E-postadresser. |
| UpdatedAdminFeatureSwitch |Den här händelsen loggas varje gång som en administrationsfunktionsväxel ändras. |– Namn på växel.<br/>– Nya växelstatus. |
| OptInForProTrial |Den här händelsen loggas när en användare väljer att testa Power BI Pro i tjänsten. |– e-postadress |

## <a name="next-steps"></a>Nästa steg

[Power BI-administratörsportalen](service-admin-portal.md)  
[Power BI Premium – vad är det?](service-premium.md)  
[Köpa Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Behörigheter i Exchange Online](https://technet.microsoft.com/library/jj200692\(v=exchg.150\).aspx)  
[Ansluta till Exchange Online PowerShell](https://technet.microsoft.com/library/jj984289\(v=exchg.160\).aspx)  
[Search-UnifiedAuditLog](https://technet.microsoft.com/library/mt238501\(v=exchg.160\).aspx)  
[Detaljerade egenskaper i Office 365-granskningsloggen](https://support.office.com/article/Detailed-properties-in-the-Office-365-audit-log-ce004100-9e7f-443e-942b-9b04098fcfc3)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)