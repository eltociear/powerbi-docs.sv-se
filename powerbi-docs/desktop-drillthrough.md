---
title: Använd drillthrough i Power BI Desktop
description: Lär dig att öka detaljnivån för data på en ny rapportsida i Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 4/10/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 7be260a5989ffb6a9dc1b72dad90d227e0b6295b
ms.sourcegitcommit: bdb1fee3612bcc66153dcad8c4db2e99fb041014
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2018
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Använd drillthrough i Power BI Desktop
Med **drillthrough** i **Power BI Desktop** kan du skapa en sida i rapporten som fokuserar på en specifik enhet – till exempel en leverantör, kund eller tillverkare. Med den fokuserade rapportsidan kan användare högerklicka på en datapunkt i andra rapportsidor och använda drillthrough till sidan i fokus för att hämta information som har filtrerats för det sammanhanget.

![](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Använda drillthrough
1. För att använda **drillthrough** skapar du en rapportsida med visuella objekt som du vill se för typen av enhet på vilken du ökar detaljnivån. 

    Om du vill använda drillthrough för en tillverkare kan du skapa en drillthrough-sida med visuella objekt som visar totalförsäljning, totalt antal levererade enheter, försäljning enligt kategori, försäljning enligt region och så vidare. Därmed är visualiseringen alltid specifik för tillverkaren du valde.

2. Sedan, på drillthrough-sidan i avsnittet **Fält** i rutan **Visuella objekt** kan du dra fältet som du vill använda drillthrough på i brunnen för **Drillthrough-filter**.

    ![](media/desktop-drillthrough/drillthrough_02.png)

    När du lägger till ett fält i brunnen **Drillthrough-filter** skapar **Power BI Desktop** automatiskt en *bakåtknapp*. Knappen visas i publicerade rapporter och låter användare av rapporten **Power BI-tjänsten** enkelt komma tillbaka till sidan som de kommer ifrån (sidan där de har valt drillthrough).

    ![](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>Använda en egen bild för en bakåtknapp    
 Eftersom bakåtknappen är en bild kan du ersätta den med vilken bild du vill och den kommer fortfarande att fungera som en bakåtknapp för att låta användaren gå tillbaka till ursprungssidan.

1. På fliken **Hem** klickar du på **Bild**, letar upp bilden och placerar den på drillthrough-sidan.
2. Markera den nya bilden på drillthrough-sidan och under avsnittet Formatera bild genom att ange slutreglaget **Länk** till på och ange den **typen** som **Bakåt**. Bilden fungerar nu som en bakåtknapp.

    ![](media/desktop-drillthrough/drillthrough_05.png)

    När din **drillthrough**-sida är klar och användare högerklickar på en datapunkt i rapporten som använder fältet du la till i **drillthrough-filtret**, visas en snabbmeny som stöder drillthrough för sidan.

    ![](media/desktop-drillthrough/drillthrough_04.png)

    När rapportkonsumenterna valde drillthrough filtrerades sidan för att visa information om datapunkten som de högerklickade på. Om de högerklickade på en datapunkt om Contoso (en tillverkare) och har valt drillthough filtreras drillthrough-sidan till Contoso.

    > [!NOTE]
    > Endast fältet som finns i brunnen **drillthroug-filter** skickas vidare till rapportsidan för detaljerad information. Ingen övrig kontextinformation skickas.
    > 
    > 

Svårare än så är det inte att använda **drillthrough** i dina rapporter. Det är ett bra sätt att få en utökad vy över den enhetsinformation som du har valt för ditt drillthrough-filter.

