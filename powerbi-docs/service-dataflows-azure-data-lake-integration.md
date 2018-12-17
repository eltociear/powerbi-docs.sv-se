---
title: Dataflöden och Azure Data Lake-integrering
description: Översikt över hur Power BI-dataflöden integrerar med Azure Data Lake Storage Gen2
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/10/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 09f001edc787d50db1de3291c483374948e50d66
ms.sourcegitcommit: f25464d5cae46691130eb7b02c33f42404011357
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2018
ms.locfileid: "53181712"
---
# <a name="dataflows-and-azure-data-lake-integration-preview"></a>Dataflöden och Azure Data Lake-integrering (förhandsversion)

Som standard lagras data som används med Power BI i intern lagring som tillhandahålls av Power BI. Med integreringen av dataflöden och Azure Data Lake Storage Gen2 (ADLS Gen2) kan du lagra dina dataflöden på din organisations Azure Data Lake Storage Gen2 konto. 

![Dataflöden i Azure Storage](media/service-dataflows-azure-data-lake-integration/dataflows-azure-integration_01.jpg)

> [!NOTE]
> Dataflödesfunktionen är en förhandsversion och kan komma att ändras och uppdateras innan den är allmänt tillgänglig.

## <a name="how-cdm-folders-relate-to-dataflows"></a>Hur CDM-mappar relaterar till dataflöden

Med **dataflöden** kan användare och organisationer samla data från olika källor och förbereda dem för modellering. Med i Common Data Model (CDM) kan organisationer använda ett dataformat som tillhandahåller semantisk konsekvens i alla program och distributioner. Och med Azure Data Lake Storage gen2 (ADLS Gen2) kan detaljerad kontroll av åtkomst och auktorisering tillämpas på data lakes i Azure. I kombination ger de här elementen övertygande centraliserade data, strukturerade data, detaljerad åtkomstkontroll och semantisk konsekvens för appar och initiativ i hela företaget.

Data som lagras i CDM-format har semantisk konsekvens i alla program och distributioner i en organisation. Med CDM-integrering med ADLS Gen2 kan samma strukturella konsekvens och semantiska betydelse tillämpas på data som lagras i (ADLS Gen2) med hjälp av CDM-mappar som innehåller schematiserade data i CDM-standardformat. Standardiserade metadata och självbeskrivande data i en Azure Data Lake möjliggör enkel metadataidentifiering och interoperation mellan dataproducenter och konsumenter som Power BI, Azure Data Factory, Azure Data Lake, Databricks och Azure Machine Learning (ML). 

Dataflöden lagrar sin definition och sina data i CDM-mappar i följande format:

**Model.json**
* **Model.json**-beskrivningsfilen med metadata innehåller semantisk information om entitetsposter och attribut och länkar till underliggande datafiler. Förekomsten av model.json-filen anger efterlevnad med CDM-metadataformat och kan innehålla standardentiteter som har ytterligare omfattande färdiga semantiska metadata som program kan använda.
* PowerBI lagrar också information om varje datakälla tillsammans med den **fråga och transformeringar** som genereras av redigeringsprogrammet för dataflöden i Power BI-tjänsten. Lösenord till datakällorna lagras inte i modellfilen.

**Datafiler**
* Datafilerna läggs i CDM-mappen i en väldefinierad struktur och ett välordnat format (undermappar är valfria, enligt beskrivningen nedan) och refereras i model.json-filen. För närvarande datafiler måste vara i CSV-format, men ytterligare format kan komma att stödjas i efterföljande uppdateringar. 

Följande diagram visar ett exempel på en CDM-mapp som skapats av ett Power BI-dataflöde, med tre enheter:

![Dataflöden i Azure Storage](media/service-dataflows-azure-data-lake-integration/dataflows-azure-integration_01.jpg)

Filen model.json eller metadatafilen i föregående bild skulle ange hänvisningar till enhetsdatafiler i hela CDM-mappen.

## <a name="power-bi-organizes-cdm-folders-in-the-data-lake"></a>Power BI organiserar CDM-mappar i en data lake

