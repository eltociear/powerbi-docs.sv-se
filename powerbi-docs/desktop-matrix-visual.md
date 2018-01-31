---
title: "Använd det visuella matrisobjektet i Power BI Desktop"
description: "Läs mer om hur visuella matrisobjekt möjliggör steglayouter och detaljerad markering i Power BI Desktop"
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: ff29fa49cc3ad1a57ae0d09596b6e0d086b4d349
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="use-the-matrix-visual-in-power-bi-desktop"></a>Använd det visuella matrisobjektet i Power BI Desktop
Med det visuella **matris**objektet kan du skapa visuell matrisinformation (kallas ibland också *tabeller*) i **Power BI Desktop**-rapporter och markera flera element i matrisen med andra visuella objekt. Dessutom kan du välja rader, kolumner och även enskilda celler och korsmarkeringar. Matrisen har dessutom stöd för stegvis layout för optimal användning av utrymmet.

![](media/desktop-matrix-visual/matrix-visual_2a.png)

Det finns många funktioner som är kopplade till matrisen och vi ska gå igenom dem i följande avsnitt i den här artikeln.

> [!NOTE]
> Från och med lanseringen i juli 2017 speglar matriser och tabeller i **Power BI Desktop** formatmallar(inklusive färger) från den kopplade **rapportens tema**. Dessa kanske inte är de färger som du förväntar dig för din matris, vilket kan ändras i konfigurationen för ditt **Rapporttema**. Se [**Använda rapportteman i Power BI Desktop**](desktop-report-themes.md) för mer information om teman.
> 
> 

## <a name="using-drill-down-with-the-matrix-visual"></a>Använd detaljerad vy i matris
Det finn sen mängd intressanta aktiviteter som ökar detaljnivån i **matrisen** som inte var tillgängliga tidigare. Detta inkluderar möjligheten att specificera med rader, kolumner och även i enskilda avsnitt och celler. Nu ska vi titta på hur var och en av dessa fungerar.

### <a name="drill-down-on-row-headers"></a>Specificera radrubriker
I fönstret **Visuella objekt**, när du lägger till flera fält i området **Rader** avsnitt brunnen **fält** aktiveras specificering på raderna i matrisen. Detta påminner om hur du skapar en hierarki som sedan låter dig specificera (och återgå) i hierarkin och analysera data på varje nivå.

I följande bild skapar avsnittet **Rader** *Kategori* och *Underkategori* en gruppering (eller hierarki) i de rader som vi kan se i större detalj.

![](media/desktop-matrix-visual/matrix-visual_4.png)

När en gruppering har skapats i avsnittet **Rader** visar det visuella objektet ikonerna *detaljgranska* och *expandera* i det övre vänstra hörnet.

![](media/desktop-matrix-visual/matrix-visual_5.png)

På samma sätt som funktionerna detaljgranska och expandera i andra visuella objekt kan vi detaljgranska hierarkin (eller återgå) med dessa knappar. I det här fallet vi gå från *Kategori* till *Underkategori*, vilket visas i följande bild, där ikonen för att gå ned en detaljnivå (högaffeln) har valts.

![](media/desktop-matrix-visual/matrix-visual_6.png)

Förutom dessa ikoner kan du högerklicka på någon av dessa radrubriker och öka detaljnivån genom att välja från menyn som visas.

![](media/desktop-matrix-visual/matrix-visual_7.png)

Observera att det finns flera alternativ på menyn som visas, vilket genererar olika resultat:

Genom att välja den **detaljnivån** expanderas matrisen för *den* radnivån, *exklusive* radrubriken som högerklickades. I följande bild högerklickade du på *datorer* och valde **detaljnivån**. Observera att andra topprader inte längre visas i matrisen. Detta är en mycket användbar funktion och som är särskilt fiffig när det är dags att **korsmarkera** avsnitt.

![](media/desktop-matrix-visual/matrix-visual_8.png)

Vi kan klicka på ikonen **Byt detaljnivå uppåt** för att gå tillbaka till föregående toppnivån. Om vi sedan väljer **Visa nästa nivå** från snabbmenyn ser vi en alfabetisk lista över alla objekt på nästa nivå (i det här fallet fältet *underkategori*) utan kategoriseringen för nästa hierarkinivå.

![](media/desktop-matrix-visual/matrix-visual_8a.png)

Klicka på ikonen **Byt detaljnivå uppåt** i det övre vänstra hörnet av matrisen visas alla toppkategorier, högerklicka igen och välj **Expandera till nästa nivå**, så visas följande:

![](media/desktop-matrix-visual/matrix-visual_9.png)

Du kan också använda menyalternativen **Inkludera** och **Undanta** för att behålla (eller ta bort, respektive) raden du högerklickade på (och eventuella underkategorier) från matrisen.

### <a name="drill-down-on-column-headers"></a>Gå nedåt i kolumnrubriker
På samma sätt som du kan gå nedåt en nivå i Rader kan du göra samma med **Kolumner**. I följande bild ser du att det finns två fält i fältbrunnen **kolumner**, vilket skapar en hierarki som liknar den som vi använder för rader tidigare i den här artikeln. I fältbrunnen **Kolumner**har vi *Klass* och *Färg*.

![](media/desktop-matrix-visual/matrix-visual_10.png)

När vi högerklickar på en kolumn i **matrisen** visas alternativet att gå nedåt. I följande bild, högerklickar vi på *Deluxe* och väljer **Öka detaljnivån**.

![](media/desktop-matrix-visual/matrix-visual_11.png)

När **detaljnivån** väljs visas nästa nivå i hierarkin för kolumnen *Deluxe*, vilket i detta fall är *Färg*.

