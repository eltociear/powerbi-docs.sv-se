---
title: Använda DirectQuery i Power BI Desktop
description: Använd DirectQuery, även kallat en live-anslutning i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d8432ae10afab6cbf12c017a8f315fd55825212d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77427241"
---
# <a name="use-directquery-in-power-bi-desktop"></a>Använda DirectQuery i Power BI Desktop
När du ansluter till din datakälla i *Power BI Desktop* kan du alltid importera en kopia av data till Power BI Desktop. En annan metod är tillgänglig för vissa datakällor: att ansluta direkt till datakällan med DirectQuery.

## <a name="supported-data-sources"></a>Datakällor som stöds
Du kan se en fullständig lista med de datakällor som har stöd för DirectQuery i [Datakällor som stöds av DirectQuery](power-bi-data-sources.md).

## <a name="how-to-connect-using-directquery"></a>Så ansluter du med DirectQuery
När du använder **Hämta data** för att ansluta till en datakälla som stöds av DirectQuery kan du välja anslutningsmetod i dialogrutan. I Power BI Desktop går du till menyfliksområdet **Start** och väljer **Hämta data** > **SQL Server**. I dialogrutan **SQL Server-databas** så har **Läge för dataanslutning** alternativen **Import** och **DirectQuery**:

![Alternativen Import och DirectQuery i dialogrutan SQL Server-databas, Power BI Desktop](media/desktop-use-directquery/directquery_sqlserverdb.png)

Här är skillnaderna mellan att välja **Import** och **DirectQuery**:

- **Import**: Valda tabeller och kolumner importeras till Power BI Desktop. När du skapar eller interagerar med en visualisering använder Power BI Desktop importerade data. Om du vill se dataändringar som gjorts sedan den senaste importen måste du uppdatera dina data, och då läses hela datamängden in på nytt.

- **DirectQuery**: Inga data importeras eller kopieras till Power BI Desktop. För relationella källor visas valda tabeller och kolumner i listan **Fält**. Flerdimensionella källor som SAP Business Warehouse dimensioner och mått i den markerade kuben visas i listan **Fält**. När du skapar eller interagerar med en visualisering kör Power BI Desktop frågor mot den underliggande datakällan, så du visar alltid aktuella data.

Många datamodelleringar och datatransformationer är tillgängliga när du använder DirectQuery, men med vissa begränsningar. När du skapar eller interagerar med en visualisering måste du köra frågor mot den underliggande källan. Hur lång tid det tar att uppdatera visualiseringen beror på den underliggande datakällans prestanda. När de data som behövs för att hantera förfrågan nyligen har använts så använder Power BI Desktop den nyligen använda versionen för att kunna visa det visuella objektet snabbare. Om du väljer **Uppdatera** från menyfliksområdet **Start** uppdateras alla visualiseringar med aktuella data.

I artikeln [Power BI och DirectQuery](desktop-directquery-about.md) beskrivs DirectQuery i detalj. Du kan även läsa mer om fördelar, begränsningar och viktiga överväganden när du använder DirectQuery i de här avsnitten.

## <a name="benefits-of-using-directquery"></a>Fördelar med att använda DirectQuery
Det finns några fördelar med att använda DirectQuery:

- Med DirectQuery kan du skapa visualiseringar över mycket stora datamängder där det annars inte skulle praktiskt genomförbart att först importera alla data med förhandsaggregering.
- Underliggande dataändringar kan göra att data måste uppdateras. I en del rapporter kan behovet av att visa aktuella data medföra stora dataöverföringar, och då är det inte rimligt att importera alla data. I DirectQuery-rapporter används å andra sidan alltid aktuella data.
- Datamängdsbegränsning på 1 GB gäller *inte* för DirectQuery.

## <a name="limitations-of-directquery"></a>Begränsningar hos DirectQuery
Det finns några begränsningar när du använder DirectQuery:

- Om frågan i **frågeredigeraren** är alltför komplex uppstår ett fel. Du kan lösa felet genom att antingen ta bort det problematiska steget i **frågeredigeraren** eller *importera* data istället för att använda DirectQuery. För flerdimensionella källor som SAP Business Warehouse finns det ingen **frågeredigerare**.

- Det finns inga tidsinformationsfunktioner i DirectQuery. Det går till exempel inte att behandla datumkolumner (som år, kvartal, månad och dag) annorlunda i DirectQuery-läge.

- Det finns begränsningar för DAX-uttryck som tillåts i mått så att frågor som skickas till den underliggande datakällan har acceptabel prestanda.

