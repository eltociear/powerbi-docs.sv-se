---
title: Fyllda kartor (koropleter) i Power BI
description: Dokumentation om att skapa fyllda kartor (koropletkartor) i Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/19/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 9c35e97fba55230277f9f144a5155071656b6add
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73870967"
---
# <a name="filled-maps-choropleths-in-power-bi"></a>Fyllda kartor (koropleter) i Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

En fylld karta använder skuggning, toning eller mönster för att visa hur ett värde skiljer sig åt proportionellt på en geografisk plats eller i en region.  Du kan snabbt visa dessa relativa skillnader med skuggning som sträcker sig från ljus (mindre ofta/lägre) till mörk (mer frekvent/fler).    

![Karta över USA](media/power-bi-visualization-filled-maps-choropleths/large-map.png)

## <a name="what-is-sent-to-bing"></a>Vad som skickas till Bing
Power BI integrerar med Bing för att tillhandahålla kartkoordinater av standardtyp (en process som kallas geokodning). När du skapar en kartvisualisering i Power BI-tjänsten eller i Power BI Desktop, skickas dina data i behållarna **Plats**, **Latitud** och **Longitud** (som används för att skapa visualiseringen) till Bing.

Du eller din administratör kan behöva uppdatera brandväggen för att tillåta åtkomst till de URL:er Bing använder för geokodning.  Dessa URL:er är:
- https://dev.virtualearth.net/REST/V1/Locations    
- https://platform.bing.com/geo/spatial/v1/public/Geodata    
- https://www.bing.com/api/maps/mapcontrol

Mer information om de data som skickas till Bing och tips för bättre geokodning hittar du i [Tips and tricks for map visualizations (Tips och råd om kartvisualiseringar)](power-bi-map-tips-and-tricks.md).

## <a name="when-to-use-a-filled-map"></a>När du ska använda en fylld karta
Fyllda kartor är ett bra alternativ:

* för att visa kvantitativ information på en karta,
* för att visa spatiala mönster och relationer,
* när dina data är standardiserade,
* när du arbetar med socioekonomiska data,
* när definierade regioner är viktiga,
* för att få en översikt över distributionen på flera geografiska platser.

### <a name="prerequisites"></a>Förutsättningar
De här självstudierna använder sig av [PBIX-filen Exempel på detaljhandelsanalys](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix).
1. Välj **Arkiv** > **Öppna** uppe till vänster i menyraden
   
2. Leta reda på kopian av **PBIX-filen Exempel för detaljhandelsanalys**

