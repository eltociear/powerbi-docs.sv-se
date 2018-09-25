---
title: Lägg till bild-, text-, video- och strömmande data på instrumentpanelen
description: Dokumentation om hur du använder lägg till panel-widgeten för att lägga till en bild, video, textruta, webbkod och strömmande datapanel till en instrumentpanel.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: e2PD8m1Q0vU
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 68195883f2aad0f3131ec14c508334ac41cd918b
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/21/2018
ms.locfileid: "46545877"
---
# <a name="add-image-text-video-and-more-to-your-dashboard"></a>Lägg till bild, text, video och mer till din instrumentpanel
<iframe width="560" height="315" src="https://www.youtube.com/embed/e2PD8m1Q0vU" frameborder="0" allowfullscreen></iframe>


## <a name="add-tile"></a>Lägg till panel
Kontrollen **lägg till panel** låter dig direkt lägga till en bild, textruta, video, strömmande data eller webbkod till din instrumentpanel.

1. Välj **lägg till panel** från den översta menyraden. Beroende på utrymmesbegränsningarna kanske du bara ser plustecknet ![plustecken](media/service-dashboard-add-widget/power-bi-add-tile-icon-small.png).
   
    ![Ikonen Lägg till panel](media/service-dashboard-add-widget/power-bi-add-tile-icon.png)
2. Välj vilken typ av panel du vill lägga till: **bild**, **textruta**, **video**, **webbinnehåll** eller **anpassade strömmande data**.
   
    ![fönstret Lägg till panel](media/service-dashboard-add-widget/power-bi-add-tile.png)

## <a name="add-an-image"></a>Lägg till en bild
Anta att du vill ha företagets logotyp på instrumentpanelen eller någon annan bild. Du behöver då spara bildfilen online och länka till den. Kontrollera att det inte behövs särskilda autentiseringsuppgifter för att komma åt bildfilen. OneDrive och SharePoint kräver till exempel autentisering så bilder som lagras där går inte att lägga till på en instrumentpanel på det sättet.  

1. Välj **bild** > **nästa**.
2. Lägg till bildinformation till fönstret **Lägg till bildpanel**.
   
    ![Fönstret Lägg till bildpanel](media/service-dashboard-add-widget/pbi-widget-add-image-new.png)
   
   * Om du vill visa en rubrik ovanför bilden, väljer du *visa rubrik och underrubrik* och anger en rubrik och/eller underrubrik.
   * ange bildens URL
   * om du vill göra panelen till en hyperlänk, väljer du **ställ in anpassad länk** och ange URL:en.  När kollegor klickar på den här bilden eller rubriken, vidarebefordras de till denna URL.
   * Välj **Tillämpa**.  På instrumentpanelen, ändrar du storlek på och flyttar bilden efter behov.
     
     ![bild på instrumentpanel](media/service-dashboard-add-widget/power-bi-add-image-dash.png)

## <a name="add-a-text-box-or-dashboard-heading"></a>Lägg till en rubrik för en textruta eller instrumentpanel
1. Välj **textruta > nästa**.
   
   > **Obs**: Om du vill lägga till en rubrik för en instrumentpanel, skriver du in rubriken i textrutan och ökar teckensnittet.
   > 
2. Formatera textrutan:
   
   * om du vill visa en rubrik ovanför textrutan, väljer du **visa rubrik och underrubrik** och anger en rubrik och/eller underrubrik.
   * ange och formatera innehållet i textrutan.  
   * Du kan också ange en anpassad länk för rubriken. En anpassad länk kan gå till en extern webbplats eller en instrumentpanel eller rapport på arbetsytan. Men i det här exemplet har vi lagt till hyperlänkar i själva textrutan så vi lämnar **Ställ in anpassad länk** avmarkerad.

     ![Fönstret Lägg till textrutepanel](media/service-dashboard-add-widget/power-bi-add-textbox.png)
   
3. Välj **Tillämpa**.  På instrumentpanelen, ändrar du storlek på och flyttar textrutan efter behov.
   
   ![instrumentpanel med bild och textruta](media/service-dashboard-add-widget/pbi-widget-text-added-new.png)

## <a name="add-a-video"></a>Lägg till en video
När du lägger till en YouTube eller Vimeo-videopanel på instrumentpanelen, spelar videon direkt på din instrumentpanel.

1. Välj **video > nästa**.
2. Lägg till videoinformation till panelen **Lägg till videopanel**.
   
    ![Fönstret Lägg till videopanel](media/service-dashboard-add-widget/power-bi-add-video-new.png)
   
   * om du vill visa en rubrik och underrubrik ovanför videopanelen, väljer du *visa rubrik och underrubrik* och anger en rubrik och/eller underrubrik. I det här exemplet ska vi lägga till en underrubrik och omvandla den till en hyperlänk till hela spellistan på YouTube.
   * ange URL:en för videon
   * Lägg till en hyperlänk för rubriken och underrubriken.  När dina kollegor tittar på det inbäddade videoklippet kanske de vill kunna se hela spellistan på YouTube – lägg till en länk till din spellista här.
   * Välj **Tillämpa**.  På instrumentpanelen, ändrar du storlek på och flyttar videopanelen efter behov.
     
      ![instrumentpanel med tillagd videopanel](media/service-dashboard-add-widget/pbi-widget-video-added-new.png)
