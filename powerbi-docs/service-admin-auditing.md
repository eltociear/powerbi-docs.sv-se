---
title: Använda granskning i din organisation
description: Lär dig hur du kan övervaka och undersöka åtgärder genom att använda granskning med Power BI. Du kan använda säkerhets- och efterlevnadscentret eller PowerShell.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 868d3dc2463f5ed94b8d8ccd85e5edff33ca1c6e
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698933"
---
# <a name="use-auditing-within-your-organization"></a>Använda granskning i din organisation

Att veta vem som har vidtagit en viss åtgärd för ett visst objekt i din Power BI-klientorganisation kan vara av avgörande betydelse när det gäller att hjälpa organisationen att uppfylla olika krav, till exempel regelefterlevnad och posthantering. Använd Power BI-granskning för att granska åtgärder som utförs av användare, till exempel ”Visa rapport” och ”Visa instrumentpanel”. Du kan inte använda granskning för att granska behörigheter.

Du arbetar med granskning i säkerhets- och efterlevnadscentrumet för Office 365 eller använder PowerShell. Granskningen förlitar sig på funktioner i Exchange Online, som etableras automatiskt som stöd för Power BI.

Du kan filtrera granskningsdata efter datumintervall, användare, instrumentpanel, rapport, datamängd och aktivitetstyp. Du kan även ladda ned aktiviteterna till en CSV-fil för att analysera dem offline.

## <a name="requirements"></a>Krav

Du måste uppfylla följande krav för att komma åt granskningsloggar:

* Du måste antingen vara global administratör eller ha tilldelats rollen Spårningsloggar eller Visa enbart spårningsloggar i Exchange Online för att få åtkomst till spårningsloggen. För rollgrupperna Efterlevnadshantering och Organisationsledning är de här rollerna som standard tilldelade på sidan **Behörigheter** i administrationscentret för Exchange.

    Om du vill ge åtkomst till granskningsloggen för icke-administratörskonton måste du lägga till användaren som en medlem i någon av dessa rollgrupper. Om du vill göra det på ett annat sätt kan du skapa en anpassad rollgrupp i administrationscentret för Exchange, tilldela gruppen någon av rollerna Spårningsloggar eller Visa enbart spårningsloggar, och sedan lägga till icke-administratörskontot till den nya rollgruppen. Mer information finns i [Hantera rollgrupper i Exchange Online](/Exchange/permissions-exo/role-groups).

    Om du inte får åtkomst till administrationscentret för Exchange från administrationscenter för Microsoft 365 går du till https://outlook.office365.com/ecp och loggar in med dina autentiseringsuppgifter.

