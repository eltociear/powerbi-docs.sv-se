---
title: 'DAX: Funktionen DIVIDERA jämfört med divisionsoperatorn (/)'
description: Vägledning om när du ska använda funktionen DAX DIVIDERA.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: 91acaa3a2252250e2a10674bae0e9be81f142696
ms.sourcegitcommit: f1f57c5bc6ea3057007ed8636ede50188ed90ce1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74410943"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: Funktionen DIVIDERA jämfört med divisionsoperatorn (/)

När du som datamodellerare skriver ett DAX-uttryck för att dividera en täljare med en nämnare, kan du välja att använda funktionen [DIVIDERA](/dax/divide-function-dax) eller divisionsoperatorn (/).

När du använder funktionen DIVIDERA måste du ange uttryck för täljare och nämnare. Du kan också ange ett värde som representerar ett _alternativt resultat_.

```dax
DIVIDE(<numerator>, <denominator> [,<alternateresult>])
```

Funktionen DIVIDERA har utformats för att automatiskt kunna hantera division med noll. Om ett alternativt resultat inte anges och nämnaren är noll eller TOM, returnerar funktionen TOM. Om ett alternativt resultat har angetts returneras det resultatet i stället för TOM.

Funktionen DIVIDERA är praktisk eftersom uttrycket inte behöver testa värdet för nämnaren först. Funktionen är också bättre optimerad för testning av nämnarvärdet än funktionen [OM](/dax/if-function-dax). Prestandaförbättringen är avsevärd eftersom det är dyrt att kontrollera för division med noll. Att använda DIVIDERA resulterar i ett mer tydligt och elegant uttryck.

## <a name="example"></a>Exempel

Följande måttuttryck skapar en säker division men det innebär att du måste använda fyra DAX-funktioner.

```dax
Profit Margin =
IF(
    OR(
        ISBLANK([Sales]),
        [Sales] == 0
    ),
    BLANK(),
    [Profit] / [Sales]
)
```

Detta måttuttryck uppnår samma resultat, men är mer effektivt och elegant.

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

## <a name="recommendations"></a>Rekommendationer

Vi rekommenderar att du använder funktionen DIVIDERA när nämnaren är ett uttryck som _kan_ returnera noll eller TOM.

Om nämnaren är ett konstant värde rekommenderar vi att du använder divisionsoperatorn. I det här fallet kommer divisionen garanterat att lyckas och ditt uttryck fungerar bättre eftersom det inte behöver genomföra någon onödig testning.

Du bör noga överväga om DIVIDERA-funktionen ska returnera ett alternativt värde. För mått är det vanligtvis bättre att de returnerar TOM. Att returnera TOM är bättre eftersom rapportvisualiseringar, som standard, eliminerar grupperingar när summeringarna är TOM. Det gör att det visuella objektet kan fokusera på grupper där det finns data. Vid behov kan du konfigurera det visuella objektet så att det visar alla grupper (som returnerar värden eller TOM) i filterkontexten genom att aktivera alternativet ”Visa poster utan data”.

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Data Analysis uttryck (DAX)-referens](/dax/)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
