---
title: Använda knappar i Power BI
description: Du kan lägga till knappar i Power BI-rapporter som gör att dina rapporter fungerar som appar, och fördjupar engagemanget hos användarna.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/21/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 7597d135bc05783d0d43bb481e24fc197abd9d4b
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85222396"
---
# <a name="use-buttons-in-power-bi"></a>Använda knappar i Power BI
Med hjälp av **knappar** i Power BI kan du skapa rapporter som fungerar ungefär som appar. Därigenom skapar du en engagerande miljö så att användarna kan hovra, klicka och interagera ytterligare med Power BI-innehåll. Du kan lägga till knappar i rapporter i **Power BI Desktop** och i **Power BI-tjänsten**. När du delar dina rapporter i Power BI-tjänsten ger de en appliknande upplevelse för dina användare.

![Knappar i Power BI](media/desktop-buttons/power-bi-buttons.png)

## <a name="create-buttons-in-reports"></a>Skapa knappar i rapporter

### <a name="create-a-button-in-power-bi-desktop"></a>Skapa en knapp i Power BI Desktop

Du skapar en knapp i **Power BI Desktop** genom att gå till fliken **Infoga** och välja **Knappar**. Då visas en listmeny där du kan välja en knapp från en samling med alternativ, enligt följande bild. 

![Lägg till en knappkontroll i Power BI Desktop](media/desktop-buttons/power-bi-button-dropdown.png)

### <a name="create-a-button-in-the-power-bi-service"></a>Skapa en knapp i Power BI-tjänsten

I **Power BI-tjänsten** skapar du en knapp genom att öppna rapporten i redigeringsvyn. Välj **Knappar** i det övre menyfältet så visas en listmeny där du kan välja en knapp från en samling med alternativ, enligt följande bild. 

![Lägga till en knappkontroll i Power BI-tjänsten](media/desktop-buttons/power-bi-button-service-dropdown.png)

## <a name="customize-a-button"></a>Anpassa en knapp

Oavsett om du skapar knappen i Power BI Desktop eller Power BI-tjänsten, är resten av processen densamma. När du väljer knappen på rapportarbetsytan visas de många sätt som du kan anpassa knappen efter dina behov i fönstret **Visualiseringar**. Du kan till exempel aktivera eller inaktivera **Knapptext** genom att växla skjutreglaget i det kortet i fönstret **Visualiseringar**. Du kan också ändra knappens ikon, knappfyllning, rubrik och vad som händer när användare väljer knappen i en rapport, bland andra egenskaper.

