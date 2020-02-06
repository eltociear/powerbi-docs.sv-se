---
title: Anpassning av PDF-återgivningstillägg till ISO 14289-1 – Power BI-rapportserver och SSRS
description: I det här dokumentet beskrivs specifikationer för anpassning av PDF-återgivningstillägg till ISO 14289-1 (PDF/UA) för Power BI-rapportserver och SQL Server Reporting Services.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/04/2019
ms.author: maggies
ms.openlocfilehash: bfefcef18b8cd92a5c3b15c2dcbd4653a6c7c9cd
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819524"
---
# <a name="pdf-rendering-extension-conformance-to-iso-14289-1---power-bi-report-server--ssrs"></a>Anpassning av PDF-återgivningstillägg till ISO 14289-1 – Power BI-rapportserver och SSRS

Gäller för: Power BI-rapportserver och SQL Server Reporting Services (SSRS)

I det här dokumentet beskrivs specifikationer för anpassning av PDF-återgivningstillägg till [ISO 14289-1 (PDF/UA)](https://www.pdfa.org/publication/pdfua-in-a-nutshell/) för Power BI-rapportserver och SQL Server Reporting Services.

> [!NOTE]
> Du kan spara eller skriva ut detta white paper genom att välja **Skriv ut** i webbläsaren och sedan välja **Spara som PDF**.

## <a name="1--scope"></a>1.  Omfång

Ej tillämpligt

## <a name="2--normative-references"></a>2.  Normativa referenser

Ej tillämpligt

## <a name="3--terms-and-definitions"></a>3.  Villkor och definitioner

Ej tillämpligt

## <a name="4--notation"></a>4.  Notation

Ej tillämpligt

## <a name="5-version-identification"></a>5. Versionsidentifiering

PDF-återgivningstillägget ger stöd för PDF/UA enligt beskrivningen i det här dokumentet. I vissa fall (anges nedan) är det användaren som ska vidta åtgärder för att säkerställa att en PDF-fil är helt kompatibel med PDF/UA.  Vi förväntar oss att användaren lägger till rätt PDF/UA-version och anpassnings-ID:n som det sista steget i den här processen, vilket visar att nödvändiga åtgärder har vidtagits för att PDF-filen ska vara helt PDF/UA-kompatibel.

Allt som anges i det här dokumentet baseras på återgivning av ett PDF-dokument med enhetsinformationsinställningen AccessiblePdf angiven som `true`. I vissa fall kan efterlevnadsbegränsningar bero på begränsningar i RDL (Report Definition Language).

## <a name="6--conformance-requirements"></a>6.  Krav för överensstämmelse

|     Villkor     |     Funktion som stöds     |     Kommentarer      |
|----|--------|--------|
|    6.1 Allmänt    |                 Stöds    |    PDF-återgivningstillägget skapar PDF-version 1.7.    |
|    6.2 Filer som uppfyller kraven    |                 Stöds med undantag    |    Se anmärkningar i avsnitt 7 – Krav på filformat.    |
|    6.3 Läsare som uppfyller kraven    |     Ej tillämpligt     |         |
|    6.4 Hjälpmedelsteknik som uppfyller kraven    |     Ej tillämpligt     |         |

## <a name="7--file-format-requirements"></a>7.  Krav på filformat

|     Villkor     |     Funktion som stöds     |     Kommentarer      |
|-----|-------|------------------------|
|    7.1 Allmänt    |                 Stöds med undantag    |    Allt verkligt innehåll skall taggas enligt definitionen i ISO 32000-1:2008, 14.8. Artefakter (ISO 32000-1:2008, 14.8.2.2.2) får inte vara taggade i strukturträdet. <li> PDF-återgivningstillägget kan inte explicit markera enskilda objekt som artefakter, så allt som mappas till villkoret i ISO 32000-1:2008, 14.8.2.2.2 kommer att anges som artefakter.<br>Innehållet ska markeras i strukturträdet med semantiskt lämpliga taggar i en logisk läsordning. <br> **Obs!** 4   WCAG 2.0, riktlinjer 1.4 beskriver problem gällande kontrast, färg och annan formatering för hjälpmedel. <br><li> Användarna måste säkerställa att deras dokument inte omfattas av de här problemen. <br>Standardtaggar som definieras i ISO 32000-1:2008, 14.8.4, får inte mappas om. <li> PDF-återgivningstillägget mappar inte om standardtaggarna. Dokument inleds med dokumentets rotelement. <br>Filer där anspråk görs på att följa denna internationella standard ska ha ett värde för misstänkta tillägg som falskt (ISO 32000-1:2008, tabell 321). <li> Det finns ingen post för misstänkta tillägg i PDF-återgivningstillägget. Den här egenskapen är valfri.    |
|    7.2 Text    |                 Stöds med undantag    |    Innehållet ska vara taggat i logisk läsordning. Den mest semantiskt lämpliga taggen skall användas för varje logiskt element i dokumentinnehållet. <br><li> PDF-återgivningstillägget taggar innehåll i logisk läsordning i så hög utsträckning som möjligt.<br>Teckenkoderna ska mappas till Unicode enligt beskrivningen i ISO 32000-1:2008, 14.8.2.4.2. Tecken som inte ingår i Unicode-specifikationen kan använda Unicodes privata användningsområden eller deklarera en annan teckenkodning. <br>Naturligt språk skall deklareras enligt beskrivningen i ISO 32000-1:2008, 14.9.2 och/eller enligt beskrivningen i ISO 32000-1:2008, 7.9.2. Ändringar i naturligt språk skall deklareras. Ändringar i naturligt språk inuti textsträngar (t.ex. inuti alternativa beskrivningar) ska deklareras med en språkidentifierare enligt beskrivningen i ISO 32000-1:2008, 14.9.2.2. <br><li> PDF-återgivningstillägget deklarerar bara naturligt språk på dokumentnivå    |
|    7.3 Grafik    |                 Stöds med undantag    |    Grafiska objekt, förutom textobjekt, ska vara taggade med en figurtagg enligt beskrivningen i ISO 32000-1:2008, 14.8.4.5, tabell 340. Om något av följande undantag är sant, ska det grafiska objektet taggas som en artefakt: <br><li> det grafiska objektet visar inte något meningsfullt innehåll, eller <li>  det grafiska objektet visas som en bakgrund i en länkanteckning. I dessa fall ska den alternativa texten i länken beskriva både det grafiska objektet och länken. <li> PDF-återgivningstillägg taggar grafiska objekt med figurtaggen. <br>En bildtext som tillhör en figur är taggad med en bildtexttagg. <li> PDF-återgivningstillägget taggar för närvarande inte bildtexter i figurer med en bildtexttagg. <br>Figurtaggar skall innehålla en alternativ visnings- eller ersättningstext för innehållet som markerats med figurtaggen, enligt vad som anges i ISO 32000-1:2008, 14.7.2, tabell 323. <br>**Obs!** 1 Se även WCAG 2.0, riktlinje 1.1. <br>Om text som visas i ett grafiskt objekt inte är text på ett naturligt språk som är avsett att läsas av en mänsklig läsare, ska en alternativ text som beskriver arten eller syftet med grafiken tillhandahållas. <br>**Obs!** 2 Text som är ett typexempel eller ett exempel på det skrivsystem som används av ett språk är exempel på text som inte är på ett naturligt språk.   PDF-återgivningstillägget stöder alternativ text i figurer, men det är användarens ansvar att lägga till alternativtexten. <br>Ytterligare kommentar om BBox-attributet: <br><li> PDF-återgivningstillägget skriver för närvarande inte BBox-attributet. <li> En lösning är att manuellt göra en ny taggning av illustrationer som nya figurer eller artefakter.    |
|    7.4 Rubriker    |                 Ej tillämpligt    |    RDL stöder inte markering av rubriker på något sätt. Det är upp till användaren att tagga dem efter behov.    |
|    7.5 Tabeller    |                 Stöds med undantag    |    Tabeller bör innehålla rubriker. Tabellrubriker ska taggas enligt ISO 32000-1:2008, tabell 337 och tabell 349. <br>**Obs!** 1 Tabeller kan innehålla kolumnrubriker, radrubriker eller både och. <br>**Obs!** 2 Så mycket information som möjligt om tabellstrukturen måste vara tillgänglig när hjälpmedelsteknik används. Rubriker spelar en viktig roll när det gäller att tillhandahålla strukturell information. <br><li> Det är upp till användaren att inkludera rubriker i sina tabeller. RDL och PDF-återgivningstillägget har stöd för radrubriker. <br>  Strukturelement av typen TH måste ha ett omfångsattribut.   <li> PDF-återgivningstillägget innehåller ett omfångsattribut i TH-elementen för kolumn- och radmedlemmar, men inte för hörnceller.<br>Tabelltaggningsstrukturer får endast användas för att tagga innehåll som presenteras i logiska rad- och/eller kolumnrelationer.   <li> Detta beror på hur användaren har valt att använda tabeller i sitt RDL.    |
|    7.6 Listor    |                 Ej tillämpligt    |    RDL stöder inte markering av listor. I RDL är de strukturellt sett en tabell med en enda tabellcell. <br>Det är upp till användaren att tagga om dem efter behov.    |
|    7.7 Matematiska uttryck    |                 Stöds med undantag    |    Alla matematiska uttryck ska omges av en formeltagg, enligt beskrivningen i ISO 32000-1:2008, 14.8.4.5 och ha ett alternativt attribut. <br><li> PDF-återgivningstillägget omger inte matematiska uttryck med en formeltagg för närvarande. <br>Kraven för mappning av tecken till Unicode ska gälla för matematiska uttryck, enligt vad som anges i ISO 32000-1:2008, 9.10.2 och 14.8.2.4. <br><li> Detta stöds av PDF-återgivningstillägget.    |
|    7.8 Sidhuvuden och sidfötter    |                 Stöds    |    Löpande sidhuvuden och sidfötter måste identifieras som sidnumreringsartefakter och klassificeras som antingen sidhuvuds- eller sidfotsundertyper, enligt ISO 32000-1:2008, 14.8.2.2.2, tabell 330. <br><li> Sidhuvuden eller sidfötter behandlas och taggas som artefakter.    |
|    7.9 Anteckningar och referenser    |                 Ej tillämpligt    |    PDF-återgivningstillägget stöder inte markering av anteckningar och referenser. <br>Det är upp till användaren att tagga dem efter behov.    |
|    7.10 Valfritt innehåll    |                 Ej tillämpligt    |         |
|    7.11 Inbäddade filer    |                 Ej tillämpligt    |         |
|    7.12 Artikeltrådar    |                 Ej tillämpligt    |         |
|    7.13 Digitala signaturer    |                 Ej tillämpligt    |         |
|    7.14 Icke-interaktiva formulär    |                 Ej tillämpligt    |         |
|    7.15 XFA    |                 Ej tillämpligt    |         |
|    7.16 Säkerhet    |                 Ej tillämpligt    |         |
|    7.17 Navigering    |                 Stöds    |    Ett dokument ska innehålla en dokumentdisposition som matchar läsordningen och nivån för navigeringsmålen (ISO 32000-1:2008, 12.3.3). <br><li> RDL stöder bokmärken för ett rapportobjekt, men användaren måste välja det här alternativet. Bokmärkena återges sedan som en dokumentdisposition av PDF-återgivningstillägget. <br>Om detta finns ska posterna i PageLabels-nummerträdet (ISO 32000-1:2008, 7.7.2, tabell 28) vara semantiskt lämpliga. <br><li> PDF-återgivningstillägget innehåller inte något PageLabels-nummerträd.    |
|    7.18 Anteckningar    |                 Ej tillämpligt    |    RDL stöder inte anteckningar    |
|    7.21 Teckensnitt    |                 Stöds    |         |
|    7.21.1 Allmänt    |                 Stöds    |         |
|    7.21.2 Teckensnittstyper    |                 Stöds    |         |
|    7.21.3 Sammansatta teckensnitt    |                 Stöds    |         |
|    7.21.3.1 Allmänt    |                 Stöds    |         |
|    7.21.3.2 CIDFonts    |                 Stöds    |         |
|    7.21.3.3 CMaps    |                 Stöds    |         |
|    7.21.4 Inbäddning    |                 Stöds    |         |
|    7.21.4.1 Allmänt    |                 Stöds    |         |
|    7.21.4.2 Inbäddning av delmängd    |                 Stöds    |         |
|    7.21.5 Teckensnittsmått    |                 Stöds    |         |
|    7.21.6 Teckenkodning    |                 Stöds    |         |
|    7.21.7 Unicode-teckenuppsättningar    |                 Stöds    |         |
|    7.21.8 Användning av .notdef-glyf    |                 Stöds    |         |

## <a name="8--conforming-reader-requirements"></a>8.  Anpassa läsarkrav

Ej tillämpligt

## <a name="9--at-requirements"></a>9.  AT-krav

Ej tillämpligt

## <a name="disclaimer"></a>Disclaimer

© 2017 Microsoft Corporation. All rights reserved. The names of actual companies and products mentioned herein may be the trademarks of their respective owners. The information contained in this document represents the current view of Microsoft Corporation on the issues discussed as of the date of publication. Microsoft cannot guarantee the accuracy of any information presented after the date of publication. Microsoft regularly updates its websites with new information about the accessibility of products as that information becomes available.

Customization of the product voids this conformance statement from Microsoft. Please consult with Assistive Technology (AT) vendors for compatibility specifications of specific AT products.

This document is for informational purposes only. MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS DOCUMENT.


## <a name="next-steps"></a>Nästa steg
[Administratörsöversikt](admin-handbook-overview.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

