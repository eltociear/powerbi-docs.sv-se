---
title: Använd frågor och svar med live-anslutningar
description: Dokumentation för att använda Power BI frågor och svar med frågor med naturligt språk på live-anslutningar till Analysis Services-data och den lokala datagatewayen.
services: powerbi
documentationcenter: ''
author: mihart
manager: kfile
backup: mihart
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/01/2018
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: c6fa26d85d362af0d66276509f4e52ba718d338a
ms.sourcegitcommit: 65426de556cd7207cbc4f478198664e25c33a769
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/30/2018
---
# <a name="enable-qa-for-live-connections"></a>Aktivera frågor och svar för live-anslutningar
## <a name="what-is-on-premises-data-gateway--what-is-a-live-connection"></a>Vad är den lokala datagatewayen?  Vad är en live-anslutning?
Datauppsättningar i Power BI kan importeras till Power BI eller så kan du skapa en live-anslutning till dem. Datauppsättningar med live-anslutning kallas ofta lokala. Live-anslutningarna hanteras med en [gateway](service-gateway-onprem.md). Data och frågor skickas fram och tillbaka med hjälp av live-frågor.

## <a name="qa-for-on-premises-data-gateway-datasets"></a>Frågor och svar för datauppsättningar för den lokala datagatewayen
Om du vill använda frågor och svar med datauppsättningar som du kommer åt via en gateway, måste du först aktivera dem.

När du har aktiverat dem, skapar Power BI ett index av din datakälla och överför en delmängd av dessa data till Power BI för att aktivera att ställa frågor. Det kan ta flera minuter att skapa det initiala indexet och Power BI bibehåller och uppdaterar indexet automatiskt allteftersom dina data ändras. Använd frågor och svar med de här datauppsättningarna fungerar på samma sätt som med data som publicerats till Power BI. Den fullständiga uppsättningen funktioner som finns i frågor och svar-upplevelsen stöds i bägge fall, inklusive att använda datakällan med Cortana.

När du ställer frågor i Power BI så fastställer frågor och svar den bästa visualiseringen att skapa eller rapportarket att använda för att svara på din fråga med ett index av din datauppsättning. Efter att ha fastställt det bästa potentiella svaret, använder frågor och svar sig av DirectQuery för att hämta live-data från datakällan via gatewayen för att fylla i diagram. Det här säkerställer att resultat från Power BI frågor och svar alltid visar de mest uppdaterade data från den underliggande datakällan.

Eftersom Power BI frågor och svar använder sig av text- och schemavärden från din datakälla för att fastställa hur den ska fråga den underliggande modellen, förlitar sig sökningar för specifika nya eller borttagna textvärden (som att fråga efter ett kundnamn relaterat till en nytillagd textpost) på att indexet är uppdaterat med de senaste värdena. Power BI håller automatiskt text- och schemaindexet uppdaterat inom ett 60 minuter från att ändringar görs.

Mer information finns i:

* Vad är den [lokala datagatewayen](service-gateway-onprem.md)?
* [Introduktion till Power BI frågor och svar](power-bi-q-and-a.md)

## <a name="enable-qa"></a>Aktivera frågor och svar
När du har ställt in datagatewayen, kan du ansluta till dina data från Power BI.  Skapa antingen en instrumentpanel med hjälp av dina lokala data eller ladda upp en .pbix-fil som använder lokala data.  Du kan också redan har lokala data i instrumentpaneler, rapporter och datauppsättningar som har delats med dig.

1. I det övre högra hörnet i Power BI väljer du kugghjulsikonen ![kugghjulsikon](media/service-q-and-a-direct-query/power-bi-cog.png) och **Inställningar**.
   
   ![Menyn Inställningar](media/service-q-and-a-direct-query/powerbi-settings.png)
2. Välj **datauppsättningar** och välj datauppsättningen att aktivera för frågor och svar.
   
   ![Skärmen Datauppsättningar i menyn Inställningar](media/service-q-and-a-direct-query/power-bi-q-and-a-settings.png)
3. Expandera **frågor och svar och Cortana**, markerar kryssrutan för **aktivera frågor och svar för den här datauppsättningen** och välj **tillämpa**.
   
    ![Utökat område för frågor och svar](media/service-q-and-a-direct-query/power-bi-q-and-a-directquery.png)

## <a name="what-data-is-cached-and-how-is-privacy-protected"></a>Vilka data cachelagras och hur skyddas sekretessen?
När du aktiverar frågor och svar för dina lokala data, cachelagras en delmängd av dina data i tjänsten. Det här görs för att säkerställa att frågor och svar fungerar med en rimlig prestanda. Power BI utesluter värden som är längre än 24 tecken från cachelagring. Cachen tas bort inom några timmar när du inaktiverar frågor och svar genom att avmarkera **aktivera frågor och svar för den här datauppsättningen**, eller när du tar bort din datauppsättning.

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
Det finns flera begränsningar under förhandsvisningsfasen av den här funktionen:

* Inledningsvis finns funktionen endast tillgänglig för SQL Server 2016 Analysis Services Tabular-datakällor. Funktionen är optimerad för att arbeta med tabelldata. Vissa funktioner är tillgänglig för flerdimensionella datakällor, men den fullständiga frågor och svar-upplevelsen stöds inte ännu för flera dimensioner. Ytterligare datakällor som stöds av den lokala datagatewayen kommer att lanseras löpande.
* Fullständigt stöd för säkerhet på radnivå som definierats i SQL Server Analysis Services är inte tillgängligt från början i den allmänna förhandsvisningen. När du ställer frågor i frågor och svar, kan automatisk komplettering av frågor medan du skriver visa strängvärden som en användare inte har åtkomst till. RLS som definierats i modellen respekteras dock för visuella objekt i rapporten och diagrammet så inga underliggande numeriska data kan visas. Alternativ för att styra det här beteenden kommer att släppas i kommande uppdateringar.
* Live-anslutningar stöds bara med den lokala datagatewayen. Därmed kan de inte användas med din den personliga gatewayen.

## <a name="next-steps"></a>Nästa steg
[Lokal datagateway](service-gateway-onprem.md)  
[Hantera din datakälla – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Power BI – grundläggande begrepp](service-basic-concepts.md)  
[Översikt över Power BI frågor och svar](power-bi-q-and-a.md)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

