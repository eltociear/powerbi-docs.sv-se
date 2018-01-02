---
title: "Använd SAP HANA i Power BI Desktop"
description: "Använd SAP HANA i Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 9cbeb0b2504612a9eb32fdad1d95fd90b57e07d9
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/06/2017
---
# <a name="use-sap-hana-in-power-bi-desktop"></a>Använd SAP HANA i Power BI Desktop
Med Power BI Desktop kan du nu komma åt **SAP HANA**-databaser. Om du vill använda **SAP HANA**, måste SAP HANA ODBC-drivrutinen installeras på den lokala klientdatorn för att Power BI Desktop **SAP HANA**-dataanslutningen ska fungera korrekt. Du kan hämta SAP HANA ODBC-drivrutinen från [SAP Software Download Center](https://support.sap.com/swdc). Därifrån söker du efter SAP HANA-klienten för Windows-datorer. Eftersom **SAP Software Download Center** ofta ändrar struktur, finns det inte tydligare riktlinjer för att navigera den webbplatsen.

Om du vill ansluta till en **SAP HANA**-databas, väljer du **Hämta data > Databas > SAP HANA-databas** enligt följande bild.

![](media/desktop-sap-hana/sap-hana-1.png)

När du ansluter till en SAP HANA-databas, anger du servernamnet och porten i formatet *server:port*. Följande bild visar ett exempel på en server med namnet *ServerXYZ* och port *30015*.

![](media/desktop-sap-hana/sap-hana-2.png)

I den här versionen stöds **SAP HANA** i [DirectQuery](desktop-use-directquery.md)-läge i Power BI Desktop och Power BI-tjänsten och du kan publicera och ladda upp rapporter som använder sig av **SAP HANA** i DirectQuery-läge till Power BI-tjänsten. Du kan även publicera och ladda upp rapporter till Power BI-tjänsten när du inte använder **SAP HANA** i DirectQuery-läge.

### <a name="supported-features-for-sap-hana"></a>Funktioner som stöds för SAP HANA
Den här versionen har många funktioner för **SAP HANA**som visas i listan nedan:

* Anslutningsprogrammet för Power BI för **SAP HANA** använder sig av SAP ODBC-drivrutinen för att tillhandahålla den bästa användarupplevelsen
* **SAP HANA** stöder både alternativen DirectQuery och importera
* Powerbi stöder HANA-informationsmodeller (som Analytic- och Calc-vyer) och har optimerad navigering
* Med **SAP HANA** kan du också använda direkt SQL-funktionen för att ansluta till rad- och kolumntabeller
* Inkluderar optimerad navigering för HANA-modeller
* Power BI stöder **SAP HANA**-variabler och indataparametrar

### <a name="installing-the-sap-hana-odbc-driver"></a>Installera SAP HANA ODBC-drivrutinen
### <a name="limitations-of-sap-hana"></a>Begränsningar för SAP HANA
Det finns några begränsningar med att använda **SAP HANA** som visas nedan:

* NVARCHAR-strängar trunkeras till högst 4 000 Unicode-tecken
* SMALLDECIMAL stöds inte
* VARBINARY stöds inte
* Giltiga datum är mellan 1899-12-30 och 9999-12-31

