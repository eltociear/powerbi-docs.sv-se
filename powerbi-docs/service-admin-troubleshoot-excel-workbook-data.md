---
title: 'Fel: Det gick inte att hitta några data i din Excel-arbetsbok'
description: 'Fel: Det gick inte att hitta några data i din Excel-arbetsbok'
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 04/30/2019
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 1976567029454445f625ff400fb1d87ae6c01219
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74698427"
---
# <a name="error-we-couldnt-find-any-data-in-your-excel-workbook"></a>Fel: Det gick inte att hitta några data i din Excel-arbetsbok

>[!NOTE]  
>Den här artikeln gäller för Excel 2007 och senare.

När du importerar en Excel-arbetsbok till Power BI kan du se följande fel:

*Fel: Det gick inte att hitta några data som är formaterade som en tabell. För att importera från Excel till Power BI-tjänsten behöver du formatera data som en tabell. Markera alla data som du vill använda i tabellen och tryck på CTRL + T.*

![Det gick inte att hitta data i arbetsboken](media/service-admin-troubleshoot-excel-workbook-data/power-bi-we-couldnt-find-any-data.png)

## <a name="quick-solution"></a>Snabblösning
1. Redigera din arbetsbok i Excel.
2. Välj cellområdet som innehåller dina data. Den första raden ska innehålla kolumnrubrikerna (kolumnnamnen).
3. Tryck på **Ctrl + T** för att skapa en tabell.
4. Spara din arbetsbok.
5. Gå tillbaka till Power BI och importera arbetsboken igen, eller om du arbetar i Excel 2016 och du har sparat din arbetsbok på OneDrive för företag, klickar du på fil > publicera i Excel.

## <a name="details"></a>Information
### <a name="cause"></a>Orsak
I Excel, kan du skapa en **tabell** från ett cellområde, vilket gör det enklare att sortera, filtrera och formatera data.

När du importerar en Excel-arbetsbok, letar Power BI efter dessa tabeller och importerar dem till en datauppsättning. Om den inte hittar några tabeller, visas detta felmeddelande.

### <a name="solution"></a>Lösning
1. Öppna din arbetsbok i Excel. 
    >[!NOTE]
    >De här bilderna är från Excel 2013. Om du använder en annan version, kan saker se något annorlunda ut, men stegen är desamma.
    
    ![Öppna arbetsboken](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-1.png)
2. Välj cellområdet som innehåller dina data. Den första raden ska innehålla dina kolumnrubriker (kolumnnamnen):
   
    ![Markera ett cellintervall](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-2.png)
3. I menyfliksområdet på fliken **infoga**, klickar du på **tabell**. (Eller, som ett kortkommando, trycker du på **Ctrl + T**.)
   
    ![Infoga en tabell](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-3.png)
4. Du ser följande dialogruta. Kontrollera att **min tabell har rubriker** är markerat och välj **Ok**:
   
    ![Skapa en tabell](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-create-table.png)
5. Nu är dina data formaterade som en tabell:
   
    ![Data formaterade som en tabell](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-table.png)
6. Spara din arbetsbok.
7. Gå tillbaka till Power BI. Välj Hämta data längst ned i navigeringsfönstret.
   
    ![Hämta data](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-data.png)
8. I rutan **Filer** väljer du **Hämta**.
   
    ![Hämta filer](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-files.png)
9. Importera din Excel-arbetsbok igen. Den här gången borde importen hitta tabellen och lyckas.
   
    Om importen fortfarande misslyckas, berättar du för oss genom att klicka på **Community ** i hjälp-menyn:
   
    ![Community-länk](media/service-admin-troubleshoot-excel-workbook-data/power-bi-question-menu-community.png)
