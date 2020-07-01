---
title: Låt användarna anpassa visuella objekt i en rapport
description: Låt rapportläsarna skapa egna vyer av en rapport utan att redigera den.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/21/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 0fdee37f682774e1dac2b1ac6a4fc7a6e8dabe91
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238081"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Låt användarna anpassa visuella objekt i en rapport

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

När du delar en rapport med en bred publik kan en del av dina användare vilja se något annorlunda vyer av specifika visuella objekt. Kanske vill de byta ut vad som finns på axeln, ändra typ av visuellt objekt eller lägga till något i knappbeskrivningen. Det är svårt att göra ett visuellt objekt som uppfyller allas krav. Med den här nya funktionen kan du göra det möjligt för dina användare att utforska och anpassa visuella objekt, allt i rapportens läsvy. De kan justera det visuella objektet på det sätt de önskar och spara det som ett bokmärke att komma tillbaka till. De behöver inte ha redigeringsbehörighet för rapporten eller gå tillbaka till rapportens författare för att få en ändring.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Anpassa ett visuellt objekt":::
 
## <a name="what-report-consumers-can-change"></a>Vilken rapport konsumenter kan ändra

Med den här funktionen kan användarna få ytterligare insikter via ad hoc-utforskning av visuella objekt på en Power BI-rapport. Information om hur du använder den här funktionen som konsument finns i [Anpassa visuella objekt i dina rapporter](../consumer/end-user-personalize-visuals.md). Funktionen är idealisk för rapportförfattare som vill aktivera grundläggande utforskningsscenarier för rapportläsarna. Följande är ändringar som kan utföras av rapportläsare:

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


## <a name="limitations-and-known-issues"></a>Begränsningar och kända problem

För närvarande har funktionen några begränsningar som du bör vara medveten om.

- Den här funktionen stöds inte för inbäddade scenarier, som att publicera på webben.
- Användares utforskningar sparas inte automatiskt. Du måste spara vyn som ett personligt bokmärke för att kunna samla in dina ändringar.
- Den här funktionen stöds i mobilappar för Power BI för iOS och Android-surfplattor och i Power BI Windows-appen. Det finns inte stöd för Power BI-appar för telefoner. Men eventuella ändringar av visuella objekt som du sparar i ett personligt bokmärke i Power BI-tjänsten sparas i alla Power BI-mobilappar.

Det finns även några kända problem som vi ska lösa:

- Det finns inte stöd för att lägga till hierarki. Du måste lägga till de enskilda underordnade objekten.
- Du kan inte ändra en datumhierarki till ett datum eller vice versa. 
- Med personliga bokmärken kan du få resultat som skiljer sig något från de sekvenser du väljer. Avvikelser är möjliga eftersom vi inte fångar upp rapportens fullständiga status, utan bara de ändringar som har gjorts. Du löser det genom att välja **Återställ till standard** och sedan välja det bokmärke som du vill visa. 

## <a name="next-steps"></a>Nästa steg

[Anpassa visuella objekt i dina rapporter](../consumer/end-user-personalize-visuals.md).     

Testa den nya anpassningen av visuella objekt. Lämna gärna feedback om den här funktionen och hur vi kan fortsätta att förbättra den på [Power BI:s webbplats för idéer](https://ideas.powerbi.com/forums/265200-power-bi). 

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
