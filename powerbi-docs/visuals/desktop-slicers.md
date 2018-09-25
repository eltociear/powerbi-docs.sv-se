---
title: Använda utsnitt i Power BI Desktop
description: Du kan använda utsnitt i Power BI Desktop för att filtrera, markera och anpassa rapporter
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: 161ea8f20db36c129787e84242ea002980d0f8dd
ms.sourcegitcommit: 70192daf070ede3382ac13f6001e0c8b5fb8d934
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2018
ms.locfileid: "46565876"
---
# <a name="using-slicers-power-bi-desktop"></a>Använda utsnitt i Power BI Desktop

Du kan använda ett **utsnitt** i **Power BI Desktop** för att filtrera resultaten av visualiseringar på rapportsidan. Med utsnitt kan du enkelt ändra de filter som används genom att interagera med själva utsnittet. Du kan också ange alternativ för hur ditt utsnitt visas och hur du interagerar med det. Följande bild visar ett utsnitt med dess *typ* av listruta synlig. 

![Utsnitt i Desktop](./media/desktop-slicers/desktop-slicers_01.png)

Ett utsnitt kan visas från någon av flera olika typer:

* Lista
* Listruta
* Mellan
* Mindre än eller lika med
* Större än eller lika med

Du kan lägga till ett utsnitt i en rapport genom att klicka på visualiseringen **utsnitt** i fönstret **Visualiseringar**.

![Visualiseringstypen Utsnitt](./media/desktop-slicers/desktop-slicers_02.png)

Utsnitt fungerar på liknande sätt i både **Power BI Desktop** och **Power BI-tjänsten**. Information om hur du använder utsnitt finns i artikeln [Utsnitt i Power BI-tjänsten](power-bi-visualization-slicers.md).

## <a name="synchronize-slicers-across-report-pages"></a>Synkronisera utsnitt mellan rapportsidor

I **Power BI Desktop** kan du synkronisera utsnitt över flera rapportsidor. För att synkronisera utsnitt väljer du **synkronisera utsnitt** i rutan **Visa** i menyfliken. När du synkroniserar utsnitt, visas fönstret **Synkronisiera utsnitt** såsom det visas på följande bild.

![Visa fönstret Synkronisera utsnitt](./media/desktop-slicers/desktop-slicers_03.png)

I fönstret **Synkronisera utsnitt** kan du ange hur utsnittet ska synkroniseras mellan rapportsidor. Du kan ange om varje utsnitt ska **tillämpas** på varje enskild rapportsida, och om utsnittet ska vara **synligt** på varje enskild rapportsida.

Du kan till exempel placera ett utsnitt på **sidan 2** i rapporten, enligt följande bild. Sedan kan du välja om det utsnittet bör *gälla* på alla valda sidor, och om det utsnittet ska vara *synligt* på alla valda sidor i rapporten. Du kan använda en valfri kombination av dessa för varje utsnitt. 

![synkronisera utsnitt](./media/desktop-slicers/desktop-slicers_04.png)

Med länken **Lägg till i alla** i fönstret appliceras alla valda utsnitt på alla sidor i rapporten.


Observera att inställningarna som visas i fönstret **Synkronisera utsnitt** endast gäller för det *valda utsnittet*. Du kan använda flera utsnitt på olika sidor och använda fönstret för att definiera hur varje utsnitt tillämpas individuellt på olika sidor i rapporten. 

När valet av utsnitt kan synkroniseras, synkroniseras *inte* andra alternativ, såsom stil, redigera och ta bort. 

## <a name="advanced-options-for-slicers"></a>Avancerade alternativ för utsnitt

Du kan också använda ett **gruppnamn** för en samling utsnitt i avsnittet **Avancerade alternativ** i fönstret **Synkronisera utsnitt** om du vill synkronisera utsnitt i samma grupp mellan sidor. 

![Gruppnamn för utsnitt](./media/desktop-slicers/desktop-slicers_05.png)

Med den här funktionen kan du skapa en anpassad grupp med utsnitt som ska synkroniseras. Ett standardnamn anges, men du kan använda valfritt namn som du föredrar. 

Gruppnamnet ger ytterligare flexibilitet när du arbetar med utsnitt. Du kan skapa separata grupper om du vill synkronisera utsnitt som använder samma fält, eller om du vill placera utsnitt som använder olika fält i samma grupp. 


## <a name="next-steps"></a>Nästa steg

Följande artiklar kan också vara av intresse för dig:

* [Utsnitt i Power BI-tjänsten](power-bi-visualization-slicers.md)
* [Använd numeriska intervallutsnitt i Power BI Desktop](../desktop-slicer-numeric-range.md)
* [Använda ett relativt datumutsnitt och filter i Power BI Desktop](desktop-slicer-filter-date-range.md)

