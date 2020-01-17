---
title: Ansluta till en webbsida från Power BI Desktop
description: Anslut enkelt till och använd webbdata i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f76d3e61c3817d3e5ab4480c935abe4dc7346e54
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761529"
---
# <a name="connect-to-webpages-from-power-bi-desktop"></a>Ansluta till webbsidor från Power BI Desktop

Du kan ansluta till en webbsida och importera data från den till Power BI Desktop för användning i visuella objekt och i datamodeller.

I **Power BI Desktop** väljer du **Hämta data > Webb** från fliken Start i menyfliksområdet.

![](media/desktop-connect-to-web/connect-to-web_1.png)

En dialogruta visas som frågar om URL-adressen till sidan som du vill importera data från.

![](media/desktop-connect-to-web/connect-to-web_2.png)

När du har skrivit (eller klistrat in) URL:en, väljer du **OK**. Power BI Desktop ansluter till sidan och sedan visas sidans tillgängliga data i fönstret **Navigator**. När du väljer ett av de tillgängliga dataelementen, till exempel en tabell över hela sidan, visar fönstret **Navigator** en förhandsgranskning av dessa data på höger sida av fönstret.

![](media/desktop-connect-to-web/connect-to-web_3.png)

Du kan välja knappen **Redigera**, som startar **Frågeredigeraren** där du kan utforma och transformera data från OData-feeden innan du importerar dem till Power BI Desktop. Eller så kan du välja knappen **Hämta** och importera alla dataelement som du har valt i den vänstra rutan.

När vi väljer **Hämta** importerar Power BI Desktop de markerade objekten och gör dem tillgängliga i fönstret **Fält** tillgängliga på höger sida av vyn Rapporter i Power BI Desktop.

![](media/desktop-connect-to-web/connect-to-web_4.png)

Svårare än så är det inte att ansluta till en webbplats och överföra dess data till Power BI Desktop.

Därifrån kan du dra fält till rapportarbetsytan och alla visuella objekt som du vill skapa. Du kan också använda data från webbplatsen precis som med andra data – du kan forma dem, skapa relationer mellan dem och andra datakällor i din modell och i övrigt göra vad du vill för att skapa den Power BI-rapporten du vill ha.

Om du vill lära dig mer om att ansluta till en webbplats, kan du läsa [Komma igång-guiden för Power BI Desktop](desktop-getting-started.md).

## <a name="next-steps"></a>Nästa steg
Det finns alla möjliga sorters data du kan ansluta till med Power BI Desktop. Kolla in följande resurser för mer information om datakällor:

* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till Excel-arbetsböcker i Power BI Desktop](desktop-connect-excel.md)   
* [Anslut till CSV-filer i Power BI Desktop](desktop-connect-csv.md)   
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

