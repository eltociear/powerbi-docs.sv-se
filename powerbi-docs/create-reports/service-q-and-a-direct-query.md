---
title: Använda Frågor och svar med live-anslutningar i Power BI
description: Dokumentation för att använda Power BI frågor och svar med frågor med naturligt språk på live-anslutningar till Analysis Services-data och den lokala datagatewayen.
author: maggiesMSFT
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/29/2020
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: cceeb3c874bf3320b7c826790c46b4cafd6d45a2
ms.sourcegitcommit: b66c913a50a5100082e1c8ff7cd1c4f76f514fe7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/30/2020
ms.locfileid: "84219495"
---
# <a name="enable-qa-for-live-connections-in-power-bi"></a>Aktivera Frågor och svar för live-anslutningar i Power BI

Du kan importera datauppsättningar till Power BI eller så kan du skapa en *live-anslutning* till dem. Datauppsättningar med live-anslutning är ofta lokala. I så fall kan du hantera live-anslutningar med en [gateway](../connect-data/service-gateway-onprem.md). Data och frågor skickas fram och tillbaka med hjälp av live-frågor.

> [!NOTE]
> Live-anslutningar har också stöd för Azure Analysis Services-datauppsättningar, som inte kräver en gateway.

## <a name="qa-for-on-premises-data-gateway-datasets"></a>Frågor och svar för datauppsättningar för den lokala datagatewayen
Om du vill använda frågor och svar med datauppsättningar som du kommer åt via en gateway, måste du först aktivera dem.

När du har aktiverat dem, skapar Power BI ett index av din datakälla och överför en delmängd av dessa data till Power BI för att aktivera att ställa frågor. Det kan ta flera minuter att skapa det initiala indexet och Power BI bibehåller och uppdaterar indexet automatiskt allteftersom dina data ändras. Använd frågor och svar med de här datauppsättningarna fungerar på samma sätt som med data som publicerats till Power BI. Den fullständiga uppsättningen funktioner som är tillgängliga i Frågor och svar-miljön stöds i båda fallen.

När du ställer frågor i Power BI så fastställer frågor och svar den bästa visualiseringen att skapa eller rapportarket att använda för att svara på din fråga med ett index av din datauppsättning. Efter att ha fastställt det bästa potentiella svaret, använder frågor och svar sig av DirectQuery för att hämta live-data från datakällan via gatewayen för att fylla i diagram. Det innebär att Power BI Frågor och svar alltid visar de mest aktuella data direkt från den underliggande datakällan.

Eftersom Power BI frågor och svar använder sig av text- och schemavärden från din datakälla för att fastställa hur den ska fråga den underliggande modellen, förlitar sig sökningar för specifika nya eller borttagna textvärden (som att fråga efter ett kundnamn relaterat till en nytillagd textpost) på att indexet är uppdaterat med de senaste värdena. Power BI håller automatiskt text- och schemaindexet uppdaterat inom 60 minuter från att ändringar görs.

Mer information finns i:

* Vad är den [lokala datagatewayen](../connect-data/service-gateway-onprem.md)?
* [Frågor och svar om Power BI för konsumenter](../consumer/end-user-q-and-a.md)

## <a name="enable-qa"></a>Aktivera frågor och svar
När du har ställt in datagatewayen, kan du ansluta till dina data från Power BI.  Skapa antingen en instrumentpanel med hjälp av dina lokala data eller ladda upp en .pbix-fil som använder lokala data.  Du kan också redan har lokala data i instrumentpaneler, rapporter och datauppsättningar som har delats med dig.

1. I det övre högra hörnet i Power BI väljer du kugghjulsikonen ![kugghjulsikon](media/service-q-and-a-direct-query/power-bi-cog.png) och **Inställningar**.
   
   ![Menyn Inställningar](media/service-q-and-a-direct-query/powerbi-settings.png)
2. Välj **datauppsättningar** och välj datauppsättningen att aktivera för frågor och svar.
   
   ![Skärmen Datauppsättningar i menyn Inställningar](media/service-q-and-a-direct-query/power-bi-q-and-a-settings.png)
3. Expandera **Frågor och svar**, markera kryssrutan **Aktivera Frågor och svar för den här datauppsättningen** och välj **Använd**.
   
    ![Utökat område för frågor och svar](media/service-q-and-a-direct-query/power-bi-qna-dataset-direct-query.png)

## <a name="what-data-is-cached-and-how-is-privacy-protected"></a>Vilka data cachelagras och hur skyddas sekretessen?
När du aktiverar frågor och svar för dina lokala data, cachelagras en delmängd av dina data i tjänsten. Den här cachelagringen garanterar att Frågor och svar fungerar med rimliga prestanda. Power BI utesluter värden som är längre än 24 tecken från cachelagring. Cachen tas bort inom några timmar när du inaktiverar frågor och svar genom att avmarkera **aktivera frågor och svar för den här datauppsättningen**, eller när du tar bort din datauppsättning.

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
Funktionen har vissa begränsningar:

* Inledningsvis finns funktionen endast tillgänglig för SQL Server 2016 Analysis Services Tabular-datakällor. Funktionen är optimerad för att arbeta med tabelldata. Funktionen för Frågor och svar stöds inte ännu för flera dimensioner. Ytterligare datakällor som stöds av den lokala datagatewayen kommer att lanseras löpande.
* Fullständigt stöd för säkerhet på radnivå som definierats i SQL Server Analysis Services är inte tillgängligt från början. När frågor ställs i Frågor och svar kan automatisk komplettering av frågor medan de skrivs visa strängvärden som en användare inte har åtkomst till. RLS som definierats i modellen respekteras dock för visuella objekt i rapporten och diagrammet så inga underliggande numeriska data kan visas. Alternativ för att styra det här beteenden kommer att släppas i kommande uppdateringar.
* Säkerhet på objektnivå (OLS) stöds inte. Frågor och svar tar inte hänsyn till säkerhet på objektnivå och kan visa tabell- eller kolumnnamn för användare som inte har tillgång till dem. Du bör aktivera RLS för att se till att datavärdena skyddas på lämpligt sätt. 
* Live-anslutningar stöds bara med den lokala datagatewayen. Det betyder att den här funktionen inte kan användas med den personliga gatewayen.

## <a name="next-steps"></a>Nästa steg

- [On-premises data gateway (Lokal datagateway)](../connect-data/service-gateway-onprem.md)  
- [Hantera din datakälla – Analysis Services](../connect-data/service-gateway-enterprise-manage-ssas.md)  
- [Grundläggande begrepp för designers i Power BI-tjänsten](../fundamentals/service-basic-concepts.md)  
- [Översikt över Power BI frågor och svar](../consumer/end-user-q-and-a.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
