---
title: Prestandaövervakning för gateway (offentlig förhandsversion)
description: Den här artikeln innehåller information om övervakning av prestanda i lokala data gateway aktiviteter.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 05/08/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 8c5f4170383f31ea465ebb7035aebfb53f551982
ms.sourcegitcommit: af2b2238fe77eaa1b2392a19a143a0250b8665cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535377"
---
# <a name="gateway-performance-monitoring-public-preview"></a>Prestandaövervakning för gateway (offentlig förhandsversion)

För att övervaka prestanda, gateway-administratörer har traditionellt är beroende av manuellt övervaka prestandaräknare med verktyget Windows Performance Monitor. Nu erbjuder vi ytterligare loggning och en [Gateway prestanda PBI-mallfil](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) att visualisera resultatet. Den här funktionen ger nya insikter om gatewayens användning och tillåter dig att felsöka långsamma frågor.

> [!NOTE]
> Den här funktionen finns för närvarande endast för den lokala datagatewayen i standard-läge och inte för det personliga läget.

## <a name="enable-performance-logging"></a>Aktivera prestandaloggning

Om du vill aktivera den här funktionen gör följande ändringar till den *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* fil i den ”\Program Files\On-lokal datagateway” mappen:

1. Uppdatera **QueryExecutionReportOn** till _SANT_ att aktivera ytterligare loggning för frågor som körs med gatewayen. Aktivera det här alternativet skapar både Körningsrapport fråga och fråga aggregering Körningsrapport-filer.

   ``` xml
   <setting name="QueryExecutionReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Uppdatera **SystemCounterReportOn** till _SANT_ att aktivera ytterligare loggning för minne och CPU-Systemräknare. När du aktiverar det här alternativet skapas rapportfilen System räknaren aggregering.

   ```xml
   <setting name="SystemCounterReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Det finns andra värden i konfigurationsfilen som du kan uppdatera efter behov.

    - **ReportFilePath**: Anger sökvägen till platsen där tre loggfilerna lagras. Som standard är den här sökvägen ”\Users\PBIEgwService\AppData\Local\Microsoft\On-premises data gateway\Report” eller ”Windows\ServiceProfiles\PBIEgwService\AppData\Local\Microsoft\On lokala data gateway\Report”, beroende på versionen av Operativsystemet. Om du använder ett tjänstkonto för gatewayen än _PBIEgwService_, ersätter den här delen av sökvägen med namnet på tjänstkontot.
    - **ReportFileCount**: Anger antalet loggfiler för varje typ om du vill behålla. Standardvärdet är 10.
    - **ReportFileSizeInBytes**: Anger storleken på filen för att underhålla. Standardvärdet är 104857600.
    - **QuerExecutionAggregationTimeInMinutes**: Anger hur många minuter som frågan körning informationen sammanställs. Standardvärdet är 5.
    - **SystemCounterAggregationTimeInMinutes**: Anger hur många minuter som Systemräknare slås samman. Standardvärdet är 5.

1. När du har gjort ändringarna i konfigurationsfilen, startar du om gatewayen för dessa konfigurationsvärden ska börja gälla. Nu börjar du se de filer som genereras i den plats du angav för **ReportFilePath**.

    > [!NOTE]
    > Det kan ta upp till 10 minuter plus tidsperioden som angetts för **QuerExecutionAggregationTimeInMinutes** i konfigurationsfilen tills filerna börjar visas i mappen.

## <a name="understand-performance-logs"></a>Förstå Prestandaloggar

När du aktiverar den här funktionen skapar vi tre nya loggfiler:

- Körningsrapport fråga
- Fråga aggregering Körningsrapport
- System räknaren aggregering-rapport

Körningsrapport frågan innehåller detaljerade frågeinformation för körning. Vi samla in följande attribut:

|Attribut |Beskrivning |
| ---- | ---- |
|**GatewayObjectId** |Unik identifierare för gatewayen. |
|**RequestId** |Unik identifierare för en gateway-begäran. Det kan vara samma för flera frågor. |
|**DataSource** |Innehåller både typ av datakälla och datakällan. |
|**QueryTrackingId** |Unik identifierare för en fråga. |  
|**QueryExecutionEndTimeUTC** |Tid när körningen av frågan har slutförts. |
|**QueryExecutionDuration**(ms) |Varaktighet för körning av en fråga. |
|**QueryType** |Typ av fråga – till exempel, skickas frågan kan vara en uppdatering/DirectQuery i Power BI eller frågor från PowerApps och Microsoft Flow. |
|**DataProcessingEndTimeUTC** |Tid då databearbetning aktiviteter som uppskjutna, datahämtning, komprimering, databearbetning och så vidare har slutförts. |
|**DataProcessingDuration**(ms) |Varaktighet för bearbetning av aktiviteter som uppskjutna, datahämtning, komprimering, databearbetning och så vidare. |
|**Lyckades** |Anger om frågan lyckades eller misslyckades. |
|**ErrorMessage** |Om frågan misslyckades, anger du ett felmeddelande. |
| | |

