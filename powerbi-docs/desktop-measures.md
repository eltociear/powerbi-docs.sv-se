---
title: Använda mått i Power BI Desktop
description: Mått i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 43c103dcef6caad7e9aa36ab0f1c32939ee2dda6
ms.sourcegitcommit: f01a88e583889bd77b712f11da4a379c88a22b76
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39328590"
---
# <a name="measures-in-power-bi-desktop"></a>Mått i Power BI Desktop
**Power BI Desktop** hjälper dig att skapa insikter om dina data med bara några klickningar. Men data innehåller ibland inte allt du behöver för att besvara några av dina viktigaste frågor. Mått kan vara en hjälp på vägen.

Mått används i några av de vanligaste dataanalyserna; till exempel summa, medelvärden, lägsta eller högsta värden, antal eller mer avancerade beräkningar som du skapar själv med hjälp av en DAX-formel. Det beräknade resultatet av mått ändras alltid när du interagerar med dina rapporter, vilket ger snabb och dynamisk utforskning av dina data. Låt oss ta en närmare titt.

## <a name="understanding-measures"></a>Förstå mått
I **Power BI Desktop** skapas och används mått i **Rapportvyn** eller **Datavyn**. Åtgärder som du skapar själv visas i fält med en Kalkylatorikon. Du kan kalla åtgärder vad du vill och lägga till dem i en ny eller befintlig visualisering precis som ett annat fält.

![](media/desktop-measures/measuresinpbid_measinfieldlist.png)

> [!NOTE]
> Du kan också vara intresserad av **snabbåtgärder**, som är färdiga åtgärder som du kan välja från dialogrutor. Det är ett bra sätt att snabbt skapa mått och ett bra sätt att lära dig DAX-syntaxen, eftersom de automatiskt skapade formlerna DAX är tillgängliga att granska. Läs artikeln: [snabbåtgärder](desktop-quick-measures.md).
> 
> 

## <a name="data-analysis-expressions"></a>Data Analysis-uttryck
Mått beräknar ett resultat från en uttrycksformel. När du skapar egna åtgärder, använder du formelspråket [Data Analys-uttryck](https://msdn.microsoft.com/library/gg413422.aspx) (DAX). DAX innehåller ett bibliotek med över 200 funktioner, operatörer och konstruktioner och ger stor flexibilitet vid skapande av mått för att beräkna resultat för nästan alla dataanalysbehov.

DAX-formler påminner mycket om Excel formler. DAX innehåller även många funktionerna som DATE, SUM och LEFT. Men funktionerna i DAX är avsedda för användning med relationsdata som de vi har i Power BI Desktop.

## <a name="lets-look-at-an-example"></a>Låt oss ta en titt på ett exempel
Jan är försäljningschef på Contoso. Hon har blivit ombedd att ange försäljningsprognoser för återförsäljare under nästa räkenskapsår. Hon bestämmer sig för att basera sina uppskattningar på förra årets försäljningar med sex procents årlig ökning baserat på olika kampanjer som har schemalagts över de senaste sex månaderna.

För att rapportera uppskattningarna importerar hon fjolårets säljdata i Power BI Desktop. Hon hittar fältet SalesAmount i tabellen Reseller Sales. Eftersom de data som hon har importerat endast innehåller försäljningssiffror för det senaste året ändrar hon namn på fältet SalesAmount till Förra årets försäljning. Sedan drar hon Förra årets försäljning till rapportarbetsytan. Den visas i ett diagram som ett enda värde, vilket är summan av alla återförsäljares försäljning förra året.

Hon observerar att en beräkning har angetts automatiskt, trots att hon inte har specificerat någon. Power BI Desktop skapade ett eget mått genom att addera alla värden i Förra årets försäljning.

Men Jan behöver ett mått för att beräkna en uppskattning för nästa år som bygger på förra årets försäljning multiplicerat med 1,06, för att ta den förväntade ökningen på 6 procent i beräkningen. För den här beräkningen skapar hon sitt eget mått. Med funktionen Nytt mått skapar hon ett nytt mått och anger sedan följande DAX-formel:

    Projected Sales = SUM('Sales'[Last Years Sales])*1.06

Jan drar sedan måttet Säljprognos till diagrammet.

![](media/desktop-measures/measuresinpbid_lastyearsales.png)

Nu har Jan ett mått för att beräkna framtida försäljning med minimal ansträngning. Hon kan analysera sina prognoser ytterligare genom att filtrera specifika återförsäljare eller lägga till andra fält i rapporten.

## <a name="learn-more"></a>Läs mer
Det här er bara en snabbintroduktion till mått men det finns mycket mer information om att skapa egna mått. Läs [Självstudie: skapa dina egna mått i Power BI Desktop](desktop-tutorial-create-measures.md), där du kan ladda ned en exempelfil och få stegvisa anvisningar om hur du skapar fler mått.  

Om du vill fördjupa dig i DAX kan du läsa [Grunderna för DAX i Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Lathunden för [Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) innehåller detaljerade artiklar om alla funktioner, syntaxer operatörer och namnkonventioner. DAX har funnits i åratal i Power Pivot i Excel och SQL Server Analysis Services så det finns en mängd andra bra resurser som är tillgängliga. Läs [DAX Resource Center Wiki](http://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx), där inflytelserika BI-experter delar med sig av sina kunskaper om DAX.