3. Välj videopanelen för att spela videon.
4. Välj underrubriken för att gå till spellistan på YouTube.

## <a name="add-streaming-data"></a>Lägg till strömmande data
<iframe width="560" height="315" src="https://www.youtube.com/embed/kOuINwgkEkQ" frameborder="0" allowfullscreen></iframe>

## <a name="add-web-content"></a>Lägg till webbinnehåll
Klistra in eller skriv in valfritt HTML-innehåll.  Power BI lägger till det, som en panel, på din instrumentpanel. Ange inbäddningskoden manuellt eller kopiera och klistra in från webbplatser som Twitter, YouTube, embed.ly och många fler.

1. Välj **webbinnehåll > nästa**.
2. Lägg till information i fönstret **lägg till webbinnehållspanel**.
   
    ![Fönstret Lägg till webbinnehållspanel](media/service-dashboard-add-widget/power-bi-add-web-content.png)
   
   * om du vill visa en rubrik ovanför panelen, väljer du *visa rubrik och underrubrik* och anger en rubrik och/eller underrubrik.
   * ange inbäddningskoden. I det här exemplet kopierar vi och klistrar in ett Twitter-flöde.
3. Välj **Tillämpa**.  På instrumentpanelen, ändrar du storlek på och flyttar webbinnehållspanelen efter behov.
     
      ![instrumentpanel med 4 paneler](media/service-dashboard-add-widget/pbi-widget-code-added-new.png)

## <a name="tips-for-embedding-web-content"></a>Tips för inbäddning av webbinnehåll
* Använd en säker källa för iframes. Om du anger din iframe-inbäddningskod och får en tom panel, kontrollerar du att du använder **http** för iframe-källan.  Om så är fallet, kan du ändra till **https**.
  
  ```
  <iframe src="https://xyz.com">
  ```
* Redigera bredd- och höjdinformation. Den här inbäddningskoden bäddar in en video och ställer in videospelaren till 560 x 315 bildpunkter.  Den här storleken ändras inte när du ändrar storlek på panelen.
  
  ```
  <iframe width="560" height="315"
  src="https://www.youtube.com/embed/Cle_rKBpZ28" frameborder="0"
   allowfullscreen></iframe>
  ```
  
  Om du vill att spelaren ändrar storlek för att passa panelen, anger du bredd och höjd till 100%.
  
  ```
  <iframe width="100%" height="100%"
  src="https://www.youtube.com/embed/Cle_rKBpZ28" frameborder="0"
   allowfullscreen></iframe>
  ```
* Den här koden bäddar in en tweet och bevarar, som separata länkar på instrumentpanelen, länkar till **AFK**-podcasten,  **@GuyInACubes Twittersida**, **följ**,  **#analytics**, **svara**, **retweeta**, och **gilla**.  Om du väljer själva panelen så går du till podcasten på Twitter.
  
  ```
  <blockquote class="twitter-tweet" data-partner="tweetdeck">
  <p lang="en" dir="ltr">Listen to
  <a href="https://twitter.com/GuyInACube">@GuyInACube</a> talk to
  us about making videos about Microsoft Business Intelligence
  platform
  <a href="https://t.co/TmRgalz7tv">https://t.co/TmRgalz7tv </a>
  <a href="https://twitter.com/hashtag/analytics?src=hash">
  #analytics</a></p>&mdash; AFTK Podcast (@aftkpodcast) <a
  href="https://twitter.com/aftkpodcast/status/693465456531771392">
  January 30, 2016</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
  ```

## <a name="edit-a-tile"></a>Redigera en panel
Om du vill göra ändringar i en panel...

1. Hovra över övre högra hörnet på panelen och välj ellipserna.
   
    ![välj panelellips](media/service-dashboard-add-widget/pbi_ellipses.png)
2. Välj redigeringsikonen för att öppna fönstret **panelinformation** och göra ändringar.
   
    ![pennredigeringsikonen](media/service-dashboard-add-widget/pbi-edit.png)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
* Om du vill göra det lättare att flytta panelen på din instrumentpanel, kan du lägga till en rubrik och/eller underrubrik.
* Om du vill bädda in innehåll från en webbplats, men inte får någon inbäddningskod från webbplatsen att kopiera och klistra in, kan du kolla embed.ly för hjälp med att skapa inbäddningskoden.

## <a name="next-steps"></a>Nästa steg
[Instrumentpaneler](consumer/end-user-tiles.md)

Har du fler frågor? [Testa Power BI Community](http://community.powerbi.com/).

