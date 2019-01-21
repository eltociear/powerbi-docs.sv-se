---
title: Dynamisk säkerhet på radnivå med Analysis Services-tabellmodell i Power BI
description: Dynamisk säkerhet på radnivå med Analysis Services-tabellmodell
author: selvarms
manager: amitaro
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 10/21/2017
ms.author: selvar
LocalizationGroup: Connect to data
ms.openlocfilehash: 546ae48aac10ae6c72a062665c7d8f448432a194
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54292647"
---
# <a name="dynamic-row-level-security-with-analysis-services-tabular-model"></a>Dynamisk säkerhet på radnivå med Analysis Services-tabellmodell
Den här självstudien visar de steg som krävs för att implementera **säkerhet på radnivå** inom din **Analysis Services-tabellmodell** samt hur du använder den i en Power BI-rapport. Stegen i den här självstudien har utformats så att du kan följa med och lära dig de steg som krävs genom att slutföra en samplingsdatauppsättning.

Under självstudien beskrivs följande steg i detalj, vilket hjälper dig att förstå vad du behöver göra om du vill implementera dynamisk säkerhet på radnivå med Analysis Services-tabellmodellen:

* Skapa en ny säkerhetstabell i databasen **AdventureworksDW2012**
* Skapa tabellmodellen med nödvändiga fakta- och dimensionstabeller
* Definiera roller och behörigheter för användarna
* Distribuera modellen till en **Analysis Services-tabell**instans
* Använd Power BI Desktop för att skapa en rapport som visar datan som motsvarar användarens åtkomst till rapporten
* Distribuera rapporten till **Power BI-tjänsten**
* Skapa en ny instrumentpanel som baseras på rapporten och slutligen,
* Dela instrumentpanelen med dina medarbetare

För att följa stegen i den här självstudien behöver du databasen **AdventureworksDW2012**, som du kan hämta från **[lagringsplatsen](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)**.

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>Uppgift 1: Skapa användarens säkerhetstabell och definiera datarelationen
Det finns många publicerade artiklar som beskriver hur du definierar dynamisk säkerhet på radnivå med **SQL Server Analysis Services (SSAS) tabell**modell. I vårt exempel följer vi artikeln [Implement Dynamic Security by Using Row Filters](https://msdn.microsoft.com/library/hh479759.aspx) (Implementera dynamisk säkerhet med hjälp av radfilter). Följande steg vägleder dig genom den första aktiviteten i självstudien:

1. I vårt exempel använder vi relationsdatabasen **AdventureworksDW2012**. I databasen skapar du tabellen **DimUserSecurity**, enligt följande bild. I det här exemplet använder vi SQL Server Management Studio (SSMS) till att skapa tabellen.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)
2. När tabellen har skapats och sparats måste vi skapa relationen mellan **DimUserSecurity**-tabellens **SalesTerritoryID**-kolumn och **DimSalesTerritory**-tabellens **SalesTerritoryKey**-kolumn, enligt följande bild. Detta kan göras från **SSMS** genom att högerklicka på tabellen **DimUserSecurity** och välja **Design**. Välj sedan **Tabelldesigner -> Relationer...** på menyn.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)
3. Spara tabellen och lägg sedan till några rader med användarinformation i tabellen genom att högerklicka igen på **DimUserSecurity**-tabellen och sedan välja **Redigera de översta 200 raderna**. När du har lagt till användarna kommer raderna i tabellen **DimUserSecurity** se ut som i följande bild:
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)
   
   Vi återkommer till dessa användare i senare uppgifter.
4. Därefter gör vi en *inre koppling* med **DimSalesTerritory**-tabellen, vilket visar regionsinformationen som är associerad med användaren. Följande kod utför den *inre kopplingen* och bilden nedan visar tabellen när den *inre kopplingen* är klar.
   
       select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join  [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_join_users.png)
