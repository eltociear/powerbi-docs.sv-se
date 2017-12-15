---
title: Azure SQL Data Warehouse med DirectQuery
description: Azure SQL Data Warehouse med DirectQuery
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 08/10/2017
ms.author: asaxton
ms.openlocfilehash: 0f712763f37df60814d93080c9d0149541b8530c
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="azure-sql-data-warehouse-with-directquery"></a>Azure SQL Data Warehouse med DirectQuery
Med Azure SQL Data Warehouse med DirectQuery kan du skapa dynamiska rapporter baserade på data och mått som du redan har i Azure SQL Data Warehouse. Med DirectQuery skickas frågor tillbaka till din Azure SQL Data Warehouse i realtid medan du utforskar dessa data. Detta i kombination med skalan för SQL Data Warehouse gör att du kan skapa dynamiska rapporter på några få minuter mot flera terabyte av data. Dessutom tillåter införandet av knappen **Öppna i Power BI** användare att ansluta Power BI direkt till SQL Data Warehouse utan att behöva ange informationen manuellt.

När du använder SQL Data Warehouse-anslutningsprogrammet:

* Ange det fullständigt kvalificerade servernamnet vid anslutning (se nedan för information)
* Se till att brandväggsreglerna för servern är konfigurerade för ”Tillåt åtkomst till Azure-tjänster”.
* Varje åtgärd, som att markera en kolumn eller lägga till ett filter, kommer direkt att fråga informationslagret
* Paneler är inställda på att uppdateras ungefär var 15:e minut och uppdatering behöver inte schemaläggas.  Detta kan justeras i Avancerade inställningar när du ansluter.
* Frågor och svar är inte tillgänglig för DirectQuery-datauppsättningar
* schemaändringar plockas inte upp automatiskt

Dessa begränsningar och anteckningar kan ändras när vi fortsätter att förbättra upplevelsen. Nedan beskrivs steget för att ansluta.

## <a name="using-the-open-in-power-bi-button"></a>Använda knappen ”Öppna i Power BI”
Det enklaste sättet att flytta mellan din SQL Data Warehouse och Power BI är med knappen **Öppna i Power BI** i Azure Preview Portal. Med den här knappen kan du sömlöst börja skapa nya instrumentpaneler i Power BI.

1. Kom igång genom att gå till din SQL Data Warehouse-instans i Azure Preview Portal. Observera att SQL Data Warehouse bara finns i Azure Preview Portal just nu.
2. Klicka på knappen **Öppna i Power BI**
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/openinpowerbi.png)
3. Om vi inte kan logga in dig direkt eller om du inte har ett Power BI-konto, behöver du logga in.
4. Du dirigeras till sidan för SQL Data Warehouse-anslutning med informationen från ditt SQL Data Warehouse ifylld. Ange dina autentiseringsuppgifter och tryck på anslut för att skapa en anslutning.

## <a name="connecting-through-power-bi"></a>Ansluta via Power BI
SQL Data Warehouse visas också på sidan Power BI Hämta data. 

1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.  
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/getdatabutton.png)
2. I **Databaser**, välj **Hämta**.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/databases.png)
3. Välj **SQL Data Warehouse** \> **Anslut**.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/azuresqldatawarehouseconnect.png)
4. Ange nödvändig information för att ansluta. Avsnittet **Hitta parametrar** nedan visar var dessa data kan finnas i Azure Portal.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/servername.png)
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/servernamewithadvanced.png)
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/username.png)
   
   > [!NOTE]
   > Användarnamnet ska vara en användare som har definierats i din Azure SQL Data Warehouse-instans.
   > 
   > 
5. Granska datauppsättningen mer detaljerat genom att välja den nya panelen eller den nyligen skapade datauppsättningen som anges med en asterisk. Den här datauppsättningen har samma namn som din databas.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/dataset2.png)
6. Du kan utforska alla tabeller och kolumner. Att markera en kolumn kommer att skicka en fråga till källan, vilket dynamiskt skapar ditt visuella objekt. Filter ska också översättas till frågor tillbaka till ditt informationslager. Detta visuella objekt kan sparas i en ny rapport och fästas igen på instrumentpanelen.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/explore3.png)

## <a name="finding-parameter-values"></a>Hitta parametervärden
Det fullständigt kvalificerade servernamnet och databasnamnet återfinns i Azure Preview Portal. Observera att SQL Data Warehouse bara finns i Azure Preview Portal just nu.

![](media/service-azure-sql-data-warehouse-with-direct-connect/azureportal.png)

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)  
[Hämta data för Power BI](service-get-data.md)  
[Azure SQL Data Warehouse](https://azure.microsoft.com/en-us/documentation/services/sql-data-warehouse/)  
Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

