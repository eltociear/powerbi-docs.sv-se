---
title: Använd insikter i Power BI Desktop för att förklara ökningar och minskningar i visuella objekt (förhandsversion)
description: Hämta insikter om ökningar och minskningar enkelt i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: c01af129e15025b97925f59532d1be7a6671b47f
ms.sourcegitcommit: 0611860a896e636ceeb6e30ce85243bfd8e7b61d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50909627"
---
# <a name="use-insights-in-power-bi-desktop-to-explain-increases-and-decreases-seen-in-visuals-preview"></a>Använd insikter i Power BI Desktop för att förklara ökningar och minskningar som visas i visuella objekt (förhandsversion)

Ofta ser du i visuella objekt en stor ökning och sedan ett brant fall i värden och undrar vad dessa variationer beror på. Med **insikter** i **Power BI Desktop** får du reda på orsaken med bara några få klick.

Se till exempel på följande visuella objekt som visar *Sales Amount* (Försäljningsbelopp) efter *Year* (År) och *Country* (Land). En stor minskning i försäljningen sker 2014, där försäljningen faller mycket mellan *Qtr 1* (Kvartal 1) och *Qtr 2* (Kvartal 2). I sådana fall kan du utforska data för att förklara förändringen. 

![Visuellt objekt med ökningar och minskningar](media/desktop-insights/insights_01a.png)

Du kan uppmana **Power BI Desktop** att förklara ökningar eller minskningar i diagram, visa distributionsfaktorer i diagram och få snabba, automatiserade, insiktsfulla analyser om dina data. Det är bara att högerklicka på en datapunkt och välja **Analysera> Förklara minskningen** (eller öka, om tidigare fält var lägre), or **Analysera > Sök efter var den här distributionen är annorlunda**, så levereras insikter till dig i ett lättanvänt fönster.

![Insikter visade i visuellt objekt](media/desktop-insights/insights_01.png)

Funktionen insikter är sammanhangsberoende och bygger på den direkt föregående datapunkten, till exempel föregående stapel eller kolumn.

> [!NOTE]
> Den här funktionen är en förhandsversion och kan komma att ändras. Funktionen insikter aktiveras som standard (du inte behöver markera kryssrutan Förhandsgranskning för att aktivera den) från och med versionen från September 2017 av **Power BI Desktop**.


## <a name="using-insights"></a>Använda insikter
Om du vill använda insikter till att förklara ökningar eller minskningar högerklickar du på en datapunkt i ett stapel- eller linjediagram och väljer **Analysera > Förklara ökningen** (eller *förklara minskningen* eftersom alla insikter baseras på ändringar från den tidigare datapunkten).

![Visa menyn för insikter](media/desktop-insights/insights_02.png)

**Power BI Desktop** kör sedan maskininlärningsalgoritmer över dessa data och fyller ett fönster med ett visuellt objekt och en beskrivning som visar vilka kategorier som har påverkat ökningen eller minskningen mest. Som standard visas insikter som ett *vattenfallsdiagram*, enligt följande bild.

![popup-fönster för insikter](media/desktop-insights/insights_03.png)

Genom att välja små ikoner längst ned i vattenfallsdiagrammet kan du låta insikterna visas som ett punktdiagram, stående stapeldiagram eller ett diagram i menyfliksområdet.

![trio med visuella objekt för insikter](media/desktop-insights/insights_04.png)

Ikonerna *tummen upp* och *Tummen ned* överst på sidan finns där så att du kan ge feedback om det visuella objektet och funktionen. Genom att göra det kan du lämna feedback. För närvarande innebär detta dock inte att algoritmen tränas så att resultatet påverkas nästa gång du använder funktionen.

Knappen **+** längst upp i det visuella objektet låter dig lägga till det markerade visuella objektet i rapporten, precis som om du hade skapat det visuella objektet manuellt. Sedan kan du formatera eller justera det nya visuella objektet på samma sätt som något annat visuellt objekt i din rapport. Du kan bara lägga till ett visuellt objekt med insikter när du redigerar en rapport i **Power BI Desktop**.

Du kan använda insikter när rapporten är i läs- eller redigeringsläge, vilket gör det flexibelt för dataanalys och för att skapa visuella objekt som du kan lägga till i dina rapporter.

## <a name="details-of-the-results-returned"></a>Information om de returnerade resultaten

Informationen som returneras av insikterna är tänkt att markera vad skillnaden var mellan de två tidsperioderna, så att du kan förstå förändringen mellan dem.  

Om till exempel *Sales* (Försäljning) ökade med 55 % totalt från *Qtr 3* (Kvartal 3) till *Qtr 4* (Kvartal 4), och det gäller för varje *Category* (Kategori) av produkt (försäljningen av Computer (Dator) ökade med 55 % och Audio (Stereo) och så vidare), och gäller även för alla länder och för alla kundtyper finns det inte mycket som kan identifieras i data som kan förklara förändringen. Men så är vanligtvis inte fallet och det går normalt att hitta skillnader i vad som har hänt, som att kategorierna *Computers* (Datorer) och *Home Appliances* (Hushållsapparater) växte mycket mer, 63 %, medan *TV and Audio* (TV och stereo) vara växte med 23 %, och därför bidrog *Computers* (Datorer) och *Home Appliances* (Hushållsapparater) med en större mängd av totalsumman för *Qtr 4* (Kvartal 4) än de gjorde för *Qtr 3* (Kvartal 3).  Med det här exemplet skulle en rimlig förklaring av ökningen vara: *särskilt stark försäljning för datorer och TV och stereo*. 

Så algoritmen returnerar inte bara värdena som utgör den största förändringen. Om den stora majoriteten (98 %) av försäljningen kom från USA skulle det normala vara att den stora majoriteten av ökningen också sker i USA. Men om inte USA eller några andra länder skulle ha en betydande förändring av det relativa bidraget till totalsumman skulle *Country* (Land) inte anses vara intressant i det här sammanhanget.  

