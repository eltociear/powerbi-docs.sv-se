---
title: Använd drillthrough i Power BI Desktop
description: Lär dig att använda visning av detaljerad information för att öka detaljnivån för data på en ny rapportsida i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: a7b00b0cb611dd3e0921885ddaca6547fdb43fd3
ms.sourcegitcommit: 7f27b9eb0e001034e672050735ab659b834c54a3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74310925"
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Använd drillthrough i Power BI Desktop
Med *drillthrough* i Power BI Desktop kan du skapa en sida i rapporten som fokuserar på en specifik enhet – till exempel en leverantör, kund eller tillverkare. För att använda visning av detaljerad information väljer du det genom att högerklicka på en datapunkt i andra rapportsidor och använda visning av detaljerad information till sidan i fokus för att hämta information som har filtrerats för det sammanhanget.

![Använda drillthrough](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Använda drillthrough
1. För att använda drillthrough skapar du en rapportsida med visuella objekt som du vill se för typen av enhet på vilken du ökar detaljnivån. 

    Anta exempelvis att du vill låta tillverkare visa detaljerad information. I det här fallet kan du skapa en drillthrough-sida med visuella objekt som visar totalförsäljning, totalt antal levererade enheter, försäljning enligt kategori, försäljning enligt region och så vidare. Därmed är visualiseringen alltid specifik för tillverkaren du valde när du ökar detaljnivån.

2. Sedan, på drillthrough-sidan i avsnittet **Fält** i rutan **Visuella objekt** kan du dra fältet som du vill aktivera drillthrough för på i brunnen för **Drillthrough-filter**.

    ![Drillthrough-brunn](media/desktop-drillthrough/drillthrough_02.png)

    När du lägger till ett fält i brunnen **Drillthrough-filter** skapar Power BI Desktop automatiskt en *bakåtknapp*. Det visuella objektet blir en knapp i publicerade rapporter. Användare av rapporten i Power BI-tjänsten kan använda den här knappen för att gå tillbaka till sidan som de kommer ifrån.

    ![Drillthrough-bld](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>Använda en egen bild för en bakåtknapp    
 Eftersom bakåtknappen är en bild kan du ersätta bilden för det visuella objektet med vilken bild du vill. Den kommer fortfarande att fungera som en bakåtknapp så att användaren kan gå tillbaka till ursprungssidan. 

Om du vill använda en egen bild för en bakåtknapp följer du de här stegen:

1. Välj **Bild** på fliken **Start**. Leta upp bilden och placera den på drillthrough-sidan.

2. Välj din nya bild på drillthrough-sidan. Under fönstret **Formatera bild** ställer du in skjutreglaget **Åtgärd** till **På** och anger sedan **Typen** som **Bakåt**. Bilden fungerar nu som en bakåtknapp.

    ![Läs in bild och ange typ som bakåt](media/desktop-drillthrough/drillthrough_05.png)

    
     Nu kan användare högerklicka på en datapunkt i rapporten och få en snabbmeny som stöder drillthrough för sidan. 

    ![Drillthrough-meny](media/desktop-drillthrough/drillthrough_04.png)

    När rapportkonsumenterna valde drillthrough filtrerades sidan för att visa information om datapunkten som de högerklickade på. Låt oss till exempel anta att de högerklickade på en datapunkt om Contoso (en tillverkare) och valde att öka detaljnivån (drillthrough). Drillthroughsidan de går till filtreras till Contoso.

## <a name="pass-all-filters-in-drillthrough"></a>Skicka alla filter i drillthrough

Från och med versionen från maj 2018 av Power BI Desktop kan du överföra alla filter till drillthrough-fönstret. Till exempel kanske du bara har valt en viss kategori av produkter och visualiseringarna filtrerats till denna kategori, då väljer du drillthrough. Du kan vara intresserad hur denna drillthrough skulle se ut med alla de filter som används.

För att behålla alla filter i avsnittet **Drillthrough** i fönstret **Visualiseringar** ställer du bara in **Behåll alla filter** till **På**. 

![Behåll alla filter](media/desktop-drillthrough/drillthrough_06.png)

I versioner av Power BI Desktop som lanserats före maj 2018 är beteendet likvärdigt med att ha den här inställningen satt till **Av**.

När du sedan genomför drillthrough på någon visualisering ser du vilka filter som har tillämpats på grund av att källvisualiseringen har tillfälliga filter. I avsnittet **Visning av detaljerad information** i fönstret **Visualisering** visas dessa tillfälliga filter i kursiv stil. 

![Tillfälliga filter i kursiv stil](media/desktop-drillthrough/drillthrough_07.png)

Observera att även om du kan göra detta med sidorna för knappbeskrivningar så skulle vara en konstig upplevelse eftersom knappbeskrivningen inte skulle verka som att den fungerar korrekt. Därför rekommenderas du att inte göra det med verktygstips.

## <a name="add-a-measure-to-drillthrough"></a>Lägg till ett mått i drillthrough

Förutom att överföra alla filter till drillthrough-fönstret kan du även lägga till ett mått (eller en sammanfattande numerisk kolumn) i drillthrough-området. Du behöver bara dra drillthrough-fältet till **Drillthrough**-kortet för att tillämpningen ska börja gälla. 

![Lägg till ett mått i drillthrough](media/desktop-drillthrough/drillthrough_08.png)

När du lägger till ett mått (eller en sammanfattade numerisk kolumn) kan du gå till sidan när fältet används i området *Värde* i en visualisering.

Svårare än så är det inte att använda drillthrough i dina rapporter. Det är ett bra sätt att få en utökad vy över den enhetsinformation som du har valt för ditt drillthrough-filter.

## <a name="next-steps"></a>Nästa steg

Följande artiklar kan också vara av intresse för dig:

* [Använd visning av detaljerad information mellan rapporter i Power BI Desktop](desktop-cross-report-drill-through.md)
* [Använda utsnitt i Power BI Desktop](visuals/power-bi-visualization-slicers.md)

