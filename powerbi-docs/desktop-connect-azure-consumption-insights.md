---
title: Ansluta till Azure Consumption Insights-data i Power BI Desktop (beta)
description: Det är enkelt att ansluta till Azure och få insikter om användning med Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1e82ec988389790a3d96cb6f98f0db5d1a385fda
ms.sourcegitcommit: 00b4911ab5fbf4c2d5ffc000a3d95b3149909c28
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="connect-to-azure-consumption-insights-in-power-bi-desktop-beta"></a>Ansluta till Azure Consumption Insights i Power BI Desktop (beta)
Med anslutningsappen **Azure förbrukning Insights** kan du använda **Power BI Desktop** för att ansluta till Azure och få detaljerade data och information om din organisations användning av Azure-tjänster. Du kan också skapa mått, anpassade kolumner och visuella objekt för att rapportera och dela information om organisationens Azure-användning. Den här versionen av **Azure Consumption and Insights** är en beta-version och kan ändras.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_01.png)

Den här artikeln beskriver hur du ansluter med anslutningsappen **Azure Consumption Insights** och hämtar de data du behöver, hur du migrerar med hjälp av Azure Enterprise Connector och hur du hittar en mappning av *användningsinformationskolumner* som är tillgängliga i API:et **ACI** (Azure Consumption Insights) API.

## <a name="connect-to-azure-consumption-insights"></a>Ansluta till Azure Consumption Insights
För att ansluta med hjälp av anslutningsappen **Azure Consumption Insights** måste du ha åtkomst till företagsfunktioner i Azure-portalen.

Om du vill ansluta med hjälp av anslutningsappen **Azure Consumption Insights** väljer du **Hämta data** från fältet **Start** i **Power BI Desktop**. Välj **Onlinetjänster** från kategorierna till vänster för att visa **Microsoft Azure Consumption Insights (beta)**. Välj **Anslut**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_01b.png)

Ange ditt *registreringsnummer* i dialogrutan.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_02.png)

* Du kan hämta ditt registreringsnummer från [Azure Enterprise Portal](https://ea.azure.com), på den plats som visas i följande bild:
  
  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_08.png)
  
  Den här versionen av anslutningsappen stöder bara enterprise-registreringar från https://ea.azure.com. Registreringar från Kina stöds inte för tillfället.

Ange därefter din *åtkomstnyckel* för att ansluta.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_03.png)

* Din åtkomstnyckel för certifikatregistrering kan hittas på [Azure Enterprise Portal](https://ea.azure.com).
  
  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_09.png)

När du har angett din *åtkomstnyckeln* och valt **Anslut**, visas fönstret **Navigator** och visar de fyra tabellerna som är tillgängliga för dig: *Sammanfattning*, *Användning*, *Prisdokument* och *MarketPlace*. Du kan markera kryssrutan intill varje tabell för att visa en förhandsgranskning. Du kan markera en eller flera tabeller genom att markera rutan bredvid användarens namn och sedan välja **Ladda**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_04.png)

> [!NOTE]
> Tabellerna *Sammanfattning* och *Prisdokument* är bara tillgängliga för API-nycklar på registreringsnivå. Som standard har data i dessa tabeller dessutom den aktuella månadens data för *Användning* och *Prisdokument*. Tabellerna *Sammanfattning* och *MarketPlace* är inte begränsade till den aktuella månaden.
> 
> 

När du väljer **Ladda** läsas data in i **Power BI Desktop**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_05.png)

De dina valda data har laddats kommer dina valda tabeller och fält att visas i panelen **Fält**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_06.png)

## <a name="using-azure-consumption-insights"></a>Använda Azure Consumption Insights
För att använda anslutningsappen **Azure Consumption Insights** måste du ha åtkomst till företagsfunktioner i Azure-portalen.

När du har läst in data med hjälp av anslutningsappen **Azure Consumption Insights** kan du skapa dina egna anpassade mått och kolumner med hjälp av **frågeredigeraren** och du kan skapa visuella objekt, rapporter och instrumentpaneler som du kan dela i tjänsten **Power BI**.

Azure innehåller också en samling anpassade exempelfrågor som du kan hämta genom att använda en tom fråga. I **Start** menyfliksområdet av **Power BI Desktop** väljer du den nedåtpilen i **Hämta data** och välj sedan **Tom fråga**. Du kan också göra detta i **frågeredigeraren** genom att högerklicka på panelen **Frågor** till vänster och välja **Ny fråga >Tom fråga** från menyn.

