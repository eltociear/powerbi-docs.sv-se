---
title: Använda Vad om-parametrar för att visualisera variabler i Power BI Desktop
description: Skapa dina egna Vad om-variabler för att skapa och visualisera variabler i Power BI-rapporter
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: daedbb480f09dbd8fc71044d78a532a1ea96b1ac
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="create-and-use-a-what-if-parameter-to-visualize-variables-in-power-bi-desktop"></a>Skapa och använd en Vad om-parameter för att visualisera variabler i Power BI Desktop
Från och med augusti 2017-utgåvan av **Power BI Desktop**, kan du skapa **Vad om**-variabler för dina rapporter, interagera med variablerna som ett utsnitt och därmed visualisera och kvantifiera olika nyckelvärden i dina rapporter.

![](media/desktop-what-if/what-if_01.png)

**Vad om**-parametern finns i fliken **Modellering** i **Power BI Desktop**. När du väljer den, visas en dialogruta där du kan konfigurera parametern.

## <a name="creating-a-what-if-parameter"></a>Skapa en Vad om-parameter
Du skapar en **Vad om**-parameter genom att välja knappen **Vad om** från fliken **Modellering** i **Power BI Desktop**. I följande bild har vi skapat en parameter som heter *rabattprocent* och ställt in dess datatyp till *Decimaltal.* *Minimi*värdet är noll, *Max* är 0,50 (50 procent). Vi har också ställt in *inkrementet* till 0,05 eller fem procent. Det är så mycket parametern justeras när du har interagerat med den i rapporten.

![](media/desktop-what-if/what-if_02.png)

> [!NOTE]
> Kontrollera för decimaltal att du skriver noll innan, som i 0,50 istället för bara ,50. Annars kommer numret inte att valideras och **OK**-knappen kan inte väljas.
> 
> 

För din bekvämlighet sätter kryssrutan **Lägg till ett utsnitt till den här sidan** automatiskt ett utsnitt med din **Vad om**-parameter på den aktuella rapportsidan.

![](media/desktop-what-if/what-if_03.png)

Förutom att skapa parametern, skapar en **Vad om**-parameter också ett mått som du kan använda för att visualisera det aktuella värdet för **Vad om**-parametern.

![](media/desktop-what-if/what-if_04.png)

Det är viktigt och användbart att vara medveten om att när du skapar en **Vad om**-parameter så blir både parametern och måttet en del av din modell. De finns därmed tillgängliga i hela rapporten och kan användas på andra rapportsidor. Och eftersom de är en del av modellen, kan du ta bort utsnittet från rapportsidan eller om du vill ha det tillbaka, behöver du bara hämta **Vad om**-parametern från **Fält**-listan och dra den till arbetsytan (ändra därefter visualiseringen till ett utsnitt) för att enkelt hämta tillbaka parametern till rapporten.

## <a name="using-a-what-if-parameter"></a>Använd en Vad om-parameter
Nu ska vi skapa ett enkelt exempel på hur du använder en **Vad om**-parameter. Vi har skapat **Vad om**-parametern i det föregående avsnittet, nu ska vi använda det genom att skapa ett nytt mått vars värde justeras med skjutreglaget. För att åstadkomma detta skapar vi ett nytt mått.

![](media/desktop-what-if/what-if_05.png)

Det nya måttet ska bara vara de totala försäljningssiffrorna med den diskonteringsränta som tillämpas. Du kan givetvis skapa komplexa och intressanta mått, som låter dina rapporters användare visualisera variabeln för din **Vad om**-parameter. Du kan till exempel skapa en rapport som gör att säljare ser sin kompensation om de uppfyller vissa säljmål eller procentsatser, eller ser relationen mellan ökad försäljning och mer rabatter.

När vi anger måttformeln i formelfältet och ger den namnet **försäljning efter rabatt**, ser vi dess resultat:

![](media/desktop-what-if/what-if_06.png)

Sedan skapar vi en kolumnvisualisering med *OrderDate* på axeln och både *SalesAmount* och det just skapade måttet *Försäljning efter rabatt* som värden.

![](media/desktop-what-if/what-if_07.png)

Sedan, när vi flytta skjutreglaget, ser vi att kolumnen *försäljning efter rabatt* återspeglar det reducerade försäljningsbeloppet.

![](media/desktop-what-if/what-if_08.png)

Det är allt. Du kan använda **Vad om**-parametrar i alla typer av situationer, för att låta rapportanvändare interagera med olika scenarier som du skapar i dina rapporter.

