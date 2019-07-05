---
title: Filtertyper i Power BI-rapporter
description: Lägg till ett sidfilter, ett visualiseringsfilter eller ett rapportfilter till en rapport i Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 499a4f3be9f153a1994802e9707f855b71d2a506
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67409855"
---
# <a name="types-of-filters-in-power-bi-reports"></a>Filtertyper i Power BI-rapporter

Alla filter fungerar inte på samma sätt eftersom de inte är skapade på samma sätt. Hur du skapar dem påverkar hur de beter sig i det nya filterfönstret nytt i redigeringsläget. I den här artikeln beskriver vi de olika typerna av filter, olika metoder för att skapa dem och vad de används till. Läs om hur du [lägger till filter i rapporter](power-bi-report-add-filter.md). 

![Filterfönster](media/power-bi-report-filter-types/power-bi-filter-pane.png)

Vi börjar med de två vanligaste filtertyperna: manuella och automatiska.

## <a name="manual-filters"></a>Manuella filter 

Manuella filter är de filter som rapportskapare drar och släpper var som helst i det nya filterfönstret. Användare med redigeringsbehörighet för rapporten kan redigera, ta bort, rensa, dölja, låsa, byta namn på eller sortera det här filtret i det nya fönstret.

## <a name="automatic-filters"></a>Automatiska filter 

Automatiska filter är de filter som automatiskt läggs till på filterrutans visuella nivå när du skapar ett visuellt objekt. De här filtren baseras på de fält som ditt visuella objekt består av. Användare med redigeringsbehörighet för rapporten kan redigera, rensa, dölja, låsa, byta namn på eller sortera det här filtret i det nya fönstret. De kan inte ta bort automatiska filter, eftersom det visuella objektet refererar till dessa fält.

## <a name="more-advanced-filters"></a>Mer avancerade filter

De följande filtyperna är mindre vanliga, men det är fortfarande viktigt att förstå dem om de visas i rapporten. Dessutom kan de vara användbara för att skapa precis rätt filter i en rapport.

## <a name="include-and-exclude-filters"></a>Inkludera och exkludera filter

Inkludera och exkludera filter läggs automatiskt till i filterfönstret när du använder funktionen för att inkludera eller exkludera funktioner för ett visuellt objekt. Användare med redigeringsbehörighet till rapporten kan ta bort, låsa, dölja eller sortera det här filtret i det nya fönstret. De kan inte redigera, ta bort eller byta namn på ett inkluderings- eller exkluderingsfilter eftersom det associeras med inkluderings- och exkluderingsfunktionerna för visuella objekt.

![Exkludera filter](media/power-bi-report-filter-types/power-bi-filters-exclude.png)

## <a name="drill-down-filters"></a>Filter för att öka detaljnivån

Filter för att öka detaljnivån läggs automatiskt till i filterfönstret när du använder funktionen för att öka detaljnivån för ett visuellt objekt i rapporten. Användare med redigeringsbehörighet till rapporten kan redigera eller rensa filtret i det nya fönstret. De kan inte ta bort, dölja, låsa, byta namn på eller sortera det här filtret eftersom det är associerat med funktionen för att öka detaljnivån för visuella objekt. Du klickar på knappen för att minska detaljnivån för det visuella objektet om du vill ta bort filtret för att öka detaljnivån.

![Filter för att öka detaljnivån](media/power-bi-report-filter-types/power-bi-filters-drill-down.png)

## <a name="cross-drill-filters"></a>Filter för korsgranskning

Filter för korsgranskning läggs automatiskt till i det nya fönstret när ett filter för att öka detaljnivån skickas till ett annat visuellt objekt på rapportsidan via funktionen för korsfiltrering eller korsmarkering. Användare med redigeringsbehörighet för rapporten kan inte ta bort, dölja, låsa, byta namn på eller sortera det här filtret eftersom det är associerat med funktionen för att öka detaljnivån för visuella objekt. De kan också redigera det här filtret eftersom det härstammar från att öka detaljnivån i ett annat visuellt objekt. Du klickar på knappen för att minska detaljnivån för det visuella objektet som passerar filtret om du vill ta bort filtret för att öka detaljnivån.

## <a name="drillthrough-filters"></a>Filter för visning av detaljerad information

Filter för visning av detaljerad information skickas från en sida till en annan via funktionen för visning av detaljerad information. De visas i fönstret för visning av detaljerad information. Det finns två typer av filter för visning av detaljerad information. Den första typen är den som anropar visning av detaljerad information. Rapportredigerare kan redigera, ta bort, rensa, dölja eller låsa den här typen av filter. Den andra typen är filtret för visning av detaljerad information som skickas till målet, baserat på källsidans sidnivåfilter. Rapportredigerare kan redigera, ta bort eller rensa den här tillfälliga typen av filter för visning av detaljerad information. De kan inte låsa eller dölja det här filtret för slutanvändare.

## <a name="url-filters"></a>URL-filter

URL-filter läggs till i det nya fönstret genom att lägga till en URL-frågeparameter. Användare med redigeringsbehörighet för rapporten kan redigera, ta bort eller rensa filtret i det nya fönstret. De kan inte dölja, låsa, byta namn på eller sortera det här filtret eftersom det är associerat med URL-parametern. Om du vill ta bort filtret måste du ta bort parametern från URL:en. Här är en exempel-URL med en parameter:

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=Stores~2FStatus%20eq%20'Off'

![URL-filter](media/power-bi-report-filter-types/power-bi-filter-url.png)

Läs mer om [URL-filter](service-url-filters.md).

## <a name="pass-through-filters"></a>Genomströmningsfilter

Genomströmningsfiltren är filter på visuell nivå som skapas via Frågor och svar. Författare kan ta bort, dölja eller sortera dessa filter i det nya fönstret. De kan dock inte byta namn på, redigera, rensa eller låsa filtren.

![Genomströmningsfilter med Frågor och svar](media/power-bi-report-filter-types/power-bi-filters-qna.png)

## <a name="comparing-filter-types"></a>Jämföra filtertyper

Den här tabellen jämför vad författare kan göra med olika typer av filter.

| Filtertyp | Redigera | Rensa | Ta bort | Dölj | Låsa | Sortera | Byt namn |
|----|----|----|----|----|----|----|----|
| Manuella filter | Y | Y | Y | Y | Y | Y | Y |
| Automatiska filter | Y | Y | N | Y | Y | Y | Y |
| Inkludera/exkludera filter | N | N | Y | Y | Y | Y | N |
| Filter för att öka detaljnivån | Y | Y | N | N | N | N | N |
| Filter för korsgranskning | N | N | N | N | N | N | N |
| Filter för visning av detaljerad information (anropar detaljerad information) | Y | Y | Y | Y | Y | N | N |
| Filter för visning av detaljerad information (tillfälliga) | Y | Y | Y | N | N | N | N |
| URL-filter – tillfälliga | Y | Y | Y | N | N | N | N |
| Genomströmningsfilter | N | N | Y | Y | N | Y | N |



## <a name="next-steps"></a>Nästa steg

[Lägga till filter i rapporter](power-bi-report-add-filter.md)

[Ta en titt på panelen för rapportfilter](consumer/end-user-report-filter.md)

[Filtrera och markera i rapporter](power-bi-reports-filters-and-highlighting.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

