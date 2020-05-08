---
title: Separera rapporter från modeller i Power BI Desktop
description: Vägledning för hur du separerar rapporter från modeller i Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/11/2020
ms.author: v-pemyer
ms.openlocfilehash: dad451da460abed65a69990394522f268d7f21cd
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "81525289"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>Separera rapporter från modeller i Power BI Desktop

När du skapar en ny Power BI Desktop-lösning är en av de första uppgifter som du behöver göra att ”hämta data”. Att hämta data kan leda till två olika resultat. Det kan:

- Skapa en [Live-anslutning](../desktop-report-lifecycle-datasets.md) till en modell som redan har publicerats, vilket kan vara en Power BI-datamängd eller en fjärrhanterad Analysis Services-modell.
- Påbörja utvecklingen av en ny modell som kan vara antingen en import-, DirectQuery- eller kompositmodell.

Den här artikeln handlar om det andra scenariot. I den finns vägledning om huruvida en rapport och en modell ska kombineras till en enskild Power BI Desktop-fil.

## <a name="single-file-solution"></a>Lösning med enskild fil

En _lösning med enskild fil_ fungerar bra om det bara finns en enda rapport baserad på modellen. I det här fallet är det troligt att både modellen och rapporten skapades av samma person. Vi definierar det som en _Personlig BI_-lösning, även om rapporten kan delas med andra. Sådana lösningar kan representera rapporter med rollomfång eller engångsbedömningar av en affärsutmaning – dessa beskrivs ofta som _ad hoc_-rapporter.

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="En enskild fil innehåller en modell och en rapport som har utvecklats av samma person." border="true":::

## <a name="separate-report-files"></a>Separata rapportfiler

Det är logiskt att separera modell- och rapportutveckling till separata Power BI Desktop-filer när:

- Datamodellerare och rapportförfattare är olika personer.
- Det står klart att en modell kommer att utgöra källan till flera rapporter antingen nu eller i framtiden.

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="Det finns tre PBIX-filer. Den första innehåller bara en modell. De andra två innehåller bara rapporter, och de är live-anslutna till den modell som hanteras i Power BI-tjänsten. Rapporterna utvecklas av olika personer." border="true":::

Datamodellerare kan fortfarande använda Power BI Desktop-funktionen för rapportskapande för att testa och validera sina modelldesigner. Men precis efter publicering av filen till Power BI-tjänsten bör de ta bort rapporten från arbetsytan. Och de måste komma ihåg att ta bort rapporten varje gången de publicerar och skriver över datamängden.

### <a name="preserve-the-model-interface"></a>Bevara modellgränssnittet

Ibland är modelländringar oundvikliga. Datamodellerare måste då se till att inte bryta modellgränssnittet. Om de gör det kan det hända att relaterade visuella rapportobjekt eller instrumentpanelsrutor slutar fungera. Brutna visuella objekt visas som fel och kan leda till problem för rapportförfattare och -användare. Dessutom kan de minska förtroendet för data.

Därför bör modelländringar hanteras med försiktighet. Undvik om möjligt följande ändringar:

- Namnbyte för tabeller, kolumner, hierarkier, hierarkinivåer och mått.
- Ändring av kolumndatatyper.
- Ändring av måttuttryck så att de returnerar en annan datatyp.
- Flytt av mått till en annan hemtabell. Detta beror på att om ett mått flyttas så kan det bryta mått med omfång för rapporten som fullständigt kvalificerar mått i hemtabellens namn. Vi rekommenderar inte att du skriver DAX-uttryck med fullständigt kvalificerade måttnamn. Mer information finns i [DAX: Referenser för kolumner och mått](dax-column-measure-references.md).

Att lägga till nya tabeller, kolumner, hierarkier, hierarkinivåer och mått är säkert med ett undantag: Det är möjligt att ett nytt måttnamn kan krocka med ett måttnamn som har rapportomfång. För att undvika kollision rekommenderar vi att rapportförfattare inför en namngivningskonvention när de definierar mått i sina rapporter. De kan prefigera måttnamn med rapportomfång med ett understreck eller något annat tecken.

Om du måste göra icke-bakåtkompatibla ändringar av dina modeller rekommenderar vi att du gör något av följande:

- [Visa relaterat innehåll för datamängden](../consumer/end-user-related.md#view-related-content-for-a-dataset) i Power BI-tjänsten.
- Utforska vyn [Dataursprung](../collaborate-share/service-data-lineage.md) i Power BI-tjänsten.

Båda dessas alternativ gör att du snabbt kan identifiera relaterade rapporter och instrumentpaneler. Vyn Dataursprung är förmodligen det bästa valet eftersom det är enkelt att se kontaktpersonen för varje relaterad artefakt. I själva verket är det en hyperlänk som öppnar ett e-postmeddelande adresserat till kontakten.

Vi rekommenderar att du kontaktar ägaren av varje relaterad artefakt för att meddela dem om icke-bakåtkompatibla ändringar. På så sätt kan de förbereda sig och vara redo att åtgärda och publicera sina rapporter på nytt, vilket minimerar avbrottstiden och användarnas frustration.

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Ansluta till datauppsättningar i Power BI-tjänsten från Power BI Desktop](../desktop-report-lifecycle-datasets.md)
- [Visa relaterat innehåll i Power BI-tjänsten](../consumer/end-user-related.md)
- [Dataursprung](../collaborate-share/service-data-lineage.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
