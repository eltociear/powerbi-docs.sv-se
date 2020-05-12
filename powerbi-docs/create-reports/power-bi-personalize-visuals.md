---
title: Låt användarna anpassa visuella objekt i en rapport
description: Låt rapportläsarna skapa egna vyer av en rapport utan att redigera den.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: abc936c6ea4b61e4837e05fbde110e5159296815
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867126"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Låt användarna anpassa visuella objekt i en rapport

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

När du delar en rapport med en bred publik kan en del av dina användare vilja se något annorlunda vyer av specifika visuella objekt. Kanske vill de byta ut vad som finns på axeln, ändra typ av visuellt objekt eller lägga till något i knappbeskrivningen. Det är svårt att göra ett visuellt objekt som uppfyller allas krav. Med den här nya funktionen kan du göra det möjligt för dina användare att utforska och anpassa visuella objekt, allt i rapportens läsvy. De kan justera det visuella objektet på det sätt de önskar och spara det som ett bokmärke att komma tillbaka till. De behöver inte ha redigeringsbehörighet för rapporten eller gå tillbaka till rapportens författare för att få en ändring.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Anpassa ett visuellt objekt":::
 
## <a name="what-report-consumers-can-change"></a>Vilken rapport konsumenter kan ändra

Med den här funktionen kan användarna få ytterligare insikter via ad hoc-utforskning av visuella objekt på en Power BI-rapport. Funktionen är idealisk för rapportgenererare som vill aktivera grundläggande utforskningsscenarier för sina rapportläsare. Följande är ändringar som kan utföras av rapportläsare:

- Ändra visualiseringstyp
- Byta ut ett mått eller en dimension
- lägga till eller ta bort en förklaring,
- Jämföra två eller flera mått
- ändra sammansättningar osv.

Den här funktionen tillåter inte bara nya utforskningsfunktioner. Det omfattar också sätt för konsumenter att samla in och dela sina ändringar:

- Avbilda deras ändringar
- Dela deras ändringar
- Återställ alla ändringar för en rapport
- Återställ alla ändringar för ett visuellt objekt
- Ta bort de senaste ändringarna

## <a name="turn-on-the-preview-feature"></a>Aktivera förhandsgranskningsfunktionen

Eftersom den här funktionen finns i förhandsversion måste du först aktivera funktionsväxeln. Gå till **Arkiv** > **Alternativ och inställningar** > **Alternativ**. Under **Globala inställningar** > **Förhandsgranskningsfunktioner** ser du till att **Anpassa visuella objekt** är markerat.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-preview-personalize-visual.png" alt-text="Aktivera Anpassa visuella objekt":::

Du kan behöva starta om Power BI Desktop för att se det i inställningarna för den aktuella filen.

## <a name="enable-personalization-in-a-report"></a>Aktivera anpassning i en rapport

När du har aktiverat förhandsgranskningsväxeln måste du särskilt aktivera den för de rapporter som du vill att användarna ska kunna anpassa visuella objekt för.

Du kan antingen aktivera den här funktionen i Power BI Desktop eller i Power BI-tjänsten.

### <a name="in-power-bi-desktop"></a>I Power BI Desktop

Om du vill aktivera funktionen i Power BI Desktop går du till **Arkiv** > **Alternativ och inställningar** > **Alternativ** > **Aktuell fil** > **Rapportinställningar**. Se till att **Anpassa visuella objekt (förhandsversion)** är aktiverat.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-settings-personalize-visual.png" alt-text="Aktivera anpassning i en rapport":::

### <a name="in-the-power-bi-service"></a>I Power BI-tjänsten

Om du vill aktivera funktionen i Power BI-tjänsten i stället går du till **Inställningar** för rapporten.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Rapportinställningar i Power BI-tjänsten":::

Aktivera **Anpassa visuella objekt (förhandsversion)**  > **Spara**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-personalize-visual.png" alt-text="Aktivera Anpassa visuella objekt i tjänsten":::

## <a name="select-visuals-that-can-be-personalized"></a>Välj visuella objekt som kan anpassas

När du aktiverar den här inställningen för en specifik rapport kan du som standard anpassa alla visuella objekt i rapporten. Om du inte vill att alla visuella objekt ska anpassas kan du aktivera eller inaktivera inställningen per visuellt objekt.

Välj det visuella objektet > välj **Formatera** i fönstret **Visualiseringar** > expandera **Sidhuvud för visuellt objekt**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="Välj sidhuvud för visuellt objekt":::
 
Växla **Anpassa visuella objekt** >  till **På** eller **Av**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="Ange på eller av för skjutreglaget för anpassning av visuellt objekt":::

## <a name="personalize-visuals-in-the-power-bi-service"></a>Anpassa visuella objekt i Power BI-tjänsten

