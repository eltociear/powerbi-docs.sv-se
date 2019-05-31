---
title: Uttrycksbaserade rubriker i Power BI Desktop
description: Skapa dynamiska rubriker i Power BI Desktop som ändras baserat på programmässiga uttryck med villkorsstyrd formatering programmässig
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b90ef66d2c118a70f1b18ed4fe302ce1db23e45c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769740"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Uttrycksbaserade rubriker i Power BI Desktop

Du kan skapa dynamiska, anpassade rubriker för Power BI-visualiseringar. Genom att skapa Dataanalysuttryck (DAX) baserat på fält, variabler eller andra programmässiga element kan kan dina visualiseringar rubriker automatiskt justera efter behov. Dessa ändringar är baserade på filter, val, eller andra användarinteraktioner och konfigurationer.

![Skärmbild av Power BI Desktop villkorlig formateringsalternativ](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

Skapa dynamiska titlar, kallas ibland *uttrycksbaserade rubriker*, det är enkelt. 

## <a name="create-a-field-for-your-title"></a>Skapa ett fält för din rubrik

Det första steget i att skapa en uttrycksbaserade rubrik är att skapa ett fält i din modell ska använda för rubriken. 

Det finns olika typer av kreativa sätt att ha din visuell rubrik återspegla vad du vill att säga eller vad du vill express. Låt oss ta en titt på några exempel.

Du kan skapa ett uttryck som ändras, baserat på filterkontext som det visuella objektet som tar emot för Produktnamn varumärke. Följande bild visar DAX-formeln för ett sådant fält.

![Skärmbild av DAX-formel](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Ett annat exempel är att använda en dynamisk rubrik som ändras, baserat på användarens språk eller kultur. Du kan skapa språkspecifika rubriker i en DAX-mått med hjälp av den `USERCULTURE()` funktion. Den här funktionen returnerar kultur-koden för den användare, baserat på deras operativsystem eller webbläsarinställningar. Du kan använda följande DAX switch-satsen för att välja rätt översatta värde. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

Eller du kan hämta strängen från en uppslagstabell som innehåller alla översättningar. Du kan placera tabellen i din modell. 

Det här är några exempel som du kan använda för att skapa dynamiska, uttrycksbaserat rubrikerna för dina visuella objekt i Power BI Desktop. Vad du kan göra med dina rubriker begränsas bara av din fantasi och din modell.


## <a name="select-your-field-for-your-title"></a>Välj ditt på texten

När du har skapat DAX-uttrycket för fältet som du skapar i din modell, måste du tillämpa den på din visuella objektets rubrik.

Markera fältet och tillämpa den, går du till den **visualiseringar** fönstret. I den **Format** Välj **rubrik** att visa rubrikalternativ för det visuella objektet. 

När du högerklickar på **rubriktext**, visas en snabbmeny som gör det möjligt att välja ***fx * villkorsstyrd formatering**. När du väljer menyalternativet, en **rubriktext** dialogrutan visas. 

![Skärmbild av titeln text i dialogrutan](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

Du kan välja det fält som du skapade för att använda för din rubrik från det aktuella fönstret.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

Det finns några begränsningar för den aktuella implementationen av uttrycksbaserade rubriker för visuella objekt:

* Uttrycksbaserade formatering stöds för närvarande inte på Python visuella objekt, visuella R-objekt eller Nyckelpåverkare-visualiseringen.
* Fältet som du skapar för rubriken måste vara av datatypen string. Mått som returnerar tal eller datum/tid (eller någon annan datatyp) stöds inte för närvarande.

## <a name="next-steps"></a>Nästa steg

Den här artikeln beskrivs hur du skapar DAX-uttryck som aktiverar titlarna på dina visuella objekt i dynamiska fält som kan ändras när användare interagerar med dina rapporter. Du kan vara användbara i följande artiklar samt.

* [Använd detaljinformation för cross-rapport i Power BI Desktop](desktop-cross-report-drill-through.md)
* [Använd detaljinformation i Power BI Desktop](desktop-drillthrough.md)