---
title: Anslut till en Oracle-databas
description: Steg och hämtningsbara filer som krävs för att ansluta Oracle till Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 826338a5e5524bb54c2ebb2207a3d438a8d428b1
ms.sourcegitcommit: 3c8196be5626a0f037599abb6ccbd294fb1249df
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54899237"
---
# <a name="connect-to-an-oracle-database"></a>Anslut till en Oracle-databas
För att ansluta till en Oracle-databas med **Power BI Desktop** måste rätt Oracle-klientprogramvara vara installerad på datorn med Power BI Desktop. Vilken Oracle-klientprogramvaran som du använder beror på vilken version av Power BI Desktop som du har installerat – **32-bitars**-versionen eller **64-bitars**-versionen.

**Versioner som stöds**: Oracle 9 och senare, Oracle-klientprogramvaran 8.1.7 och senare.

## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Så här fastställer du vilken version av Power BI Desktop som är installerad
För att kontrollera vilken version av Power BI Desktop som är installerad väljer du **Arkiv > Hjälp > Om** och kontrollerar raden **Version:**. I följande bild är en 64-bitarsversion av Power BI Desktop installerad:

![](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Installera klienten för Oracle
För **32-bitars** versionen av Power BI Desktop använder du följande länk för att hämta och installera **32-bitars** Oracle-klient:

* [32-bitars Oracle Data Access Components (ODAC) med Oracle Developer Tools för Visual Studio (12.1.0.2.4)](http://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

För **64-bitars** versionen av Power BI Desktop använder du följande länk för att hämta och installera **64-bitars** Oracle-klient:

* [64-bitars ODAC 12c version 4 (12.1.0.2.4) för Windows x64](http://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

## <a name="connect-to-an-oracle-database"></a>Anslut till en Oracle-databas
När den matchande Oracle-klientdrivrutinen har installerats kan du ansluta du till en Oracle-databas. Vidta följande steg för att upprätta anslutningen:

1. I fönstret hämta data markerar du **Databasen > Oracle-databas**
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. I dialogrutan **Oracle-databas** som visas, ange namnet på servern och välj **Anslut**. Om det krävs ett SID kan du ange det med formatet: *Servernamn/SID*, där SID är det unika namnet på databasen. Om formatet *Servernamn/SID* inte fungerar, försöker du med *Servernamn/tjänstnamn*, där tjänstnamn är det alias som används vid anslutning.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_3.png)
3. Om du vill importera data med hjälp av en intern databasfråga anger du din fråga i **SQL-instruktionen** genom att expandera området **Avancerade alternativ** i dialogrutan **Oracle-databas**.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. När din information för Oracle-databas har angetts i dialogrutan för Oracle-databasen (inklusive eventuell frivillig information, till exempel ett SID eller en intern databasfråga) väljer du **OK** för att ansluta.
5. Ange autentiseringsuppgifterna i dialogrutan när du uppmanas om Oracle-databasen kräver autentiseringsuppgifter för databasen.


## <a name="troubleshooting"></a>Felsökning

Om du har laddat ned Power BI Desktop från Microsoft Store kanske du inte kan ansluta till Oracle-databaser på grund av ett problem med en Oracle-drivrutin. Om du påträffar det här problemet visas ett felmeddelande om att objektreferensen inte har angetts. Gör något av följande för att hantera det här problemet:

* Ladda ned Power BI Desktop från https://powerbi.microsoft.com/desktop istället.

* Om du vill använda versionen från Microsoft Store kopierar du oraons.dll från _12.X.X\client_X_ till _12.X.X\client_X\bin_ på din lokala dator. X representerar versions-och katalognummer.