* Om du har åtkomst till granskningsloggen men inte är global administratör eller administratör för Power BI-tjänsten får du inte åtkomst till Power BI-administratörsportalen. I det här fallet måste du använda en direktlänk till [Centrum för säkerhet och efterlevnad för Office 365](https://sip.protection.office.com/#/unifiedauditlog).

## <a name="access-your-audit-logs"></a>Komma åt dina granskningsloggar

För att komma åt loggar ska du först aktivera loggning i Power BI. Mer information finns i [Granskningsloggar](service-admin-portal.md#audit-logs) i dokumentationen för administratörsportalen. Det kan dröja upp till 48 timmar från att du aktiverar granskning till att du kan visa granskningsdata. Om du inte ser data omedelbart kontrollerar du granskningsloggarna senare. Det kan förekomma en liknande fördröjning mellan hämtning av behörighet för att visa granskningsloggar och att komma åt loggarna.

Granskningsloggar för Power BI är tillgängliga direkt via [säkerhets- och efterlevnadscenter för Office 365](https://sip.protection.office.com/#/unifiedauditlog). Det finns även en länk från Power BI-administratörsportalen:

1. I Power BI väljer du **kugghjulsikonen** i det övre högra hörnet och väljer sedan **Administratörsportalen**.

   ![Skärmbild av den nedrullningsbara kugghjulsmenyn med alternativet Administratörsportalen framhävt.](media/service-admin-auditing/powerbi-admin.png)

1. Välj **Granskningsloggar**.

1. Välj **Gå till administrationscentret för O365**.

   ![Skärmbild av Administratörsportalen med alternativen Granskningsloggar och Gå till administrationscenter för Microsoft O365 framhävda.](media/service-admin-auditing/audit-log-o365-admin-center.png)

## <a name="search-only-power-bi-activities"></a>Sök endast efter Power BI-aktiviteter

Du kan begränsa resultaten till enbart Power BI-aktiviteter genom att utföra följande steg. En lista över aktiviteter finns i [listan med aktiviteter som granskas av Power BI](#activities-audited-by-power-bi) längre fram i den här artikeln.

1. På sidan **Sök i granskningslogg** går du till **Sök** och väljer listrutan för **Aktiviteter**.

2. Välj **PowerBI-aktiviteter**.

   ![Skärmbild av Sök i granskningslogg med Power BI-aktiviteter framhävda.](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Stäng markeringsrutan genom att klicka någonstans utanför den.

Dina sökningar returnerar endast Power BI-aktiviteter.

## <a name="search-the-audit-logs-by-date"></a>Sök efter datum i granskningsloggarna

Du kan söka i loggarna efter datumintervall med hjälp av fälten **Startdatum** och **Slutdatum**. Standardvalet är de sju senaste dagarna. Datum och tid visas i UTC-format (Coordinated Universal Time). Det maximala datumintervall som du kan ange är 90 dagar. 

Ett felmeddelande visas om det valda datumintervallet är längre än 90 dagar. Om du använder det maximala datumintervallet 90 dagar, så välj den aktuella tiden som **Startdatum**. I annat fall får du ett felmeddelande som säger att startdatumet är senare än slutdatumet. Om du har aktiverat granskning under de senaste 90 dagarna, kan datumintervallet inte starta före det datum då granskningen aktiverades.

![Skärmbild av Sök i granskningslogg med alternativen Startdatum och Slutdatum framhävda.](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Sök i granskningsloggarna efter användare

Du kan söka efter granskningsloggposter för aktiviteter som utförts av specifika användare. Ange ett eller flera användarnamn i fältet **Användare**. Användarnamnet ser ut som en e-postadress. Det är det konto som användarna loggar in på Power BI med. Om du lämnar den här rutan tom returneras poster för alla användare (och tjänstkonton) i organisationen.

![Sök via användare](media/service-admin-auditing/search-audit-log-by-user.png)

## <a name="view-search-results"></a>Visa sökresultat

När du har valt **Sök** läses sökresultatet in. Efter en liten stund visas det under **Resultat**. När sökningen är klar visas antalet funna träffar. **Sök i granskningsloggs** visar högst 1000 händelser. Om fler än 1000 händelser uppfyller sökkriterierna visar appen de senaste 1000 händelserna.

### <a name="view-the-main-results"></a>Visa de viktigaste resultaten

Området **Resultat** innehåller följande information om varje händelse som returneras av sökningen. Sortera resultaten genom att välja en kolumnrubrik under **Resultat**.

| **Kolumn** | **Definition** |
| --- | --- |
| Datum |Datum och tid (i UTC-format) när händelsen inträffade. |
| IP-adress |IP-adressen för den enhet som användes för den loggade aktiviteten. Appen visar IP-adressen i antingen IPv4- eller IPv6-adressformat. |
| Användare |Den användare (eller det tjänstkonto) som utförde den åtgärd som utlöste händelsen. |
| Aktivitet |Den aktivitet som utfördes av användaren. Det här värdet motsvarar de aktiviteter som du har markerat i listrutan **Aktiviteter**. Värdet i den här kolumnen är en Exchange-cmdlet för en händelse från Exchange-administratörens granskningslogg. |
| Objekt |Det objekt som skapades eller ändrades till följd av motsvarande aktivitet. Det kan till exempel vara den visade eller ändrade filen, eller det uppdaterade användarkontot. Alla aktiviteter har inte något värde i den här kolumnen. |
| Information |Ytterligare information om en aktivitet. Som redan nämnts har inte alla aktiviteter något värde. |

### <a name="view-the-details-for-an-event"></a>Visa information om en händelse

Om du vill visa mer information om en händelse väljer du händelseposten i listan med sökresultat. Sidan **Information** visas med detaljerade egenskaper från händelseposten. På sidan **Information** visas egenskaper som beror på vilken Office 365-tjänst händelsen inträffar i.

Om du vill visa denna information väljer du **Mer information**. Alla Power BI-poster har värdet 20 för egenskapen RecordType (typ av post). Information om andra egenskaper finns i [detaljerade egenskaper i granskningsloggen](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/).

   ![Skärmbild av dialogrutan Granskningsinformation med alternativet Mer information framhävt.](media/service-admin-auditing/audit-details.png)

## <a name="export-search-results"></a>Exportera sökresultat

Du kan exportera Power BI-granskningsloggen till en CSV-fil med dessa steg.

1. Välj **Exportera resultat**.

1. Välj **Spara inlästa resultat** eller **Hämta alla resultat**.

    ![Skärmbild av alternativet Exportera resultat.](media/service-admin-auditing/export-auditing-results.png)

## <a name="use-powershell-to-search-audit-logs"></a>Använd PowerShell för att söka igenom granskningsloggar

Du kan också använda PowerShell för att få åtkomst till granskningsloggarna utifrån din inloggning. I följande exempel visas hur du ansluter till Exchange Online PowerShell och sedan använder kommandot [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) för att hämta granskningsloggsposter i Power BI. Om du vill köra skriptet måste en administratör ge dig rätt behörigheter, så som beskrivs i avsnittet [Krav](#requirements).

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

## <a name="use-powershell-to-export-audit-logs"></a>Använd PowerShell för att exportera granskningsloggar

Du kan också använda PowerShell till att exportera resultatet av din granskningsloggsökning. I följande exempel visas hur du skickar från kommandot [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) och exporterar resultatet med hjälp av cmdleten [Export-Csv](/powershell/module/microsoft.powershell.utility/export-csv). Om du vill köra skriptet måste en administratör ge dig rätt behörigheter, så som beskrivs i avsnittet [Krav](#requirements).

```powershell
$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2019 -EndDate 9/15/2019 -RecordType PowerBI -ResultSize 5000 |
Export-Csv -Path "c:\temp\PowerBIAuditLog.csv" -NoTypeInformation

Remove-PSSession $Session
```

Mer information om hur du ansluter till Exchange Online finns i [Anslut till Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/). Ett annat exempel hur PowerShell används med granskningsloggar finns i [Använda Power BI-granskningsloggen och PowerShell för att tilldela Power BI Pro-licenser](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/).

## <a name="activities-audited-by-power-bi"></a>Aktiviteter som granskas av Power BI

Följande aktiviteter granskas av Power BI:

| Eget namn                                     | Åtgärdsnamn                              | Anteckningar                                  |
|---------------------------------------------------|---------------------------------------------|------------------------------------------|
| En datakälla lades till i Power BI-gatewayen             | AddDatasourceToGateway                      |                                          |
| Power BI-mappåtkomst har lagts till                      | AddFolderAccess                             | Används inte för närvarande                       |
| Power BI-gruppmedlemmar har lagts till                      | AddGroupMembers                             |                                          |
| Administratören anslöt ett lagringskonto för dataflöde till klientorganisationen | AdminAttachedDataflowStorageAccountToTenant | Används inte för närvarande                       |
| Power BI-datauppsättning analyserades                         | AnalyzedByExternalApplication               |                                          |
| Power BI-datarapport analyserades                          | AnalyzeInExcel                              |                                          |
| Lagringskonto för dataflöden anslöts                 | AttachedDataflowStorageAccount              |                                          |
| Power BI-datamängd har bundits till gateway                | BindToGateway                               |                                          |
| Uppdatering av dataflöde avbröts                        | CancelDataflowRefresh                       |                                          |
| Kapacitetsstatus ändrades                            | ChangeCapacityState                         |                                          |
| Användartilldelning för kapacitet ändrades                  | UpdateCapacityUsersAssignment               |                                          |
| Anslutningar för Power BI-datauppsättning ändrades              | SetAllConnections                           |                                          |
| Power BI gateway-administratörer ändrades                   | ChangeGatewayAdministrators                 |                                          |
| Användare av Power BI-gatewayens datakälla ändrades        | ChangeGatewayDatasourceUsers                |                                          |
| Organisationens Power BI-innehållspaket ändrades      | CreateOrgApp                                |                                          |
| Power BI-app skapades                              | CreateApp                                   |                                          |
| Power BI-instrumentpanel skapades                        | CreateDashboard                             |                                          |
| Power BI-dataflöde skapades                         | CreateDataflow                              |                                          |
| Power BI-datauppsättning skapades                          | CreateDataset                               |                                          |
| E-postprenumeration för Power BI skapades               | CreateEmailSubscription                     |                                          |
| Power BI-mapp skapades                           | CreateFolder                                |                                          |
| Power BI-gateway skapades                          | CreateGateway                               |                                          |
| Power BI-grupp skapades                            | CreateGroup                                 |                                          |
| Power BI-rapport skapades                           | CreateReport                                |                                          |
| Dataflöde migrerades till externt lagringskonto     | DataflowMigratedToExternalStorageAccount    | Används inte för närvarande                       |
| Dataflödesbehörigheter har lagts till                        | DataFlowPermissionsAdded                    | Används inte för närvarande                       |
| Dataflödesbehörigheter har tagits bort                      | DataflowPermissionsRemoved                  | Används inte för närvarande                       |
| Organisationens Power BI-innehållspaket har tagits bort      | DeleteOrgApp                                |                                          |
| Power BI-kommentar togs bort                          | DeleteComment                               |                                          |
| Power BI-instrumentpanel togs bort                        | DeleteDashboard                             | Används inte för närvarande                       |
| Power BI-dataflöde togs bort                         | DeleteDataflow                              | Används inte för närvarande                       |
| Power BI-datauppsättning togs bort                          | DeleteDataset                               |                                          |
| E-postprenumeration för Power BI togs bort               | DeleteEmailSubscription                     |                                          |
| Power BI-mapp togs bort                           | DeleteFolder                                |                                          |
| Power BI-mappåtkomst togs bort                    | DeleteFolderAccess                          | Används inte för närvarande                       |
| Power BI-gateway togs bort                          | DeleteGateway                               |                                          |
| Power BI-grupp togs bort                            | DeleteGroup                                 |                                          |
| Power BI-rapport togs bort                           | DeleteReport                                |                                          |
| Datakällor för Power BI-datauppsättning identifierades          | GetDatasources                              |                                          |
| Power BI-rapport hämtades                        | DownloadReport                              |                                          |
| Egenskaper för dataflöde redigerades                        | EditDataflowProperties                      |                                          |
| Behörighet för Power BI-certifiering redigerades          | EditCertificationPermission                 | Används inte för närvarande                       |
| Power BI-instrumentpanel redigerades                         | EditDashboard                               | Används inte för närvarande                       |
| Power BI-datauppsättning redigerades                           | EditDataset                                 |                                          |
| Egenskaper för Power BI-datauppsättning redigerades                | EditDatasetProperties                       | Används inte för närvarande                       |
| Power BI-rapport redigerades                            | EditReport                                  |                                          |
| Power BI-dataflöde exporterades                        | ExportDataflow                              |                                          |
| Visuella data för Power BI-rapport exporterades              | ExportReport                                |                                          |
| Power BI-paneldata exporterades                       | ExportTile                                  |                                          |
| Det gick inte att lägga till behörigheter för dataflöde                | FailedToAddDataflowPermissions              | Används inte för närvarande                       |
| Det gick inte att ta bort behörigheter för dataflöde             | FailedToRemoveDataflowPermissions           | Används inte för närvarande                       |
| SAS-token för Power BI dataflöde genererades             | GenerateDataflowSasToken                    |                                          |
| Inbäddningstoken för Power BI genererades                    | GenerateEmbedToken                          |                                          |
| Fil importerades till Power BI                         | Importera                                      |                                          |
| Power BI-appen installerades                            | InstallApp                                  |                                          |
| Arbetsytan migrerades till en kapacitet                  | MigrateWorkspaceIntoCapacity                |                                          |
| Power BI-kommentar lades upp                           | PostComment                                 |                                          |
| Power BI-instrumentpanel skrevs ut                        | PrintDashboard                              |                                          |
| Power BI-rapportsida skrevs ut                      | PrintReport                                 |                                          |
| Power BI-rapport publicerades på webben                  | PublishToWebReport                          |                                          |
| Power BI-dataflödeshemlighet togs emot från Key Vault  | ReceiveDataflowSecretFromKeyVault           |                                          |
| En datakälla togs bort från Power BI-gatewayen         | RemoveDatasourceFromGateway                 |                                          |
| Power BI-gruppmedlemmar togs bort                    | DeleteGroupMembers                          |                                          |
| Arbetsyta togs bort från en kapacitet                 | RemoveWorkspacesFromCapacity                |                                          |
| Power BI-instrumentpanel döptes om                        | RenameDashboard                             |                                          |
| Uppdatering av Power BI-dataflöde begärdes               | RequestDataflowRefresh                      | Används inte för närvarande                       |
| Uppdatering av Power BI-datauppsättning begärdes                | RefreshDataset                              |                                          |
| Power BI-arbetsytor hämtades                     | GetWorkspaces                               |                                          |
| Lagringsplats för dataflöden för en arbetsyta angavs     | SetDataflowStorageLocationForWorkspace      |                                          |
| Schemalagd uppdatering i Power BI-dataflödet konfigurerades        | SetScheduledRefreshOnDataflow               |                                          |
| Schemalagd uppdatering i Power BI-datauppsättningen konfigurerades         | SetScheduledRefresh                         |                                          |
| Power BI-instrumentpanel delades                         | ShareDashboard                              |                                          |
| Power BI-rapport delades                            | ShareReport                                 |                                          |
| En utökad utvärderingsversion av Power BI har startats                   | OptInForExtendedProTrial                    | Används inte för närvarande                       |
| Power BI-utvärderingsversion startades                            | OptInForProTrial                            |                                          |
| Datakälla för Power BI togs över                   | TakeOverDataset                          |                                          |
| Datauppsättning för Power BI togs över                        | TakeOverDataset                             |                                          |
| Ett dataflöde i Power BI togs över                     | TookOverDataflow                             |                                          |
| Power BI-appen avpublicerades                          | UnpublishApp                                |                                          |
| Kapacitetens resursstyrningsinställningar uppdaterades      | UpdateCapacityResourceGovernanceSettings    | För närvarande inte i administrationscenter för Microsoft 365 |
| Kapacitetsadministratörer uppdaterades                            | UpdateCapacityAdmins                        |                                          |
| Kapacitetens visningsnamn uppdaterades                     | UpdateCapacityDisplayName                   |                                          |
| Behörigheter för tilldelning av dataflödeslagring uppdaterades   | UpdatedDataflowStorageAssignmentPermissions |                                          |
| Organisationens Power BI-inställningar uppdaterades          | UpdatedAdminFeatureSwitch                   |                                          |
| Power BI-appen uppdaterades                              | UpdateApp                                   |                                          |
| Power BI-dataflödet uppdaterades                         | UpdateDataflow                              |                                          |
| Datakällor för Power BI-datauppsättning uppdaterades             | UpdateDatasources                           |                                          |
| Parametrar för Power BI-datauppsättning uppdaterades               | UpdateDatasetParameters                     |                                          |
| E-postprenumeration för Power BI uppdaterades               | UpdateEmailSubscription                     |                                          |
| Power BI-mapp uppdaterades                           | UpdateFolder                                |                                          |
| Power BI-mappåtkomst uppdaterades                    | UpdateFolderAccess                          |                                          |
| Inloggningsuppgifter för Power BI-gatewayens datakälla uppdaterades  | UpdateDatasourceCredentials                 |                                          |
| Power BI-instrumentpanelen visades                         | ViewDashboard                               |                                          |
| Power BI-dataflödet visades                          | ViewDataflow                                |                                          |
| Power BI-rapporten visades                            | ViewReport                                  |                                          |
| Power BI-panelen visades                              | ViewTile                                    |                                          |
| Användningsstatistik för Power BI visades                     | ViewUsageMetrics                            |                                          |
|                                                   |                                             |                                          |

## <a name="next-steps"></a>Nästa steg

[Vad är Power BI-administration?](service-admin-administering-power-bi-in-your-organization.md)  

[Power BI-administratörsportalen](service-admin-portal.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
