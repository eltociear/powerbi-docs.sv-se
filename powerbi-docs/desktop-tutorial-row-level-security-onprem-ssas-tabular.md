---
title: Dynamisk säkerhet på radnivå med Analysis Services-tabellmodell
description: Dynamisk säkerhet på radnivå med Analysis Services-tabellmodell
author: davidiseminger
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1b90357aa6d8f66612857e8247a8b48dc2c2c369
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76539674"
---
# <a name="implement-row-level-security-in-an-analysis-services-tabular-model"></a>Implementera säkerhet på radnivå i en Analysis Services-tabellmodell

När du använder en exempeldatamängd och går igenom stegen nedan får du i den här självstudien lära dig att implementera [**säkerhet på radnivå**](service-admin-rls.md) för en *Analysis Services-tabellmodell* och använda den i en Power BI-rapport.

* Skapa en ny säkerhetstabell i [AdventureworksDW2012-databasen](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
* Skapa tabellmodellen med nödvändiga fakta- och dimensionstabeller
* Definiera användarroller och behörigheter
* Distribuera modellen till en *Analysis Services-tabell*instans
* Skapa en Power BI Desktop-rapport som visar data anpassade till användaren som öppnar rapporten
* Distribuera rapporten till *Power BI-tjänsten*
* Skapa en ny instrumentpanel som baseras på rapporten
* Dela instrumentpanelen med dina medarbetare

För den här självstudien behöver du [AdventureworksDW2012-databasen](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>Uppgift 1: Skapa användarens säkerhetstabell och definiera datarelationen

Det finns många artiklar som beskriver hur du definierar dynamisk säkerhet på radnivå med *SSAS-tabellmodellen (SQL Server Analysis Services)* . I vårt exempel använder vi [Implement Dynamic Security by Using Row Filters](/analysis-services/tutorial-tabular-1200/supplemental-lesson-implement-dynamic-security-by-using-row-filters) (Implementera dynamisk säkerhet med hjälp av radfilter).

För stegen här måste du använda AdventureworksDW2012-relationsdatabasen.

1. I AdventureworksDW2012 skapar du tabellen `DimUserSecurity` enligt nedan. Du kan använda [SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) till att skapa tabellen.

   ![Skapa DimUserSecurity-tabell](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)

1. När du har skapat och sparat tabellen behöver du upprätta relationen mellan `DimUserSecurity`-tabellens `SalesTerritoryID`-kolumn och `DimSalesTerritory`-tabellens `SalesTerritoryKey`-kolumn enligt nedan.

   I SSMS högerklickar du på **DimUserSecurity** och väljer **Design**. Välj sedan **Tabelldesigner** > **Relationer...** . Spara tabellen när du är färdig.

   ![Sekundärnyckelrelationer](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)

1. Lägg till användare i tabellen. Högerklicka på **DimUserSecurity** och välj **Redigera de översta 200 raderna**. När du har lagt till användare bör tabellen `DimUserSecurity` se ut ungefär som i följande exempel:

   ![Tabellen DimUserSecurity med exempelanvändare](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)

   Du kommer att se de här användarna i senare uppgifter.

1. Nu ska du göra en *inre koppling* med tabellen `DimSalesTerritory`, vilket visat användarassocierad regionsinformation. Den här SQL-koden skapar den inre kopplingen. I bilden ser du hur tabellen visas efteråt.

    ```sql
    select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
    ```

   Den kopplade tabellen visar vem som ansvarar för varje försäljningsregion, tack vare den relation som du skapade i steg 2. Du kan till exempel se att *Rita Santos* ansvarar för *Australien*.

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>Uppgift 2: Skapa tabellmodellen med fakta- och dimensionstabeller

När ditt relationsinformationslager finns på plats ska du definiera tabellmodellen. Du kan skapa modellen med hjälp av [SQL Server Data Tools](/sql/ssdt/sql-server-data-tools) (SSDT). Mer information finns i [Skapa ett nytt tabellmodellprojekt](/sql/analysis-services/lesson-1-create-a-new-tabular-model-project).

1. Importera alla nödvändiga tabeller till modellen enligt vad som visas nedan.

    ![Importerad SQL Server för användning med dataverktyg](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)

1. När du har importerat de tabeller som krävs behöver du definiera en roll med namnet *SalesTerritoryUsers* med läsbehörighet. Välj menyn **Modell** i SQL Server Data Tools och välj sedan **Roller**. I **Rollhanteraren** väljer du **Ny**.

1. Under **Medlemmar** i **Rollhanteraren** lägger du till de användare som du definierade i tabellen `DimUserSecurity` i [Uppgift 1](#task-1-create-the-user-security-table-and-define-data-relationship).

    ![Lägga till användare i Rollhanteraren](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)

1. Lägg sedan till rätt funktioner för både tabellen `DimSalesTerritory` och `DimUserSecurity` enligt vad som visas nedan på fliken **Radfilter**.

    ![Lägga till funktioner till radfilter](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)

1. Funktionen `LOOKUPVALUE` returnerar värden för en kolumn där Windows-användarnamnet matchar det namn som returneras av funktionen `USERNAME`. Du kan sedan begränsa frågor så att värden som returneras av `LOOKUPVALUE` matchar värdena i samma eller en relaterad tabell. I kolumnen **DAX-filter** skriver du följande formel:

    ```sql
        =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])
    ```

    I den här formeln returnerar funktionen `LOOKUPVALUE` alla värden för kolumnen `DimUserSecurity[SalesTerritoryID]`, där `DimUserSecurity[UserName]` är samma som det aktuella inloggade Windows-användarnamnet och `DimUserSecurity[SalesTerritoryID]` är samma som `DimSalesTerritory[SalesTerritoryKey]`.

    > [!IMPORTANT]
    > När du använder säkerhet på radnivå saknas stöd för DAX-funktionen [USERELATIONSHIP](/dax/userelationship-function-dax).

   Den uppsättning av `SalesTerritoryKey` för försäljning som `LOOKUPVALUE` returnerar används sedan för att begränsa de rader som visas i `DimSalesTerritory`. Endast rader där värdet `SalesTerritoryKey` finns med bland de ID:n som returneras av funktionen `LOOKUPVALUE` visas.

1. För tabellen `DimUserSecurity` lägger du i kolumnen **DAX Filter** till följande formel:

    ```sql
        =FALSE()
    ```

    Den här formeln anger att alla kolumner matchas till `false`, vilket innebär du inte kan köra frågor mot kolumner i tabellen `DimUserSecurity`.

Nu ska du bearbeta och distribuera modellen. Mer information finns i [Distribuera](/sql/analysis-services/lesson-13-deploy).

## <a name="task-3-add-data-sources-within-your-on-premises-data-gateway"></a>Uppgift 3: Lägga till datakällor inom din lokala datagateway

När din tabellmodell är distribuerad och är redo för användning, måste du lägga till en datakällsanslutning till din lokala Analysis Services-tabellserver.

1. För att kunna ge Power BI-tjänsten åtkomst till din lokala analystjänst behöver du en [lokal datagateway](service-gateway-onprem.md) installerad och konfigurerad i miljön.

1. När gatewayen är korrekt konfigurerad måste du skapa en datakällsanslutning för din *Analysis Services*-tabellinstans. Mer information finns i [Hantera din datakälla – Analysis Services](service-gateway-enterprise-manage-ssas.md).

   ![Skapa anslutning till datakälla](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)

När den här proceduren är klar är gatewayen konfigurerad och redo att interagera med din lokala Analysis Services-datakälla.

## <a name="task-4-create-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>Uppgift 4: Skapa en rapport baserad på Analysis Services-tabellmodellen med Power BI Desktop

1. Starta Power BI Desktop och välj **Hämta data** > **Databas**.

1. I listan med datakällor väljer du **SQL Server Analysis Services-databas** och sedan **Anslut**.

   ![Ansluta till SQL Server Analysis Services-databas](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)

1. Fyll i informationen för Analysis Services-tabellinstansen och välj **Anslut live**. Välj sedan **OK**.
  
   ![Analysis Services-information](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

   I Power BI fungerar dynamisk säkerhet enbart med en live-anslutning.

1. Du ser att den distribuerade modellen finns i Analysis Services-instansen. Välj respektive modell och sedan **OK**.

   Power BI Desktop visar nu alla tillgängliga fält till höger om arbetsytan i fönstret **Fält**.

1. I fönstret **Fält** väljer du måttet **SalesAmount** från tabellen **FactInternetSales** och dimensionen **SalesTerritoryRegion** från tabellen **SalesTerritory**.

1. Vi vill hålla rapporten enkel och lägger därför inte till fler kolumner just nu. Data återges mer meningsfullt om du ändrar visualiseringen till ett **ringdiagram**.

   ![Visualisering med ringdiagram](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)

1. När rapporten är klar kan du publicera den direkt till Power BI-portalen. I menyfliksområdet **Start** i Power BI Desktop väljer du **Publicera**.

## <a name="task-5-create-and-share-a-dashboard"></a>Uppgift 5: Skapa och dela en instrumentpanel

Du har skapat rapporten och publicerat den till **Power BI**-tjänsten. Nu kan du använda exemplet som skapades i föregående steg till att demonstrera modellsäkerhetsscenariot.

I rollen som *Sales Manager* kan användaren Grace se data från alla olika försäljningsregioner. Grace skapar den här rapporten och publicerar den till Power BI-tjänsten. Den här rapporten skapades i föregående uppgifter.

När Grace har publicerat rapporten blir nästa steg att skapa en instrumentpanel i Power BI-tjänsten med namnet *TabularDynamicSec* som baseras på rapporten. I följande bild framgår det att Grace kan se data för alla försäljningsregioner.

   ![Instrumentpanel i Power BI-tjänsten](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)

Nu delar Grace instrumentpanelen med sin kollega Rita, som ansvarar för försäljningen i regionen Australia.

   ![Dela en Power BI-instrumentpanel](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)

När Rita loggar in på Power BI-tjänsten och visar den delade instrumentpanel som Grace skapade ska endast försäljningen från regionen Australien visas.

Grattis! Power BI-tjänsten visar den dynamiska säkerhet på radnivå som definierats i den lokala Analysis Services-tabellmodellen. Power BI använder egenskapen `EffectiveUserName` till att skicka den aktuella Power BI-användarens autentiseringsuppgifter till den lokala datakällan för att köra frågorna.

## <a name="task-6-understand-what-happens-behind-the-scenes"></a>Uppgift 6: Förstå vad som händer i bakgrunden

I den här uppgiften förutsätts att du känner till [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler), eftersom du behöver samla in en SQL Server Profiler-spårning från din lokala SSAS-tabellinstans.

Sessionen initieras när användaren Rita öppnar instrumentpanelen i Power BI-tjänsten. Kan du se att rollen **salesterritoryusers** börjar gälla omedelbart med det gällande användarnamnet **<EffectiveUserName>rita@contoso.com</EffectiveUserName>**

       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>rita@contoso.com</EffectiveUserName></PropertyList>

Baserat på gällande begäran om användarnamn konverterar Analysis Services begäran till de faktiska autentiseringsuppgifterna `contoso\rita` efter att ha skickat en fråga till den lokala Active Directory. När Analysis Services får autentiseringsuppgifterna returnerar Analysis Services de data som användaren har behörighet att visa och komma åt.

Om det uppstår mer aktivitet i instrumentpanelen kan du med SQL Profiler se att en specifik fråga kommer tillbaka till Analysis Services-tabellmodellen som en DAX-fråga. Om Rita till exempel går från instrumentpanelen till den underliggande rapporten sker följande fråga.

   ![DAX-frågan kommer tillbaka till Analysis Services-modellen](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)

Nedan kan du även se den DAX-fråga som körs för att fylla i rapportdata.
   
   ```sql
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>rita@contoso.com</EffectiveUserName>
             <LocaleIdentifier>1033</LocaleIdentifier>
             <ClientProcessID>6408</ClientProcessID>
             <Format>Tabular</Format>
             <Content>SchemaData</Content>
             <Timeout>600</Timeout>
             <DbpropMsmdRequestID>8510d758-f07b-a025-8fb3-a0540189ff79</DbpropMsmdRequestID>
             <DbPropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbPropMsmdActivityID>
             <ReturnCellProperties>true</ReturnCellProperties>
             <DbpropMsmdFlattened2>true</DbpropMsmdFlattened2>
             <DbpropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbpropMsmdActivityID>
           </PropertyList>
   ```

## <a name="considerations"></a>Att tänka på

* Lokal säkerhet på radnivå med Power BI är bara tillgänglig med en live-anslutning.

* Om data ändras efter att modellen har bearbetats visas de omedelbart för användare som har åtkomst till rapporten via en live-anslutning från Power BI-tjänsten.

