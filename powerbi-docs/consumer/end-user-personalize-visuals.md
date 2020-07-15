---
title: Anpassa visuella objekt i en rapport
description: Skapa egna vyer av en rapport utan att redigera den.
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 05/21/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: c34c4ff3dbeabafbdae9c286e03443abed52af2f
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/11/2020
ms.locfileid: "86263769"
---
# <a name="personalize-visuals-in-a-report"></a>Anpassa visuella objekt i en rapport

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

Det är svårt att göra ett visuellt objekt som uppfyller allas krav. Men när en kollega delar en rapport med dig kanske du vill ändra de visuella objekten utan att behöva be din kollega att göra ändringarna åt dig. 

Du vill kanske byta ut det som finns på axeln, ändra typ av visuellt objekt eller lägga till något i knappbeskrivningen. Med funktionen **Anpassa det här visuella objektet** kan du göra ändringarna själv och när du är nöjd sparar du det som ett bokmärke som du kan återvända till. Du behöver inte ens redigeringsbehörighet för rapporten.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize.png" alt-text="Anpassa ett visuellt objekt":::
 
## <a name="what-you-can-change"></a>Det här kan du ändra

Med den här funktionen kan du få ytterligare insikter via ad hoc-utforskning av visuella objekt på en Power BI-rapport. Här följer några av de ändringar som du kan göra. Vilka alternativ som är tillgängliga varierar beroende på typ av visuella objekt. 

- Ändra visualiseringstyp
- Byta ut ett mått eller en dimension
- lägga till eller ta bort en förklaring,
- Jämföra två eller flera mått
- ändra sammansättningar osv.

Den här funktionen tillåter inte bara nya utforskningsfunktioner. Det omfattar också sätt för du att samla in och dela dina ändringar:

- Bekräfta dina ändringar
- Dela dina ändringar
- Återställa alla ändringar i en rapport
- Återställa alla ändringar i ett visuellt objekt
- Ta bort de senaste ändringarna


## <a name="personalize-visuals-in-the-power-bi-service"></a>Anpassa visuella objekt i Power BI-tjänsten

Genom att anpassa ett visuellt objekt kan du utforska dina data på många sätt utan att lämna rapporten i läsvyn. I följande exempel visas olika sätt som du kan ändra ett visuellt objekt för att uppfylla dina behov. 

1. Öppna en rapport i läsvyn i Power BI-tjänsten.

2. I menylisten för det visuella objektet markerar du kryssrutan **Anpassa det här visuella objektet** ![ikonen Anpassa det här visuella objektet](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png). 

3. Om du vill rensa något av **Anpassningsfälten** väljer du **Fler alternativ (...)** och därefter **Ta bort fält**.

### <a name="change-the-visualization-type"></a>Ändra visualiseringstyp

Tror du att data visas bättre som ett liggande stapeldiagram? Ändra **visualiseringstyp**.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="Ändra visualiseringstyp":::
 
### <a name="swap-out-a-measure-or-dimension"></a>Byta ut ett mått eller en dimension
Ersätt fältet som används för X-axeln genom att välja det fält som du vill ersätta och välj sedan ett annat fält.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="Ändra axeln":::
 
### <a name="add-or-remove-a-legend"></a>Lägga till eller ta bort en förklaring
Genom att lägga till en förklaring kan du färgkoda ett visuellt objekt baserat på en kategori. I det här exemplet använder vi färgkodning baserad på företagsnamn. 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="Lägga till eller ta bort en förklaring":::

### <a name="compare-two-or-more-different-measures"></a>Jämföra två eller flera olika mått
Jämför och kontrastera värden för olika mått genom att använda +-ikonen för att lägga till flera mått för ett visuellt objekt. Om du vill ta bort ett mått väljer du **Fler alternativ (...)** och sedan **Ta bort fält**.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="Jämföra mått":::

### <a name="change-aggregations"></a>Ändra sammansättningar
Ändra hur ett mått beräknas genom att ändra sammansättningen i rutan **Anpassa**. Välj **Fler alternativ (...)** och välj den sammansättning som ska användas.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="Ändra sammansättningar":::

### <a name="capture-changes"></a>Avbilda ändringar 
Använd personliga bokmärken för att spara ändringarna så att du kan återgå till den anpassade vyn. Välj **Bokmärken** > **Personliga bokmärken** och ge bokmärket ett namn. 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="Skapa ett bokmärke":::
 
Du kan också göra bokmärket till en standardvy.

### <a name="share-changes"></a>Dela ändringar 
Om du har behörigheter för att läsa och dela kan du välja att inkludera ändringarna när du delar rapporten.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="Dela ändringar":::
 
### <a name="reset-all-your-changes-to-a-report"></a>Återställa alla ändringar i en rapport

Välj **Återställ till standard** i det övre högra hörnet på rapportarbetsytan. Detta tar bort alla ändringar i rapporten och återställa den till författarens senast sparade vy i rapporten.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="Återställ alla ändringar":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>Återställa alla ändringar i ett visuellt objekt

Från menylisten för det visuella objektet, välj **Återställ visuellt objekt** om du vill ta bort alla ändringar för ett specifikt virtuellt objekt och återställa den till författarens senast sparade vy av det visuella objektet.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="Återställ alla ändringar av visuellt objekt":::
 
### <a name="clear-recent-changes"></a>Rensa nyligen gjorda ändringar

Välj radergummiikonen för att rensa alla nyligen gjorda ändringar som du har gjort sedan du öppnade fönstret **Anpassa**.  

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="Återställa nyligen gjorda ändringar":::

## <a name="limitations-and-known-issues"></a>Begränsningar och kända problem

För närvarande har funktionen några begränsningar som du bör vara medveten om.

- **Anpassa det här visuella objektet** kan inaktiveras för en hel rapport eller för ett visst visuellt objekt. Kontakta klientadminstratören eller rapportens ägare om du inte har ett alternativ som låter dig anpassa det visuella objektet. Om du vill visa kontaktinformation för rapportägaren väljer du namnet på rapporten på Power BI-menyraden.
- Användares utforskningar sparas inte automatiskt. Du måste spara vyn som ett personligt bokmärke för att kunna samla in dina ändringar.
- Den här funktionen stöds i mobilappar för Power BI för iOS och Android-surfplattor och i Power BI Windows-appen. Det finns inte stöd för Power BI-appar för telefoner. Men eventuella ändringar av visuella objekt som du sparar i ett personligt bokmärke i Power BI-tjänsten sparas i alla Power BI-mobilappar.

Det finns även några kända problem som vi ska lösa:

- Det finns inte stöd för att lägga till hierarki. Du måste lägga till de enskilda underordnade objekten individuellt.
- Med personliga bokmärken kan du få resultat som skiljer sig något från de sekvenser du väljer. Avvikelser är möjliga eftersom vi inte fångar upp rapportens fullständiga status, utan bara de ändringar som har gjorts. Du löser det genom att välja **Återställ till standard** och sedan välja det bokmärke som du vill visa. 

## <a name="next-steps"></a>Nästa steg
[Kopiera ett visuellt rapportobjekt som en statisk bild](../visuals/power-bi-visualization-copy-paste.md)    
Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

