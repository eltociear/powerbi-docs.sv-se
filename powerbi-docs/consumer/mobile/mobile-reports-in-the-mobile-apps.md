---
title: Utforska rapporter i Power BI-mobilappar
description: Läs mer om att visa och interagera med rapporter i Power BI-mobilappar på din telefon eller surfplatta. Du skapar rapporter i Power BI-tjänsten eller Power BI Desktop och interagerar med dem i mobilapparna.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 08/09/2019
ms.author: mshenhav
ms.openlocfilehash: 166b7d88e6ab55481ec56b0cf4f91628cd141bef
ms.sourcegitcommit: e62889690073626d92cc73ff5ae26c71011e012e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/23/2019
ms.locfileid: "69985734"
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Utforska rapporter i Power BI-mobilappar
Gäller:

| ![iPhone](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Android-telefon](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Android-surfplatta](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Windows 10-enheter](./media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:---: |:---: |:---: |:---: |:---: |
| iPhone-telefoner |iPad-surfplattor |Android-telefoner |Android-surfplattor |Windows 10-enheter |

En Power BI-rapport är en interaktiv vy över dina data med visuella objekt som representerar olika resultat och insikter från dessa data. Att visa rapporter i Power BI-mobilappar är det tredje steget i en trestegsprocess:

1. [Skapa rapporter i Power BI Desktop](../../desktop-report-view.md). Du kan även [optimera en rapport för telefoner](mobile-apps-view-phone-report.md) i Power BI Desktop.
2. Publicera de rapporterna till Power BI-tjänsten [(https://powerbi.com)](https://powerbi.com) eller [Power BI-rapportserver](../../report-server/get-started.md).  
3. Interagera med rapporter i Power BI-mobilapparna.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Öppna en Power BI-rapport i mobilappen
Power BI-rapporter lagras på olika ställen i mobilappen, beroende på var du fick dem från. De kan vara i appar, delade med mig, arbetsytor (inklusive Min arbetsyta) eller på en rapportserver. Du går ibland igenom en relaterad instrumentpanel för att komma till en rapport, och ibland anges de.

I listor och menyer finns en ikon intill ett rapportnamn som visar att objektet är en rapport:

![Rapporter i Min arbetsyta](./media/mobile-reports-in-the-mobile-apps/reports-my-workspace.png)

Det finns två ikoner för rapporter i Power BI-mobilapparna:

* ![Rapportikonen](./media/mobile-reports-in-the-mobile-apps/report-default-icon.png) anger en rapport som kommer att visas i liggande orientering i appen. Den ser ut som på samma sätt som i en webbläsare.

* ![Telefonrapportikon](./media/mobile-reports-in-the-mobile-apps/report-phone-icon.png) anger en rapport som har minst en telefonoptimerad rapportsida som visas i stående orientering.

> [!NOTE]
> Genom att hålla telefonen i liggande orientering får du alltid liggande layout, även om rapportsidan har en telefonlayout.

Om du vill gå till en rapport från en instrumentpanel trycker du på ellipsen (...) i det övre högra hörnet på en panel och sedan på **Öppna rapporten**:
  
  ![Öppna rapporten](./media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Det går inte att öppna alla paneler som rapporter. Paneler som har skapats genom att ställa en fråga i frågor och svar-rutan, öppnar inte rapporter när du klickar på dem.
  
## <a name="interact-with-reports"></a>Interagera med rapporter
När du har öppnat en rapport i appen kan du börja arbeta med den. Det finns många saker du kan göra med rapporten och dess data. I rapportens sidfot finns åtgärder som du kan utföra i rapporten. Genom att trycka och trycka länge på de data som visas i rapporten, kan du också dela upp och blanda datan.

### <a name="using-tap-and-long-tap"></a>Använda tryckning och lång tryckning
En tryckning är detsamma som en musklickning. Om du vill korsmarkera rapporten baserat på en datapunkt trycker du därför på den datapunkten.
När du trycker på ett sektorvärde markeras värdet och resten av rapporten delas upp med det värdet.
När du trycker på en länk, knapp eller ett bokmärke kommer den åtgärd som har definierats av rapportens författare att utföras.

Du märkte förmodligen att en kantlinje visas när du trycker på ett visuellt objekt. I det övre högra hörnet av kantlinjen finns det en ellips (…). Om du trycker på ellipsen visas en meny med åtgärder som du kan utföra på det visuella objektet:

![Visuellt objekt och meny](./media/mobile-reports-in-the-mobile-apps/report-visual-menu.png)

### <a name="tooltip-and-drill-actions"></a>Knappbeskrivning och detaljgranskningsåtgärder

När du trycker länge (trycker och håller ned) på en datapunkt, visas en knappbeskrivning med de värden som datapunkten representerar:

![Knappbeskrivning](./media/mobile-reports-in-the-mobile-apps/report-tooltip.png)

Om rapportens författare har konfigurerat en knappbeskrivning på rapportsidan, ersätts standardbeskrivningen med rapportsidans knappbeskrivning:

![Rapportsidans knappbeskrivning](./media/mobile-reports-in-the-mobile-apps/report-page-tooltip.png)

> [!NOTE]
> Knappbeskrivningar för rapporter stöds för enheter som har minst 640 bildpunkter och ett visningsområde på 320 bildpunkter. Om enheten är mindre visar appen standardknappbeskrivningarna.

Rapportens författare kan definiera hierarkier i data och relationer mellan rapportsidor. Med hierarkier kan du öka detaljnivån, minska detaljnivån och visa detaljerad information från ett visuellt objekt och ett värde. När du trycker länge på ett värde visas utöver knappbeskrivningen de relevanta alternativen för detaljnivån i sidfoten:

![Detaljnivååtgärder](./media/mobile-reports-in-the-mobile-apps/report-drill-actions.png)


När du trycker på en viss del av ett visuellt objekt och sedan trycker för att visa *detaljerad information*, växlar Power BI till en annan sida i rapporten som filtreras till det värde som du tryckt på. Rapportens författare kan definiera ett eller flera alternativ för visning av detaljerad information som växlar till olika sidor. I dessa fall kan du välja vilket alternativ som du vill visa detaljerad information för. Bakåtknappen tar dig tillbaka till föregående sida.


Läs mer om hur du [lägger till visning av detaljerad information i Power BI Desktop](../../desktop-drillthrough.md).
   
   > [!IMPORTANT]
   > I Power BI-mobilapparna är detaljgranskningsåtgärder i matriser och visuella tabellobjekt enbart möjliga via cellvärden, inte i kolumn- eller radrubriker.
   
   
   
### <a name="using-the-actions-in-the-report-footer"></a>Använda åtgärderna i rapportsidfoten
Från rapportens sidfot kan du utföra flera åtgärder på den aktuella rapportsidan eller i hela rapporten. Sidfoten ger snabb åtkomst till de vanligaste åtgärderna. Du kan komma åt andra åtgärder genom att trycka på ellipsen (...):

![Rapportens sidfot](./media/mobile-reports-in-the-mobile-apps/report-footer.png)

De åtgärder som du kan utföra från sidfoten är:
- Återställa rapportfiltret och korsmarkera urvalet tillbaka till ursprungligt läge.
- Öppna konversationsfönstret för att se eller lägga till kommentarer om rapporten.
- Öppna filterfönstret för att se eller ändra det filter som för närvarande tillämpas på rapporten.
- Skapa en lista med alla sidor i rapporten. När du trycker på sidnamnet läses den sidan in och visas.
Du kan flytta mellan rapportsidor genom att svepa från kanten av skärmen till mitten.
- Visa alla rapportåtgärder.

#### <a name="all-report-actions"></a>Alla rapportåtgärder
När du trycker på ellipsen (...) i rapportens sidfot, ser du alla åtgärder som du kan utföra i en rapport:


![Alla rapportåtgärder](./media/mobile-reports-in-the-mobile-apps/report-all-actions.png)

Vissa av åtgärderna kan vara inaktiverade eftersom de är beroende av de specifika rapportfunktionerna.
Till exempel:

**Filtrera efter aktuell plats** är aktiverat om rapportens författare har kategoriserat rapporten med geografiska data. Mer information finns i avsnittet om att [identifiera geografiska data i en rapport](https://docs.microsoft.com/power-bi/desktop-mobile-geofiltering).

**Genomsök för att filtrera rapporten efter streckkod** är endast aktiverat om datamängden i rapporten har taggats som **Streckkod**. Mer information finns i artikeln om att [tagga streckkoder i Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-mobile-barcodes).

**Bjud in** är endast aktiverat om du har behörighet att dela rapporten med andra. Du får bara behörighet om du är ägare till rapporten eller om du har fått behörighet att dela vidare av ägaren.

**Anteckna och dela** kan vara inaktiverat om det finns en [Intune-skyddsprincip](https://docs.microsoft.com/intune/app-protection-policies) i din organisation som förbjuder delning från Power BI-mobilappen.

## <a name="next-steps"></a>Nästa steg
* [Visa och interagera med Power BI-rapporter som är optimerade för din telefon](mobile-apps-view-phone-report.md)
* [Skapa en version av en rapport som är optimerad för telefoner](../../desktop-create-phone-report.md)
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)