Enkelt sett kan algoritmen betraktas som att den tar alla andra kolumner i modellen och gör en detaljberäkning efter den kolumnen för tidsperioderna *före* och *efter*, där det fastställs hur stor förändring som skedde på den detaljnivån, och returnerar sedan kolumnerna med den största förändringen. Till exempel valdes *Category* (Kategori) i exemplet ovan, eftersom bidraget från *TV and Video* (TV och video) föll med 7 % från 33 % till 26 %, medan bidraget från *Home Appliances* (Hushållsapparater) växte från ingenting till över 6 %. 

För varje returnerad kolumn finns det fyra visuella objekt som kan visas. Tre av dessa visuella objekt är tänkta att markera förändringen i bidrag mellan de två tidsperioderna. Till exempel förklaringen av ökningen från *Qtr 2* (Kvartal 2) till *Qtr 3* (Kvartal 3).

### <a name="the-scatter-plot"></a>Punktdiagram

Punktdiagrammet visar värdet av måttet i den första tidsperioden (på x-axeln) mot värdet av måttet i den andra tidsperioden (på y-axeln) för varje värde i kolumnen (i det här fallet *Category* (Kategori)). Därför visas alla datapunkter i den gröna regionen om värdet har ökat och i den röda regionen om det har minskat, som visas i följande bild. 

Den prickade linjen anger det bästa valet och således ökade datapunkterna ovanför den här linjen mer än den övergripande trenden och de nedanför linjen ökade mindre.  

![Punktdiagram med prickad linje](media/desktop-insights/insights_01b.png)

Obs! Dataobjekten vars värden var tomma i någon av tidsperioderna visas inte i punktdiagrammet (i det här fallet till exempel *Home Appliances* (Hushållsapparater))

### <a name="the-100-stacked-column-chart"></a>100 % stående stapeldiagram

Det visuella objektet 100 % stående stapeldiagram visar värdet på måttet före och efter, efter den valda kolumnen, med ett 100 % stående stapeldiagram. På så sätt kan du göra en jämförelse sida-vid-sida av bidraget före och efter. Knappbeskrivningarna visar det faktiska bidraget för det valda värdet.

![100 % stående stapeldiagram](media/desktop-insights/insights_01c.png)

### <a name="the-ribbon-chart"></a>Banddiagram

Det visuella objektet banddiagram visar också värdet av måttet före och efter. Det är särskilt användbart för att visa förändringarna i bidrag när *ordningen* på bidragsgivarna har förändrats (till exempel om *Computers* (Datorer) förut var den främsta bidragsgivaren men har fallit till nummer tre). 

![banddiagram](media/desktop-insights/insights_01d.png)

### <a name="the-waterfall-chart"></a>Vattenfallsdiagram

Det fjärde visuella objektet är ett vattenfallsdiagram, som visar de huvudsakliga faktiska minskningarna mellan tidsperioderna. Det här visuella objektet visar tydligt de faktiska förändringarna men anger inte ensamt förändringarna i nivån av bidrag som faktiskt visar varför kolumnen har valts som intressant. 

![vattenfallsdiagram](media/desktop-insights/insights_01e.png)

När kolumnerna rangordnas efter vilka som har de största skillnaderna i relativa bidrag tas det hänsyn till följande: 

* Kardinaliteten vägs in, då en skillnad är statistiskt mindre betydande, och mindre intressant, när en kolumn har en stor kardinalitet. 

* Skillnader mellan dessa kategorier där de ursprungliga värdena är väldigt höga eller väldigt nära noll viktas högre än andra. Exempel: Om en kategori bara har bidragit med 1 % av försäljningen och det har ändrats till 6 % är det statistiskt mer betydande, och därför anses som mer intressant, än en kategori vars bidrag har ändrats från 50 % till 55 %. 

* Olika heuristiker används för att välja det mest meningsfulla resultatet, till exempel genom att överväga andra relationer mellan data.
 
Efter att ha undersökt de olika kolumnerna väljs de kolumner som har den största förändringen av relativt bidrag och matas ut. För varje kolumn framhävs i beskrivningen värdena med den mest betydande bidragsförändringen. Dessutom framhävs även värdena med de största faktiska ökningarna och minskningarna.


## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
Eftersom dessa insikter baseras på ändringar från tidigare datapunkter är de inte tillgängliga när du väljer den första datapunkten i ett visuellt objekt. 

Följande lista är de scenarier som just nu inte stöds för att **förklara minskningen/ökningen**:

* TopN-filter
* Inkludera/exkludera filter
* Måttfilter
* Icke-numeriska mått
* Användning av ”Visa värde som”
* Filtrerade mått – Filtrerade mått är beräkningar på visuell nivå med ett specifikt filter (till exempel *totalförsäljningen för Frankrike*), och används i vissa visuella objekt som skapas av funktionen Insikter
* Kategoriska kolumner på x-axeln, såvida inte den definierar en skalär sortering enligt kolumn. Om du använder en hierarki måste alla kolumner i den aktiva hierarkin matcha det här villkoret


Dessutom stöds följande modelltyper och datakällor inte för närvarande med insikter:

* DirectQuery
* Live Connect
* Lokal Reporting Services
* Bädda in

## <a name="next-steps"></a>Nästa steg
För mer information om **Power BI Desktop**, och hur du kommer igång, ta en titt i följande artiklar.

* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
* [Frågeöversikt med Power BI Desktop](desktop-query-overview.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Anslut till data i Power BI Desktop](desktop-connect-to-data.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Vanliga frågeuppgifter i Power BI Desktop](desktop-common-query-tasks.md)   