I **formelfältet** skriver du följande:

    = MicrosoftAzureConsumptionInsights.Contents

En samling exempel visas enligt följande bild:

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_07.png)

När du arbetar med rapporter och skapa frågor kan du använda följande:

* Om du vill definiera antalet månader från dagens datum använder du *numberOfMonth*
  * Använd ett värde mellan ett och 36 som representerar antalet månader från dagens datum som du vill importera. Vi rekommenderar att du hämtar max tolv månaders data för att undvika tröskelvärden med importbegränsningar och tillåten datavolym för frågor i Power BI.
* Om du vill definiera månader i ett historikfönster väljer du *startBillingDataWindow* och *endBillingDataWindow*
* Använd *inte* *numberOfMonth* tillsammans med *startBillingDataWindow* eller *endBillingDataWindow*

## <a name="migrating-from-the-azure-enterprise-connector"></a>Migrera från Azure Enterprise Connector
Vissa kunder har skapat visuella objekt med hjälp av *Azure Enterprise Connector (beta)* som snart kommer att upphöra och ersätts av anslutningsappen **Azure Consumption Insights**. Anslutningsappen **Azure Consumption Insights** har bland annat följande funktioner och förbättringar:

* Fler datakällor som är tillgängliga för *Saldosammanfattning* och *Inköp från Marketplace*
* Nya och avancerade parametrar som *startBillingDataWindow* och *endBillingDataWindow*
* Bättre prestanda och tillgänglighet

För att hjälpa kunder att övergå till den nya anslutningsappen **Azure Consumption Insights** och för att bevara deras arbete med anpassade instrumentpaneler och rapporter visar följande steg hur övergången går till.

### <a name="step-1-connect-to-azure-using-the-new-connector"></a>Steg 1: Anslut till Azure med hjälp av den nya anslutningsappen
Det första steget är att ansluta med anslutningsappen **Azure Consumption Insights** som beskrevs i detalj tidigare i den här artikeln. Nästa steg är att välja **Hämta data > Tom fråga** från menyfliksområdet **Start** i **Power BI Desktop**.

### <a name="step-2-use-the-advanced-editor-to-create-a-query"></a>Steg 2: Använd Avancerad redigerare för att skapa en fråga
I **Frågeredigeraren** väljer du **Avancerad redigerare** från området **Fråga** i menyfliksområdet **Start**. I fönstret **Avancerad redigerare** som visas anger du följande fråga:

    let    
        enrollmentNumber = "100",
        optionalParameters = [ numberOfMonth = 6, dataType="DetailCharges" ],
        data = MicrosoftAzureConsumptionInsights.Contents(enrollmentNumber, optionalParameters)   
    in     
        data

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_10.png)

Naturligtvis måste du ersätta värdet för *enrollmentNumber* med ditt egen registreringsnummer som du kan hämta från [Azure Enterprise Portal](https://ea.azure.com). Parametern *numberOfMonth* är antalet månaders data du vill hämta räknat från dagens datum. Använd noll (0) för den aktuella månaden.

När du har valt **Klar** i fönstret **Avancerad redigerare** uppdateras förhandsgranskningen, och data från det valda månadsintervallet visas i tabellen. Välj **Stäng & tillämpa** och gå tillbaka.

### <a name="step-3-move-measures-and-custom-columns-to-the-new-report"></a>Steg 3: Flytta mått och anpassade kolumner till den nya rapporten
Därefter måste du flytta eventuella anpassade kolumner eller mått som du skapade i den nya informationstabellen. Gör så här:

1. Öppna Anteckningar (eller något annat textredigeringsprogram).
2. Välj det mått som du vill flytta, kopiera text från fältet *Formel* och placera den i anteckningar.
   
   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_11.png)
3. Byt namn på *Fråga1* till ursprungliga informationstabellens namn.
4. Skapa nya åtgärder och anpassade kolumner i tabellen genom att högerklicka på tabellen och välja **Nytt mått**. Klipp och klistra in dina lagrade mått och kolumner tills du är klar.

### <a name="step-4-re-link-tables-that-had-relationships"></a>Steg 4: Länka tabeller med relationer
Många instrumentpaneler har ytterligare tabeller som används för sökning och filtrering, till exempel datumtabeller eller tabeller som används för anpassade projekt. Du kan lösa merparten av återstående problem genom att återupprätta dessa relationer. Gör så här.

