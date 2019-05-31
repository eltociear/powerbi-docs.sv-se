---
title: Felsöka uppdateringsscenarier
description: Felsöka uppdateringsscenarier
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: mblythe
LocalizationGroup: Data refresh
ms.openlocfilehash: ce353ec70b933319faaabb0040c0df1a31103a27
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770521"
---
# <a name="troubleshooting-refresh-scenarios"></a>Felsöka uppdateringsscenarier
Här hittar du information om olika scenarier som du kan stöta på när du uppdaterar data i Power BI-tjänsten.

> [!NOTE]
> Om det uppstår ett fel som inte finns i listan nedan och det orsakar problem, kan du be att få ytterligare hjälp på [community-webbplatsen](http://community.powerbi.com/) eller så kan du skapa ett [supportärende](https://powerbi.microsoft.com/support/).
> 
> 

## <a name="refresh-using-web-connector-doesnt-work-properly"></a>Uppdatering med hjälp av webbanslutningen fungerar inte korrekt
Om du har ett webbanslutningsskript som använder funktionen [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx) och du har uppdaterat din datauppsättning eller rapport efter den 18 november 2016, måste du använda en gateway för att uppdateringen ska fungera korrekt.

## <a name="unsupported-data-source-for-refresh"></a>Datakälla utan stöd för uppdatering
När du konfigurerar en datauppsättning, kan du få ett felmeddelande om att datauppsättningen använder en datakälla som inte stöds för uppdatering. Mer information finns i [Felsöka datakälla utan stöd för uppdatering](service-admin-troubleshoot-unsupported-data-source-for-refresh.md)

## <a name="dashboard-doesnt-reflect-changes-after-refresh"></a>Instrumentpanelen återger inte ändringar efter uppdatering
Vänta ungefär 10–15 minuter för att uppdateringen ska återspeglas på instrumentpanelens paneler.  Om den fortfarande inte visas, fäster du visualiseringen på instrumentpanelen på nytt.

## <a name="gatewaynotreachable-when-setting-credentials"></a>GatewayNotReachable när du anger autentiseringsuppgifter
Du kan stöta på GatewayNotReachable vid försök att ange autentiseringsuppgifter för en datakälla. Detta kan bero på en inaktuell gateway.  Installera den senaste gatewayen och försök igen.

## <a name="processing-error-the-following-system-error-occurred-type-mismatch"></a>Bearbetningsfel: Följande systemfel uppstod: Typmatchningsfel
Detta kan bero på ett problem med M-skriptet i din Power BI Desktop-fil eller Excel-arbetsbok.  Det kan också bero på en inaktuell version av Power BI Desktop.

## <a name="tile-refresh-errors"></a>Paneluppdateringsfel
En lista över fel som kan uppstå med panelerna på instrumentpaneler och förklaringar till dessa visas i [Felsöka panelfel](refresh-troubleshooting-tile-errors.md).

## <a name="refresh-fails-when-updating-data-from-sources-that-use-aad-oauth"></a>Uppdateringen misslyckas vid uppdatering av data från källor som använder AAD OAuth
Ett Azure Active Directory (**AAD**) OAuth-token som används av flera olika datakällor, upphör att gälla om ungefär en timme. Du kan hamna i situationer där inläsning av data tar längre tid än den tid du har på dig innan ditt token upphör att gälla (mer än en timme), eftersom Power BI-tjänsten väntar upp till två timmar vid inläsning av data. I dessa fall kan processen för datainläsning misslyckas och ett fel relaterat till autentiseringsuppgifter kan visas.

De datakällor som använder AAD OAuth är bland annat **Microsoft Dynamics CRM Online**, **SharePoint Online** (SPO) och så vidare. Om du ansluter till sådana datakällor och får ett fel relaterat till autentiseringsuppgifter när datainläsningen tar mer än en timme, kan detta vara orsaken.

Microsoft undersöker en lösning som medför att datainläsningsprocessen uppdaterar din token och fortsätter. Om din Dynamics CRM Online- eller SharePoint Online-instans (eller annan AAD OAuth-datakälla) är så stor att den kan överskrida datainläsningströskeln på två timmar, kan det hända att även Power BI-tjänsten tar en datainläsnings-timeout.

Observera också att du måste använda samma konto som du använder för att logga in i **Power BI-tjänsten** för att uppdateringen ska fungera korrekt vid anslutning till en **SharePoint Online**-datakälla med AAD OAuth.

## <a name="uncompressed-data-limits-for-refresh"></a>Gränser för okomprimerade data vid uppdatering
Den maximala storleken för datauppsättningar som importerats till **Power BI-tjänsten** är 1 GB. Dessa datauppsättningar är kraftigt komprimerade för att säkerställa hög prestanda. Dessutom begränsar tjänsten mängden okomprimerade data som bearbetas under uppdateringen till 10 GB vid delad kapacitet. Denna begränsning rör komprimeringen och är därför mycket högre än 1 GB. Datauppsättningar i Power BI Premium omfattas inte av den här gränsen. Om uppdateringen i Power BI-tjänsten misslyckas av det här skälet, kan du minska mängden data som importeras till Power BI och försöka igen.

## <a name="scheduled-refresh-timeout"></a>Timeout vid schemalagd uppdatering
Tidsgränsen för schemalagd uppdatering för importerade datauppsättningar är två timmar. Denna timeout ökar till fem timmar för datauppsättningar på **Premium**-arbetsytor. Om du stöter på den här gränsen kan du minska datauppsättningens storlek eller komplexitet eller dela upp den i mindre delar.

## <a name="scheduled-refresh-failures"></a>Fel vid schemalagd uppdatering
Om en schemalagd uppdatering misslyckas fyra gånger i rad inaktiverar uppdateringen i Power BI. Korrigera bakomliggande problem och sedan återaktivera den schemalagda uppdateringen.

## <a name="access-to-the-resource-is-forbidden"></a>Åtkomst till resursen är förbjuden  
Det här felet kan inträffa på grund av utgångna cachelagrade autentiseringsuppgifter. Rensa cacheminnet för webbläsaren genom att logga in i Power BI och gå till https://app.powerbi.com?alwaysPromptForContentProviderCreds=true. Detta tvingar fram en uppdatering av dina autentiseringsuppgifter. 
    
    
## <a name="data-refresh-failure-because-of-password-change-or-expired-credentials"></a>Uppdatering av data misslyckades på grund av ändring av lösenord eller att autentiseringsuppgifterna har upphört att gälla 
Datauppdatering kan också misslyckas på grund av utgångna cachelagrade autentiseringsuppgifter. Rensa cacheminnet för webbläsaren genom att logga in i Power BI och gå till https://app.powerbi.com?alwaysPromptForContentProviderCreds=true. Detta tvingar fram en uppdatering av dina autentiseringsuppgifter.


## <a name="next-steps"></a>Nästa steg
[Datauppdatering](refresh-data.md)  
[Felsöka den lokala datagatewayen](service-gateway-onprem-tshoot.md)  
[Felsöka Power BI Gateway – Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

