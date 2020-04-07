---
title: Lägg till en CDM-mapp i Power BI som ett dataflöde
description: Konfigurera en arbetsyta så att den lagrar dataflödesdefinitionen och datafilerna i Azure Data Lake Storage Gen2
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: f1e48fb2f20c531f4dc66e86d13b76f54165b81c
ms.sourcegitcommit: 444f7fe5068841ede2a366d60c79dcc9420772d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80404772"
---
# <a name="add-a-cdm-folder-to-power-bi-as-a-dataflow-preview"></a>Lägga till en CDM-mapp i Power BI som ett dataflöde (förhandsversion)

I Power BI, kan du lägga till CDM-mappar (Common Data Model) som lagras i din organisations Azure Data Lake Store Gen2 som dataflöden. Och när du väl skapar ett dataflöde från en CDM-mapp, kan du använda **Power BI Desktop** och **Power BI-tjänsten** för att skapa datauppsättningar, rapporter, instrumentpaneler och appar som baseras på de data som du lägger till i CDM-mappar.

![Dataflöde från CDM-mapp](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_01.jpg)

Det finns några krav som måste uppfyllas för att skapa dataflöden från CDM-mappar och de beskrivs i följande lista:

* En administratör måste länka ADLS Gen2-lagringskontot i Power BI innan det kan användas. Mer information om hur du länkar ett ADLS Gen2-konto till Power BI finns i [Ansluta Azure Data Lake Storage Gen2 för lagring av dataflöde](service-dataflows-connect-azure-data-lake-storage-gen2.md).
* Möjligheten att skapa dataflöden från CDM-mappar finns *bara* tillgänglig i den [nya arbetsytan](service-create-the-new-workspaces.md). 
* För att lägga till en CDM-mapp i Power BI krävs det att användaren har [behörighet för CDM-mappen och dess filer](https://go.microsoft.com/fwlink/?linkid=2029121).
* Du måste läsas beviljas läs- och körbehörighet för alla filer och mappar i CDM-mappen för att lägga till dem i Power BI.

I följande avsnitt beskrivs hur du skapar ett dataflöde från en CDM-mapp.

## <a name="create-a-dataflow-from-a-cdm-folder"></a>Skapa ett dataflöde från en CDM-mapp

Om du vill skapa ett dataflöde från en CDM-mapp, så börja med att starta **Power BI-tjänsten** och välja en **arbetsyta** i navigeringsfönstret. Du kan också skapa en ny arbetsyta där du kan skapa ditt nya dataflöde.

![Skapa ett dataflöde i Power BI-tjänsten](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_02.jpg)

På skärmen som visas väljer du att **skapa och bifoga** enligt följande bild.

![Skapa och bifoga ett nytt dataflöde](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_03.jpg)

På den skärm som sedan visas  kan du namnge ditt dataflöde, ge en beskrivning av dataflödet och ange sökvägen till CDM-mappen i din organisations Azure Data Lake Gen2-konto. Läs avsnittet i artikeln som beskriver [hur du hämtar din CDM-mappsökväg](service-dataflows-configure-workspace-storage-settings.md#get-the-uri-of-stored-dataflow-files). 

![Dataflöde från CDM-mapp](media/service-dataflows-add-cdm-folder/dataflow-from-cdm-folder_01.jpg)

När du har angett informationen väljer du **Skapa och bifoga** för att skapa dataflödet.

Dataflöden från CDM-mappar markeras med en *extern* ikon när de visas i Power BI. I nästa avsnitt beskriver vi skillnaderna mellan dataflöden av standardtyp och dataflöden som skapats från CDM-mappar.

När behörigheter har ställts in korrekt, enligt beskrivningen tidigare i den här artikeln, kan du ansluta till ditt dataflöde i **Power BI Desktop**.


## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

När du arbetar med behörigheter till ett dataflöde som skapats från en CDM-mapp, liknar processen den för externa datakällor i Power BI. Behörigheter hanteras i datakällan och inte inifrån Power BI. Behörigheter måste ställas in på rätt sätt i själva datakällan, till exempel ett dataflöde som skapas från en CDM-mapp för att fungera korrekt med Power BI.

Följande listor tydliggör hur dataflöden från CDM-mappar fungerar med Power BI.

Power BI Pro-, Premium- och Embedded-arbetsytor:
* Det går inte att redigera dataflöden från CDM-mappar
* Behörighet att läsa ett dataflöde som skapats från en CDM-mapp hanteras av CDM-mappens ägare och inte av Power BI.

Power BI Desktop:
* Endast användare som har behörighet för både arbetsytan där dataflödet skapades och CDM-mappen kan få åtkomst till dess data från Power BI-dataflödenas anslutningsapp


Det finns några ytterligare saker att ta hänsyn till, som beskrivs i följande lista:

* Möjligheten att skapa dataflöden från CDM-mappar finns *bara* tillgänglig i den [nya arbetsytan](service-create-the-new-workspaces.md).
* Länkade entiteter är inte tillgängliga för dataflöden som skapats från CDM-mappar.


**Power BI Desktop**-användare kan inte komma åt dataflöden som är lagrade i Azure Data Lake Storage Gen2-kontot, såvida inte de är ägare av dataflödet eller de uttryckligen har godkänts för detta dataflödes CDM-mapp. Se följande situation:

1.    Anna skapar en ny arbetsyta och konfigurerar den för lagring av dataflöden från en CDM-mapp.
2.    Ben, som också är medlem i arbetsytan som Anna skapade, vill använda Power BI Desktop och anslutningsappen för dataflöden för att hämta data från det dataflöde som Anna skapade.
3.    Ben får ett fel eftersom han inte har lagts till som auktoriserad användare i dataflödets CDM-mapp i datasjön.

  ![Fel vid försök att använda dataflöde](media/service-dataflows-configure-workspace-storage-settings/dataflow-storage-settings_08.jpg)

För att lösa problemet, måste Ben beviljas läsbehörighet till CDM-mappen och dess filer. Du kan läsa mer om hur du ger åtkomst till CDM-mappen i [den här artikeln](https://go.microsoft.com/fwlink/?linkid=2029121).


## <a name="next-steps"></a>Nästa steg

I den här artikeln får du information om hur du konfigurerar arbetsytans lagring av dataflöden. Mer information finns i följande artiklar:

Mer information om dataflöden, CDM och Azure Data Lake Storage Gen2 finns i följande artiklar:

* [Dataflöden och Azure Data Lake-integrering (förhandsversion)](service-dataflows-azure-data-lake-integration.md)
* [Konfigurera inställningar för arbetsytans dataflöde (förhandsversion)](service-dataflows-configure-workspace-storage-settings.md)
* [Ansluta Azure Data Lake Storage Gen2 för lagring av dataflöde (förhandsversion)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

Allmän information om dataflöden finns i de här artiklarna:

* [Skapa och använda dataflöden i Power BI](service-dataflows-create-use.md)
* [Använda beräknade entiteter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Använda dataflöden med lokala datakällor](service-dataflows-on-premises-gateways.md)
* [Resurser för utvecklare för Power BI-dataflöden](service-dataflows-developer-resources.md)

Mer information om Azure Storage finns i de här artiklarna:
* [Säkerhetsguiden för Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-security-guide)
* [Konfigurera schemalagd uppdatering](refresh-scheduled-refresh.md)
* [Kom igång med github-exempel från Azure Data Services](https://aka.ms/cdmadstutorial)

Mer information om Common Data Service finns i dess översiktsartikel:
* [Common Data Service – översikt ](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [CDM-mappar](https://go.microsoft.com/fwlink/?linkid=2045304)
* [CDM-modellfildefinition](https://go.microsoft.com/fwlink/?linkid=2045521)

Och du kan alltid prova att [ställa frågor till Power BI Community](https://community.powerbi.com/).

