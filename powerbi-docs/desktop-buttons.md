---
title: Använda knappar i Power BI
description: Du kan lägga till knappar i Power BI-rapporter som gör att dina rapporter fungerar som appar, och fördjupar engagemanget hos användarna.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 6629165ec031fea0d1c1af443e1d7b311bc743aa
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79201652"
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
- Med **Detaljerad information (förhandsversion)** navigerar användaren till en detaljgranskningssida som filtrerats efter deras val, utan att använda bokmärken. Läs mer om [detaljgranskningsknappar i rapporter](desktop-drill-through-buttons.md).
- Med **Sidnavigering** navigerar användaren till en annan sida i rapporten, också utan att använda bokmärken. Mer information finns i [Skapa sidnavigering](#create-page-navigation) i den här artikeln.
- **Frågor och svar** öppnar fönstret **Frågor och svar-utforskaren**. 

Vissa knappar har en standardåtgärd som väljs automatiskt. För knapptypen **Frågor och svar** väljs till exempel automatiskt **Frågor och svar** som standardåtgärd. Du kan läsa mer om **Frågor och svar-utforskaren** i [det här blogginlägget](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer).

Du kan prova eller testa knapparna som du skapar för rapporten genom att *CTRL+klicka* på knappen som du vill använda. 

### <a name="create-page-navigation"></a>Skapa sidnavigering

Med **Åtgärd**-typen **Sidnavigering** kan du snabbt skapa en hel navigeringsupplevelse utan att behöva spara eller hantera några bokmärken.

Om du vill konfigurera en sidnavigeringsknapp, skapar du en knapp med **Sidnavigering** som åtgärdstyp och väljer **Mål**-sidan.

![Åtgärden Sidnavigering](media/desktop-buttons/power-bi-page-navigation.png)

Du kan snabbt skapa ett anpassat navigeringsfönster. Du undviker att behöva redigera och hantera bokmärken om du vill ändra vilka sidor som ska visas i navigeringsfönstret.

![Skapa en navigeringssida](media/desktop-buttons/power-bi-build-navigation-pane.png)

Du kan också använda villkorlig formatering för knappbeskrivningen som du kan göra med andra knapptyper.

## <a name="next-steps"></a>Nästa steg
Mer information om liknande funktioner eller funktioner som interagerar med knappar finns i följande artiklar:

* [Använda detaljvisning i Power BI-rapporter](desktop-drillthrough.md)
* [Använda bokmärken för att dela information och skapa artiklar i Power BI](desktop-bookmarks.md)

