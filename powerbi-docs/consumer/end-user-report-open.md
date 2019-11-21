---
title: Visa en rapport
description: Det här avsnittet visar hur Power BI-användare öppnar och visar en Power BI-rapport.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/04/2018
ms.author: mihart
ms.openlocfilehash: b22da2df92c0cc7130c7a5ebf69e2284c12ffef4
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73861978"
---
# <a name="view-a-report-in-the-power-bi-service-for-consumers"></a>Visa en rapport i Power BI-tjänsten för *konsumenter*

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

En rapport är en eller flera sidor med visuella objekt. Rapporter skapas av Power BI-*designer* och [delas med *användare* direkt](end-user-shared-with-me.md) eller som en del av en [app](end-user-apps.md). 

Det finns många olika sätt att öppna en rapport och vi kommer att visa dig två av dem: Öppna från startsidan och öppna från en instrumentpanel. 

<!-- add art-->


## <a name="open-a-report-from-power-bi-home"></a>Öppna en rapport från Power BI-start
Nu ska vi öppna en rapport som har delats med dig direkt och sedan öppnar en rapport som har delats som en del av en app.

   ![Startsida](./media/end-user-report-open/power-bi-home-canvas.png)

### <a name="open-a-report-that-has-been-shared-with-you"></a>Öppna en rapport som har delats med dig
Power BI-*designers* kan dela en enskild rapport direkt med dig via en länk i ett e-postmeddelande eller genom att lägga till den automatiskt. Innehåll som delas på detta sätt visas i containern **delat med mig** i navigeringfönstret och i avsnittet **delat med mig** på Hem-arbetsytan.

1. Öppna Power BI-tjänsten (app.powerbi.com).

2. Visa Hem-arbetsytan genom att välja **Hem** i navigeringsfönstret.  

   ![Hem-arbetsytan](./media/end-user-report-open/power-bi-select-home-new.png)
   
3. Rulla nedåt tills du ser **delat med mig**. Leta efter rapportikonen ![rapportikon](./media/end-user-report-open/power-bi-report-icon.png). På den här skärmbilden har vi en instrumentpanel och en *rapport med namnet* försäljnings- och marknadsföringsexempel. 
   
   ![delat med mig-delen av startsidan](./media/end-user-report-open/power-bi-shared-new.png)

4. Öppna rapporten genom att välja *rapportkortet*.

   ![rapportsida](./media/end-user-report-open/power-bi-open.png)

5. Observera flikarna längs vänster sida.  Varje flik representerar en *sida* i rapporten. Just nu är sidan för *Tillväxtmöjligheter* öppen. Välj fliken *YTD-kategori* för att öppna rapportsidan i stället. 

   ![flikar för rapportsida](./media/end-user-report-open/power-bi-ytd.png)

6. Expandera fönstret **Filter** till höger. Filter som har tillämpats på den här rapportsidan eller i hela rapporten visas här.

7. När du hovrar över ett visuellt rapportobjekt visas flera ikoner och **Fler alternativ** (...). Om du vill se de filter som används för ett visst visuellt objekt väljer du filterikonen. Här har vi valt filterikonen för linjediagrammet *Totalt antal enheter efter rullande period och region*.

   ![flikar för rapportsida](./media/end-user-report-open/power-bi-visual-filters.png)

6. Just nu ser vi hela rapportsidan. Om du vill ändra visningen (zoomning) av sidan väljer du listrutan Visa från det övre högra hörnet och väljer **Faktisk storlek**.

   ![ändra zoom](./media/end-user-report-open/power-bi-fit-new.png)

   ![anpassa till sida](./media/end-user-report-open/power-bi-actual.png)

### <a name="open-a-report-that-is-part-of-an-app"></a>Öppna en rapport som är en del av en app
Om du har tagit emot appar från kollegor eller från AppSource, är dessa appar tillgängliga från startsidan och från containern **Appar** i navigeringsfönstret. En [app](end-user-apps.md) är ett paket med instrumentpaneler och rapporter.

### <a name="prerequisites"></a>Förutsättningar
Om du vill följa med hämtar du appen Försäljning och marknadsföring.
1. Navigera till appsource.microsoft.com i webbläsaren.
1. Sök efter "Försäljning och marknadsföring" och välj **Microsofts exempel – Försäljning & marknadsföring**.
1. Välj **Hämta nu** > **Fortsätt** > **Installera** för att installera appen i din appbehållare. 

Du kan öppna appen från din appbehållare eller från Start.
1. Gå tillbaka till startsidan genom att välja **Start** i navigeringsfönstret.

7. Rulla nedåt tills du ser **delat med mig**.

   ![Startsida](./media/end-user-report-open/power-bi-app.png)

8. Välj den nya försäljnings- och marknadsföringsappen för att öppna den. Beroende på vilka alternativ som angetts av appens *designer*, kommer appen att öppnas sin en instrumentpanel eller en rapport. Den här appen öppnas på en instrumentpanel.  


## <a name="open-a-report-from-a-dashboard"></a>Öppna en rapport från en instrumentpanel
Rapporter kan öppnas från en instrumentpanel. De flesta [paneler](end-user-tiles.md) på instrumentpanelen är *fästa* från rapporter. Om du väljer en panel öppnas rapporten som användes för att skapa panelen. 

1. Välj en panel från en instrumentpanel. I det här exemplet har vi valt kolumndiagramspanelen Totalt antal enheter hittills i år...

    ![instrumentpanel med vald panel](./media/end-user-report-open/power-bi-dashboard.png)

2.  Den associerade rapporten öppnas. Du märker att vi är på sidan kategori hittills i år. Det är den rapportsidan som innehåller kolumndiagrammet som vi valt från instrumentpanelen.

    ![öppen rapport i Läsvyn](./media/end-user-report-open/power-bi-report-tabs.png)

> [!NOTE]
> Inte alla paneler leder till en rapport. Om du väljer en panel som [skapades med Frågor och svar](end-user-q-and-a.md), visas Frågor och svar-skärmen. Om du väljer en panel som [skapades med instrumentpanelens **Lägg till panel**-widget](../service-dashboard-add-widget.md), kan flera saker hända: en video kanske spelas upp, en webbplats öppnas eller annat.  


##  <a name="still-more-ways-to-open-a-report"></a>Ännu fler sätt att öppna en rapport
När du börjar bli mer bekväm med att använda Power BI-tjänsten, kommer du att lista ut vilka arbetsflöden som fungerar bäst för dig. Några andra sätt att komma åt rapporter:
- Från navigeringsfönstret med **Favoriter** och **Senaste**    
- Med [Visa relaterade](end-user-related.md)    
- I ett e-postmeddelande när någon [delar med dig](../service-share-reports.md) eller [ställer in en avisering](end-user-alerts.md)    
- Från ditt [Meddelandecenter](end-user-notification-center.md)    
- Från en arbetsyta
- och mycket mer

## <a name="next-steps"></a>Nästa steg
[Öppna och visa en instrumentpanel](end-user-dashboard-open.md)    
[Rapportfilter](end-user-report-filter.md)