- Det finns en begränsning på en miljon rader för att returnera data när du använder DirectQuery, såvida du inte använder en Premium-kapacitet. Den här begränsningen påverkar inte aggregeringar eller beräkningar som används till att skapa datamängden som returneras med DirectQuery. Den gäller bara de rader som returneras. Premium-kapaciteter kan ange gränser för maximalt antal rader, så som beskrivs i [det här inlägget](https://powerbi.microsoft.com/blog/five-new-power-bi-premium-capacity-settings-is-available-on-the-portal-preloaded-with-default-values-admin-can-review-and-override-the-defaults-with-their-preference-to-better-fence-their-capacity/). 

    Du kan till exempel aggregera 10 000 000 rader med din fråga som körs mot datakällan. Frågan returnerar resultatet av aggregeringen till Power BI med DirectQuery om de Power BI-data som returneras innehåller färre än 1 000 000 rader. Om över 1 miljon rader returneras från DirectQuery så returnerar Power BI ett fel (såvida inte i Premium-kapacitet används, och radantalet understiger den administratörsfastställda gränsen).

## <a name="important-considerations-when-using-directquery"></a>Att tänka på när du använder DirectQuery
Du måste tänka på följande tre punkter när du använder DirectQuery:

- **Prestanda och belastning**: Alla DirectQuery-förfrågningar skickas till källdatabasen, så hur lång tid det tar att uppdatera ett visuellt objekt beror på hur lång tid tar att svara med frågeresultatet. Rekommenderad svarstid är högst fem sekunder (där begärda data returneras) när du använder DirectQuery för visuella objekt, maximal rekommenderad är 30 sekunder. Om det tar längre blir upplevelsen för användaren oacceptabel. När en rapport har publicerats till Power BI-tjänsten kan alla frågor som tar längre tid än några minuter avbrytas och användaren får då ett felmeddelande.
  
    Belastningen på källdatabasen bör också övervägas, baserat på antalet Power BI-användare som kommer att använda den publicerade rapporten. Att använda **säkerhet på radnivå** (RLS) kan också ha stor inverkan. En panel på instrumentpanelen som delas av flera användare och inte har RLS genererar en enda fråga till databasen. Om RLS används för panelen innebär det dock att en uppdatering kräver en fråga *per användare*, vilket avsevärt ökar belastningen på källdatabasen och kan påverka systemets prestanda.
  
    Power BI skapar så effektiva frågor som möjligt. I en del situationer kan dock den fråga som genereras vara så ineffektiv att uppdateringar misslyckas. Ett exempel på det här är när en genererad fråga returnerar ett mycket stort antal rader från datakällan i serverdelen. I så fall ser du följande fel:

    ```output
    The resultset of a query to external data source has exceeded
    ```
  
    Den här situationen kan uppstå med ett enkelt diagram som innehåller en mycket hög kardinalitet-kolumn med aggregeringsalternativet inställt på **Sammanfatta inte**. Det visuella objektet måste ha kolumner med en kardinalitet under 1 miljon, eller så måste du använda lämpliga filter.

- **Säkerhet**: Som standard kan alla användare som använder en publicerad rapport ansluta till datakällan i serverdelen med de autentiseringsuppgifter som anges efter publiceringen till Power BI-tjänsten. Samma sak gäller för data som importeras: alla användare ser samma data, oavsett vilka säkerhetsregler som har definierats för källan i serverdelen.

    Kunder som vill implementera användarbaserad säkerhet för DirectQuery-källor bör antingen använda RLS eller konfigurera Kerberos-begränsad autentisering mot källan. Kerberos är inte tillgängligt för alla källor. [Läs mer om RLS](service-admin-rls.md). [Läs mer om Kerberos i DirectQuery](service-gateway-sso-kerberos.md).

- **Funktioner som stöds**: Det är inte alla funktioner i Power BI Desktop som stöds i DirectQuery-läge, och andra funktioner har begränsningar. Dessutom är det vissa funktioner i Power BI-tjänsten (som *Snabbinsikter*) som inte är tillgängliga för datamängder som använder DirectQuery. När du bestämmer om du ska använda DirectQuery bör du ha de här begränsningarna i åtanke.

## <a name="publish-to-the-power-bi-service"></a>Registrera dig på Power BI-tjänsten
Rapporter som skapas med DirectQuery kan publiceras i Power BI-tjänsten.

Om den datakälla du använder inte behöver en **lokal datagateway** (**Azure SQL Database**, **Azure SQL Data Warehouse** eller **Redshift**) måste du tillhandahålla autentiseringsuppgifter innan Power BI-tjänsten visar den publicerade rapporten. Gör så här för att ange autentiseringsuppgifterna:

1. Logga in i [Power BI](https://www.powerbi.com/).
2. Välj **kugghjulsikonen** i Power BI-tjänsten och sedan alternativet **Inställningar**.

    ![Inställningar, Power BI-tjänsten](media/desktop-use-directquery/directquery_pbiservicesettings.png)

3. På sidan **Inställningar** i Power BI-tjänsten väljer du fliken **Datamängder**, den datamängd som använder DirectQuery och sedan **Redigera autentiseringsuppgifter**.

4. Lägg till autentiseringsuppgifterna. Annars inträffar ett fel när du öppnar en publicerad rapport eller utforskar en datamängd som har skapats via en DirectQuery-anslutning.

Om du vill skapa en dataanslutning för andra datakällor än **Azure SQL Database**, **Azure SQL Data Warehouse**, **Redshift** eller **Snowflake Data Warehouse** som använder DirectQuery måste du installera en **lokal datagateway** och registrera datakällan. Mer information finns i [Vad är en lokal datagateway?](service-gateway-onprem.md)

## <a name="next-steps"></a>Nästa steg
Mer information om DirectQuery finns i följande resurser:

- [Använd DirectQuery i Power BI](desktop-directquery-about.md)
- [Datakällor som stöds av DirectQuery](power-bi-data-sources.md)
- [DirectQuery och SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
- [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)
- [Vad är en lokal datagateway?](service-gateway-onprem.md)