![Formatera en knapp i en Power BI-rapport](media/desktop-buttons/power-bi-button-properties.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>Ange knappegenskaper vid inaktivitet, hovring eller markering

Knappar i Power BI har tre lägen: standard (hur de visas utom vid hovring eller markering), vid hovring eller vid markering (kallas ofta för *klickning*). Många av korten i fönstret **Visualiseringar** kan ändras individuellt baserat på dessa tre lägen, vilket ger stor flexibilitet för anpassning av knapparna.

På följande kort i fönstret **Visualiseringar** kan du ändra formatering eller funktion för en knapp baserat på dess tre lägen:

* Knapptext
* Ikon
* Kontur
* Fyllning

Du väljer hur knappen ska visas för respektive läge genom att expandera ett av korten och välja listrutan som visas längst upp på kortet. På följande bild är kortet **Ikon** expanderat, med listrutan vald så att de tre lägena visas.

![Tre lägen för en knapp i en Power BI-rapport](media/desktop-buttons/power-bi-button-format.png)

## <a name="select-the-action-for-a-button"></a>Välja åtgärden för en knapp

Du kan välja vilken åtgärd som ska utföras när en användare markerar en knapp i Power BI. Du hittar alternativen för knappåtgärder på kortet **Åtgärd** i fönstret **Visualiseringar**.

![Åtgärd för en knapp i Power BI](media/desktop-buttons/power-bi-button-action.png)

Alternativen för knappåtgärder är:

- Med **Bakåt** kommer användaren tillbaka till föregående sida i rapporten. Detta är användbart för att gå igenom sidor.
- Med **Bokmärke** visas rapportsidan som är kopplad till ett bokmärke som har definierats för den aktuella rapporten. Läs mer om [bokmärken i Power BI](desktop-bookmarks.md). 
- Med **Detaljerad information** navigerar användaren till en detaljgranskningssida som filtrerats efter deras val, utan att använda bokmärken. Läs mer om [detaljgranskningsknappar i rapporter](desktop-drill-through-buttons.md).
- Med **Sidnavigering** navigerar användaren till en annan sida i rapporten, också utan att använda bokmärken. Mer information finns i [Skapa sidnavigering](#create-page-navigation) i den här artikeln.
- **Frågor och svar** öppnar fönstret **Frågor och svar-utforskaren**. 

Vissa knappar har en standardåtgärd som väljs automatiskt. För knapptypen **Frågor och svar** väljs till exempel automatiskt **Frågor och svar** som standardåtgärd. Du kan läsa mer om **Frågor och svar-utforskaren** i [det här blogginlägget](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer).

Du kan prova eller testa knapparna som du skapar för rapporten genom att *CTRL+klicka* på knappen som du vill använda. 

## <a name="create-page-navigation"></a>Skapa sidnavigering

Med **Åtgärd**-typen **Sidnavigering** kan du skapa en hel navigeringsupplevelse utan att behöva spara eller hantera några bokmärken.

Om du vill konfigurera en sidnavigeringsknapp, skapar du en knapp med **Sidnavigering** som åtgärdstyp och väljer **Mål**-sidan.

![Åtgärden Sidnavigering](media/desktop-buttons/power-bi-page-navigation.png)

Du kan skapa ett anpassat navigeringsfönster och lägga till navigeringsknapparna till det. Du undviker att behöva redigera och hantera bokmärken om du vill ändra vilka sidor som ska visas i navigeringsfönstret.

![Skapa en navigeringssida](media/desktop-buttons/power-bi-build-navigation-pane.png)

Du kan också använda villkorlig formatering för knappbeskrivningen som du kan göra med andra knapptyper.

## <a name="set-the-navigation-destination-conditionally"></a>Ange villkor för navigeringsmålet

Du kan använda villkorsstyrd formatering för att ställa in ett mål för navigering baserat på utdata för ett mått. Du kanske till exempel vill spara utrymme på rapportarbetsytan genom att ha en enda knapp för att navigera till olika sidor baserat på användarens val.

:::image type="content" source="media/desktop-buttons/button-navigate-go.png" alt-text="Navigera med en Go-knapp":::
 
Om du vill skapa exemplet ovan börjar du med att skapa en tabell med en kolumn med namnen på navigeringsmålen:

:::image type="content" source="media/desktop-buttons/button-create-table.png" alt-text="Skapa en tabell":::

Power BI använder den exakta strängmatchningen för att ställa in detaljgranskningsmålet, så dubbelkolla att värdena som anges exakt överensstämmer med dina namn för detaljnivån.

När du har skapat tabellen lägger du till den på sidan som ett utsnitt för enskilt val:

:::image type="content" source="media/desktop-buttons/button-navigate-slicer.png" alt-text="Navigera utsnitt":::

Skapa sedan en navigeringsknapp för sidan och välj alternativet Villkorsstyrd formatering för målet:

:::image type="content" source="media/desktop-buttons/button-set-page-nav-destination.png" alt-text="Sidnavigeringsknapp":::
 
Välj namnet på kolumnen som du skapade, i det här fallet **Välj ett mål**:

:::image type="content" source="media/desktop-buttons/button-select-destination.png" alt-text="Välj ett mål":::

Nu kan knappen navigera till olika sidor beroende på användarens val.

:::image type="content" source="media/desktop-buttons/button-navigate-go.png" alt-text="Navigera med en Go-knapp":::
 
### <a name="shapes-and-images-for-navigation"></a>Former och bilder för navigering

Sidnavigeringsåtgärd stöds för former och bilder, inte bara knappar. Här är ett exempel på en av de inbyggda formerna:

:::image type="content" source="media/desktop-buttons/button-navigation-arrow.png" alt-text="Använd en pil för navigering":::
 
Här är ett exempel på hur du använder en avbildning:

:::image type="content" source="media/desktop-buttons/button-navigation-image.png" alt-text="Använd en bild för navigering":::
 
## <a name="buttons-support-fill-images"></a>Knappar stöder fyllningsbilder

Knappar stöder fyllningsbilder. Du kan anpassa utseendet på knappen med fyllningsbilder tillsammans med de inbyggda knapptillstånden: standard, vid hovring, vid musklickning och inaktiverad (för ökad detaljnivå).

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-fill-images.png" alt-text="Knapp för att gå ner på detaljnivå för fyllnadsbilder":::

Ställ in **Fyllning** på **På**och skapa sedan avbildningar för de olika tillstånden.

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-fill-state-settings.png" alt-text="Inställningar för fyllningsbilder":::


## <a name="next-steps"></a>Nästa steg
Mer information om liknande funktioner eller funktioner som interagerar med knappar finns i följande artiklar:

* [Använda detaljvisning i Power BI-rapporter](desktop-drillthrough.md)
* [Använda bokmärken för att dela information och skapa artiklar i Power BI](desktop-bookmarks.md)
* [Skapa en knapp för att gå ner på detaljnivå](desktop-drill-through-buttons.md)