5. Observera att bilden ovan visar information som till exempel vilken användare som är ansvarig de olika försäljningsregionerna. Den informationen visas på grund av relationen som vi skapade i **steg 2**. Observera också att användaren **Jon Doe ingår i Australiens försäljningsregion**. Vi kommer tillbaka till Jon Doe i kommande steg och uppgifter.

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>Uppgift 2: Skapa tabellmodellen med fakta- och dimensionstabeller
1. När ditt relationsinformationslager finns på plats är det dags att definiera tabellmodellen. Modellen kan skapas med **SQL Server Data Tools (SSDT)**. Om du vill veta mer om hur du definierar en tabellmodell kan du läsa informationen i [Create a New Tabular Model Project](https://msdn.microsoft.com/library/hh231689.aspx) (Skapa ett nytt tabellmodellsprojekt).
2. Importera alla nödvändiga tabeller till modellen enligt vad som visas nedan.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)
3. När du har importerat tabellerna som krävs, måste du definiera en roll med namnet **SalesTerritoryUsers** med **Läs** behörighet. Detta gör du genom att klicka på menyn **Modell** i SQL Server Data Tools och sedan på **Roller**. I dialogrutan **Rollhanteraren** klickar du på **Ny**.
4. Under fliken **Medlemmar** i **Rollhanteraren** lägger du till de användare som vi definierade i tabellen **DimUserSecurity** i **Uppgift 1 – steg 3**.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)
5. Lägg till rätt funktioner för både **DimSalesTerritory**- och **DimUserSecurity**-tabellerna enligt vad som visas nedan på fliken **Radfilter**.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)
6. I det här steget ska vi använda funktionen **LOOKUPVALUE** till att returnera värden för en kolumn där Windows-användarnamnet är samma som användarnamnet som returneras av funktionen **USERNAME**. Frågorna kan sedan begränsas när värdena som returneras av **LOOKUPVALUE** matchar värden i samma eller en relaterad tabell. I kolumnen **DAX-filter** skriver du följande formel:
   
       =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])
    I den här formeln returnerar funktionen **LOOKUPVALUE** alla värden för kolumnen **DimUserSecurity[SalesTerritoryID]** när **DimUserSecurity[UserName]** är samma som det aktuella inloggade Windows-användarnamnet och **DimUserSecurity[SalesTerritoryID]** är samma som **DimSalesTerritory[SalesTerritoryKey]**.
   
    > [!IMPORTANT]
    > Tänk på att DAX-funktionen [USERELATIONSHIP](https://msdn.microsoft.com/query-bi/dax/userelationship-function-dax) inte stöds när du använder säkerhet på radnivå.

   Uppsättningen för SalesTerritoryKey som returnerades av **LOOKUPVALUE** används sedan för att begränsa de rader som visas i **DimSalesTerritory**. Endast rader där **SalesTerritoryKey** för raden finns i uppsättningen med ID:n som returnerades av funktionen **LOOKUPVALUE** visas.
8. Skriv följande formel för tabellen **DimUserSecurity** i kolumnen **DAX-filter**:
   
       =FALSE()

    Den här formeln anger att alla kolumner matchar det falska booleska villkoret, därför går det inte att fråga efter några kolumner för tabellen **DimUserSecurity**.
1. Vi måste nu bearbeta och distribuera modellen. Du kan läsa [artikeln om Distribution](https://msdn.microsoft.com/library/hh231693.aspx) om du behöver hjälp med att distribuera modellen.

## <a name="task-3-adding-data-sources-within-your-on-premises-data-gateway"></a>Uppgift 3: Lägga till datakällor inom din lokala datagateway
1. När din tabellmodell har distribuerats och är redo för användning, måste du lägga till en datakällsanslutning till din lokala Analysis Services-tabellserver i Power BI-portalen.
2. För att kunna ge **Power BI-tjänsten** åtkomst till din lokala analystjänst måste du ha en **[lokal datagateway](service-gateway-onprem.md)** installerad och konfigurerad i din miljö.
3. När gatewayen är korrekt konfigurerad måste du skapa en datakällsanslutning för din **Analysis Services**-tabellinstans. Den här artikeln hjälper dig med att [lägga till en datakälla i Power BI-portalen](service-gateway-enterprise-manage-ssas.md).
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)
4. När det föregående steget är klart är gatewayen konfigurerad och redo att interagera med din lokala **Analysis Services**-datakälla.

## <a name="task-4-creating-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>Uppgift 4: Skapa en rapport baserad på analystjänsternas tabellmodell med Power BI Desktop
1. Vi börjar i **Power BI Desktop** och väljer **Hämta data > Databas**.
2. I listan med datakällor väljer du **SQL Server Analysis Services-databas** och **Anslut**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)
3. Fyll i informationen för **Analysis Services**-tabellinstansen och välj **Anslut live**. Välj **OK**. I **Power BI** fungerar dynamisk säkerhet enbart med en **live-anslutning**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)
4. Du ser att den modell som distribuerades finns i **Analysis Services**-instansen. Välj respektive modell och välj **OK**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)
5. **Power BI Desktop** visar nu alla tillgängliga fält till höger om arbetsytan i fönstret **Fält**.
6. I fönstret **Fält** till höger väljer du **SalesAmount**-måttet från **FactInternetSales**-tabellen och **SalesTerritoryRegion**-dimensionen från **SalesTerritory**-tabellen.
7. Vi håller rapporten enkel, så nu ska vi inte lägga till flera kolumner. För att få en mer meningsfull återgivning av dessa data ska vi ändra visualiseringen till ett **ringdiagram**.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)
8. När rapporten är klar kan du publicera den direkt till Power BI-portalen. Välj **Publicera** i menyfliksområdet **Start** i **Power BI Desktop**.

