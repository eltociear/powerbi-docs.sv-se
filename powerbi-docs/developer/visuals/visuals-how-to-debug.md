---
title: Felsöka visuella Power BI-objekt
description: I den här artikeln beskrivs hur du felsöker visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: 4ce61fcd4f322abc0362956453d76ced9b78d887
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78264253"
---
# <a name="how-to-debug-power-bi-visuals"></a>Felsöka visuella Power BI-objekt

På den här sidan visas några tips för felsökning när du skapar ditt visuella objekt. Den innehåller grundläggande steg och visar skillnaderna mellan standard-frontend-program och felsökning av visuella Power BI-objekt.
När du har läst artikeln kan du felsöka anpassade visuella objekt med hjälp av brytpunkter, loggundantag och catch-undantag i Chrome och Edge.

## <a name="using-breakpoints"></a>Använda brytpunkter

När det visuella objektets Java Script läses in varje gång det visuella objektet uppdateras, försvinner eventuella brytpunkter som du lägger till när det felsökta visuella objektet uppdateras. Som en lösning använder du `debugger`-instruktioner i koden. Vi rekommenderar att du inaktiverar automatisk inläsning när du använder `debugger` i koden.

```typescript
public update(options: VisualUpdateOptions) {
    console.log('Visual update', options);
    debugger;
    this.target.innerHTML = `<p>Update count: <em>${(this.updateCount</em></p>`;
}
```


## <a name="showing-exceptions"></a>Visar undantag

När du arbetar med ditt visuella objekt ser du att alla fel är ”förbrukade” av Power BI-tjänsten. Det här är en avsiktlig funktion i Power BI för att förhindra felfungerande andra visuella objekt som gör att hela appen blir instabil.

Som en lösning kan du lägga till kod för att fånga upp och logga dina undantag eller ställa in felsökningsprogrammet så att det bryter vid insamlade undantag.


## <a name="log-exceptions"></a>Logga undantag

Om du vill logga undantag i Power BI visuella objekt lägger du till följande kod i ditt visuella objekt för att definiera en decorator för undantagsloggning.

```typescript
export function logExceptions(): MethodDecorator {
     return function (target: Object, propertyKey: string, descriptor: TypedPropertyDescriptor<Function>)
    : TypedPropertyDescriptor<Function> {
            
        return {
            value: function () {
                try {
                    return descriptor.value.apply(this, arguments);
                } catch (e) {
                    console.error(e);
                    throw e;
                }
            }
        }
    }
}
```
Sedan kan du använda denna decorator på alla funktioner för att se felloggningen.

```typescript
@logExceptions()
public update(options: VisualUpdateOptions) {
```

## <a name="break-on-exceptions"></a>Bryt vid undantag

Du kan också ange att webbläsaren ska bryta vid insamlade undantag. Detta stoppar kodkörningen där ett fel inträffar och gör det möjligt att felsöka därifrån.

### <a name="edge"></a>Microsoft Edge

1. Öppna utvecklarverktyg (F12).
2. Gå till fliken **felsökningsprogram**.
3. Klicka på ikonen **Bryt vid undantag** (sexhörning med en paussymbol).
4. Välj **Bryt vid alla undantag**.

![Fält för dataroller](./media/how-to-debug-edge.png)

## <a name="chrome"></a>Chrome

1. Öppna utvecklarverktyg (F12).
2. Gå till fliken **Källor**.
3. Klicka på ikonen **Bryt vid undantag** (stopptecken med en paussymbol).
4. Markera kryssrutan **pausa vid fångade undantag**.

![Fält för dataroller](./media/how-to-debug-chrome.png)

## <a name="next-steps"></a>Nästa steg
* [Felsöka anpassade visuella Power BI-objekt](../power-bi-custom-visuals-troubleshoot.md)
* Mer information och svar på frågor finns i [Vanliga frågor och svar om visuella Power BI-objekt](../power-bi-custom-visuals-faq.md#organizational-power-bi-visuals)
