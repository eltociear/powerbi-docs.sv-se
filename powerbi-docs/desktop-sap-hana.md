---
title: Använd SAP HANA i Power BI Desktop
description: Använd SAP HANA i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/21/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1932848cb2f8ad7d75e841870265cc22308467c2
ms.sourcegitcommit: a00fe5fb545c3df13b7cd13a701fd6a2b2521a17
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/31/2019
ms.locfileid: "70200858"
---
# <a name="use-sap-hana-in-power-bi-desktop"></a>Använd SAP HANA i Power BI Desktop
Med Power BI Desktop kan du nu komma åt **SAP HANA**-databaser. Om du vill använda **SAP HANA**, måste SAP HANA ODBC-drivrutinen installeras på den lokala klientdatorn för att Power BI Desktop **SAP HANA**-dataanslutningen ska fungera korrekt. Du kan hämta SAP HANA ODBC-drivrutinen från [SAP Software Download Center](https://support.sap.com/swdc). Därifrån söker du efter SAP HANA-klienten för Windows-datorer. Eftersom **SAP Software Download Center** ofta ändrar struktur, finns det inte tydligare riktlinjer för att navigera den webbplatsen.

Om du vill ansluta till en **SAP HANA**-databas, väljer du **Hämta data > Databas > SAP HANA-databas** enligt följande bild:

![](media/desktop-sap-hana/sap-hana-1.png)

När du ansluter till en SAP HANA-databas anger du servernamnet. Ange sedan porten i listrutan och indatarutan.

I den här versionen stöds **SAP HANA** i [DirectQuery](desktop-directquery-sap-hana.md)-läge i Power BI Desktop och Power BI-tjänsten och du kan publicera och ladda upp rapporter som använder sig av **SAP HANA** i DirectQuery-läge till Power BI-tjänsten. Du kan även publicera och ladda upp rapporter till Power BI-tjänsten när du inte använder **SAP HANA** i DirectQuery-läge.

## <a name="supported-features-for-sap-hana"></a>Funktioner som stöds för SAP HANA
Den här versionen har många funktioner för **SAP HANA**som visas i listan nedan:

* Anslutningsprogrammet för Power BI för **SAP HANA** använder sig av SAP ODBC-drivrutinen för att tillhandahålla den bästa användarupplevelsen
* **SAP HANA** stöder både alternativen DirectQuery och importera
* Power BI har stöd för HANA-informationsmodeller (t.ex. analys- och beräkningsvyer) och har en optimerad navigering
* Med **SAP HANA** kan du också använda direkt SQL-funktionen för att ansluta till rad- och kolumntabeller
* Inkluderar optimerad navigering för HANA-modeller
* Power BI stöder **SAP HANA**-variabler och indataparametrar
* Vyer för HDI-containerbaserade beräkningsvyer
  * Stödet för HDI-containerbaserade beräkningsvyer finns i en offentlig förhandsversion i augusti 2019-versionen av Power BI Desktop. Om du vill öppna dina HDI-containerbaserade beräkningsvyer i Power BI, kontrollerar du att den/de HANA-databasanvändare som du använder i Power BI har behörighet till HDI-körningscontainern där de vyer som du vill ha åtkomst till finns. För att bevilja åtkomsten måste du skapa en roll som ger åtkomst till din HDI-container och tilldela rollen till den HANA-databasanvändare som du kommer att använda med Power BI (denna användare måste också ha behörighet att läsa från systemtabellerna i \_SYS\_BI-schemat). I den officiella SAP-dokumentationen finns detaljerade anvisningar för hur du skapar och tilldelar databasroller. Det kan vara klokt att börja med [det här SAP-blogginlägget](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fblogs.sap.com%2F2018%2F01%2F24%2Fthe-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user%2F&data=02%7C01%7Cv-adbold%40microsoft.com%7Cf7e0a405fe334598ba0608d7096ef5b4%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636988244476739316&sdata=PuRu61GPRYp34mLuGbQk6gdbRikdgbxfqo8q1RBQtm0%3D&reserved=0).
  * Observera att det för närvarande finns vissa begränsningar för HANA-variabler som är kopplade till HDI-baserade beräkningsvyer. De här begränsningarna beror på fel på HANA-sidan och kommer att åtgärdas i framtida versioner av SAP HANA. För det första är det inte möjligt att tillämpa en HANA-variabel på en delad kolumn i en HDI-containerbaserad beräkningsvy. Den här begränsningen kan åtgärdas genom att uppgradera till HANA 2 version 37.02 och senare, eller HANA 2 version 42 och senare. För det andra visas inte standardvärden med flera poster för variabler och parametrar i Power BI-gränssnittet. Detta beror också på ett fel i SAP HANA, men SAP har ännu inte meddelat när detta ska åtgärdas.

## <a name="limitations-of-sap-hana"></a>Begränsningar för SAP HANA
Det finns några begränsningar med att använda **SAP HANA** som visas nedan:

* NVARCHAR-strängar trunkeras till högst 4 000 Unicode-tecken
* SMALLDECIMAL stöds inte
* VARBINARY stöds inte
* Giltiga datum är mellan 1899-12-30 och 9999-12-31


## <a name="next-steps"></a>Nästa steg
Mer information om DirectQuery och SAP HANA finns i följande resurser:

* [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery](desktop-directquery-data-sources.md)
* [Aktivera kryptering för SAP HANA](desktop-sap-hana-encryption.md)