## <a name="task-5-creating-and-sharing-a-dashboard"></a>Uppgift 5: Skapa och dela en instrumentpanel
1. När du har skapat rapporten och klickat på **Publicera** i **Power BI Desktop**, publiceras rapporten till **Power BI**-tjänsten. Nu när den används kan vårt modellsäkerhetsscenario visas med hjälp av de exempel som vi skapade i föregående steg.
   
   **Försäljningschefen Sumit** kan se data från alla de olika försäljningsregionerna. Så han skapar den här rapporten (rapporten som skapas i föregående uppgift) och publicerar den till Power BI-tjänsten.
   
   När han publicerar rapporten skapar han en instrumentpanel i Power BI-tjänsten med namnet **TabularDynamicSec**, som baseras på rapporten. I följande bild kan du se att försäljningschefen (Sumit) kan visa de data som motsvarar alla försäljningsregioner.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)
2. Sumit delar nu instrumentpanelen med sin kollega Jon Doe, som ansvarar för försäljningen i Australien.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/user_jon_doe.png)
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)
3. När Jon Doe loggar in på **Power BI**-tjänsten och visar den delade instrumentpanel som Sumit skapade, bör han **endast** se försäljningen från den region som han ansvarar för. Så Jon Doe loggar in, öppnar den instrumentpanel som Sumit delade med honom och ser **endast** försäljningen från Australien.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/dashboard_jon_doe.png)
4. Grattis! Den dynamiska säkerhet på radnivå som definierades i den lokala **Analysis Services**-tabellmodellen återspeglas och visas i **Power BI**-tjänsten. Power BI använder egenskapen **effectiveusername** till att skicka den aktuella Power BI-användarens autentiseringsuppgifter till den lokala datakällan för att köra frågorna.

## <a name="task-6-understanding-what-happens-behind-the-scenes"></a>Uppgift 6: Förstå vad som händer i bakgrunden
1. Den här uppgiften förutsätter att du känner till SQL Profiler, eftersom du behöver samla in en SQL Server Profiler-spårning i din lokala SSAS-tabellinstans.
2. Sessionen initieras när användaren (i det här fallet Jon Doe) öppnar instrumentpanelen i Power BI-tjänsten. Kan du se att rollen **salesterritoryusers** börjar gälla omedelbart med det gällande användarnamnet **<EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>**
   
       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>jondoe@moonneo.com</EffectiveUserName></PropertyList>
3. Baserat på begäran från det gällande användarnamnet konverterar Analysis Services begärandet till autentiseringsuppgifterna moonneo\jondoe efter att ha skickat en fråga till den lokala Active Directory. Så snart **Analysis Services** får de faktiska autentiseringsuppgifterna från Active Directory kommer **Analysis Services** endast returnera de data som användaren har behörighet för.
4. Om det uppstår mer aktivitet i instrumentpanelen, till exempel om Jon Doe går från instrumentpanelen till den underliggande rapporten, kan med SQL Profiler en specifik fråga komma tillbaka till Analysis Services-tabellmodellen som en DAX-fråga.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)
5. Du kan också se den DAX-fråga som körs för att fylla i data för rapporten nedan.
   
   ```
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>
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
Det finns några saker att tänka på när du arbetar med säkerhet på radnivå, SSAS och Power BI:

1. Lokal säkerhet på radnivå med Power BI är bara tillgänglig med en live-anslutning.
2. Ändringar i data efter bearbetning av modellen blir omedelbart tillgängliga för användare (som har åtkomst till rapporten med en **live-anslutning**) från Power BI-tjänsten.

