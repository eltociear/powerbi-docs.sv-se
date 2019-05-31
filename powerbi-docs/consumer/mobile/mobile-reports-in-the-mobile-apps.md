---
title: Utforska rapporter i Power BI-mobilappar
description: Läs mer om att visa och interagera med rapporter i Power BI-mobilappar på din telefon eller surfplatta. Du skapar rapporter i Power BI-tjänsten eller Power BI Desktop och interagerar med dem i de mobila apparna.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/21/2019
ms.author: mshenhav
ms.openlocfilehash: bee60dd6f3254b049f2445e6e985c625933caf5b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565457"
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Utforska rapporter i Power BI-mobilappar
Gäller:

| ![iPhone](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Android-telefon](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Android-surfplatta](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Windows 10-enheter](./media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone-telefoner |iPad-surfplattor |Android-telefoner |Android-surfplattor |Windows 10-enheter |

En Power BI-rapport är en interaktiv vy över dina data med visuell information som representerar olika resultat och insikter från dessa data. Att visa rapporter i Power BI-mobilappar är det tredje steget i en trestegsprocess.

1. [Skapa rapporter i Power BI Desktop](../../desktop-report-view.md). Du kan även [optimera en rapport för telefoner](mobile-apps-view-phone-report.md) i Power BI Desktop. 
2. Publicera de rapporterna till Power BI-tjänsten [(https://powerbi.com)](https://powerbi.com) eller [Power BI-rapportserver](../../report-server/get-started.md).  
3. Interagera sedan med dessa rapporter i Power BI-mobilappar.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Öppna en Power BI-rapport i mobilappen
Power BI-rapporter lagras på olika ställen i mobilappen, beroende på var du fick dem från. De kan vara i appar, delade med mig, arbetsytor (inklusive Min arbetsyta) eller på en rapportserver. Du går ibland igenom en relaterad instrumentpanel för att komma till en rapport och ibland listas de.

Listor och menyer innehåller en ikon bredvid ett rapportnamn, vilket hjälper dig att förstå att det här objektet är en rapport. 

![rapporter i Min arbetsyta](./media/mobile-reports-in-the-mobile-apps/reports-my-workspace.png) 

Det finns två ikoner för rapporter i Power BI Mobile-appar:

* ![rapportikon](./media/mobile-reports-in-the-mobile-apps/report-default-icon.png) Anger en rapport som visas i liggande orientering i appen och ser likadana ut i webbläsaren.

* ![Telefonrapportikon](./media/mobile-reports-in-the-mobile-apps/report-phone-icon.png) Anger en rapport som har minst en optimerad rapport på sidan telefonnummer, som visas i stående. 

OBS! Hålla telefonen i liggande vy får du alltid den liggande layouten, även om rapportsidan har telefonens layout. 

Om du vill ha i en rapport från en instrumentpanel, trycker du på ellipsen (...) i det övre högra hörnet av en panel > **Öppna rapport**.
  
  ![Öppna rapporten](./media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Alla paneler går inte att öppna i en rapport. Paneler som skapats genom att ställa en fråga i frågor och svar-rutan, öppnar inte rapporter när du klickar på dem. 
  
## <a name="interacting-with-reports"></a>Interagera med rapporter
När du har en rapport som öppnas i appen kan börja du arbeta med den. Det finns många saker du kan göra med rapporten och dess data. Du hittar åtgärder du kan utföra i rapporten och genom att trycka på och lång tid att trycka på de data som visas i rapporten du kan också statistikforskning data i rapportsidfoten.

### <a name="using-tap-and-long-tap"></a>Med hjälp av trycker och på länge
Tryck på lika med musen klickar du på. Så om du vill korsmarkera rapport som baseras på en datapunkt, tryck på den datapunkten.
Trycka på ett utsnittsvärde, gör det värdet som valts och uppdelning resten av rapporten genom att detta värde. Trycka på en aktiveras knapp eller bokmärke baserat på den åtgärd som definierats av författaren.

Du antagligen lagt märke till att en kantlinje ska visas när du trycker på ett visuellt objekt. Det finns ellipsen (...) i det övre högra hörnet på kantlinjen. Att trycka på den kommer att få en meny med åtgärder som du kan göra på det visuella objektet.

![visuellt rapportobjekt och menyn](./media/mobile-reports-in-the-mobile-apps/report-visual-menu.png)

### <a name="tooltip-and-drill-actions"></a>Knappbeskrivning och test-åtgärder

När du länge trycker på (tryck och håll ned) en datapunkt en knappbeskrivning visas presenterar de värden som representerar den här datapunkten. 

![rapportknappbeskrivningen](./media/mobile-reports-in-the-mobile-apps/report-tooltip.png)

Rapportförfattarna kan definiera hierarkier i data och relationer mellan rapportsidor. Hierarkin kan detaljnivå, gå in och Sök i en annan rapportsida från ett visuellt objekt och ett värde. När du tryck länge på ett värde, förutom knappbeskrivning, så visas de relevanta test alternativen i sidfoten. 

![ökad detaljnivå rapportåtgärder](./media/mobile-reports-in-the-mobile-apps/report-drill-actions.png)

Med *visning av detaljerad information*, när du trycker på en viss del av en visualisering, växlar Power BI till en annan sida i rapporten som filtreras till det värde som du tryckt på.  Rapportförfattare kan definiera ett eller flera alternativ för visning av detaljerad information som växlar till olika sidor. I så fall kan du välja vilken som du vill visa detaljerad information för. Bakåt-knappen tar dig till föregående rapportsida.

Läs mer om hur du [lägger till visning av detaljerad information i Power BI Desktop](../../desktop-drillthrough.md).
   
   > [!IMPORTANT]
   > I Power BI-appen aktiverat ökad detaljnivå i matriser och tabeller genom ett cellvärde, inte av kolumn- och rubriker.
   
   
   
### <a name="using-the-actions-in-the-report-footer"></a>Med åtgärderna som i rapporten sidfot
Sidfoten i rapporten har åtgärder som du kan göra på den aktuella rapportsidan eller hela rapporten. Sidfoten har snabb åtkomst till de mest användbara åtgärderna och alla åtgärder som kan vara åtkomst från ellipsen (...).

![rapporten sidfot](./media/mobile-reports-in-the-mobile-apps/report-footer.png)

Åtgärder som du kan utföra från sidfoten är:
1) Återställ rapportfilter och mellan Markera val tillbaka till det ursprungliga tillståndet.
2) Öppna konversationsfönstret om du vill visa eller lägga till kommentarer i den här rapporten.
3) Öppna filterfönstret om du vill visa och ändra filtret för närvarande används i rapporten.
4) Lista över alla sidor i den här rapporten. Att trycka på sidnamn automatiskt läsa in och sidan.
Flytta mellan rapportsidor kan göras genom att svepa från gränsen på skärmen till center.
5) Visa alla rapportåtgärder.

