---
title: Använda konsekvensparametrar för att visualisera variabler
description: Skapa dina egna Vad om-variabler för att framställa och visualisera variabler i Power BI-rapporter
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 8a72bc43bcceae6e676728934ceec81c8cb27d04
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76539484"
---
# <a name="create-and-use-what-if-parameters-to-visualize-variables-in-power-bi-desktop"></a>Skapa och använd Vad om-parametrar för att visualisera variabler i Power BI Desktop

Från och med augusti 2018-utgåvan av *Power BI Desktop* kan du skapa *Vad om*-variabler för dina rapporter, interagera med variablerna som ett utsnitt samt visualisera och kvantifiera olika nyckelvärden i dina rapporter.

![Alternativet Ny parameter](media/desktop-what-if/what-if_01.png)

Skapa en *Vad om-parameter* på fliken **Modellering** i Power BI Desktop. När du väljer det visas en dialogruta där du kan konfigurera parametern.

## <a name="creating-a-what-if-parameter"></a>Skapa en Vad om-parameter

Du skapar en Vad om-parameter genom att välja **Ny parameter** på fliken **Modellering** Power BI Desktop. I följande bild har vi skapat en parameter som heter *Discount percentage* (Rabattprocent) och angett dess datatyp till **Decimaltal**. **Minimivärdet** är noll. **Maxvärdet** är 0,50 (50 procent). Vi har också ställt in **inkrementet** till 0,05 eller fem procent. Det är så mycket parametern justeras när du har interagerat med den i rapporten.

![Värden för Vad om-parameter](media/desktop-what-if/what-if_02.png)

> [!NOTE]
> För decimaltal ska du skriva en nolla framför värdet, till exempel 0,50 i stället för bara ,50. Annars valideras inte numret, och det går inte att välja knappen **OK**.
> 
> 

Kryssrutan **Lägg till ett utsnitt på den här sidan** lägger automatiskt till ett utsnitt med din Vad om-parameter på den aktuella rapportsidan.

![Nytt utsnitt på den aktuella rapportsidan](media/desktop-what-if/what-if_03.png)

När du skapar en Vad om-parameter skapas utöver parametern även ett mått som du kan använda för att visualisera det aktuella värdet för Vad om-parametern.

![Mått som skapas för Vad om-parameter](media/desktop-what-if/what-if_04.png)

Det är viktigt och användbart att vara medveten om att när du skapar en Vad om-parameter så blir både parametern och måttet en del av din modell. De finns därmed tillgängliga i hela rapporten och kan användas på andra rapportsidor. Och eftersom de är en del av modellen kan du ta bort utsnittet från rapportsidan. Om du vill ha tillbaka den drar du bara Vad om-parametern i listan **Fält** till arbetsytan och ändrar sedan det visuella objektet till ett utsnitt.

## <a name="using-a-what-if-parameter"></a>Använda en Vad om-parameter

Nu ska vi skapa ett enkelt exempel på hur du använder en Vad om-parameter. Vi skapade Vad om-parametern i föregående avsnitt. Nu ska vi använda den genom att skapa ett nytt mått vars värde justeras med skjutreglaget.

![Lägga till ett nytt mått som ska användas med parametern](media/desktop-what-if/what-if_05.png)

Det nya måttet ska bara vara de totala försäljningssiffrorna med den diskonteringsränta som tillämpas. Du kan skapa komplexa och intressanta mått som dina rapportanvändare kan använda för att visualisera variabeln för din Vad om-parameter. Du kan till exempel skapa en rapport där säljare kan se sin provision om de uppfyller vissa säljmål eller procentandelar, eller ser relationen mellan ökad försäljning och mer rabatter.

Ange måttformeln i formelfältet och ge formeln namnet *Försäljning efter rabatt*.

![Definition av Försäljning efter rabatt](media/desktop-what-if/what-if_06.png)

Sedan skapar vi en kolumnvisualisering med **OrderDate** på axeln och både **SalesAmount** och det just skapade måttet **Försäljning efter rabatt** som värden.

![Visualisering för SalesAmount](media/desktop-what-if/what-if_07.png)

Sedan, när vi flytta skjutreglaget, ser vi att kolumnen **försäljning efter rabatt** återspeglar det reducerade försäljningsbeloppet.

![Skjutreglaget interagerar med det visuella objektet](media/desktop-what-if/what-if_08.png)

Det är allt. Du kan använda Vad om-parametrar i många olika situationer. Med de här parametrarna kan rapportanvändare interagera med olika scenarier som du skapar i dina rapporter.
