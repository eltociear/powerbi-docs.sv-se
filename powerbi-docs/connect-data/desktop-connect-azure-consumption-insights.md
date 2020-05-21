---
title: Ansluta till Azure Consumption Insights-data i Power BI Desktop
description: Det är enkelt att ansluta till Azure och få insikter om användning med Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/14/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 8959e703da2587b7633df4313606bdb11a8c983b
ms.sourcegitcommit: 21b06e49056c2f69a363d3a19337374baa84c83f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/15/2020
ms.locfileid: "83407503"
---
# <a name="connect-to-azure-consumption-insights-data-in-power-bi-desktop"></a>Ansluta till Azure Consumption Insights-data i Power BI Desktop

Du kan använda Power BI Desktop för att ansluta till Azure och få detaljerade data om din organisations användning av Azure-tjänster. Med dessa data kan du skapa anpassade rapporter och åtgärder för att bättre förstå och analysera dina Azure-kostnader.

> [!NOTE]
> Det finns ett begränsat stöd för Microsoft Azure Consumption Insights (beta). Nya funktioner finns i [Azure Cost Management-anslutningsprogrammet för Power BI](desktop-connect-azure-cost-management.md).

## <a name="connect-with-azure-consumption-insights"></a>Ansluta till Azure Consumption Insights

Med Azure Consumption Insights kan du ansluta till Azure Enterprise-avtal för faktureringskonton.

I det här avsnittet lär du dig att hämtar de data du behöver migrera med hjälp av Azure Enterprise-anslutningsprogrammet. Det finns även en mappning av *kolumner med användningsinformation* i **ACI**-API:et (Azure Consumption Insights).

För att korrekt använda **Azure Consumption Insights**-anslutningsprogrammet behöver du ha åtkomst till Enterprise-funktionerna i Azure-portalen.

Så här använder du **Azure Consumption Insights**-anslutningsprogrammet i **Power BI Desktop**: 

1. På menyfliksområdet **Start** väljer du **Hämta data**.

1. I kategorierna till vänster väljer du **Onlinetjänster**.  

1. Välj **Microsoft Azure Consumption Insights (Beta)** . 

1. Välj **Anslut**.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_01b.png)

   I den dialogruta som visas anger du ditt **Azure-registreringsnummer**.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_02.png)

   * Du kan hämta ditt registreringsnummer från [Azure Enterprise Portal](https://ea.azure.com), på den plats som visas i följande bild:

  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_08.png)

   Den här versionen av anslutningsprogrammet stöder bara Enterprise-registreringar från https://ea.azure.com. Registreringar från Kina stöds inte för tillfället.

   Ange därefter din *åtkomstnyckel* för att ansluta.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_03.png)

   * Din åtkomstnyckel för certifikatregistrering kan hittas på [Azure Enterprise Portal](https://ea.azure.com).

  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_09.png)

När du har angett din *åtkomstnyckel* och valt **Anslut** visas ett **navigatörsfönster** som visar de nio tillgängliga tabellerna:

| Tabell        | Beskrivning |
|------------- | -------------------------------------------------------------|
| **Budgetar** | Budgetinformation för att visa faktiska kostnader eller användning mot befintliga budgetmål. |
| **MarketPlace** | Användningsbaserade Azure Marketplace-avgifter. |
| **PriceSheets** | Tillämpliga priser efter mätare för en registrering. |
| **RICharges** | Kostnader som är kopplade till dina reserverade instanser under de senaste 24 månaderna. |
| **RIRecommendations_Single** | Rekommendationer för köp av reserverade instanser baserat på dina användningstrender för en enstaka prenumeration under de senaste 7, 30 eller 60 dagarna. |
| **RIRecommendations_Shared** | Rekommendationer för köp av reserverade instanser baserat på dina användningstrender för alla dina prenumerationer under de senaste 7, 30 eller 60 dagarna. |
| **RIUsage** | Information om förbrukning för dina befintliga reserverade instanser under den senaste månaden. |
| **Sammanfattningar** | En månatlig sammanfattning av saldon, nya inköp, Azure Marketplace-tjänstavgifter, justeringar och överförbrukningskostnader. |
| **UsageDetails** | Detaljer om förbrukade kvantiteter och uppskattade registreringskostnader. |

