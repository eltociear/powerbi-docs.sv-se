---
title: Exportera rapporter till PDF-format från Power BI Desktop
description: Exportera enkelt till PDF från Power BI Desktop och skriv enkelt ut PDF-rapporterna
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/28/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 6e468ac429c26f3b1880501914816ac60f8b7858
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79378741"
---
# <a name="export-reports-to-pdf-from-power-bi-desktop"></a>Exportera rapporter till PDF från Power BI Desktop
I **Power BI Desktop** eller Power BI desktop-tjänsten kan du exportera rapporter till en PDF-fil och på så sätt enkelt dela eller skriva ut dina rapporter från PDF-filen.

![Exportera till PDF](media/desktop-export-to-pdf/export-to-pdf_01.png)

Det är enkelt att exportera rapporter från **Power BI Desktop** till en PDF-fil, så att du kan skriva ut PDF-filen eller dela PDF-dokumentet med andra. Välj bara **Fil > Exportera till PDF** från Power BI Desktop.

Funktionen **Exportera till PDF** exporterar alla *synliga* sidor i rapporten, och varje rapportsida exporteras till en separat sida i PDF-filen. Rapportsidor som för närvarande inte visas, till exempel knappbeskrivningar eller dolda sidor, exporteras inte till PDF-filen. 

![Så här fungerar Exportera till PDF](media/desktop-export-to-pdf/export-to-pdf_02.png)

När du väljer **Fil > Exportera till PDF** initieras exporten och en dialogruta öppnas som visar exportprocessen. Dialogrutan finns kvar på skärmen tills exporten har slutförts. Under exportprocessen inaktiveras all interaktion med rapporten som exporteras. Det enda sättet att interagera med rapporten är att vänta tills exporten har slutförts eller att avbryta exporten. 

När exporten har slutförts läses PDF-filen in i det förvalda PDF-visningsprogrammet på datorn. 

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
Det finns några saker som du bör tänka på när du använder funktionen **Exportera till PDF**:

* Visuella Power BI-objekt exporteras med funktionen, men skrivbordsunderlägg som har lagts till i rapporten exporteras *inte*.

Eftersom skrivbordsunderlägg inte exporteras till PDF-filen bör du vara särskilt uppmärksam på rapporter som har mörk bakgrund. Om texten i rapporten är ljus eller vit, så att den framhävs mot den mörka bakgrunden, blir den svårläst eller oläslig eftersom funktionen Exportera till PDF inte exporterar skrivbordsunderlägget med resten av rapporten. 



## <a name="next-steps"></a>Nästa steg
Det finns en mängd intressanta visuella element och funktioner i **Power BI Desktop**. Mer information finns här:

* [Använda visuella element för att förbättra Power BI-rapporter](desktop-visual-elements-for-reports.md)
* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)


