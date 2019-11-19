---
title: API:et för lokal lagring i visuella Power BI-objekt
description: I den här artikeln beskrivs hur du använder visuella objekt i Power BI för åtkomst till webbläsarens lokala lagring
author: uve
ms.author: v-grniki
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/31/2019
ms.openlocfilehash: f69a3c8928b8079f79b8a6dd5f5b132235a7089c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879893"
---
# <a name="local-storage-api"></a>API för lokal lagring

API:et för lokal lagring är ett API som anpassade visuella objekt kan använda till att begära att värden sparar eller läser in data från enhetens lagringsutrymme. Det är isolerat så till vida att lagringsåtkomsten är separerad mellan olika visuella typer.

## <a name="sample"></a>Exempel

Om det anpassade visuella objektet ska öka någon räknare varje gång uppdateringsmetoden anropas, men räknarvärdet också ska bevaras och inte återställas vid varje start av visualiseringen:

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>Kända begränsningar och problem

API:et för lokal lagring är inte aktiverat för anpassade visuella objekt som standard. Om du vill aktivera det för ditt anpassade visuella objekt skickar du begäran till supporten för Power BI Custom Visuals `pbicvsupport@microsoft.com`
