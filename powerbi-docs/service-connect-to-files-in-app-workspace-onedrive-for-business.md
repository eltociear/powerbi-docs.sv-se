---
title: "Anslut till filer i OneDrive för en Power BI-apparbetsyta"
description: "Läs mer om att lagra och ansluta till dina Excel-, CSV- och Power BI Desktop-filer på OneDrive för din Power BI-apparbetsyta."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: maggies
ms.openlocfilehash: fae3fb4e9ca6b6013538d0cb223909aea6c88271
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="connect-to-files-stored-in-onedrive-for-your-power-bi-app-workspace"></a>Anslut till filer som lagras i OneDrive för din Power BI-apparbetsyta
När du har [skapat en apparbetsyta i Power BI](service-create-distribute-apps.md), kan du lagra dina Excel-, CSV-, och Power BI Desktop-filer på OneDrive för företag för din Power BI-apparbetsyta. Du kan fortsätta att uppdatera de filer som du lagrar i OneDrive och de uppdateringarna visas automatiskt i Power BI-rapporter och instrumentpaneler som baseras på filerna. 

Att lägga till filer i din apparbetsyta är en tvåstegsprocess: 

1. Först [laddar du upp filer till OneDrive för företag](service-connect-to-files-in-app-workspace-onedrive-for-business.md#1-upload-files-to-the-onedrive-for-business-for-your-app-workspace) för din apparbetsyta.
2. Sedan [ansluter du till dessa filer från Power BI](service-connect-to-files-in-app-workspace-onedrive-for-business.md#2-import-excel-files-as-datasets-or-as-excel-online-workbooks).

> [!NOTE]
> Apparbetsytor är bara tillgängliga med [Power BI Pro](service-free-vs-pro.md).
> 
> 

## <a name="1-upload-files-to-the-onedrive-for-business-for-your-app-workspace"></a>1 Ladda upp filer till OneDrive för företag för din apparbetsyta
1. I Power BI-tjänsten väljer du pilen bredvid Arbetsytor > och väljer ellipsen (**…**) bredvid namnet på din arbetsyta. 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-ellipsis.png)
2. Välj **filer** för att öppna OneDrive för företag för din apparbetsyta i Office 365.
   
   > [!NOTE]
   > Om du inte ser **filer** överst i menyn för apparbetsytan, väljer du **medlemmar** för att öppna OneDrive för företag för din apparbetsyta. Där väljer du **filer**. Office 365 ställer in en lagringsplats för OneDrive för din apps filer för grupparbetsytan. Den här processen kan ta lite tid. 
   > 
   > 
3. Här kan du överföra dina filer till OneDrive för företag för din apparbetsyta. Välj **överför**, och navigera till dina filer.
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grpfilesonedrive.png)

## <a name="2-import-excel-files-as-datasets-or-as-excel-online-workbooks"></a>2 importera Excel-filer som datauppsättningar eller som Excel Online-arbetsböcker
Nu när dina filer finns i OneDrive för företag för din apparbetsyta, har du ett val. Du kan: 

* [Importera data från Excel-arbetsboken som en datauppsättning](service-get-data-from-files.md) och använda data för att skapa rapporter och instrumentpaneler som du kan visa i en webbläsare och på mobila enheter.
* Eller [ansluta till en hel Excel-arbetsbok i Power BI](service-excel-workbook-files.md) och visa den exakt som den visas i Excel Online.

### <a name="import-or-connect-to-the-files-in-your-app-workspace"></a>Importera eller anslut till filer i din app-arbetsyta
1. I Power BI växlar du till apparbetsytan så att apparbetsytans namn är i det övre vänstra hörnet i Power BI. 
2. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret. 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-get-data-button.png)
3. I rutan **Filer** väljer du **Hämta**.
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_getfiles.png)
4. Välj **OneDrive** - *apparbetsytans namn*.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grp_one_drive_shrpt.png)
5. Välj den fil du vill > **ansluta**.
   
    Det är nu du väljer om du vill [importera data från Excel-arbetsboken](service-get-data-from-files.md), eller [ansluta till hela Excel-arbetsboken](service-excel-workbook-files.md).
6. Välj **importera** eller **anslut**.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_importexceldataorwholecrop.png)
7. Om du väljer **imporera** så visas arbetsboken i fliken **datauppsättningar**. 
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-import.png)
   
    Om du väljer **anslut** så visas arbetsboken i fliken **arbetsböcker**.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-connect.png)

## <a name="next-steps"></a>Nästa steg
* [Skapa appar och apparbetsytor i Power BI](service-create-distribute-apps.md)
* [Importera data från Excel-arbetsböcker](service-get-data-from-files.md)
* [Ansluta till hela Excel-arbetsböcker](service-excel-workbook-files.md)
* Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)
* Feedback? Besök [Power BI-idéer](https://ideas.powerbi.com/forums/265200-power-bi)