Du kan markera kryssrutan intill varje tabell för att visa en förhandsgranskning. Du kan markera en eller flera tabeller genom att markera rutan bredvid användarens namn och sedan välja **Ladda**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_04b.png)

> [!NOTE]
> Tabellerna *Sammanfattning* och *Prisdokument* är bara tillgängliga för API-nycklar på registreringsnivå. Som standard har data i dessa tabeller dessutom den aktuella månadens data för *Användning* och *Prisdokument*. Tabellerna *Sammanfattning* och *MarketPlace* är inte begränsade till den aktuella månaden.
>
>

När du väljer **Ladda** läsas data in i **Power BI Desktop**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_05.png)

De dina valda data har laddats kommer dina valda tabeller och fält att visas i panelen **Fält**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_06.png)

## <a name="using-azure-consumption-insights"></a>Använda Azure Consumption Insights
För att använda **Azure Consumption Insights**-anslutningsprogrammet behöver du ha åtkomst till Enterprise-funktionerna i Azure-portalen.

När du har läst in data med hjälp av **Azure Consumption Insights**-anslutningsprogrammet kan du skapa dina egna anpassade mått och kolumner med hjälp av **frågeredigeraren**. Du kan även skapa visuella objekt, rapporter och instrumentpaneler för delning i **Power BI-tjänsten**.

Med en tom fråga kan du hämta en exempelsamling med anpassade Azure-frågor. Det finns två sätt att utföra den här hämtningen: 

I **Power BI Desktop**: 

1. Välj menyfliksområdet **Start** 
2. Välj **Hämta data** > **Tom fråga** 

Eller i **frågeredigeraren**: 

1. Högerklicka i det vänstra fönstret **Frågor** 
2. Välj **Ny fråga > Tom fråga** i den meny som visas

I **formelfältet** skriver du:

    = MicrosoftAzureConsumptionInsights.Contents

I följande bild finns en exempelsamling som visas.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_07.png)

När du arbetar med rapporter och skapar frågor kan du göra följande:

* Om du vill definiera antalet månader från dagens datum använder du *numberOfMonth*
  * Använd ett värde mellan 1 och 36. Representerar det antal månader från dagens datum som du vill importera. Vi rekommenderar att du inte hämtar data för fler än 12 månader. Den här gränsen förhindrar begränsningar för Power BI-frågeimport och trösklar för datavolym.
* Om du vill definiera månader i ett historikfönster väljer du *startBillingDataWindow* och *endBillingDataWindow*
* Använd inte *numberOfMonth* tillsammans med *startBillingDataWindow* eller *endBillingDataWindow*

## <a name="migrate-from-the-azure-enterprise-connector"></a>Migrera från Azure Enterprise-anslutningsprogrammet

Vissa kunder skapade visuella objekt med hjälp av *Azure Enterprise-anslutningsprogrammet (beta)* . Så småningom kommer det att ersättas med **Azure Consumption Insights**-anslutningsprogrammet. Det nya anslutningsprogrammet har funktioner och förbättringar som omfattar:

* Fler datakällor som är tillgängliga för *Saldosammanfattning* och *Inköp från Marketplace*
* Nya och avancerade parametrar som *startBillingDataWindow* och *endBillingDataWindow*
* Bättre prestanda och tillgänglighet

Nästa steg visar hur du övergår till **Azure Consumption Insights**-anslutningsprogrammet. De här stegen bevarar det arbete som du redan har gjort vid skapandet av anpassade instrumentpaneler eller rapporter.

