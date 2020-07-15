---
title: Använda utsnitt i Power BI-tjänsten
description: Ett utsnitt i Power BI är en alternativ filtreringsmetod som begränsar den del av datauppsättningen som visas i övriga visualiseringar i en rapport.
author: v-thepet
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 04/06/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5c25f19a17ab24398b5a4992104b5487036e2171
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/11/2020
ms.locfileid: "86264176"
---
# <a name="slicers-in-the-power-bi-service"></a>Utsnitt i Power BI-tjänsten

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-yynn.md)]

![jämförelse av 2 olika val i ett horisontellt utsnitt](media/end-user-slicer/power-bi-slider.png)

Ett utsnitt är en typ av visualisering som filtrerar de andra visuella objekten på en rapportsida. När du använder Power BI-rapporter kommer du att stöta på många typer av utsnitt. I bilden ovan ser du samma utsnitt men med olika val. Observera hur varje val filtrerar de andra visuella objekten på sidan.  


## <a name="how-to-use-slicers"></a>Så här använder du utsnitt
När *designers* skapar rapporter lägger de till utsnitt för att kunna berätta en historia och ge dig verktyg för att utforska dina data.

### <a name="numeric-range-slicer"></a>Numeriskt intervallutsnitt
 Det numeriska intervallutsnittet ovan hjälper dig att utforska den totala försäljningen per geografi, enheter i lager och beställningsdatum. Använd handtagen till att välja ett intervall. 

![handtagen för ett intervallutsnitt](media/end-user-slicer/power-bi-handles.png)

### <a name="basic-vertical-checkbox-slicer"></a>Utsnitt för grundläggande vertikala kryssrutor

I ett utsnitt för grundläggande kryssrutor markerar du en eller flera kryssrutor för att se hur de andra visuella objekten på sidan påverkas. Om du vill välja fler än en kryssruta använder du CTRL-välj. Ibland kan *rapportdesignern* ställa in utsnittet så att du bara får välja ett värde åt gången. 

![grundläggande vertikalt utsnitt](media/end-user-slicer/power-bi-basic.png)

### <a name="image-and-shape-slicers"></a>Bild- och formutsnitt
När utsnittsalternativen är bilder eller former gör du dina val ungefär som med kryssrutor. Du kan välja en eller flera bilder eller former för att tillämpa utsnittet på de andra visuella objekten på sidan. 

![bildutsnitt](media/end-user-slicer/power-bi-image.png)    

![horisontellt utsnitt](media/end-user-slicer/power-bi-horizontal.png)    

![formutsnitt](media/end-user-slicer/power-bi-boxes.png)

### <a name="hierarchy-slicer"></a>Hierarkiutsnitt

I ett utsnitt med en hierarki använder du »-tecken till att expandera och komprimera hierarkin. Rubriken uppdateras med dina val.

![hierarkiutsnitt](media/end-user-slicer/power-bi-hierarchy.png)

### <a name="relative-time-slicer"></a>Relativt tidsutsnitt
I nya scenarier med snabba uppdateringar kan det vara väldigt användbart att filtrera på en mindre tidsperiod.
Med hjälp av det relativa tidsutsnittet kan du tillämpa tidsbaserade filter på alla datum- och tidsdata i rapporten. Du kan till exempel använda det relativa tidsutsnittet till att bara visa videovisningar de senaste 2 dagarna, timmarna eller till och med minuterna. 

![relativt tidsutsnitt](media/end-user-slicer/power-bi-relative-time.png)

## <a name="deactivate-a-slicer"></a>Inaktivera ett utsnitt
Om du vill inaktivera ett utsnitt väljer du ikonen Radera.

![ikonen Radera](media/end-user-slicer/power-bi-eraser.png)

## <a name="next-steps"></a>Nästa steg
Mer information finns i följande artiklar:

[Visualiseringstyper i Power BI](end-user-visualizations.md)