Genom att anpassa ett visuellt objekt kan dina kunder utforska dina data på många sätt utan att lämna rapporten i läsvyn. I följande exempel visas olika sätt som användare kan ändra ett visuellt objekt för att uppfylla sina behov. 

1. Öppna en rapport i läsvyn i Power BI-tjänsten.

2. I det övre högra hörnet av det visuella objektet markerar du kryssrutan **Anpassa det här visuella objektet** ![ikonen Anpassa det här visuella objektet](media/power-bi-personalize-visuals/power-bi-personalize-visual-icon.png). 

### <a name="change-the-visualization-type"></a>Ändra visualiseringstyp

Du kan visa det visuella objektet till en annan representation genom att ändra **visualiseringstyp**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="Ändra visualiseringstyp":::
 
### <a name="swap-out-a-measure-or-dimension"></a>Byta ut ett mått eller en dimension
Du kan ersätta ett mått eller en dimension på X-axeln genom att välja det fält som du vill ersätta och sedan välja ett annat mått eller en annan dimension.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="Ändra axeln":::
 
### <a name="add-or-remove-a-legend"></a>Lägga till eller ta bort en förklaring
Genom att lägga till en förklaring kan du färgkoda ett visuellt objekt baserat på en kategori. Du kan eliminera kategorisk färgkodning genom att avmarkera rutan **Förklaring** i rutan **Anpassa**. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="Lägga till eller ta bort en förklaring":::

### <a name="compare-two-or-more-different-measures"></a>Jämföra två eller flera olika mått
Du kan jämföra och kontrastera värden för olika mått genom att använda +-ikonen för att lägga till flera mått för ett visuellt objekt.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="Jämföra mått":::

### <a name="change-aggregations"></a>Ändra sammansättningar
Du kan ändra hur ett mått beräknas genom att ändra sammansättningen i rutan **Anpassa**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="Ändra sammansättningar":::

### <a name="capture-changes"></a>Avbilda ändringar 
Använd personliga bokmärken för att spara ändringarna så att du kan återgå till den anpassade vyn. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="Skapa ett bokmärke":::
 
Du kan också göra bokmärket till standardvy.

### <a name="share-changes"></a>Dela ändringar 
Om du har behörigheter för att läsa och dela kan du välja att inkludera ändringarna när du delar rapporten.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="Dela ändringar":::
 
### <a name="reset-all-your-changes-to-a-report"></a>Återställa alla ändringar i en rapport

Välj **Återställ till standard** om du vill ta bort alla ändringar i rapporten och återställa den till författarens senast sparade vy i rapporten.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="Återställ alla ändringar":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>Återställa alla ändringar i ett visuellt objekt

Välj **Reset this visual** (Återställ visuellt objekt) om du vill ta bort alla ändringar för ett specifikt virtuellt objekt och återställa den till författarens senast sparade vy av det visuella objektet.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="Återställ alla ändringar av visuellt objekt":::
 
### <a name="clear-recent-changes"></a>Rensa nyligen gjorda ändringar

Välj radergummiikonen för att rensa alla nyligen gjorda ändringar som du har gjort sedan du öppnade fönstret **Anpassa**.  

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="Återställa nyligen gjorda ändringar":::

## <a name="limitations-and-known-issues"></a>Begränsningar och kända problem

För närvarande har funktionen några begränsningar som du bör vara medveten om.

- Den här funktionen stöds inte för inbäddade scenarier, som att publicera på webben.
- Användares utforskningar sparas inte automatiskt. Du måste spara vyn som ett personligt bokmärke för att kunna samla in dina ändringar.
- Du kan inte ändra visuella objekt i Power BI-mobilappar. Men eventuella ändringar av visuella objekt som du sparar i ett personligt bokmärke i Power BI-tjänsten sparas i mobilappar.

Det finns även några kända problem som vi ska lösa:

- Det finns inte stöd för att lägga till hierarki. Du måste lägga till de enskilda underordnade objekten.
- Du kan inte ändra en datumhierarki till ett datum eller vice versa. 
- Med personliga bokmärken kan du få resultat som skiljer sig något från de sekvenser du väljer. Avvikelser är möjliga eftersom vi inte fångar upp rapportens fullständiga status, utan bara de ändringar som har gjorts. Du löser det genom att välja **Återställ till standard** och sedan välja det bokmärke som du vill visa. 

## <a name="next-steps"></a>Nästa steg

Testa den nya anpassningen av visuella objekt. Lämna gärna feedback om den här funktionen och hur vi kan fortsätta att förbättra den på [Power BI:s webbplats för idéer](https://ideas.powerbi.com/forums/265200-power-bi). 

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

