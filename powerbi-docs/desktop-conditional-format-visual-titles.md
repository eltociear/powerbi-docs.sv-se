---
title: Uttrycksbaserade rubriker i Power BI Desktop
description: Skapa dynamiska rubriker i Power BI Desktop som ändras baserat på programmatiska uttryck med hjälp av villkorsstyrd programmatisk formatering
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1b4e134ef6f8da43a1856c8a5458c8c09b2c42b5
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/26/2019
ms.locfileid: "68522184"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Uttrycksbaserade rubriker i Power BI Desktop

Du kan skapa dynamiska, anpassade rubriker för visuella Power BI-objekt. När du skapar dataanalysuttryck (DAX, Data Analysis Expressions) baserat på fält, variabler eller andra programmatiska element kan rubrikerna för dina visuella objekt justeras automatiskt efter behov. Dessa ändringar baseras på filter, val eller andra användarinteraktioner och konfigurationer.

![Skärmbild av alternativet för villkorsstyrd formatering i Power BI Desktop](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

Det är enkelt att skapa dynamiska rubriker, som ibland kallas *uttrycksbaserade rubriker*. 

## <a name="create-a-field-for-your-title"></a>Skapa ett fält för rubriken

Det första steget i att skapa en uttrycksbaserad rubrik är att skapa ett fält i den modell som ska användas för rubriken. 

Det finns många kreativa sätt att få det visuella objektets rubrik att uttrycka det du vill förmedla. Vi tar en titt på några exempel.

Du kan skapa ett uttryck som ändras baserat på den filterkontext som det visuella objektet tar emot för produktens varumärkesnamn. Följande bild visar DAX-formeln för ett sådant fält.

![Skärmbild av DAX-formeln](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Ett annat exempel är att använda en dynamisk rubrik som ändras baserat på användarens språk eller kultur. Du kan skapa språkspecifika rubriker i ett DAX-mått med hjälp av funktionen `USERCULTURE()`. Den här funktionen returnerar kulturkoden för användaren baserat på användarens inställningar för operativsystem eller webbläsare. Du kan använda följande DAX-switch-instruktion för att välja rätt översatt värde. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

Eller så kan du hämta strängen från en uppslagstabell som innehåller alla översättningar. Du placerar den tabellen i din modell. 

Dessa är bara några exempel som du kan använda för att skapa dynamiska, uttrycksbaserade rubriker för dina visuella objekt i Power BI Desktop. Det du kan göra med rubriker begränsas bara av fantasin och din modell.


## <a name="select-your-field-for-your-title"></a>Välja fält för rubriken

När du har skapat DAX-uttrycket för det fält som du skapar i modellen behöver du tillämpa det på det visuella objektets rubrik.

För att markera fältet och tillämpa det går du till fönstret **Visualiseringar**. I området **Format** väljer du **Rubrik** för att visa rubrikalternativen för det visuella objektet. 

När du högerklickar på **Rubriktext** visas en snabbmeny där du kan välja ***fx*Villkorsstyrd formatering**. När du väljer det menyalternativet visas dialogrutan **Rubriktext**. 

![Skärmbild av dialogrutan Rubriktext](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

I det fönstret kan du välja det fält som du skapade för att använda för rubriken.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

Det finns några begränsningar för den aktuella implementeringen av uttrycksbaserade rubriker för visuella objekt:

* För närvarande stöds inte uttrycksbaserad formatering i visuella Python-objekt, visuella R-objekt eller det visuella objektet Viktiga influerare.
* Det fält som du skapar för rubriken måste vara av datatypen sträng. Mått som returnerar tal eller datum/tid (eller någon annan datatyp) stöds inte för närvarande.
* Uttrycksbaserade rubriker följer inte med när du fäster ett visuellt objekt på en instrumentpanel.

## <a name="next-steps"></a>Nästa steg

Den här artikeln beskrev hur du skapar DAX-uttryck som omvandlar rubrikerna för dina visuella objekt till dynamiska fält som kan ändras när användarna interagerar med dina rapporter. Följande artiklar kan också vara användbara.

* [Villkorsstyrd formatering i tabeller](desktop-conditional-table-formatting.md)
* [Använd visning av detaljerad information mellan rapporter i Power BI Desktop](desktop-cross-report-drill-through.md)
* [Använd detaljinformation i Power BI Desktop](desktop-drillthrough.md)
