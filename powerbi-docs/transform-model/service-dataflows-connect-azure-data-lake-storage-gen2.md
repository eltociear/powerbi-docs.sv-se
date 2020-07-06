---
title: Lär dig hur du ansluter Azure Data Lake Storage Gen 2 till Power BI för lagring av dataflöde
description: Ta dina egna data till dataflöden med hjälp av Azure Data Lake Storage Gen2
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 01/22/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: d6301b4eea49ab4ae5714446e051290cb254c324
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/25/2020
ms.locfileid: "85354764"
---
# <a name="connect-azure-data-lake-storage-gen2-for-dataflow-storage"></a>Ansluta Azure Data Lake Storage Gen2 för lagring av dataflöde

Du kan konfigurera Power BI-arbetsytor till att lagra dataflöden på din organisations Azure Data Lake Storage Gen2-konto. Den här artikeln beskriver de allmänna stegen som krävs för att göra det och innehåller vägledning och bästa praxis längs vägen. Det finns några fördelar med att konfigurera arbetsytor för att lagra dataflödesdefinitioner och datafiler i din data lake, inklusive följande:

* Azure Data Lake Storage Gen2 ger ett oerhört skalbart lagringsutrymme för data
* Dataflödesdata och definitionsfiler kan användas av din IT-avdelnings utvecklare för att dra nytta av Azure-data och AI-tjänster (artificiell intelligens) såsom det visas i [GitHub-exemplen från Azure Data Services](https://aka.ms/cdmadstutorial)
* Gör att utvecklare i din organisation kan integrera dataflödesdata till interna program och branschspecifika affärslösningar med hjälp av utvecklarresurser för dataflöden och Azure

Om du vill använda Azure Data Lake Storage Gen2 för dataflöden, behöver du följande:

* **Power BI-klient** – Minst ett konto i din AAD-klienten (Azure Active Directory) måste vara registrerat för Power BI
* **Ett globalt administratörskonto** – Det här kontot krävs för att ansluta och konfigurera Power BI för att lagra definitionen för dataflöde och data i ditt konto för Azure Data Lake Storage Gen2
* **En Azure-prenumeration** – Du behöver en Azure-prenumeration för att använda Azure Data Lake Storage Gen2
* **Resursgrupp** – Använd en resursgrupp som du redan har eller skapa en ny
* **Ett Azure Storage-konto med funktionen Data Lake Storage Gen2 aktiverad** 

> [!TIP]
> Om du inte har någon Azure-prenumeration kan du [skapa ett kostnadsfritt konto](https://azure.microsoft.com/free/) innan du börjar.

> [!WARNING]
> När du har konfigurerat en lagringsplats för dataflöden kan den inte ändras. Se avsnittet [Överväganden och begränsningar](#considerations-and-limitations) i slutet av den här artikeln för andra viktiga aspekter att tänka på.

## <a name="prepare-your-azure-data-lake-storage-gen2-for-power-bi"></a>Förbereda din Azure Data Lake Storage Gen2 för Power BI

Innan du kan konfigurera Power BI med ett Azure Data Lake Storage Gen2-konto, måste du skapa och konfigurera ett lagringskonto. Låt oss ta en titt på kraven för Power BI:

1. Du måste vara ADLS-lagringskontots ägare. Detta måste tilldelas på en resursnivå, inte ärvas från prenumerationsnivån.
2. Storage-kontot måste skapas i samma Microsoft Azure Active Directory-klient som Power BI-klienten.
3. Storage-kontot måste skapas i samma-region som Power BI-klienten. Om du vill ta reda på var din Power BI-klientorganisation finns kan du läsa [Var finns min Power BI-klientorganisation?](../admin/service-admin-where-is-my-tenant-located.md).
4. Lagringskontot måste ha funktionen *Hierarkiskt namnområde* aktiverad.

I följande avsnitt beskrivs de steg som krävs för att konfigurera ditt Azure Data Lake Storage Gen2-konto i detalj.

### <a name="create-the-storage-account"></a>Skapa lagringskontot

Följ stegen i artikeln [Skapa ett lagringskonto i Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. Kontrollera att du väljer samma plats som Power BI-klienten och ange din lagring som **StorageV2 (generell användning v2)**
2. Kontrollera att du aktiverar funktionen för hierarkiskt namnrymd
3. Vi rekommenderar att ställa in inställningen för lagringsreplikering på **Read-access geo-redundant-lagring (RA-GRS)**

### <a name="grant-permissions-to-power-bi-services"></a>Bevilja behörigheter till Power BI-tjänster

Därefter behöver du bevilja Power BI-tjänsten rollerna Läsare och Dataåtkomst i ditt skapade lagringskonto. De här rollerna är inbyggda, och därför är stegen enkla. 

Följ stegen i [Tilldela en inbyggd RBAC-roll](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac#assign-a-built-in-rbac-role).

I fönstret **Lägg till rolltilldelning** väljer du rollen **Läsare och Dataåtkomst**. Använd sedan sökfunktionen för att hitta programmet **Power BI-tjänst**.
Upprepa samma steg för rollen **Storage Blob Data-ägare** och tilldela rollen till programmen **Power BI-tjänst** och **Power BI Premium**.

> [!NOTE]
> Låt minst 30 minuter gå för att behörighet ska spridas till Power BI från portalen. När du ändrar behörigheter i portalen behöver du låta 30 minuter gå så att de behörigheterna återspeglas i Power BI. 

## <a name="connect-your-azure-data-lake-storage-gen2-to-power-bi"></a>Anslut din Azure Data Lake Storage Gen2 till Power BI

När du har konfigurerat ditt Azure Data Lake Storage Gen2-konto i Azure-portalen ansluter du det till Power BI i **Power BI-administratörsportalen**. Du kan även hantera Power BI-dataflödeslagring i inställningarna för **Dataflödeslagring** i Power BI-administratörsportalen. Anvisningar för start och grundläggande användning finns i [Hur du kommer till administrationsportalen](../admin/service-admin-portal.md) med detaljerad information.

Du ansluter ditt **Azure Data Lake Storage Gen2**-konto med följande steg:

1. Gå till fliken **Dataflödesinställningar** i **Power BI-administratörsportalen**

    ![Power BI-administratörsportalen](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-08b.png) 

2. Välj knappen **Anslut din Azure Data Lake Storage Gen2**. Följande fönster visas.

    ![Azure Data Lake Storage Gen2](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_09.jpg) 

3. Ange **Prenumerations-ID** för Storage-kontot.
4. Ange **Resursgruppnamnet** i vilket lagringskontot har skapats.
5. Tillhandahåll **lagringskontots namn**.
6. Välj **Anslut**.

När de här stegen har slutförts, är ditt Azure Data Lake Storage Gen2-konto anslutet till Power BI. 

> [!NOTE]
> Du måste ha behörigheter som global administratör för att konfigurera en anslutning till Azure Data Lake Storage Gen2 i Power BI-administratörsportalen. Dock kan inte globala administratörer ansluta extern lagring i administratörsportalen.  

Därefter måste du göra det möjligt personer i din organisation att konfigurera sina arbetsytor där de kan använda det här lagringskontot för dataflödesdefinition och datalagring. Låt oss göra det i nästa avsnitt. 


## <a name="allow-admins-to-assign-workspaces"></a>Tillåt att administratörer kan tilldela arbetsytor

Som standard lagras dataflödesdefinition och datafiler i det lagringsutrymme som ingår i Power BI. För att komma åt dataflödesfiler i ditt eget lagringskonto måste administratörer för arbetsytan först konfigurera arbetsytan för att tillåta tilldelning och lagring av dataflöden i det nya lagringskontot. Innan en administratör för arbetsytan kan konfigurera inställningarna för dataflöde måste administratören beviljas behörighet att tilldela lagring i **Power BI-administratörsportalen**.

Om du vill bevilja behörigheter för lagringstilldelning går du till fliken **Dataflödesinställningar** i **Power BI-administratörsportalen**. Det finns en alternativknapp *Administratörer av arbetsytan kan tilldela arbetsytor till det här lagringskontot* som måste anges till **Tillåt**. När du aktiverar skjutreglaget, väljer du knappen **Tillämpa** för att ändringen ska börja gälla. 

![Tillåt att administratörer kan tilldela arbetsytor](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_10.jpg) 

Och sedan är du klar. Administratörer för Power BI-arbetsytan kan nu tilldela arbetsflöden till filsystemet som du skapade.


## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

Den här funktionen är en förhandsgranskningsfunktion och dess beteende kan ändras när lanseringen närmar sig. Det finns några överväganden och begränsningar som du bör tänka på när du arbetar med din dataflödeslagring:

* När du har konfigurerat en lagringsplats för dataflöden kan den inte ändras.
* Endast ägare till ett dataflöde som lagrats i Azure Data Lake Storage Gen2 kan komma åt dess data som standard. För att auktorisera ytterligare personer till de dataflöden som lagras i Azure måste du lägga till dem till dataflödets Common Data Service-mapp 
* Skapa dataflöden med länkade entiteter är endast möjligt om de lagras i samma lagringskonto
* Lokala datakällor i Power BI-delade kapaciteter stöds inte i dataflöden som lagras i organisationens data lake
* Ögonblicksbilder tas inte bort automatiskt i ADLS Gen 2. Om du vill frigöra utrymme kan du skapa en Azure-funktion som regelbundet rensar bort gamla ögonblicksbilder.

Det finns också några kända problem som beskrivs i det här avsnittet.

Power BI Desktop-kunder kan inte komma åt dataflöden som lagrats på ett **Azure Data Lake Storage-konton**, såvida de inte är ägare till dataflödet eller har getts behörighet till Common Data Service-mappen i sjön. Scenariot är följande:

1. Anna har skapat en ny arbetsyta och konfigurerat den så att den lagrar dataflöden i organisationens datasjö. 
2. Ben, som också är medlem i arbetsytan som Anna skapade, vill använda Power BI Desktop och anslutningsappen för dataflöden för att hämta data från det dataflöde som Anna skapade.
3. Ben får ett liknande fel eftersom han inte var auktoriserad till dataflödets CDM-mapp i sjön.

Här följer några vanliga frågor och svar:

**Fråga:** Vad händer om jag tidigare har skapat dataflöden i en arbetsyta och vill ändra deras lagringsplats?

**Svar:** Du kan inte ändra lagringsplatsen för ett dataflöde efter att det har skapats. 

**Fråga:** När kan jag ändra dataflödets lagringsplatsen för en arbetsyta?

**Svar:** Det är bara tillåtet att ändra dataflödets lagringsplats för en arbetsyta om arbetsytan inte innehåller några dataflöden.


## <a name="next-steps"></a>Nästa steg

Den här artikeln ger information om hur du ansluter en Azure Data Lake Gen2 för lagring av dataflöde. Mer information finns i följande artiklar:

Mer information om dataflöden, CDM och Azure Data Lake Storage Gen2 finns i följande artiklar:

* [Dataflöden och Azure Data Lake-integrering (förhandsversion)](service-dataflows-azure-data-lake-integration.md)
* [Konfigurera inställningar för arbetsytans dataflöde (förhandsversion)](service-dataflows-configure-workspace-storage-settings.md)
* [Lägga till en CDM-mapp i Power BI som ett dataflöde (förhandsversion)](service-dataflows-add-cdm-folder.md)

Allmän information om dataflöden finns i de här artiklarna:

* [Skapa och använda dataflöden i Power BI](service-dataflows-create-use.md)
* [Använda beräknade entiteter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Använda dataflöden med lokala datakällor](service-dataflows-on-premises-gateways.md)
* [Resurser för utvecklare för Power BI-dataflöden](service-dataflows-developer-resources.md)

Mer information om Azure Storage finns i de här artiklarna:
* [Säkerhetsguiden för Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-security-guide)

Mer information om Common Data Service finns i dess översiktsartikel:
* [Common Data Service – översikt ](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [CDM-mappar](https://go.microsoft.com/fwlink/?linkid=2045304)
* [CDM-modellfildefinition](https://go.microsoft.com/fwlink/?linkid=2045521)

Och du kan alltid prova att [ställa frågor till Power BI Community](https://community.powerbi.com/).
