---
title: Använda ett relativt tidsutsnitt eller filter i Power BI
description: Lär dig hur du använder ett utsnitt eller filter till att begränsa relativa tidsintervall i Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 07/06/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: f1a792c7ad25600f04ca9834b1e5019d4e27efb4
ms.sourcegitcommit: 11deeccf596e9bb8f22615276a152614f7579f35
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/16/2020
ms.locfileid: "86409523"
---
# <a name="use-a-relative-time-slicer-and-filter-in-power-bi"></a>Använda ett relativt tidsutsnitt eller filter i Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

I nya scenarier med snabba uppdateringar kan det vara användbart att filtrera på en mindre tidsperiod. Med ett relativt tidsutsnitt eller relativt datumfilter kan du använda tidsbaserade filter på valfri datum- eller tidskolumn i datamodellen. Du kan till exempel använda det relativa tidsutsnittet till att bara visa videovisningar den senaste minuten eller timmen. 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time.gif" alt-text="Skärmbild på exempel på relativ tid.":::

Du behöver inte använda funktionen tillsammans med funktionen för [automatisk siduppdatering](../create-reports/desktop-automatic-page-refresh.md). Många relativa tidsscenarier är dock bra med funktionen för automatisk siduppdatering.  

> [!NOTE]
> När du använder ett relativt tidsfilter eller utsnitt på sidan eller rapportnivån filtreras alla visuella objekt på sidan eller rapporten till exakt samma tidsintervall, med hjälp av ett delad *fästpunktstid*. Eftersom visuella objekt kan ha olika körningstider ser den här delade fästpunktstiden till att visuella objekt synkroniseras på sidan eller i hela rapporten. Läs mer om [fästpunktstid](#understanding-anchor-time) i den här artikeln.

## <a name="create-a-relative-time-slicer-or-filter"></a>Skapa ett relativt tidsutsnitt eller filter

När du har aktiverat funktionen kan du dra och släppa fältet datum eller tid till fältet för ett utsnitt eller till släppa zonen i fönstret Filter. 

### <a name="create-a-slicer"></a>Skapa ett utsnitt

1. Dra ett datum- eller tidsfält till arbetsytan.

2. Välj visualiseringstypen **Utsnitt**.

    :::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-create-slicer.png" alt-text="Skärmbild som visar hur man skapar ett tidsutsnitt.":::

### <a name="create-a-filter"></a>Skapa ett filter
 
- Dra ett datum- eller tidsfält till fönstret Filter för **det här visuella objektet**, **den här sidan**eller **alla sidor**.

### <a name="set-relative-time"></a>Ange relativ tid 

Sedan ändrar du filtertypen till **Relativ tid**.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set.png" alt-text="Skärmbild av ändring till relativ tid.":::
 
Så här ser det ut i ett utsnitt:

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-slicer.png" alt-text="Skärmbild av relativ tid i ett tidsutsnitt.":::

Så här ser det ut i ett filterkort: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-filter.png" alt-text="Skärmbild av relativ tid i ett filter.":::
 
Med den nya filtertypen kan du filtrera efter **Senaste**, **Nästa** eller **Under denna tidsperiod**: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-last-next.png" alt-text="Skärmbild av alternativen Senaste, Nästa och Under denna tidsperiod.":::
 
Du anger tidsfönstret med ett heltal och en tidsenhet: **Minuter** eller **timmar**.
 
:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-minutes-hours.png" alt-text="Skärmbild av val av minuter eller timmar.":::

Om du behöver spara utrymme på arbetsytan kan du också skapa ett relativt tidsfilter som ett filterkort i fönstret Filter.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-filter.png" alt-text="Skärmbild av hur man ställer in relativ tid i ett filter i stället.":::
 
## <a name="understanding-anchor-time"></a>Förstå fästpunktstid

När ett filter används på sidan eller rapportnivån synkroniseras alla visuella objekt på sidan eller rapporten med samma exakta tidsintervall. De här frågorna utfärdas i förhållande till en tid med namnet  *fästpunktstid*. Fästpunktstiden uppdateras automatiskt under följande förhållanden:

- Inledande sidhämtning.
- Manuell uppdatering.
- Automatisk uppdatering av sida eller ändring av identifiering.
- En ändring i modellen.

### <a name="anchor-time-exceptions"></a>Undantag för fästpunktstid

- Relativ tidsfiltrering med hjälp av Visuella frågor och svar är inte relativ för den här fästpunktstiden förrän du har konverterat Visuella frågor och svar till ett visuellt standardobjekt. De andra visuella AI-objekten, till exempel viktiga influerare och nedbrytningsträd, synkroniseras dock med fästpunktstiden. 
- Dessutom är relativa datumfilter eller utsnitt inte i förhållande till fästpunktstiden, om det inte finns några relativa tidsfilter. Om ett relativt datum- och ett relativt tidsfilter finns på samma sida tar det relativa datumfiltret hänsyn till fästpunktstiden.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

Följande begränsningar och överväganden kan användas för relativt tidsutsnitt och filter.

- **Att tänka på när det gäller tidszon**: Datamodeller i Power BI omfattar inte tidszonsinformation. Modeller kan lagra tidpunkter, men det finns inget som indikerar vilken tidszonen de befinner sig i. Utsnitt och filter baseras alltid på tiden i UTC. Om du skapar ett filter i en rapport och skickar rapporten till en kollega i en annan tidszon så kommer ni båda att se samma data. Om du och din kollega inte befinner er i tidszonen UTC så måste ni justera för tidsförskjutningen. Använd frågeredigeraren för att konvertera data som hämtats i en lokal tidszon till UTC.
- Den här nya filtertypen stöds i Power BI Desktop, Power BI-tjänsten, Power BI Embedded och Power BI-mobilappar. Det finns dock några kända begränsningar av stöd:

    - Den stöds inte via API:et för inbäddning.
    - Det finns inte stöd för att publicera på webben.

- **Cachelagring av frågor**: Vi använder klientcachen. Anta att du först anger ”senaste minuten”, sedan ”de senaste fem minuterna” och därefter ändrar tillbaka till ”senaste minuten”. Då ser du samma resultat som när det kördes första gången, om du inte uppdaterar sidan eller om sidan uppdateras automatiskt.

## <a name="next-steps"></a>Nästa steg

- [Använda ett relativt datumutsnitt eller filter i Power BI](../visuals/desktop-slicer-filter-date-range.md)
- [Utsnitt i Power BI](../visuals/power-bi-visualization-slicers.md)
