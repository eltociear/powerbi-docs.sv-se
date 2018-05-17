---
title: Minska storleken på en Excel-arbetsbok för att visa den i Power BI
description: Minska storleken på en Excel-arbetsbok för att visa den i Power BI
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 479d431af4a7e904b138de1eb4fdf097bdbd68e9
ms.sourcegitcommit: f679c05d029ad0765976d530effde744eac23af5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/04/2018
---
# <a name="reduce-the-size-of-an-excel-workbook-to-view-it-in-power-bi"></a>Minska storleken på en Excel-arbetsbok för att visa den i Power BI
Du kan ladda upp Excel-arbetsböcker som är mindre än 1 GB till Power BI. En Excel-arbetsbok kan ha två delar: en datamodell och resten av rapporten. Arbetsbokens kärninnehåll. Om rapporten uppfyller följande storleksgränser, kan du spara den till **OneDrive för företag**, ansluta till den från Power BI och visa den i Excel Online:

* Arbetsboken som helhet kan vara upp till 1 GB.
* Arbetsbokens kärninnehåll kan vara upp till 10 MB.

## <a name="what-makes-core-worksheet-contents-larger-than-10-mb"></a>Vad gör arbetsbokens kärninnehåll större än 10 MB
Här följer några element som kan göra att arbetsbokens kärninnehåll är större än 10 MB:

* Bilder.
* Skuggade celler. [Ta bort ett cellskuggningsformat](https://support.office.com/article/Add-or-change-the-background-color-of-cells-ac10f131-b847-428f-b656-d65375fb815e).
* Färgade kalkylblad. [Ta bort ett arks bakgrund](https://support.office.com/en-US/article/add-or-remove-a-sheet-background-3577a762-8450-4556-96a2-cc265abc00a8).
* Textrutor.
* Clip-art.

Överväg att ta bort de här elementen om möjligt. 

Om rapporten innehåller en datamodell, finns det några andra alternativ: 

* Ta bort data från Excel-kalkylbladen och lagra dem i datamodellen i stället. Mer information finns i ta bort data från kalkylblad nedan. 
* [Skapa en minneseffektiv datamodell](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70) för att minska den sammanlagda storleken för rapporten.

Om du vill göra dessa ändringar, måste du redigera arbetsboken i Excel.

Läs mer om [filstorleksgränser för Excel-arbetsböcker i SharePoint Online](https://support.office.com/article/File-size-limits-for-workbooks-in-SharePoint-Online-9e5bc6f8-018f-415a-b890-5452687b325e).

## <a name="remove-data-from-worksheets"></a>Ta bort data från kalkylblad
Om du importerar data till Excel från Power Query-fliken eller Excel Data-fliken, kanske arbetsboken har samma data i en Excel-tabell och i datamodellen. Stora tabeller i Excel-kalkylblad kan göra att kalkylbladets kärninnehåll blir större än 10 MB. Om du tar bort tabellen i Excel och behåller data i datamodellen, kan du avsevärt minska kalkylbladet kärninnehåll i rapporten. 

Följ dessa tips när du importerar data till Excel:

* **I Power Query**: rensa rutan **läs in till arbetsblad**.
  
  Data importeras endast till datamodellen, utan data i Excel-kalkylbladen.
* **På Excel Data-fliken**, om du tidigare har markerat **tabell** i importguiden: gå till **befintliga anslutningar** \> klicka på anslutningen \> **skapa endast anslutning**. Ta bort den ursprungliga tabellen eller tabellerna som skapades under den initiala importen.
* **På Excel Data-fliken**: markera inte **tabell** i rutan **importera data**.

## <a name="workbook-size-optimizer"></a>Arbetsbokens storleksoptimering
Om din arbetsbok innehåller en datamodell, kan du köra arbetsbokens storleksoptimering för att minska storleken på din arbetsbok. [Hämta arbetsbokens storleksoptimering](https://www.microsoft.com/en-us/download/details.aspx?id=38793).

## <a name="related-info"></a>Relaterad information
[Skapa en minneseffektiv datamodell](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70)

[Använd OneDrive för företag-länkar i Power BI Desktop](desktop-use-onedrive-business-links.md)

