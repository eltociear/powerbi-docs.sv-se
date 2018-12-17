---
title: 'Fel: Det gick inte att hitta några data i din Excel-arbetsbok'
description: 'Fel: Det gick inte att hitta några data i din Excel-arbetsbok'
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: ea5312178d33986ebc3f4b9e8610012c87d54216
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53026041"
---
# <a name="error-we-couldnt-find-any-data-in-your-excel-workbook"></a>Fel: Det gick inte att hitta några data i din Excel-arbetsbok

>[!NOTE]
>Den här artikeln gäller för Excel 2007 och senare.

När du importerar en Excel-arbetsbok till Power BI kan du se följande fel:

*Fel: Det gick inte att hitta några data i din Excel-arbetsbok. Dina data är kanske inte korrekt formaterade. Du behöver redigera din arbetsbok i Excel och sedan importera den igen.*

![Det gick inte att hitta data i arbetsboken](media/service-admin-troubleshoot-excel-workbook-data/pbi_wecouldntfindanydata.png)

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
    
    ![Öppna arbetsboken](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht1.png)
2. Välj cellområdet som innehåller dina data. Den första raden ska innehålla dina kolumnrubriker (kolumnnamnen):
   
    ![Markera ett cellintervall](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht2.png)
3. I menyfliksområdet på fliken **infoga**, klickar du på **tabell**. (Eller, som ett kortkommando, trycker du på **Ctrl + T**.)
   
    ![Infoga en tabell](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht3.png)
4. Du ser följande dialogruta. Kontrollera att **min tabell har rubriker** är markerat och välj **Ok**:
   
    ![Skapa en tabell](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlcreatetbl.png)
5. Nu är dina data formaterade som en tabell:
   
    ![Data formaterade som en tabell](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xltbl.png)
6. Spara din arbetsbok.
7. Gå tillbaka till Power BI. Välj Hämta data längst ned i det vänstra navigeringsfönstret.
   
    ![Hämta data](media/service-admin-troubleshoot-excel-workbook-data/pbi_getdata.png)
8. I rutan **Filer** väljer du **Hämta**.
   
    ![Hämta filer](media/service-admin-troubleshoot-excel-workbook-data/pbi_getfiles.png)
9. Importera din Excel-arbetsbok igen. Den här gången borde importen hitta tabellen och lyckas.
   
    Om importen fortfarande misslyckas, berättar du för oss genom att klicka på **Community ** i hjälp-menyn:
   
    ![Community-länk](media/service-admin-troubleshoot-excel-workbook-data/pbi_questionmenucommunity.png)
