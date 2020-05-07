---
title: Hämta data från filer med kommaavgränsade värden (.csv)
description: Läs hur du hämtar data från CSV-filer till Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: a33c8a45f4f32efb0a47df82b8af23d42c281ae9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73855531"
---
# <a name="get-data-from-comma-separated-value-csv-files"></a>Hämta data från filer med kommaavgränsade värden (.csv)
![](media/service-comma-separated-value-files/csv_icon.png)

Filer med kommaavgränsade värden, ofta kallade .CSV-filer, är enkla textfiler med rader med data där varje värde är avgränsat med ett kommatecken. Dessa typer av filer kan innehålla mycket stora mängder data på en relativt liten storlek, vilket gör dem till en perfekt datakälla för Power BI. Du kan hämta en exempel-.CSV-fil [här](https://go.microsoft.com/fwlink/?LinkID=619356).

Om du har en .CSV, är det dags att få in den i din Power BI-plats som en datauppsättning där du kan börja utforska dina data, skapa instrumentpaneler och dela dina insikter med andra.

>[!TIP]
>Många organisationer skapar .CSV-filer med uppdaterade data varje dag. Kontrollera att din datauppsättning i Power BI håller sig synkroniserad med din uppdaterade fil, se till att den sparas till OneDrive med samma namn.

## <a name="where-your-file-is-saved-makes-a-difference"></a>Det spelar roll var du sparar filen
**Lokalt** – Om du sparar din .csv-fil till en lokal enhet på datorn eller en annan plats inom din organisation, från Power BI så kan du *importera* den till Power BI. Filen kommer att finnas kvar på den lokala enheten, så hela filen har i själva verket inte importerats till Power BI. Det som händer är att en ny datauppsättning skapas i Power BI och data .CSV-filen läses in i datauppsättningen.

**OneDrive företag**  – om du har OneDrive för företag och du loggar in med samma konto som du använder för Power BI, är detta det mest effektiva sättet att behålla din .CSV-fil och din datauppsättning, rapporter och instrumentpaneler i Power BI synkroniserade. Eftersom både Power BI och OneDrive finns i molnet, *ansluter* Power BI till din fil på OneDrive någon gång i timmen. Om det finns ändringar uppdateras dina datauppsättningar, rapporter och instrumentpaneler i Power BI automatiskt.

**OneDrive – personlig** – Om du sparar filer på ditt eget OneDrive-konto får du många av de fördelar som du får med OneDrive för företag. Den största skillnaden är att när du ansluter till din fil (med Hämta data > Filer > OneDrive – personlig) måste du logga in på ditt OneDrive med ditt Microsoft-konto som vanligtvis skiljer sig från det du använder för att logga in på Power BI. När du loggar in på din OneDrive med ditt Microsoft-konto, se till att du har alternativet jag vill förbli inloggad markerat. På så sätt kan Power BI ansluta till din fil ungefär en gång i timmen och kontrollera att din datauppsättning i Power BI är synkroniserad.

**SharePoint-gruppwebbplatser** – Du sparar Power BI Desktop-filer på SharePoint-gruppwebbplatser ungefär på samma sätt som på OneDrive för företag. Den största skillnaden är hur du ansluter till filen från Power BI. Du kan ange en URL eller ansluta till rotmappen.

## <a name="import-or-connect-to-a-csv-file"></a>Importera eller anslut till en .CSV-fil
>[!IMPORTANT]
>Maximal filstorlek som du kan importera till Power BI är 1 GB.

1. I Power BI i navigeringsfönstret, klickar du på **hämta data**.
   
   ![](media/service-comma-separated-value-files/csv_get_data_button.png)
2. I **filer**, klickar du på **hämta**.
   
   ![](media/service-comma-separated-value-files/csv_files_get.png)
3. Hitta din fil.
   
   ![](media/service-comma-separated-value-files/csv_find_your_file.png)

## <a name="next-steps"></a>Nästa steg
**Utforska dina data** – när du hämtat in data från din fil till Power BI är det dags att börja utforska. Högerklicka bara på den nya datauppsättningen och klicka sedan på **utforska**.

**Schemalägg uppdatering** – om filen sparas till en lokal enhet, kan du konfigurera schemalagd uppdatering så din datauppsättning och rapporter i Power BI kan hålla sig uppdaterade. Läs mer i [datauppdatering i Power BI](refresh-data.md). Om din fil sparas till OneDrive, synkroniseras den automatiskt av Power BI ungefär varje timme.

