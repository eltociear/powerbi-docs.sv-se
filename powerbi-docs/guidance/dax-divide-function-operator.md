---
title: 'DAX: Funktionen DIVIDERA jämfört med divisionsoperatorn (/)'
description: Vägledning om när du ska använda funktionen DAX DIVIDERA.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: 7516aaedb886e7b9e0f57ed76f0a7c5e40efbd6d
ms.sourcegitcommit: 6a44cb5b0328b60ebe7710378287f1e20bc55a25
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70877853"
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

Funktionen DIVIDERA är praktisk eftersom uttrycket inte behöver testa värdet för nämnaren först. Funktionen är också bättre optimerad för testning av nämnarvärdet än funktionen [OM](/dax/if-function-dax). Prestandaförbättringen är avsevärd eftersom det är dyrt att kontrollera för division med noll. Att använda DIVIDERA resulterar också i ett mer tydligt och elegant uttryck.

## <a name="example"></a>Exempel

Följande måttuttryck skapar en säker division men det innebär att du måste använda fyra DAX-funktioner.

```dax

=IF(OR(ISBLANK([Sales]), [Sales] == 0), BLANK(), [Profit] / [Sales])

```

Detta måttuttryck uppnår samma resultat, men är mer effektivt och elegant.

```dax

=DIVIDE([Profit], [Sales])

```

## <a name="recommendations"></a>Rekommendationer

Vi rekommenderar att du använder funktionen DIVIDERA när nämnaren är ett uttryck som _kan_ returnera noll eller TOM.

Om nämnaren är ett konstant värde rekommenderar vi att du använder divisionsoperatorn. I det här fallet kommer divisionen garanterat att lyckas och ditt uttryck fungerar bättre eftersom det inte behöver genomföra någon onödig testning.

Du bör noga överväga om DIVIDERA-funktionen ska returnera ett alternativt värde. Vid mått är det vanligtvis bättre än att de returnerar TOM. Det beror på att visuella rapportobjekt som standard eliminerar grupperingar när summeringar är tomma. Detta innebär att det visuella objektet kan fokusera på grupper där det finns data. Vid behov kan du konfigurera det visuella objektet så att det visar alla grupper (som returnerar värden eller TOM) i filterkontexten genom att aktivera alternativet ”Visa poster utan data”.
