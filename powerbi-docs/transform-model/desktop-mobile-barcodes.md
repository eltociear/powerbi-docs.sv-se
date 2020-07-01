---
title: Tagga ett streckkodsfält i Power BI Desktop för mobilappar
description: När du markera ett streckkodsfält i modellen i Power BI Desktop kan du filtrera data för streckkoder automatiskt i Power BI-appen på din iPhone.
author: maggiesMSFT
ms.author: maggies
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/16/2018
LocalizationGroup: Model your data
ms.openlocfilehash: d1def1d9686e5f764f8e6548f9ad4bce2432415d
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85232453"
---
# <a name="tag-barcodes-in-power-bi-desktop-for-use-in-the-mobile-app"></a>Tagga streckkoder i Power BI Desktop för användning i mobilappar

Du kan i Power BI Desktop [kategorisera data](desktop-data-categorization.md) för en kolumn, så Power BI Desktop vet hur värden ska hanteras i visuella objekt i en rapport. Du kan också kategorisera en kolumn som **Streckkod**. När du eller dina kollegor [skannar en streckkod på en produkt med Power BI-appen](../consumer/mobile/mobile-apps-scan-barcode-iphone.md) på en iPhone visas en rapport som innehåller den streckkoden. När du öppnar rapporten i mobilappen filtrerar Power BI rapporten automatiskt efter data som är relaterade till streckkoden.

1. Växla till datavy i Power BI Desktop.
2. Markera en kolumn med streckkodsdata. Visa en lista över [streckkodsformat som stöds](#supported-barcode-formats) nedan.
3. På fliken **Modellering** väljer du **Datakategori** > **Streckkod**.
   
    ![Listan Datakategori](media/desktop-mobile-barcodes/power-bi-desktop-barcode.png)
4. I rapporten visas lägger du till fältet den visuella informationen som ska filtreras av streckkoden.
5. Spara och publicera rapporten i Power BI-tjänsten.

Nu när du öppnar skannern i [Power BI-appen för iPhone](../consumer/mobile/mobile-iphone-app-get-started.md) och skannar en streckkod kan du se den här rapporten i listan över rapporter. När du öppnar rapporten filtreras dess visuella objekt enligt den avlästa streckkoden.

## <a name="supported-barcode-formats"></a>Streckkodsformat som stöds
Följande streckkoder kan läsas av Power BI om du taggar dem i en Power BI-rapport: 

* UPCECode 
* Code39Code  
* A39Mod43Code 
* EAN13Code 
* EAN8Code  
* 93Code  
* 128Code 
* PDF417Code 
* Interleaved2of5Code 
* ITF14Code 

## <a name="next-steps"></a>Nästa steg
* [Skanna en streckkod från Power BI-appen på din iPhone](../consumer/mobile/mobile-apps-scan-barcode-iphone.md)
* [Problem med avläsning av streckkoderna på en iPhone](../consumer/mobile/mobile-apps-scan-barcode-iphone.md#issues-with-scanning-a-barcode)
* [Datakategorisering i Power BI Desktop](desktop-data-categorization.md)  
* Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