- På fliken **Modellering** i **Power BI Desktop** väljer du **Hantera relationer** för att öppna ett fönster där du kan hantera relationer i modellen. Länka om dina tabeller, om det behövs.
   
    ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_12.png)

### <a name="step-5-verify-your-visuals-and-adjust-field-formatting-as-needed"></a>Steg 5: Kontrollera dina visuella objekt och justera fältformateringen vid behov
När du har kommit så här långt bör de flesta av dina visuella objekt, tabeller och listrutor fungera som förväntat. Du kan dock behöva göra några mindre justeringar i formatet så att allt blir precis som du vill ha det. Ägna en stund åt att titta på dina instrumentpaneler och visuella objekt så att de ser helt rätt ut.

## <a name="using-the-azure-consumption-and-insights-aci-api-to-get-consumption-data"></a>Använda API:et Azure Consumption och Insights (ACI) för att hämta förbrukningsdata
Azure tillhandahåller också API:et [**Azure Consumption and Insights (ACI)**](https://azure.microsoft.com/blog/announcing-general-availability-of-consumption-and-charge-apis-for-enterprise-azure-customers/). Du kan skapa dina egna anpassade lösningar för att hämta, rapportera och visualisera förbrukningsinformation i AZURE med ACI API.

### <a name="mapping-names-and-usage-details-between-the-portal-the-connector-and-the-api"></a>Kartlägg namn och användnings information mellan portalen, anslutningsappen och API:et
Kolumnerna och namnen på detaljerna i Azure Portal ser ut på samma sätt i API:et och anslutningsappen men de är inte alltid identiska. För att tydliggöra detta kartlägger följande tabell relationerna mellan API:et, anslutningsappen och kolumnerna du ser i Azure Portal. Här ser du även om kolumnen inte längre gäller. För mer information och definitioner av dessa begrepp kan du läsa mer i [ordlistan för faktureringsdata i Azure](https://docs.microsoft.com/azure/billing/billing-enterprise-api-usage-detail).

| ACI-anslutningsappens/Innehållspaketets kolumnnamn | ACI API-kolumnnamn | EA-kolumnnamn | Gäller inte/tillgänglig för bakåtkompatibilitet |
| --- | --- | --- | --- |
| AccountName |accountName |Account Name |Nej |
| AccountId |accountId | |Ja |
| AcccountOwnerId |accountOwnerEmail |AccountOwnerId |Nej |
| AdditionalInfo |additionalInfo |AdditionalInfo |Nej |
| AdditionalInfold | | |Ja |
| Consumed Quantity |consumedQuantity |Consumed Quantity |Nej |
| Consumed Service |consumedService |Consumed Service |Nej |
| ConsumedServiceId |consumedServiceId | |Ja |
| Cost |cost |ExtendedCost |Nej |
| Cost Center |costCenter |Cost Center |Nej |
| Date |date |Date |Nej |
| Dag | |Dag |Nej |
| DepartmentName |departmentName |Department Name |Nej |
| DepartmentID |departmentId | |Ja |
| Instance ID | | |Ja |
| InstanceId |instanceId |Instance ID |Nej |
| Location | | |Ja |
| Meter Category |meterCategory |Meter Category |Nej |
| Meter ID | | |Ja |
| Meter Name |meterName |Meter Name |Nej |
| Meter Region |meterRegion |Meter Region |Nej |
| Meter Sub-Category |meterSubCategory |Meter Sub-Category |Nej |
| MeterId |meterId |Meter ID |Nej |
| Månad | |Månad |Nej |
| Product |product |Product |Nej |
| ProductId |productId | |Ja |
| Resource Group |resourceGroup |Resource Group |Nej |
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
| Subscription Name |subscriptionName |Subscription Name |Nej |
| Tags |tags |Tags |Nej |
| TagsId | | |Ja |
| Unit Of Measure |unitOfMeasure |Unit Of Measure |Nej |
| År | |År |Nej |
| SubscriptionId |subscriptionId |SubscriptionId |Ja |
| SubscriptionGuid |subscriptionGuid |SubscriptionGuid |Nej |

## <a name="next-steps"></a>Nästa steg
Det finns alla möjliga sorters data du kan ansluta till med Power BI Desktop. Kolla in följande resurser för mer information om datakällor:

* [Komma igång med Power BI Desktop](desktop-getting-started.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till Excel-arbetsböcker i Power BI Desktop](desktop-connect-excel.md)   
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