![](media/desktop-matrix-visual/matrix-visual_12.png)

Resten av alternativen i högerklicksmenyn fungerar för kolumner på samma sätt som de gör för rader (mer information finns i föregående avsnitt **Specificera radrubriker**). Du kan **Visa nästa nivå**, **Expandera till nästa nivå**, och **Inkludera** eller **Undanta** kolumner på samma sätt som rader.

> [!NOTE]
> Ikonerna för att öka och minska detaljnivån längst upp till vänster på matrisen gäller endast för rader. Du måste använda högerklicksmenyn för att öka detaljnivån i kolumner.
> 
> 

## <a name="stepped-layout-with-matrix-visuals"></a>Stegvis layout med matriser
**Matriser** har automatiskt indrag för underkategorier i en hierarki när de visas under en överordnad kategori. Detta kallas **stegvis layout**.

I den *ursprungliga* versionen av matrisen visades underkategorier i en helt annan kolumn och tog upp mer utrymme i det visuella objektet. Följande bild visar tabellen i ursprungliga **matrisen**. Observera underkategorierna i en separat kolumn.

![](media/desktop-matrix-visual/matrix-visual_14.png)

I följande bild visas en **matris** med **stegvis layout**. Lägg märke till kategorin *datorer* visar underkategorierna något indragna (tillbehör för datorer, stationära datorer, bärbara datorer, skärmar och så vidare) vilket är tydligare och mycket mer komprimerat.

![](media/desktop-matrix-visual/matrix-visual_13.png)

Du kan enkelt ändra inställningarna för **stegvis layout**. Expandera området **radrubriker** i **format**-området (rollerikonen) i fönstret **Visuella objekt** för den valda **matrisen**. Det finns två alternativ: knappen **stegvisa layout** (som aktiverar eller inaktiverar) och **stegvis layoutindrag** (anger indrag i bildpunkter).

![](media/desktop-matrix-visual/matrix-visual_15.png)

Om du inaktiverar **stegvis layout** visas underkategorierna har i en annan kolumn snarare än under överordnad kategori.

## <a name="subtotals-with-matrix-visuals"></a>Delsummor med matriser
Du kan aktivera eller inaktivera delsummor i matriser, för såväl rader som kolumner. I följande bild ser du att raddelsummor är inställda på **På**.

![](media/desktop-matrix-visual/matrix-visual_20.png)

I området **Format** i fönstret **Visuella objekt** expanderar du kortet **Delsummor** och aktiverar skjutreglaget **Raddelsummor** till  **Inaktivera**. När du gör det visas inte delsummor.

![](media/desktop-matrix-visual/matrix-visual_21.png)

Samma sak gäller för kolumndelsummor.

## <a name="cross-highlighting-with-matrix-visuals"></a>Korsmarkering med matriser
Med **matriser** kan alla element väljs som grund för korsmarkering. Markera en kolumn i en **matris** för att markera den och alla andra visuella objekt på rapportsidan. Detta har varit en vanlig funktion för andra visuella objekt och val av datapunkter. Nu gäller detta även för **matriser**.

Dessutom fungerar CTRL + klicka för cross-markering. I följande bild valdes till exempel en samling av underkategorier från **matrisen**. Observera hur objekt som inte var markerat från det visuella objektet är nedtonade och hur övriga visuella objekt på sidan återspeglar de val du gjorde i **matrisen**.

![](media/desktop-matrix-visual/matrix-visual_16.png)

## <a name="shading-and-font-colors-with-matrix-visuals"></a>Fyllning och teckenfärger med matriser
Med **matriser** kan du använda **villkorsstyrd formatering** (färger och fyllning) för cellernas bakgrundsfärger och samt på själva texten och värdena.

Om du vill tillämpa villkorsstyrd formatering, kan du göra något av följande när en matris väljs:

* I fönstret **Fält** högerklickar du på fältet och väljer **Villkorsstyrd formatering** på menyn.
  
  ![](media/desktop-matrix-visual/matrix-visual_17.png)
* Alternativt kan du gå till fönstret **Format** och expandera kortet **Villkorsstyrd formatering** och flytta skjutreglaget till **på** för antingen **Bakgrundsfärgskalor** eller **Teckensnittfärgskalor**. När du aktiverar någon av dessa visas en länk till *avancerade kontroller*, där du kan anpassa färger och värden för formatering av färg.
  
  ![](media/desktop-matrix-visual/matrix-visual_18.png)

Båda metoder ger samma resultat. Om du väljer *avancerade kontroller* visas följande dialogruta där du kan göra justeringar:

![](media/desktop-matrix-visual/matrix-visual_19.png)

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
Det finns några begränsningar och saker du bör tänka på för den här versionen av det visuella objektet **Matris**.

* Du kan endast ändra detaljnivån för kolumner med högerklickmenyn och det finns ingen indikation på det visuella objektet som visar att du kan ändra detaljnivån för rader eller kolumner
* Du kan endast expandera alla objekt på en nivå åt gången, snarare än att expandera en kategori i taget
* **Se poster** kan visas på en meny när du högerklickar på en kolumnrubrik, men funktionen är inte aktiv
* Det finns för närvarande ingen rad med *totalsumman*
* Det har ingen verkan att stänga av raden delsummor i den stegvisa layouten
* Kolumnrubriker kan trunkeras om de inre grupperna har kortare text än den yttersta gruppen
* Om indraget för den stegvisa layouten ändras bör inte en yttersta gruppens indrag ändras

Vi kan alltid höra dina synpunkter. Vi håller på att utföra en **undersökning** om **matrisen**, så om du har några minuter uppskattar vi om du genomför [ undersökningen](https://www.instant.ly/s/PYXT1).

