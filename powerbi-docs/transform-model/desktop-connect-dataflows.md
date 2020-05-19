---
title: Ansluta till data som skapats av Power Platform-dataflöden i Power BI Desktop
description: Anslut enkelt till och använd dataflöden i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: abbe6192819daa6b5d0197d9471a8eab84596262
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83349665"
---
# <a name="connect-to-data-created-by-power-platform-dataflows-in-power-bi-desktop"></a>Ansluta till data som skapats av Power Platform-dataflöden i Power BI Desktop
I **Power BI Desktop** kan du ansluta till data som skapats av **Power Platform-dataflöden** precis som andra datakällor i Power BI Desktop.

![Anslut till dataflöden](media/desktop-connect-dataflows/connect-dataflows_01.png)

Med anslutningsappen för **Power Platform-dataflöden** kan du ansluta till entiteter som skapats av dataflöden i Power BI-tjänsten. 

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

Om du vill använda **anslutningsprogrammet för Power Platform-dataflöden** måste du köra den senaste versionen av **Power BI Desktop**. Du kan alltid [ladda ned Power BI Desktop](../fundamentals/desktop-get-the-desktop.md) och installera det på din dator för att se till att du har den senaste versionen.  

> [!NOTE]
> Den tidigare versionen av anslutningsprogrammet för Power Platform-dataflöden krävde att du hämtade en MEZ-fil och placerade den i en mapp. Aktuella versioner av **Power BI Desktop** innehåller anslutningsprogrammet för Power Platform-dataflöden, så att filen inte längre krävs och kan orsaka konflikt med den inkluderade versionen av anslutningsprogrammet. Om du manuellt placerat denna MEZ-fil i mappen *måste* du ta bort denna hämtade MEZ-fil från mappen **Dokument > Power BI Desktop > Anpassade anslutningsprogram** för att undvika konflikter. 

## <a name="desktop-performance"></a>Skrivbordsprestanda
**Power BI Desktop** körs lokalt på den dator där den är installerad. Datainmatningsprestanda för dataflöden bestäms av olika faktorer. Dessa faktorer är storleken på data, datorns processor och RAM-minne, nätverkets bandbredd, avståndet från datacentret och andra faktorer.

Du kan förbättra datainmatningens prestanda för dataflöden. Om t.ex. datainmatningen är för stor för **Power BI Desktop** för att hantera på datorn, kan du använda länkade och beräknad entiteter i dataflöden för att aggregera data (inom dataflöden) och endast mata in i förväg förberedda, sammanställda data. 

På det sättet, utförs bearbetning av stora mängder data online i dataflöden i stället för lokalt i din instans som körs av **Power BI Desktop**. Med denna metod kan Power BI Desktop mata in mindre mängder data och behåller upplevelsen av dataflöden responsiv och snabb.

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

De flesta dataflöden finns i Power BI-tjänsteklienten. Dock kan **Power BI Desktop**-användare inte komma åt dataflöden som är lagrade i Azure Data Lake Storage Gen2-kontot, såvida inte de är ägare av dataflödet eller de uttryckligen har godkänts för detta dataflödes CDM-mapp. Se följande situation:

1.  Anna skapar en ny arbetsyta och konfigurerar den så att den lagrar dataflöden i organisationens datasjö.
2.  Ben, som också är medlem i arbetsytan som Anna skapade, vill använda Power BI Desktop och anslutningsappen för dataflöden för att hämta data från det dataflöde som Anna skapade.
3.  Ben får ett fel som beror på att han inte lagts till som behörig användare i dataflödets CDM-mapp i datasjön.

    ![Fel vid försök att använda dataflöde](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_08.jpg)

För att lösa problemet, måste Ben beviljas läsbehörighet till CDM-mappen och dess filer. Du kan läsa mer om hur du ger åtkomst till Common Data Service-mappen i [den här artikeln](https://go.microsoft.com/fwlink/?linkid=2029121).




## <a name="next-steps"></a>Nästa steg
Det finns alla möjliga intressanta saker du kan göra med Power Platform-dataflöden. Mer information finns i följande källor:

* [Dataförberedelser med självbetjäning för dataflöden](service-dataflows-overview.md)
* [Skapa och använda dataflöden i Power BI](service-dataflows-create-use.md)
* [Använda beräknade entiteter i Power BI Premium (förhandsversion)](service-dataflows-computed-entities-premium.md)
* [Använda dataflöden med lokala datakällor (förhandsversion)](service-dataflows-on-premises-gateways.md)
* [Resurser för utvecklare för Power Platform-dataflöden (förhandsversion)](service-dataflows-developer-resources.md)

Mer information om integration med Azure Data Lake Storage Gen2 finns i följande artiklar:

* [Dataflöden och Azure Data Lake-integrering (förhandsversion)](service-dataflows-azure-data-lake-integration.md)
* [Konfigurera inställningar för arbetsytans dataflöde (förhandsversion)](service-dataflows-configure-workspace-storage-settings.md)
* [Lägga till en CDM-mapp i Power BI som ett dataflöde (förhandsversion)](service-dataflows-add-cdm-folder.md)
* [Ansluta Azure Data Lake Storage Gen2 för lagring av dataflöde (förhandsversion)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

Det finns även artiklar om **Power BI Desktop** som kan vara användbara:

* [Datakällor i Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Ange data direkt i Power BI Desktop](../connect-data/desktop-enter-data-directly-into-desktop.md)   
