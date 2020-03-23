---
title: API:et för lokal lagring i visuella Power BI-objekt
description: I den här artikeln beskrivs hur du använder visuella objekt i Power BI för åtkomst till webbläsarens lokala lagring
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 01/21/2019
ms.openlocfilehash: e2cb11ea9be85916e6b5557e7933f6a6b5a7159a
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380604"
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

API:et för lokal lagring är inte aktiverat för visuella Power BI-objekt som standard. Om du vill aktivera det för ditt visuella Power BI-objekt skickar du begäran till supporten för visuella Power BI-objekt `pbicvsupport@microsoft.com`.  
**Observera att det visuella objektet ska vara tillgängligt i [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) och vara [certifierat](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/).**
