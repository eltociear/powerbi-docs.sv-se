---
title: Mobil utveckling
description: Så här skapar du mobilanpassade visuella Power BI-objekt
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: 38e6ac3be143381304f1fdfc8e1427b91f398a9a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196639"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>Så här skapar du mobilanpassade visuella Power BI-objekt
Mobilanvändningen har en viktig roll för Power BI. En av dess styrkor är att du alltid är ansluten till dina data, var som helst.

En utvecklare av visuella Power BI-objekt måste beakta de unika begränsningar som gäller för varje mobil enhet för att nå så många användare som möjligt, och ge bästa möjliga mobilupplevelse.

Använd [Power BI-appen för Windows, iOS och Android](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices) för att ge dina företagsanvändare en omfattande vy över alla data, som alltid är tillgänglig, var som helst.

## <a name="requirements"></a>Krav

Följande krav är viktiga för mobilvänlig visuell utveckling:

- Rendering

  Dina visuella Power BI-objekt måste kunna återges på alla mobila enheter som stöds, inklusive webbläsare och program som stöds, utan fel i rapporter, instrumentpaneler eller när de körs i **fokusläge**. 

- Interaktiv

  Interaktiva funktioner måste tillhandahållas på samma sätt som på skrivbordsenheter. Det måste finnas stöd för alla händelser som hanteras i skrivbordswebbläsare, eller så ska jämförbara händelsehanterare för mobila enheter finnas.
  
  Grundläggande navigering och val av datapunkter ska till exempel ha samma funktioner som i webbläsare för datorer. Om ett visuellt objekt har stöd för multival med **Ctrl** måste utvecklaren överväga att lägga till en liknande händelsehanterare för mobila enheter.

  Följande tabell innehåller en lista över motsvarande händelser på mobila enheter.

  | Namn på mushändelse | Namn på touchhändelse |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | använd externt bibliotek |
  | `contextmenu` | använd externt bibliotek |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove` (eller externt bibliotek) |
  | `wheel` | `NaN` |

  > [!NOTE]
  > Alla mobila enheter och pekskärmsenheter har inte stöd för mushändelser (eller som föregås av *mus*). I sådana fall kan du hantera både *mus*- och *tryck*händelser samtidigt.

## <a name="optional"></a>Valfri
Följande betraktas som valfritt och används för att skapa en bättre slutanvändarupplevelse.

- Rendering

  Om du vill ha stöd för mindre storlekar på visuella objekt kan du prova med att lägga till formatalternativ som användaren kan ändra för att justera storleken på varje element. Du kan till exempel lägga till formatalternativ för etiketter, för användning i rapporter och på instrumentpaneler. Detta gör det möjligt för användare att anpassa ett visuellt objekt för sin mobila enhet.
  
  Samma inställningar kan också tillämpas på visuella objekt i skrivbordswebbläsare, och om det behövs åsidosätts de för att anpassa det visuella objektet till mindre skärmar.

  > [!NOTE]
  > För att optimera ett visuellt objekt i **fokusläge** måste skärmstorlekar för både stående och liggande orientering beaktas. Se [Visa innehåll i fokusläge](/power-bi/consumer/end-user-focus).

- Interaktiv

  Överväg att lägga till mobilspecifika händelsehanterare, till exempel för dra och rulla.

- Redundans

  Ett visuellt objekt bör visa ett beskrivande fel om det inte kan återges på den mobila enheten.

## <a name="supported-browsers-and-devices"></a>Webbläsare och enheter som stöds
Det visuella Power BI-objektet måste kunna återges på alla enheter som har stöd för Power BI-appar. Mer information finns i [Webbläsare som stöds för Power BI](/power-bi/power-bi-browsers) och [Power BI-mobilappar](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices).

Vid testning mot de senaste modellerna av Windows-, iOS- och Android-enheter måste utvecklaren överväga de flesta av dessa kvalitetsaspekter.

## <a name="next-steps"></a>Nästa steg
Kom igång genom att gå till [Självstudiekurs: Utveckla ett visuellt Power BI-objekt](/power-bi/developer/visuals/custom-visual-develop-tutorial).
