---
title: "Använda Vad om-parametrar för att visualisera variabler i Power BI Desktop"
description: "Skapa dina egna Vad om-variabler för att skapa och visualisera variabler i Power BI-rapporter"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 5222b6ba99c9e61d1070f66115b90aa29099fd8d
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="create-and-use-a-what-if-parameter-to-visualize-variables-in-power-bi-desktop"></a>Skapa och använd en Vad om-parameter för att visualisera variabler i Power BI Desktop
Från och med augusti 2017-utgåvan av **Power BI Desktop**, kan du skapa **Vad om**-variabler för dina rapporter, interagera med variablerna som ett utsnitt och därmed visualisera och kvantifiera olika nyckelvärden i dina rapporter.

![](media/desktop-what-if/what-if_01.png)

**Vad om**-parametern hittar du i **Modellering**-fliken i **Power BI Desktop**. När du gör det, visas en dialogruta där du kan konfigurera parametern.

## <a name="creating-a-what-if-parameter"></a>Skapa en Vad om-parameter
Du skapar en **Vad om**-parameter genom att välja knappen **Vad om** från fliken **Modellering** i **Power BI Desktop**. I följande bild har vi skapat en parameter som heter *rabattprocent* och ställt in dess datatyp till *Decimaltal.* *Minimi*värdet är noll, *Max* är 0,50 (50 procent). Vi har också ställt in *inkrementet* till 0,05 eller fem procent. Det är så mycket parametern justeras när du har interagerat med den i rapporten.

![](media/desktop-what-if/what-if_02.png)

> [!NOTE]
> Kontrollera för decimaltal att du skriver noll innan, som i 0,50 istället för bara ,50 i rutan. Annars kommer numret inte att valideras och **Ok**-knappen kan inte väljas.
> 
> 

För din bekvämlighet sätter kryssrutan **Lägg till ett utsnitt till den här sidan** automatiskt ett utsnitt med din **Vad om**-parameter på den aktuella rapportsidan.

![](media/desktop-what-if/what-if_03.png)

Förutom att skapa parametern, skapar en **Vad om**-parameter också ett mått som du kan använda för att visualisera det aktuella värdet för **Vad om**-parametern.

![](media/desktop-what-if/what-if_04.png)

Det är viktigt och användbart att vara medveten om att när du skapar en **Vad om**-parameter så blir både parametern och måttet en del av din modell. De finns därmed tillgängliga i hela rapporten och kan användas på andra rapportsidor. Och eftersom de är en del av modellen, kan du ta bort utsnittet från rapportsidan och om du vill ha det tillbaka, behöver du bara hämta **Vad om**-parametern från **Fält**-listan och dra den till arbetsytan (ändra därefter visualiseringen till ett utsnitt) för att enkelt hämta tillbaka **Vad om**-parametern till rapporten.

## <a name="using-a-what-if-parameter"></a>Använd en Vad om-parameter
Nu ska vi skapa ett enkelt exempel på hur du använder en **Vad om**-parameter. Vi har skapat **Vad om**-parametern i det föregående avsnittet, nu ska vi använda det genom att skapa ett nytt mått vars värde justeras med skjutreglaget. För att åstadkomma detta skapar vi ett nytt mått.

![](media/desktop-what-if/what-if_05.png)

Det nya måttet ska bara vara de totala försäljningssiffrorna med den diskonteringsränta som tillämpas. Du kan givetvis skapa komplexa och intressanta mått, som låter dina rapporters användare visualisera variabeln för din **Vad om**-parameter. Du kan till exempel skapa en rapport som gör att säljare ser sin kompensation om de uppfyller vissa säljmål eller procentsatser, eller ser relationen mellan ökad försäljning och mer rabatter.

När vi anger måttformeln i formelfältet och ger den namnet **försäljning efter rabatt**, ser vi dess resultat:

![](media/desktop-what-if/what-if_06.png)

Sedan skapar vi en kolumnvisualisering med *OrderDate* på axeln och både *SalesAmount* och det just skapade måttet *försäljning efter rabatt* som värden.

![](media/desktop-what-if/what-if_07.png)

Sedan, när vi flytta skjutreglaget, ser vi att kolumnen *försäljning efter rabatt* återspeglar det reducerade försäljningsbeloppet.

![](media/desktop-what-if/what-if_08.png)

Det är allt. Du kan använda **Vad om**-parametrar i alla typer av situationer, för att låta rapportanvändare interagera med olika scenarier som du skapar i dina rapporter.