### <a name="step-1-connect-to-azure-using-the-new-connector"></a>Steg 1: Anslut till Azure med hjälp av den nya anslutningsappen
Det första steget är att använda **Azure Consumption Insights**-anslutningsprogrammet enligt den detaljerade beskrivningen tidigare i den här artikeln. Nästa steg är att välja **Hämta data > Tom fråga** från menyfliksområdet **Start** i **Power BI Desktop**.

### <a name="step-2-create-a-query-in-advanced-editor"></a>Steg 2: Skapa en fråga i Avancerad redigerare
I **frågeredigeraren** väljer du **Avancerad redigerare** från menyfliksområdet **Start** -> avsnittet **Fråga**. I fönstret **Avancerad redigerare** som visas anger du den här frågan:

    let    
        enrollmentNumber = "100",
        optionalParameters = [ numberOfMonth = 6, dataType="DetailCharges" ],
        data = MicrosoftAzureConsumptionInsights.Contents(enrollmentNumber, optionalParameters)   
    in     
        data

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_10.png)

Du behöver ersätta värdet för *enrollmentNumber* med ditt registreringsnummer. Du kan hämta ditt nummer från [Azure Enterprise-portalen](https://ea.azure.com). Parametern *numberOfMonth* är det antal månaders data som du vill ha räknat tillbaka från dagens datum. Använd noll (0) för den aktuella månaden.

När du har valt **Klar** i fönstret **Avancerad redigerare** uppdateras förhandsgranskningen, och data från det valda månadsintervallet visas i tabellen. Välj **Stäng & tillämpa** och gå tillbaka.

### <a name="step-3-move-measures-and-custom-columns-to-the-new-report"></a>Steg 3: Flytta mått och anpassade kolumner till den nya rapporten
Därefter behöver du flytta eventuella anpassade kolumner eller mått som du skapade till den nya informationstabellen. Gör så här:

1. Öppna Anteckningar (eller något annat textredigeringsprogram).
2. Välj det mått som du vill flytta, kopiera text från fältet *Formel* och placera den i anteckningar.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_11.png)
3. Byt namn på *Fråga1* till ursprungliga informationstabellens namn.
4. För att skapa nya tabellmått och anpassade kolumner högerklickar du på tabellen och väljer **Nytt mått**. Klipp sedan ut och klistra in dina sparade mått och kolumner tills alla är klara.

### <a name="step-4-relink-tables-that-had-relationships"></a>Steg 4: Länka om tabeller som hade relationer
Många instrumentpaneler har ytterligare tabeller som används för sökning och filtrering, till exempel datumtabeller eller tabeller som används för anpassade projekt. Du kan lösa merparten av återstående problem genom att återupprätta dessa relationer. Gör så här.

- På fliken **Modellering** i **Power BI Desktop** väljer du **Hantera relationer** för att öppna ett fönster där du kan hantera relationer i modellen. Länka om dina tabeller om det behövs.

    ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_12.png)

### <a name="step-5-verify-your-visuals-and-adjust-field-formatting-as-needed"></a>Steg 5: Kontrollera dina visuella objekt och justera fältformateringen vid behov
Vid det här laget bör de flesta av dina ursprungliga visuella objekt, tabeller och detaljerad information fungera som förväntat. Vissa mindre justeringar kan dock vara nödvändiga för att noggrant formatera utseendet och känslan. Ägna en stund åt att titta på dina instrumentpaneler och visuella objekt så att de ser helt rätt ut.

