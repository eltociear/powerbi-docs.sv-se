---
title: "Använd drillthrough i Power BI Desktop"
description: "Lär dig att öka detaljnivån för data på en ny rapportsida i Power BI Desktop"
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: c4482b8a8b7510b54b317ef9731057a52501d47c
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Använd drillthrough i Power BI Desktop
Med **drillthrough** i **Power BI Desktop** kan du skapa en sida i rapporten som fokuserar på en specifik enhet – till exempel en leverantör, kund eller tillverkare. Med den fokuserade rapportsidan kan användare högerklicka på en datapunkt i andra rapportsidor och använda drillthrough till sidan i fokus för att hämta information som har filtrerats för det sammanhanget.

![](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Använda drillthrough
För att använda **drillthrough**skapar du en rapportsida med visuella objekt som du vill se om typen av enhet för vilken du ökar detaljnivån. Om du vill använda drillthrough för en tillverkare kan du skapa en drillthrough-sida med visuella objekt som visar totalförsäljning, totalt antal levererade enheter, försäljning enligt kategori, försäljning enligt region och så vidare. Därmed är visualiseringen alltid specifik för tillverkaren du klickade på och valde drillthrough för.

Sedan, på drillthrough-sidan i avsnittet **fält** i rutan **Visuella objekt** kan du dra fältet som du vill använda drillthrough på i brunnen **Drillthrough-filter**.

![](media/desktop-drillthrough/drillthrough_02.png)

När du lägger till ett fält i brunnen **Drillthrough-filter** skapar **Power BI Desktop** automatiskt en *bakåtknapp*. Knappen visas i publicerade rapporter och låter användare av rapporten **Power BI-tjänsten** enkelt komma tillbaka till sidan som de kommer ifrån (sidan där de har valt drillthrough).

![](media/desktop-drillthrough/drillthrough_03.png)

Eftersom den *tillbaka*-knappen är en bild kan du ersätta den med vilken bild du vill och den kommer fortfarande att fungera korrekt som knapp för att låta användaren återvända till ursprungssidan. Om du vill använda din egen bild för en bakåt-knapp är det bara att placera en bild på drillthrough-sidan, välja bilden och aktivera skjutreglaget för *bakåt*. Nu fungerar din bild som *tillbaka*-knapp.

![](media/desktop-drillthrough/drillthrough_05.png)

När din **drillthrough**-sida är klar öppnas en snabbmenyn som låter användarna gå till drillthrough-sidan när de högerklickar på en datapunkt i din rapport som använder fältet som du angav i **Drillthrough-filtret**.

![](media/desktop-drillthrough/drillthrough_04.png)

När de valde drillthrough filtrerades sidan för att visa information om datapunkten som de högerklickade på. Om de högerklickade på en datapunkt om Contoso (en tillverkare) och har valt drillthough filtreras drillthrough-sidan till Contoso.

> [!NOTE]
> Det är endast fält som finns i **Drillthrough-filterbrunnen** som skickas vidare till drillthrough-rapportsidan. Ingen övrig kontextinformation skickas.
> 
> 

Svårare än så är det inte att använda **drillthrough** i dina rapporter. Det är ett bra sätt att få en utökad vy över den enhetsinformation som du har valt för ditt drillthrough-filter.

