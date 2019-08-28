---
title: 'DAX: Funktionen DIVIDERA jämfört med divisionsoperatorn (/)'
description: Vägledning om när du ska använda funktionen DAX DIVIDERA.
author: guyinacube
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/05/2019
ms.author: v-pemyer
ms.openlocfilehash: d22491ee314ebcebd4479c4e57dbfdf7a6a1ffdb
ms.sourcegitcommit: c2197c3ad1d747b4ad490ab75771a0d32d0ae208
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/23/2019
ms.locfileid: "70010447"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: Funktionen DIVIDERA jämfört med divisionsoperatorn (/)

Den här artikeln vänder sig till datamodellerare som definierar DAX-uttryck.

## <a name="background"></a>Bakgrund

När du skriver ett DAX-uttryck för att dividera en täljare med en nämnare, kan du välja att använda funktionen [DIVIDERA](/dax/divide-function-dax)eller divisionsoperatorn (/).

När du använder funktionen DIVIDERA måste du ange uttryck för täljare och nämnare. Du kan också ange ett värde som representerar ett alternativt resultat.

```dax

DIVIDE(<numerator>, <denominator> [,<alternateresult>])

```

Funktionen DIVIDERA har utformats för att automatiskt kunna hantera division med noll. Om ett alternativt resultat inte anges och nämnaren är noll eller TOM, returnerar funktionen TOM. Om ett alternativt resultat har angetts returneras det resultatet i stället för TOM.

Funktionen DIVIDERA är praktisk eftersom uttrycket inte behöver testa värdet för nämnaren först. Funktionen är också bättre optimerad för testning av nämnarvärdet än funktionen [OM](/dax/if-function-dax). Att använda DIVIDERA resulterar också i ett mer tydligt och elegant uttryck.

## <a name="example"></a>Exempel

Följande måttuttryck skapar en säker division, men det innebär att du måste använda tre DAX-funktioner.

```dax

=IF(ISBLANK([Sales]) || [Sales] = 0, BLANK(), [Profit] / [Sales])

```

Detta måttuttryck uppnår samma resultat, men är mer effektivt och elegant.

```dax

=DIVIDE([Profit], [Sales])

```

## <a name="recommendations"></a>Rekommendationer

Vi rekommenderar att du använder funktionen DIVIDERA när nämnaren är ett uttryck som _kan_ returnera noll eller TOM.

Om nämnaren är ett konstant värde rekommenderar vi att du använder divisionsoperatorn. I det här fallet kommer divisionen garanterat att lyckas och ditt uttryck fungerar bättre eftersom det inte behöver genomföra någon onödig testning.

Du bör noga överväga om DIVIDERA-funktionen ska returnera ett alternativt värde. Vid mått är det vanligtvis bättre än att de returnerar TOM. Det beror på att visuella rapportobjekt som standard eliminerar grupperingar när summeringar är tomma. Detta innebär att det visuella objektet kan fokusera på grupper där det finns data. Vid behov kan du konfigurera det visuella objektet så att det visar alla grupper (som returnerar värden eller TOM) i filterkontexten genom att aktivera alternativet ”Visa poster utan data”.