## <a name="using-the-azure-consumption-and-insights-aci-api-to-get-consumption-data"></a>Använda API:et Azure Consumption och Insights (ACI) för att hämta förbrukningsdata
Azure tillhandahåller också API:et [**Azure Consumption and Insights (ACI)** ](https://azure.microsoft.com/blog/announcing-general-availability-of-consumption-and-charge-apis-for-enterprise-azure-customers/). Du kan skapa dina egna anpassade lösningar för att hämta, rapportera och visualisera förbrukningsinformation i AZURE med ACI API.

### <a name="mapping-names-and-usage-details-between-the-portal-the-connector-and-the-api"></a>Kartlägg namn och användnings information mellan portalen, anslutningsappen och API:et
Kolumnerna och detaljnamnen i Azure-portalen ser liknande ut i API:et och anslutningsprogrammet, men de är inte alltid identiska. Följande tabell innehåller en mappning för att klargöra. Här ser du även om kolumnen inte längre gäller. Mer information och begreppsdefinitioner finns i [ordlistan för faktureringsdata i Azure](https://docs.microsoft.com/azure/billing/billing-enterprise-api-usage-detail).

| ACI-anslutningsappens/Innehållspaketets kolumnnamn | ACI API-kolumnnamn | EA-kolumnnamn | Gäller inte/tillgänglig för bakåtkompatibilitet |
| --- | --- | --- | --- |
| AccountName |accountName |Account Name |Nej |
| AccountId |accountId | |Ja |
| AccountOwnerId |accountOwnerEmail |AccountOwnerId |Nej |
| AdditionalInfo |additionalInfo |AdditionalInfo |Nej |
| AdditionalInfold | | |Ja |
| Consumed Quantity |consumedQuantity |Consumed Quantity |Nej |
| Consumed Service |consumedService |Consumed Service |Nej |
| ConsumedServiceId |consumedServiceId | |Ja |
| Cost |cost |ExtendedCost |Nej |
| Cost Center |costCenter |Cost Center |Nej |
| Datum |date |Datum |Nej |
| Dag | |Dag |Nej |
| DepartmentName |departmentName |Department Name |Nej |
| DepartmentID |departmentId | |Ja |
| Instance ID | | |Ja |
| InstanceId |instanceId |Instance ID |Nej |
| Plats | | |Ja |
| Meter Category |meterCategory |Meter Category |Nej |
| Meter ID | | |Ja |
| Mätarnamn |meterName |Meter Name |Nej |
| Meter Region |meterRegion |Meter Region |Nej |
| Meter Sub-Category |meterSubCategory |Meter Sub-Category |Nej |
| MeterId |meterId |Meter ID |Nej |
| Månad | |Månad |Nej |
| Produkt |product |Product |Nej |
| ProductId |productId | |Ja |
| Resursgrupp |resourceGroup |Resource Group |Nej |
| Resource Location |resourceLocation |Resource Location |Nej |
| ResourceGroupId | | |Ja |
| ResourceLocationId |resourceLocationId | |Ja |
| ResourceRate |resourceRate |ResourceRate |Nej |
| ServiceAdministratorId |serviceAdministratorId |ServiceAdministratorId |Nej |
| ServiceInfo1 |serviceInfo1 |ServiceInfo1 |Nej |
| ServiceInfo1Id | | |Ja |
| ServiceInfo2 |serviceInfo2 |ServiceInfo2 |Nej |
| ServiceInfo2Id | | |Ja |
| Store Service Identifier |storeServiceIdentifier |Store Service Identifier |Nej |
| StoreServiceIdentifierId | | |Ja |
| Prenumerationsnamn |subscriptionName |Subscription Name |Nej |
| Taggar |tags |Taggar |Nej |
| TagsId | | |Ja |
| Unit Of Measure |unitOfMeasure |Unit Of Measure |Nej |
| År | |År |Nej |
| SubscriptionId |subscriptionId |SubscriptionId |Ja |
| SubscriptionGuid |subscriptionGuid |SubscriptionGuid |Nej |


## <a name="next-steps"></a>Nästa steg

Du kan ansluta till många olika datakällor med hjälp av Power BI Desktop. Mer information finns i följande artiklar:

* [Ansluta till Azures kostnadshanteringsdata i Power BI Desktop](desktop-connect-azure-cost-management.md)
* [Vad är Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till Excel-arbetsböcker i Power BI Desktop](desktop-connect-excel.md)   
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