Med Power BI-dataflöden och dess integration med ADLS Gen2 kan Power BI producera data i en data lake. Som dataproducent måste Power BI skapa en CDM-mapp för varje dataflöde som innehåller model.json-filen och dess associerade datafiler. Power BI lagras sina data isolerade från andra dataproducenter i en data lake med hjälp av *filsystem*. Du kan läsa mer om filsystem och hierarkisk namnrymd i Azure Data Lake Storage Gen2 i [den artikel som beskriver dem](https://docs.microsoft.com/azure/storage/data-lake-storage/namespace).

Power BI använder undermappar för tvetydigheter och för att organisera bättre data när de visas i **Power BI-tjänsten**. Mappnamnen och -strukturen representerar arbetsytor (mappar) och dataflöden (CDM-mappar). Följande diagram visar hur en data lake som delas av Power BI och andra dataproducenter kan struktureras. Varje tjänst, i det här fallet Dynamics 365, Dynamics for Finance and Operation och Power BI, skapar och upprätthåller sina egna filsystem. Beroende på upplevelsen i varje tjänst skapas undermappar för att organisera CDM-mappar på ett bättre sätt i filsystemet. 

![dataflöden från olika tjänster i Azure-lagring](media/service-dataflows-azure-data-lake-integration/dataflows-azure-integration_02.jpg)

## <a name="power-bi-protects-data-in-the-data-lake"></a>Power BI skyddar data i en data lake

Power BI använder *Active Directory OAuth Bearer*-tokens och funktioner för *POSIX-åtkomstkontrollistor* i Azure Data Lake Storage Gen2. Med dessa funktioner kan du styra Power BI:s åtkomst till filsystemet som den hanterar i sin data lake och endast ge personer åtkomst till dataflöden eller CDM-mappar som de skapar. 

För att skapa och hantera CDM-mappar i Power BI-filsystemet krävs läs-, skriv- och körbehörighet till filsystemet. Varje dataflöde som skapats i Power BI lagras i en egen CDM-mapp och ägaren av dataflödet beviljas skrivskyddad åtkomst till CDM-mappen och dess innehåll. Den här metoden skyddar integriteten hos de data som Power BI genererar och ger administratörer möjlighet att övervaka vilka användare som kommit åt CDM-mappen via granskningsloggarna. 

### <a name="authorizing-users-or-services-for-cdm-folders"></a>Ge användare eller tjänster behörighet till CDM-mappar

Att dela CDM-mappar med datakonsumenter, till exempel användare eller tjänster som behöver kunna läsa data, förenklas med Active Directory OAuth Bearer-tokens och POSIX-åtkomstkontrollistor. Det ger administratörer möjlighet att övervaka vem som öppnat CDM-mappen. Den enda åtgärden som krävs är att bevilja valfritt Active Directory-objekt (t.ex en användargrupp eller en tjänst) åtkomst till CDM-mappen. Vi rekommenderar att alla andra identiteter än dataproducenten endast beviljas åtkomst till CDM-mappen i skrivskyddat läge. Det skyddar integriteten hos de data som genereras av producenten.

För att kunna lägga till CDM-mappar till Power BI måste användaren ha åtkomstkontrollistor med *Läs*-behörighet, både till själva CDM-mappen och de filer och mappar som ligger i mappen. Användaren behöver också åtkomstkontrollistor med *Kör*-behörighet, både till själva CDM-mappen och dess undermappar. Vi rekommenderar att du läser artiklarna [Åtkomstkontrollistor för filer och katalog](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-access-control#access-control-lists-on-files-and-directories) och [Metodtips för att använda Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-best-practices) om du vill ha mer information.


### <a name="alternative-forms-of-authorization"></a>Alternativa typer av auktorisering

Personer eller tjänster utanför Power BI kan även använda alternativa typer av auktorisering. På så vis får användare med nyckel åtkomst till *alla* resurser på kontot och fullständig åtkomst till alla resurser i en data lake och kan inte begränsas till filsystem eller CDM-mappar. De alternativen kan vara enkla sätt att bevilja åtkomst, men de begränsar möjligheten att dela specifika resurser i en data lake och användarna kan inte granska vem som har fått åtkomst till lagringen. Fullständig information om tillgängliga auktoriseringsmetoder finns i artikeln [Åkomstkontroll i Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-access-control
).


## <a name="next-steps"></a>Nästa steg

Den här artikeln visas en översikt över integrering av Power BI-dataflöden, CDM-mappar och Azure Data Lake Storage Gen2. Mer information finns i följande artiklar:

Mer information om dataflöden, CDM och Azure Data Lake Storage Gen2 finns i följande artiklar:

* [Konfigurera inställningar för arbetsytans dataflöde (förhandsversion)](service-dataflows-configure-workspace-storage-settings.md)
* [Lägga till en CDM-mapp i Power BI som ett dataflöde (förhandsversion)](service-dataflows-add-cdm-folder.md)
* [Ansluta Azure Data Lake Storage Gen2 för lagring av dataflöde (förhandsversion)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

Allmän information om dataflöden finns i de här artiklarna:

* [Skapa och använda dataflöden i Power BI](service-dataflows-create-use.md)
* [Använda beräknade entiteter i Power BI Premium (förhandsversion)](service-dataflows-computed-entities-premium.md)
* [Använda dataflöden med lokala datakällor (förhandsversion)](service-dataflows-on-premises-gateways.md)
* [Resurser för utvecklare för Power BI-dataflöden (förhandsversion)](service-dataflows-developer-resources.md)

Mer information om Azure Storage finns i de här artiklarna:
* [Säkerhetsguiden för Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-security-guide)
* [Kom igång med github-exempel från Azure Data Services](https://aka.ms/cdmadstutorial)

Mer information om Common Data Service finns i dess översiktsartikel:
* [Common Data Service – översikt ](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [CDM-mappar](https://go.microsoft.com/fwlink/?linkid=2045304)
* [CDM-modellfildefinition](https://go.microsoft.com/fwlink/?linkid=2045521)

Och du kan alltid prova att [ställa frågor till Power BI Community](http://community.powerbi.com/).
