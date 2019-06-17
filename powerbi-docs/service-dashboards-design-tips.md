---
title: Tips för att utforma en bra Power BI-instrumentpanel
description: Tips för att utforma en bra Power BI-instrumentpanel
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/22/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 0e523707caa38c808c777eb29bb8dcbdc6af5ebf
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66721207"
---
# <a name="tips-for-designing-a-great-power-bi-dashboard"></a>Tips för att utforma en bra Power BI-instrumentpanel
Nu när du har skapat en instrumentpanel och lagt till några paneler, kan du börja fundera på hur du kan vidareutveckla instrumentpanelen från att vara snygg till att också vara funktionell. I allmänhet innebär det att få den viktigaste informationen att stå ut och att gör det rent och snyggt.

Här följer några tips.

> [!TIP]
> Många av utformningsprinciperna för rapporter kan även tillämpas för instrumentpaneler.  Läs vår white paper [Best design principles for reports and visualizations (Bästa utformningsprinciperna för rapporter och visualiseringar)](visuals/power-bi-visualization-best-practices.md).
>
>

## <a name="watch-the-dashboard-makeover-webinarhttpsinfomicrosoftcomco-powerbi-wbnr-fy16-05may-12-dashboard-makeover-registrationhtml"></a>Titta på [webbseminariet om att göra om instrumentpaneler](https://info.microsoft.com/CO-PowerBI-WBNR-FY16-05May-12-Dashboard-Makeover-Registration.html)
Se Microsofts högsta programansvarige och expert på Power BI-instrumentpanelen, Marc Reguera, [göra om instrumentpaneler](https://info.microsoft.com/CO-PowerBI-WBNR-FY16-05May-12-Dashboard-Makeover-Registration.html).

## <a name="consider-your-audience"></a>Ta hänsyn till din målgrupp
Vilka är de viktigaste måtten som kommer hjälpa dem att fatta beslut? Hur ska instrumentpanelen användas? Vilka inlärda eller kulturella antaganden kan påverka utformningsvalen? Vilken information behöver din målgrupp för att lyckas?

Kom ihåg att instrumentpanelen är en översikt, en enskild plats där dina datas aktuella tillstånd kan övervakas. Instrumentpanelen baseras på underliggande rapporter och datauppsättningar och dessa kan innehålla massor av information. Dina läsare kan gå in på detaljer i rapporterna med instrumentpanelen som utgångspunkt. Så placera inte detaljerad information på instrumentpanelen, om det inte är vad läsarna behöver för att övervaka situationen.

Var ska instrumentpanelen visas? Om den ska visas på en stor skärm kan du placera mer innehåll på den. Om läsarna ska visa den på sina surfplattor blir färre paneler lättare att läsa.

## <a name="tell-a-story-and-keep-it-to-one-screen"></a>Förmedla ditt budskap och begränsa det till en skärm
Eftersom avsikten med instrumentpaneler är ge översikt över viktig information på ett ögonblick, är det bäst att ha alla paneler på en skärm. Går det att undvika rullningslister på instrumentpanelen?

Är instrumentpanelen för plottrig?  Ta bort allt utom viktig information som enkelt kan läsas och tolkas.

## <a name="make-use-of-full-screen-mode"></a>Använd dig av helskärmsläge
Visa instrumentpanelen i [helskärm](consumer/end-user-focus.md) utan störningar.

## <a name="make-the-most-important-information-biggest"></a>Gör den viktigaste informationen störst
Om texten och visualiseringarna på instrumentpanelen har samma storlek, får läsaren svårt att fokusera på vad som är viktigt. Till exempel är kortvisualiseringar ett bra sätt att visa upp ett viktigt tal på en framträdande plats:  
![Kortvisualisering](media/service-dashboards-design-tips/pbi_card.png)

Men kom ihåg att tillhandahålla kontexten.  

Läs mer om att [skapa en panel med bara ett tal](visuals/power-bi-visualization-card.md).

## <a name="put-the-most-important-information-in-the-upper-corner"></a>Placera den viktigaste informationen i det övre hörnet
De flesta läser uppifrån och ned, så placera mer allmän information högst upp och visa fler detaljer i den riktning som målgruppen läser (från vänster till höger eller från höger till vänster).

## <a name="use-the-right-visualization-for-the-data-and-format-it-for-easy-reading"></a>Använd rätt visualisering för dina data och formatera den för enklare läsning
Undvik att variera visualiseringarna bara för sakens skull.  Visualiseringar ska skapa en översiktsbild och vara enkla att ”läsa” och tolka.  För vissa data och visualiseringar räcker det med en enkel grafisk visualisering. Men andra data kan kräva en mer komplex visualisering – var noga med att använda rubriker och etiketter och andra anpassningar för att hjälpa läsaren.  

* [Välj lämpliga datavisualiseringar](https://www.youtube.com/watch?v=-tdkUYrzrio). Var försiktig med att använda diagram som förvränger verkligheten, det vill säga 3D-diagram. Tänk på att det är svårt för den mänskliga hjärnan att tolka runda figurer. Cirkeldiagram, ringdiagram, måttdiagram och andra runda diagramtyper kan se fina ut men de är inte den bästa lösningen för datavisualisering.
* Var konsekvent när du väljer skalor för diagram, bestämmer hur diagram ska dimensioneras och väljer färger för att betecknar värden i diagram.
* Var noga med att koda kvantitativa data på ett snyggt sätt. Använd inte fler än tre eller fyra siffror när tal visas. Visa mått med en eller två siffror till vänster om decimaltecknet och skala för tusen eller miljoner, det vill säga skriv 3,4 miljoner och inte 3 400 000.
* Blanda inte olika precisions- och tidsnivåer. Kontrollera att tidsramarna är lätta att förstå.  Placera inte ett diagram från förra månaden bredvid filtrerade diagram från en specifik månad det året.
* Blanda inte stora och små mått på samma skala, t.ex i ett linje- eller stapeldiagram.  Som exempel då ett mått är i miljontal och det andra i tusental.  Med en så stor skala är det svårt att se skillnaderna mellan måtten i tusental.  Om du behöver blanda ska du välja en visualisering som tillåter användning av en andra axel.
* Fyll inte dina diagram med dataetiketter som inte behövs. Värdena i stapeldiagram är vanligtvis lätta att förstå utan att man behöver visa det faktiska talet.
* Var uppmärksam på hur [diagram sorteras](consumer/end-user-change-sort.md).  Om du vill uppmärksamma det högsta eller lägsta talet kan du sortera efter mått.  Om du vill att användare snabbt ska kunna hitta en viss kategori bland många kategorier, kan du sortera efter axeln.  
* Cirkeldiagram fungerar som bäst med mindre än åtta kategorier. Eftersom man inte kan jämföra värden sida vid sida, är det svårare för att jämföra värden i ett cirkeldiagram än i ett stapel- eller kolumndiagram. Cirkeldiagram är bättre för att visa förhållanden mellan en del och helheten, än för att jämföra delarna med varandra. Och måttdiagram är bra för att visa aktuell status i kontexten för ett mål.

Mer visualiseringsspecifika anvisningar finns i [Visualiseringstyper i Power BI](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).  

## <a name="learning-more-about-best-practice-dashboard-design"></a>Mer om bästa praxis för instrumentpanelsutformning
Överväg att lära dig mer om grundläggande Gestalt-principer för visuell perception och hur du tydligt kan kommunicera åtgärdsinriktad information i en kontext om du vill bli riktigt bra på att utforma instrumentpaneler. Som tur är finns det redan en mängd olika resurser tillgängliga och utströdda i våra bloggar. Några av våra favoritböcker är:

* *Information Dashboard Design* av Stephen Few  
* *Show Me the Numbers* av Stephen Few  
* *Now You See It* av Stephen Few  
* *Envisioning Information* av Edward Tufte  
* *Advanced Presentations* av Design by Andrew Abela   

## <a name="next-steps"></a>Nästa steg
[Skapa en instrumentpanel från en rapport](service-dashboard-create.md)  
[Grundläggande begrepp för designers i Power BI-tjänsten](service-basic-concepts.md)  
Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
