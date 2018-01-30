---
title: "Så här exporterar du en rapport från Power BI-tjänsten till Desktop (förhandsgranskning)"
description: "Hämta en rapport från Power BI-tjänsten till en Power BI Desktop-fil"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 01/20/2018
ms.author: mihart
ms.openlocfilehash: 259007c76b7b53ba0ea55a28fbdd189469383364
ms.sourcegitcommit: 2ae323fbed440c75847dc55fb3e21e9c744cfba0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2018
---
# <a name="export-a-report-from-power-bi-service-to-desktop-preview"></a>Exportera en rapport från Power BI-tjänsten till skrivbordet (förhandsgranskning)
I Power BI Desktop kan du exportera (kallas även *hämta*) en rapport till Power BI-tjänsten genom att spara rapporten och välja **Publicera**. Du kan även exportera i omvänd ordning samt och ladda ned en rapport från Power BI-tjänsten till skrivbordet. Filnamnstillägget för filer som exporteras i endera riktningen är *.pbix*.

Det finns några begränsningar och saker du bör tänka på, vilket beskrivs längre fram i den här artikeln.

![](media/service-export-to-pbix/power-bi-file-export.png)

## <a name="download-the-report-as-a-pbix"></a>Ladda ned rapporten som en .pbix-fil
Hämta .pbx-filen genom att följa dessa steg:

1. Öppna rapporten i [redigeringsvyn](service-reading-view-and-editing-view.md) i **Power BI-tjänsten**.
2. Välj **Arkiv > Hämta rapport** på menyraden.
   
   > [!NOTE]
   > Rapporten måste ha [skapats med Power BI Desktop](guided-learning/publishingandsharing.yml#step-2) efter den 23 November 2016 – eller ha uppdaterats sedan dess – för att du ska kunna hämta rapporten. Om så inte är fallet är menyalternativet *Ladda ned rapport* i Power BI-tjänsten nedtonat.
   > 
   > 
3. Medan .pbx-filen skapas, visas förloppet i en statusbanderoll. När filen är klar ombeds du att öppna eller spara .pbx-filen. Filens namn matchar rapportens titel.
   
    ![](media/service-export-to-pbix/power-bi-save-pbix.png)
   
    Nu kan du öppna .pbx-filen i Power BI-tjänsten (app.powerbi.com) eller Power BI Desktop.     
4. Välj **Öppna** om du vill öppna rapporten direkt på skrivbordet. Om du vill spara filen till en specifik plats, väljer du **Spara > Spara som**. [Installera Power BI Desktop](desktop-get-the-desktop.md) om du inte redan har gjort det.
   
    När du öppnar rapporten på skrivbordet visas ett varningsmeddelande om att vissa funktioner som är tillgängliga i rapporten i Power BI-tjänsten kanske inte är tillgängliga i Desktop.
   
    ![](media/service-export-to-pbix/power-bi-export-to-pbix_2.png)

5. Rapportredigeraren i Desktop liknar rapportredigeraren i Power BI-tjänsten.  
   
    ![](media/service-export-to-pbix/power-bi-desktop.png)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
Det finns några viktiga överväganden och begränsningar att ta hänsyn till när man hämtar (exporterar) en *.pbix*-fil från Power BI-tjänsten.

* Du måste ha redigeringsåtkomst till rapporten för att kunna hämta filen
* Rapporten måste ha sitt ursprung i **Power BI Desktop** och *publicerats* till **Power BI-tjänsten**, eller så måste .pbix-filen ha *laddats upp* till tjänsten.
* Rapporter måste ha publicerats eller uppdaterats efter den 23 november 2016. Rapporter som publicerats tidigare än så kan inte hämtas.
* Den här funktionen fungerar inte med rapporter som ursprungligen skapades i **Power BI-tjänsten**, inklusive innehållspaket.
* Du bör alltid använda den senaste versionen av **Power BI Desktop** när du öppnar filer som hämtats. Hämtade *.pbix*.filer öppnas inte i gamla versioner av **Power BI Desktop**.
* Om administratören har stängt av möjligheten att exportera data visas den här funktionen inte i **Power BI-tjänsten**.

## <a name="next-steps"></a>Nästa steg
Visa enminutsvideon **Kille i en kub** om den här funktionen:

<iframe width="560" height="315" src="https://www.youtube.com/embed/ymWqU5jiUl0" frameborder="0" allowfullscreen></iframe>

Här följer ytterligare artiklar som kan hjälpa dig att lära känna **Power BI-tjänsten**:

* [Rapporter i Power BI](service-reports.md)
* [Power BI – grundläggande begrepp](service-basic-concepts.md)

När du har installerat **Power BI Desktop** kan du komma igång med hjälp av följande innehåll:

* [Komma igång med Power BI Desktop](desktop-getting-started.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)   

