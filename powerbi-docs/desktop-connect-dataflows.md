---
title: Ansluta till data som skapats av Power BI-dataflöden i Power BI Desktop (Beta)
description: Anslut enkelt till och använd dataflöden i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f87db1f715118f346e3b8069897e92fd157f881c
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265942"
---
# <a name="connect-to-data-created-by-power-bi-dataflows-in-power-bi-desktop-beta"></a>Ansluta till data som skapats av Power BI-dataflöden i Power BI Desktop (Beta)
I **Power BI Desktop** kan du ansluta till data som skapats av **Power BI-dataflöden** precis som andra datakällor i Power BI Desktop.

![Anslut till dataflöden](media/desktop-connect-dataflows/connect-dataflows_01.png)

Med anslutningsappen för **Power BI-dataflöden (Beta)** kan du ansluta till entiteter som skapats av dataflöden i Power BI-tjänsten. 

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

Om du vill använda den här förhandsversionen av **anslutningsappen för Power BI-dataflöden** måste du köra den senaste versionen av **Power BI Desktop**. Du kan alltid [ladda ned Power BI Desktop](desktop-get-the-desktop.md) och installera det på din dator för att se till att du har den senaste versionen.  

> [!NOTE]
> Den tidigare versionen av anslutningsprogrammet för Power BI-dataflöden krävde att du hämtade en MEZ-fil och placerade den i en mapp. Aktuella versioner av **Power BI Desktop** innehåller anslutningsprogrammet för Power BI-dataflöden, så att filen inte längre krävs och kan orsaka konflikt med den inkluderade versionen av anslutningsprogrammet. Om du manuellt placerat denna MEZ-fil i mappen *måste* du ta bort denna hämtade MEZ-fil från mappen **Dokument > Power BI Desktop > Anpassade anslutningsprogram** för att undvika konflikter. 

## <a name="desktop-performance"></a>Skrivbordsprestanda
**Power BI Desktop** körs lokalt på den dator där den är installerad. Datainmatningsprestanda för dataflöden bestäms av olika faktorer. Dessa faktorer är storleken på data, datorns processor och RAM-minne, nätverkets bandbredd, avståndet från datacentret och andra faktorer.

Du kan förbättra datainmatningens prestanda för dataflöden. Om t.ex. datainmatningen är för stor för **Power BI Desktop** för att hantera på datorn, kan du använda länkade och beräknad entiteter i dataflöden för att aggregera data (inom dataflöden) och endast mata in i förväg förberedda, sammanställda data. På det sättet, utförs bearbetning av stora mängder data online i dataflöden i stället för lokalt i din instans som körs av **Power BI Desktop**. Med denna metod kan Power BI Desktop mata in mindre mängder data och behåller upplevelsen av dataflöden responsiv och snabb.


## <a name="next-steps"></a>Nästa steg
Det finns alla möjliga intressanta saker du kan göra med Power BI-dataflöden. Mer information finns i följande källor:

* [Dataförberedelser med självbetjäning för dataflöden](service-dataflows-overview.md)
* [Skapa och använd dataflöden i Power BI](service-dataflows-create-use.md)
* [Använda beräknade entiteter på Power BI Premium (förhandsversion)](service-dataflows-computed-entities-premium.md)
* [Använda dataflöden med lokala datakällor (förhandsversion)](service-dataflows-on-premises-gateways.md)
* [Resurser för utvecklare för Power BI-dataflöden (förhandsversion)](service-dataflows-developer-resources.md)

Det finns även artiklar om **Power BI Desktop** som kan vara användbara:

* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

