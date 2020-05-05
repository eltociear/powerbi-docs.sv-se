---
title: Anslut till en Oracle-databas
description: Steg och hämtningsbara filer som krävs för att ansluta Oracle till Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a118cd0874410e538ca8329e0b8c0ed1bdb430b7
ms.sourcegitcommit: 834cad24901f7fd966c4010e36a7904bc120e57f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/24/2020
ms.locfileid: "82149601"
---
# <a name="connect-to-an-oracle-database"></a>Anslut till en Oracle-databas
Anslutning till en Oracle-databas med Power BI Desktop kräver att rätt Oracle-klientprogramvara är installerad på den dator som kör Power BI Desktop. Den Oracle-klientprogramvara du använder beror på vilken version av Power BI Desktop som du har installerat: 32-bitars eller 64-bitars.

Oracle-versioner som stöds: 
- Oracle 9 och senare
- Oracle klientprogramvara 8.1.7 och senare

> [!NOTE]
> Om du konfigurerar en Oracle-databas för Power BI-rapportserver kan du läsa informationen i artikeln [Oracle-anslutningstyp](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15). 


## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Så här fastställer du vilken version av Power BI Desktop som är installerad
För att kontrollera vilken version av Power BI Desktop som är installerad väljer du **Arkiv** > **Hjälp** > **Om** och läser sedan raden **Version**. I följande bild är en 64-bitarsversion av Power BI Desktop installerad:

![Power BI Desktop-version](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Installera klienten för Oracle
- För 32-bitarsversionen av Power BI Desktop [laddar du ned och installerar 32-bitars Oracle-klient](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html).

- För 64-bitarsversionen av Power BI Desktop [laddar du ned och installerar 64-bitars Oracle-klient](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html).

## <a name="connect-to-an-oracle-database"></a>Anslut till en Oracle-databas
När du har installerat den matchande Oracle-klientdrivrutinen kan du ansluta till en Oracle-databas. Vidta följande steg för att upprätta anslutningen:

1. På fliken **Start** väljer du **Hämta data**. 

2. I fönstret **Hämta data** som visas väljer du **Mer** (om det behövs) och väljer **Databas** > **Oracle-databas** följt av **Anslut**.
   
   ![Anslutning till Oracle-databas](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. I dialogrutan **Oracle-databas** som visas anger du namnet på **Server** och väljer **OK**. Om det krävs ett SID anger du det med formatet: *Servernamn/SID*, där *SID* är det unika namnet på databasen. Om formatet *Servernamn/SID* inte fungerar använder du *Servernamn/tjänstnamn*, där *tjänstnamn* är det alias som du använder för att ansluta.


   ![Ange Oracle-servernamn](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > Om det är problem med att ansluta i det här steget provar du följande format i fältet **Server**: *(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))*
   
3. Om du vill importera data med hjälp av en intern databasfråga anger du frågan i rutan **SQL-instruktion**, som visas när du expanderar avsnittet **Avancerade alternativ** i dialogrutan **Oracle-databas**.
   
   ![Expandera Avancerade alternativ](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. När du har angett informationen för Oracle-databas i dialogrutan **Oracle-databas** (inklusive eventuell valfri information såsom ett SID eller en intern databasfråga) väljer du **OK** för att ansluta.
5. Ange autentiseringsuppgifterna i dialogrutan när du uppmanas om Oracle-databasen kräver autentiseringsuppgifter för databasen.


## <a name="troubleshooting"></a>Felsökning

Om du har laddat ned Power BI Desktop från Microsoft Store kanske du inte kan ansluta till Oracle-databaser på grund av ett problem med en Oracle-drivrutin. Om du påträffar det här problemet returneras följande felmeddelande: *Ingen objektreferens har angetts*. Åtgärda problemet med något av följande steg:

* Ladda ned Power BI Desktop från [Download Center](https://www.microsoft.com/download/details.aspx?id=58494) i stället för Microsoft Store.

* Om du vill använda versionen från Microsoft Store kopierar du oraons.dll från _12.X.X\client_X_ till _12.X.X\client_X\bin_. Här utgör _X_ versions- och katalognummer.

Om felmeddelandet *Ingen objektreferens har angetts* visas i Power BI Gateway när du ansluter till en Oracle-databas följer du anvisningarna i [Hantera din datakälla – Oracle](service-gateway-onprem-manage-oracle.md).

Om du använder Power BI-rapportservern kan du läsa mer i artikeln [Oracle-anslutningstyp](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15).