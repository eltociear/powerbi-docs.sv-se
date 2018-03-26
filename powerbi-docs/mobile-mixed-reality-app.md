---
title: Appen Power BI för Mixed Reality (förhandsversion)
description: Visa dina instrumentpaneler och rapporter i appen Power BI for Mixed Reality, antingen i en virtuell värld eller i din miljö.
services: powerbi
documentationcenter: ''
author: maggiesMSFT
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: ''
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: ''
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/13/2018
ms.author: maggies
ms.openlocfilehash: 4226973fa48470faf46db68509b05eb02d88c113
ms.sourcegitcommit: 00b4911ab5fbf4c2d5ffc000a3d95b3149909c28
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="power-bi-for-mixed-reality-app-preview"></a>Appen Power BI för Mixed Reality (förhandsversion)
Visa dina instrumentpaneler och rapporter i appen Power BI for Mixed Reality i en virtuell värld, eller placera dem på specifika platser i din miljö. 

Hämta förhandsversionen av appen Power BI for Mixed Reality från Windows Store och visa dina instrumentpaneler och rapporter. Interagera med dem i den virtuella världen, och välj sedan de som du vill placera ut. 

## <a name="two-views-windows-classic-and-holographic"></a>Två vyer: den klassiska Windows-vyn och den holografiska vyn

Power BI for Mixed Reality är baserad på Windows-mobilappen för Power BI och har ytterligare funktioner som är unika för mixad verklighet. När du startar Power BI for Mixed Reality är du i den klassiska Windows-vyn för Power BI. I den här vyn kan du navigera mellan de instrumentpaneler och rapporter som du har åtkomst till. När du hittar någon du vill ha kan du växla från den klassiska Windows-vyn till den holografiska vyn. 


## <a name="windows-classic-view-basics"></a>Grunder i den klassiska Windows-vyn

Det här avsnittet är till för dig som inte har använt mixad verklighet tidigare. Att interagera med en app med mixad verklighet skiljer sig från att interagera med en dator eller en surfplatta eller telefon. I den klassiska Windows-vyn svarar appar för mixad verklighet på en uppsättning gester och röstkommandon som ersätter musen och tangentbordet, eller telefontryckningar. 

**Trycka i luften**

Att trycka i luften är den mest grundläggande gesten som du behöver kunna för att interagera med nästan alla appar för mixad verklighet. Du trycker ihop tummen och pekfingret med handen riktad uppåt, ungefär som när du klickar med musen eller trycker på telefonen.  

![Trycka i luften, gest för mixad verklighet](media/mobile-mixed-reality-app/power-bi-hololens-airtap.png)

I Power BI trycker du i luften i den klassiska Windows-vyn på de ställen där du annars hade klickat med musen. Du kan till exempel trycka i luften för att öppna en instrumentpanel eller rapport i din arbetsyta, eller trycka i luften på en del av ett visuellt objekt för att filtrera eller korsmarkera andra visuella objekt.

![Trycka i luften i Power BI](media/mobile-mixed-reality-app/power-bi-hololens-airtap-hand.png) 

Läs mer om [Microsofts handgester i mixad verklighet](https://developer.microsoft.com/windows/mixed-reality/gestures).

**Fästa ett objekt** 

Tryck i luften på ikonen **Fästa** ![ikonen Fästa](media/mobile-mixed-reality-app/power-bi-hololens-pin.png) om du vill fästa en instrumentpanel eller rapport från den klassiska Windows-vyn till den holografiska vyn. Du kan fästa ett antal objekt på den holografiska vyn. 

**Växla till den holografiska vyn**

När du har fäst objekt i den klassiska Windows-vyn trycker du i luften på ikonen för **Helskärm** ![ikonen för Helskärm](media/mobile-mixed-reality-app/power-bi-hololens-fullscreen.png) för att växla till den holografiska vyn. 


## <a name="holographic-view-basics"></a>Grunder i den holografiska vyn

Nu när du är i den holografiska vyn finns alla artefakter som du har fäst i dockningsbältet. Du kan placera de fästa objekten på specifika platser i den fysiska rymden, till exempel bredvid den utrustning som objektet beskriver. I den holografiska vyn fungerar röstkommandon som ett komplement till handgester. Här följer några vanliga röstkommandon.

**"Följ mig"** 

Hämta en Power BI-artefakt så att den finns kvar i huvudsynfältet och följer din blick tills du placerar den någonstans.

**”Dock”** (Docka) 

Med kommandot ”dock” kan du placera en artefakt i dockningsbältet i Power BI så att du enkelt kommer åt den när du lämnar huvudsynfältet.

**”Place here”** (Placera här)

Med det här kommandot placerar du en instrumentpanel eller rapport på en vägg eller på ett föremål eller svävande i luften.

![Placera en instrumentpanel i rymden](media/mobile-mixed-reality-app/power-bi-hololens-place-visuals.png)

**”Go home”** (Gå hem)

Säg ”go home” för att återgå till den klassiska Windows-vyn för Power BI. 

**”Remove”** (Ta bort)

Använd det här kommandot när du vill ta bort en artefakt från den holografiska vyn.

**”Remove all”** (Ta bort alla) 

Använd det här kommandot när du vill ta bort alla artefakter från den holografiska vyn.


## <a name="scan-a-report-qr-code-in-holographic-view"></a>Skanna en QR-kod för en rapport i den holografiska vyn

Du kan skanna en QR-kod för en rapport i den holografiska vyn, precis som du kan [skanna QR-koder med Power BI-mobilappar](mobile-apps-qr-code.md) för iPhone och Android.

- Titta på en QR-kod i den holografiska vyn. Power BI öppnar rapporten som är associerad med den QR-koden.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

Det finns några begränsningar och överväganden för den holografiska vyn.

- Eventuella korsfiltreringar eller markeringar som du har angett i den klassiska Windows-vyn visas inte.
- Visningen av fästa instrumentpaneler och rapporter är privat. Vi stöder för närvarande inte delade upplevelser.
- Instrumentpaneler och rapporter uppdateras var 45:e sekund när data ändras.


## <a name="next-steps"></a>Nästa steg

- [Hämta data från den verkliga världen med Power BI-mobilappar](mobile-apps-data-in-real-world-context.md)

 