#### <a name="all-report-actions"></a>Alla rapportåtgärder
Trycka på den... i sidfoten i rapporten, kommer alla åtgärder som du kan utföra på en rapport. 

![Rapportera alla åtgärder](./media/mobile-reports-in-the-mobile-apps/report-all-actions.png)

Några av åtgärderna som kan vara inaktiverade, eftersom de är beroende av den specifika rapporten-funktioner.
Till exempel:
1) **Filtrera efter aktuella plats** är aktiverad om data i rapporten har kategoriserats av författaren med geografiska data. [Lär dig att identifiera geografiska data i rapporten](https://docs.microsoft.com/power-bi/desktop-mobile-geofiltering).
2) **Genomsökning för att filtrera rapporten efter streckkod** är bara aktiverad om datauppsättningen i rapporten har taggats som streckkoden. [Hur du tagga streckkoder i Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-mobile-barcodes). 
3) **Bjud in** är bara aktiverad om du har behörighet att dela rapporten med andra. Du får behörighet endast om du är ägaren av rapporten eller om du har gett dela behörighet av ägaren.
4) **Kommentera och dela** kanske inaktivera om det finns en [Intune-skyddsprincip](https://docs.microsoft.com/intune/app-protection-policies) i organisationen som inte rätt att dela Power BI-appen. 

## <a name="next-steps"></a>Nästa steg
* [Visa och interagera med Power BI-rapporter som är optimerade för din telefon](mobile-apps-view-phone-report.md)
* [Skapa en version av en rapport som är optimerad för telefoner](../../desktop-create-phone-report.md)
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)

