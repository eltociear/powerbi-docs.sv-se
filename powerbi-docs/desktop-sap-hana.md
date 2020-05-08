---
title: Använd SAP HANA i Power BI Desktop
description: Använda SAP HANA i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9b205a0ae9b58acf054a9afe43196e77ee404c84
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76753135"
---
# <a name="connect-to-sap-hana-databases-in-power-bi-desktop"></a>Ansluta till SAP HANA-databaser i Power BI Desktop

Med Power BI Desktop kan du nu komma åt *SAP HANA*-databaser. Om du vill använda SAP HANA måste SAP HANA ODBC-drivrutinen vara installerad på den lokala klientdatorn för att SAP HANA-dataanslutningen i Power BI Desktop ska fungera korrekt. Du kan ladda ned SAP HANA-klientverktyg från [SAP Development Tools](https://tools.hana.ondemand.com/#hanatools), där den ODBC-drivrutin som krävs finns. Du kan även hämta den från [SAP Software Download Center](https://support.sap.com/en/my-support/software-downloads.html). I programvaruportalen söker du efter *SAP HANA CLIENT* för Windows-datorer. Eftersom SAP Software Download Center ofta ändrar struktur finns det inga specifika riktlinjer för att navigera på den webbplatsen.

Om du vill ansluta till en SAP HANA-databas väljer du **Hämta data** följt av **Databas** > **SAP HANA-databas** och därefter **Anslut**:

![SAP HANA-databas, dialogrutan Hämta data, Power BI Desktop](media/desktop-sap-hana/sap-hana-1.png)

När du ansluter till en SAP HANA-databas anger du servernamnet. Ange sedan porten i listrutan och indatarutan.

I den här versionen stöds SAP HANA i [DirectQuery](desktop-directquery-sap-hana.md)-läge i Power BI Desktop och i Power BI-tjänsten. Du kan publicera och ladda upp rapporter som använder SAP HANA i DirectQuery-läge till Power BI-tjänsten. Du kan även publicera och ladda upp rapporter till Power BI-tjänsten när du inte använder SAP HANA i DirectQuery-läge.

## <a name="supported-features-for-sap-hana"></a>Funktioner som stöds för SAP HANA

Den här versionen har många funktioner för SAP HANA som visas i listan nedan:

* Power BI-anslutningsprogrammet för SAP HANA använder SAP ODBC-drivrutinen för att tillhandahålla den bästa användarupplevelsen.

* SAP HANA stöder både DirectQuery- och importalternativ.

* Power BI har stöd för HANA-informationsmodeller, till exempel analys- och beräkningsvyer och har optimerad navigering.

* Med SAP HANA kan du även använda SQL-direktfunktionen för att ansluta till rad- och kolumntabeller.

* Power BI inkluderar optimerad navigering för HANA-modeller.

* Power BI stöder SAP HANA-variabler och indataparametrar.

* Power BI stöder HDI-containerbaserade beräkningsvyer.

  * Stödet för HDI-containerbaserade beräkningsvyer finns i en offentlig förhandsversion i augusti 2019-versionen av Power BI Desktop. Om du vill öppna dina HDI-containerbaserade beräkningsvyer i Power BI kontrollerar du att de HANA-databasanvändare som du använder i Power BI har behörighet till den HDI-körningscontainer där de vyer som du vill ha åtkomst till finns. Om du vill bevilja den här åtkomsten skapar du en roll som tillåter åtkomst till din HDI-container. Tilldela sedan rollen till den HANA-databasanvändare som du kommer att använda med Power BI. (Den här användaren måste även ha behörighet att läsa från systemtabellerna i \_SYS\_BI-schemat, som vanligt.) I den officiella SAP-dokumentationen finns detaljerade anvisningar för hur du skapar och tilldelar databasroller. Det kan vara klokt att börja med [det här SAP-blogginlägget](https://blogs.sap.com/2018/01/24/the-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user/).

  * För närvarande finns det vissa begränsningar för HANA-variabler som är kopplade till HDI-baserade beräkningsvyer. De här begränsningarna beror på fel i HANA.
  
    För det första går det inte att tillämpa en HANA-variabel på en delad kolumn i en HDI-containerbaserad beräkningsvy. Du kan åtgärda den här begränsningen genom att uppgradera till HANA 2 version 37.02 och senare eller HANA 2 version 42 och senare. För det andra visas inte standardvärden med flera poster för variabler och parametrar i Power BI-gränssnittet. Ett fel i SAP HANA orsakar den här begränsningen, men SAP har inte meddelat någon korrigering ännu.

## <a name="limitations-of-sap-hana"></a>Begränsningar för SAP HANA

Det finns även vissa begränsningar med användning av SAP HANA, som visas nedan:

* NVARCHAR-strängar trunkeras till högst 4000 Unicode-tecken.
* SMALLDECIMAL stöds inte.
* VARBINARY stöds inte.
* Giltiga datum är mellan 1899-12-30 och 9999-12-31.

## <a name="next-steps"></a>Nästa steg

Mer information om DirectQuery och SAP HANA finns i följande resurser:

* [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)
* [Använda DirectQuery i Power BI](desktop-directquery-about.md)
* [Power BI-datakällor](power-bi-data-sources.md)
* [Aktivera kryptering för SAP HANA](desktop-sap-hana-encryption.md)