1. Öppna **PBIX-filen Exempel för detaljhandelsanalys** i rapportvyn ![Skärmbild av rapportvisningsikonen.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Välj ![Skärmbild av den gula fliken.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) för att lägga till en ny sida.


## <a name="create-a-basic-filled-map"></a>Skapa en grundläggande fylld karta
I det här videoklippet skapar Kim en grundläggande karta och konverterar den till en fylld karta.
   > [!NOTE]
   > I den här videon används en äldre version av Power BI Desktop.
   > 
   > 

<iframe width="560" height="315" src="https://www.youtube.com/embed/ajTPGNpthcg" frameborder="0" allowfullscreen></iframe>

### <a name="create-a-filled-map"></a>Skapa en koropletkarta
1. Fönstret fält, Välj den **Geo** \> **tillstånd** fältet.    

   ![gul bockmarkering bredvid Stat](media/power-bi-visualization-filled-maps-choropleths/power-bi-state.png)
2. [Konvertera diagrammet](power-bi-report-change-visualization-type.md) till en fylld karta. Observera att **Stat** nu befinner sig i **platsområdet**. Bing Maps använder fältet i **platsområdet** för att skapa kartan.  Platsen kan vara många olika giltiga platser: länder, stater, regioner, orter, postnummer och andra postkoder och så vidare. Bing Maps tillhandahåller figurer för platser runt om i världen. Power BI kan inte skapa den fyllda kartan utan en giltig post i platsområdet.  

   ![mallar med ikonen för fylld karta markerad](media/power-bi-visualization-filled-maps-choropleths/img003.png)
3. Filtrera kartan för att visa endast kontinentala USA.

   a.  Till vänster i visualiseringsfönstret finns rutan **Filter**. Expandera den om den är minimerad

   b.  Hovra över **Stat** och välj den expanderade sparren  
   ![Visuella nivåfilter som visar Stat (alla)](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   c.  Sätt en bock bredvid **Alla** och ta bort bocken bredvid **AK**.

   ![Listruta för stat där Alla och AK inte har markerats](media/power-bi-visualization-filled-maps-choropleths/img005.png)
4. Välj rollerikonen för att öppna formateringsfönstret och välj  **Datafärger**.

    ![Formatfönstret som visar alternativet Datafärger](media/power-bi-visualization-filled-maps-choropleths/power-bi-data-color.png)

5. Välj de tre lodräta punkterna och sedan **Villkorsstyrd formatering**.

    ![Knapp för villkorsstyrd formatering av datafärger](media/power-bi-visualization-filled-maps-choropleths/power-bi-conditional-formatting.png)

6. Använd skärmen **Standardfärg – Datafärger** för att bestämma hur din koropletkarta ska skuggas. De alternativ som du kan välja mellan inkluderar vilket fält du ska basera skuggningen på och hur den ska tillämpas. I det här exemplet använder vi fältet **SalesFact** > **Sentiment** och anger det lägsta värdet för sentiment som rött och det högsta värdet som grönt. Värden som faller mellan de högsta och lägsta värdena kommer att ha olika nyanser av rött och grönt. Bilden längst ned på skärmen visar de olika färger som kommer att användas. 

    ![Standardfärgfönster med Sentiment valt](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment.png)

7. Koropletkartan färgas i grönt och rött, där rött motsvarar de lägre sentimentsiffrorna och grönt de högre, positivare sentimenten.  Dra ett fält till knappbeskrivningsområdet för att visa ytterligare information.  Här jag har lagt till **sentimentgap** och markerat staten Idaho (ID) och kan se att sentimentgapet är lågt, bara 6.
   ![koropletkarta som visar knappbeskrivningar för Idaho](media/power-bi-visualization-filled-maps-choropleths/power-bi-filled-map-idaho.png)

10. [Spara rapporten](../service-report-save.md).

Power BI ger dig stor kontroll över hur din koropletkarta ska se ut. Experimentera med färgkontrollerna tills det ser ut som du önskar. 

## <a name="highlighting-and-cross-filtering"></a>Markering och korsfiltrering
Information om hur du använder filterfönstret finns i [Lägg till ett filter i en rapport](../power-bi-report-add-filter.md).

Om du markerar en plats i en koropletkarta korsfiltreras de övriga visualiseringarna på rapportsidan, och vice versa.

1. Spara den här rapporten genom att välja **Arkiv > Spara**. 

2. Kopiera koropletkartan med hjälp av CTRL-C.

3. Längst ned i rapportarbetsytan kan du välja fliken **Sentiment** för att öppna rapportsidan för sentiment.

    ![Fliken Sentiment har valts](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-tab.png)

4. Flytta och ändra storlek på visualiseringarna på sidan för att skapa mer utrymme, och använd sedan CTRL + V för att klistra in koropletkartan från föregående rapport. (Se nedanstående bilder)

   ![Koropletkarta som har lagts till på sentimentsidan](media/power-bi-visualization-filled-maps-choropleths/power-bi-map.png)

5. Välj en stat på den fyllda kartan.  Detta korsmarkerar och korsfiltrerar de övriga visualiseringarna på sidan. Om jag väljer exempelvis **Texas** ser jag att är sentimentet 75 och att Texas ligger i Central District nr 23.   
   ![Texas har valts](media/power-bi-visualization-filled-maps-choropleths/power-bi-texas.png)
2. Välj en datapunkt i linjediagrammet VanArsdel – Sentiment per månad. Detta filtrerar koropletkartan för att visa sentimentdata för VanArsdel och inte deras konkurrenter.  
   ![ny färgning](media/power-bi-visualization-filled-maps-choropleths/power-bi-yes.png)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
Kartdata kan vara tvetydiga.  Till exempel finns det ett Paris i Frankrike, men också i Texas. Dina geografiska data lagras sannolikt i separata kolumner – en kolumn för stadsnamn, en kolumn för stats- eller regionnamn och så vidare – så Bing kan förmodligen inte avgöra skillnaden mellan de två olika Paris. Om din datauppsättning redan innehåller data för latitud och longitud, har Power BI speciella fält för att hjälpa till att göra dina kartdata entydiga. Du behöver bara dra fältet som innehåller dina latituddata till området Visualiseringar \> Latitud.  Gör sedan samma sak för dina longituddata.    

![Fönster för visualiseringar och fält](media/power-bi-visualization-filled-maps-choropleths/pbi-latitude.png)

Titta på den här videon för hjälp med tvetydigheter beträffande kartdata om du har behörighet att redigera datauppsättningen i Power BI Desktop.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Co2z9b-s_yM" frameborder="0" allowfullscreen></iframe>

Om du inte har åtkomst till latitud- och longituddata, men redigeringsåtkomst till datamängden, [följer du de här instruktionerna för att uppdatera datamängden](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7).

Mer hjälp med kartvisualiseringar finns i [Tips and tricks for map visualizations (Tips och råd om kartvisualiseringar)](../power-bi-map-tips-and-tricks.md).

## <a name="next-steps"></a>Nästa steg

[Formkarta](desktop-shape-map.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)