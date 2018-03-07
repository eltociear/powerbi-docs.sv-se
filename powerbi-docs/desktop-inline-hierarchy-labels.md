---
title: "Använd infogade hierarkietiketter i Power BI Desktop"
description: "Använd infogade hierarkietiketter i Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 9d5675b17973839f52699c5af9bfad9c8714a58e
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="use-inline-hierarchy-labels-in-power-bi-desktop"></a>Använd infogade hierarkietiketter i Power BI Desktop
**Power BI Desktop** stöder användning av **infogade hierarkietiketter**, vilket är den första av två funktioner som är avsedda att förbättra hierarkisk utökning av detaljnivån. Den andra funktionen, som för närvarande är under utveckling, är möjligheten att använda kapslade hierarkietiketter (håll ögonen öppna för detta – vi uppdaterar ofta).   

## <a name="how-inline-hierarchy-labels-work"></a>Så här fungerar infogade hierarkietiketter
Med infogade hierarkietiketter visas hierarkietiketterna på samma sätt som när du expanderar visuella objekt med funktionen **Visa allt**. En fördel med att se hierarkietiketterna är att du också kan välja att **sortera** efter de olika hierarkietiketterna när du expanderar dina hierarkiska data.

### <a name="using-the-built-in-expand-all-feature-without-sorting-by-hierarchy-labels"></a>Använda funktionen Visa allt (utan att sortera efter hierarkietiketter)
Innan vi ser hur infogade hierarkietiketter används ska vi se hur standardbeteendet är för funktionen **Visa allt**. Detta hjälper oss att förstå (och uppskatta) hur användbara infogade hierarkietiketter kan vara.

Följande bild visar ett stapeldiagram ett visuellt objekt för årlig försäljning. När du högerklickar kan du välja **Visa allt**.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_4.png)

När **Visa allt** är valt expanderar det visuella objektet datumhierarkin från *År* till *Kvartal*, enligt följande bild.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_5.png)

Observera att etiketterna *År* och *Kvartal* visas tillsammans. Det här etikettschemat fortsätter allt eftersom du använder **Visa allt** till slutet av hierarkin.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_6.png)

Detta är hur den inbyggda hierarkin *Datum*, som har associerats med fält av datatypen *Datum/tid*, fungerar. Nu går vi till nästa avsnitt och ser hur den nya funktionen för infogade hierarkietiketter skiljer sig.

### <a name="using-inline-hierarchy-labels"></a>Använda infogade hierarkietiketter
Nu ska vi titta på ett annat diagram – med data som innehåller informella hierarkier. I följande visuella objekt har vi ett stapeldiagram med **Sales Amount** som använder *Color* som axel. I dessa data utgör *Color* och *Class* en informell hierarki. Härifrån kan du återigen välja *Visa allt* för att gå nedåt i hierarkin.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_7.png)

Att välja **Visa allt** visar nästa nivå med infogad visning av hierarkietiketter. Som standard sorteras infogade hierarkier efter måttvärde – i det här fallet **SalesAmount**. När infogade hierarkietiketter är aktiverade kan du sortera datan efter hierarki också, genom att välja ellipsen i det övre högra hörnet (**...**) och sedan välja **Sortera efter > Color Class** som visas i följande bild.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_8.png)

När **Color Class** är valt sorteras datan baserat på den informella hierarkimarkeringen enligt följande bild.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_9.png)

> [!NOTE]
> Funktionen med infogade hierarkietiketter tillåter inte ännu att den inbyggda tidshierarkin sorteras efter värde – den sorteras bara efter hierarkiordning.
> 
> 

## <a name="troubleshooting"></a>Felsökning
Det är möjligt att dina visuella objekt fastnar i tillståndet med den expanderade infogade hierarkinivån. I vissa fall kanske du upptäcker att en del av dina visuella objekt har fastnat i det expanderade läget och att det inte går att granska uppåt. Detta kan inträffa om du har vidtagit följande åtgärder (lösningen finns i stegen *nedan*):

Steg som kan få visuella objekt att fastna i ett expanderat tillstånd:

1. Du aktiverar funktionen **infogad hierarkietikett**
2. Du skapar vissa visuella objekt med hierarkier
3. Sedan använder du **Visa allt** och sparar filen
4. Därefter *inaktiverar* du funktionen **infogad hierarkietikett** och startar om Power BI Desktop
5. Du öppnar din fil på nytt

Om du har råkat göra detta och de visuella objekten har fastnat i expanderat läge, kan du göra följande för att felsöka dem:

1. Återaktivera funktionen **infogad hierarkietikett** och starta sedan om Power BI Desktop
2. Öppna filen igen och gå tillbaka högst upp i de visuella objekt som berörs
3. Spara filen
4. Inaktivera funktionen **infogad hierarkietikett** och starta om Power BI Desktop
5. Öppna filen igen

Du kan också ta bort ditt visuella objekt och återskapa det.