Fråga aggregering Körningsrapport innehåller frågeinformation avgifter för ett tidsintervall genom att **GatewayObjectId**, **DataSource**, **lyckades**, och **QueryType**. Standardvärdet är 5 minuter, men du kan justera det som beskrivs nedan. Vi samla in följande attribut:

|Attribut |Beskrivning |
| ---- | ---- |
|**GatewayObjectId** |Unik identifierare för gatewayen. |
|**AggregationStartTimeUTC** |Början av tidsperioden som frågan attribut har aggregeras. |
|**AggregationEndTimeUTC** |Slutet av tidsperioden för vilken fråga attribut har aggregeras. |
|**DataSource** |Innehåller både typ av datakälla och datakällan. |
|**Lyckades** |Anger om frågan lyckades eller misslyckades. |
|**AverageQueryExecutionDuration**(ms) |Genomsnittlig körningstid för frågan för aggregering tidsfönstret. |
|**MaxQueryExecutionDuration**(ms) |Maximal körningstid för aggregering tidsfönstret. |
|**MinQueryExecutionDuration**(ms) |Minsta fråga körningstid för aggregering tidsfönstret. |
|**QueryType** |Typ av fråga – till exempel, skickas frågan kan vara en uppdatering/DirectQuery i Power BI eller frågor från PowerApps och Microsoft Flow. |
|**AverageDataProcessingDuration**(ms) |Genomsnittlig tid för bearbetning av aktiviteter som uppskjutna, datahämtning, komprimering, databearbetning, och så vidare för tidsfönstret aggregering. |
|**MaxDataProcessingDuration**(ms) |Maximal tid för bearbetning av aktiviteter som uppskjutna, datahämtning, komprimering, databearbetning och så vidare för aggregering tidsfönstret. |
|**MinDataProcessingDuration**(ms) |Minsta tiden för bearbetning av aktiviteter som uppskjutna, datahämtning, komprimering, databearbetning och så vidare för aggregering tidsfönstret. |
|**Antal** |Antal frågor. |
| | |

System räknaren aggregering rapporten innehåller system räknarvärden avgifter för ett tidsintervall. Standardvärdet är 5 minuter, men du kan justera det som beskrivs nedan. Vi samla in följande attribut:

|Attribut |Beskrivning |
| ---- | ---- |
|**GatewayObjectId** |Unik identifierare för gatewayen. |
|**AggregationStartTimeUTC** |Början av tidsfönstret innehålla samlade Systemräknare. |
|**AggregationEndTimeUTC** |Slutet av tidsperioden för vilka system räknare har aggregerats. |
|**CounterName** |Systemräknare för, inklusive minne och CPU-användning av gateway, kombinationsprogram, och den totala av datorn som är värd för gatewayen. |
|**Max** |Högsta värdet för räknaren system för tidsfönstret aggregering. |
|**Min** |Minsta värde för räknaren system för tidsfönstret aggregering. |
|**Medelvärde** |Medelvärdet för räknaren system för tidsfönstret aggregering. |
| | |

## <a name="visualize-gateway-performance"></a>Visualisera gatewayens prestanda

Nu kan visualisera du de data som finns i loggfilerna.

1. Ladda ned den [Gateway prestanda PBI mall](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) och öppna den med hjälp av Power BI desktop.

1. I dialogrutan som öppnas, kontrollerar du att sökvägen till mappen matchar värdet i **ReportFilePath**.

    ![Popup-fönstret för mappsökvägen](media/service-gateway-performance-monitoring/gateway-folder-path-pop-up.png)

1. Välj **belastningen**, och mallfilen börjar läsa in data från din loggfiler. Alla visuella objekt bör sedan ha fyllts i med hjälp av data i rapporterna.

1. Du kan också spara filen som en PBIX och publicera den till din tjänst för automatiska uppdateringar.

Du kan dessutom anpassa den här mallfilen så att den passar dina behov. Mer information om Power BI-mallar finns i den här [Microsoft Power BI-blogginlägg](https://powerbi.microsoft.com/en-us/blog/deep-dive-into-query-parameters-and-power-bi-templates/).