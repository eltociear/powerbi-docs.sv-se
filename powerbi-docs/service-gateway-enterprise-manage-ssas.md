---
title: Hantera din datakälla – Analysis Services
description: Hantera den lokala datagatewayen och datakällorna som tillhör denna gateway. Detta avser Analysis Services i både flerdimensionellt läge och tabelläge.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 93475f6476f8baad73229473bd3ce60db68a320b
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271661"
---
# <a name="manage-your-data-source---analysis-services"></a>Hantera din datakälla – Analysis Services

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

När du har [installerat den lokala datagatewayen](/data-integration/gateway/service-gateway-install) behöver du [lägga till datakällor](service-gateway-data-sources.md#add-a-data-source) som kan användas med gatewayen. Den här artikeln handlar om hur du kan arbeta med gatewayer och Analysis Services-datakällor som används för antingen schemalagd uppdatering eller live-anslutningar.

[Titta på den här videon](https://www.youtube.com/watch?v=GPf0YS-Xbyo&feature=youtu.be) om du vill veta mer om hur du konfigurerar en live-anslutning till Analysis Services.

> [!NOTE]
> Om du har en Analysis Services-datakälla måste du installera gatewayen på en dator som ingår i samma skog/domän som Analysis Services-servern.

## <a name="add-a-data-source"></a>Lägga till en datakälla

Information om hur du lägger till en datakälla finns i [Lägga till en datakälla](service-gateway-data-sources.md#add-a-data-source). Välj Analysis Services för **Typ av datakälla** om du ansluter till en flerdimensionell server eller tabellserver.

![Lägga till Analysis Services-datakällan](media/service-gateway-enterprise-manage-ssas/datasourcesettings2-ssas.png)

Du kan fylla i informationen för datakällan med **Server** och **Databas**. Den **användarnamn** och **lösenord** som du anger används av gatewayen för att ansluta till Analysis Services-instansen.

> [!NOTE]
> Det Windows-konto som du anger måste ha serveradministratörsbehörighet för den instans som du ansluter till. Om det här kontots lösenord upphör att gälla, kan användaren få ett anslutningsfel om lösenordet inte uppdateras för datakällan. Mer information om hur autentiseringsuppgifter lagras finns i [Lagra krypterade autentiseringsuppgifter i molnet](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud).

![Fylla i inställningarna för datakälla](media/service-gateway-enterprise-manage-ssas/datasourcesettings3-ssas.png)

Välj **Lägg till** när du har fyllt i allt. Du kan nu använda den här datakällan för schemalagd uppdatering eller realtidsanslutningar mot en lokal Analysis Services-instans. *Anslutningen lyckades* visas om anslutningen har lyckats.

![Visa anslutningsstatus](media/service-gateway-enterprise-manage-ssas/datasourcesettings4.png)

### <a name="advanced-settings"></a>Avancerade inställningar

Om du vill kan du konfigurera sekretessnivån för datakällan. Detta styr hur data kan kombineras. Det används endast vid schemalagd uppdatering. Det gäller inte för realtidsanslutningar. Mer information om sekretessnivåer för datakälla finns i [Sekretessnivåer (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Ange sekretessnivån](media/service-gateway-enterprise-manage-ssas/datasourcesettings9.png)

## <a name="usernames-with-analysis-services"></a>Användarnamn med Analysis Services

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qb5EEjkHoLg" frameborder="0" allowfullscreen></iframe>

Varje gång en användare interagerar med en rapport ansluten till Analysis Services, skickas det effektiva användarnamnet till gatewayen och sedan vidare till den lokala Analysis Services-servern. Den e-postadress som du loggar in i molnet med är det vi skickar till Analysis Services som den gällande användaren. Detta skickas vidare i anslutningsegenskapen [EffectiveUserName](https://msdn.microsoft.com/library/dn140245.aspx#bkmk_auth). E-postadressen ska matcha ett definierat UPN (användarens huvudnamn) i den lokala Active Directory-domänen. UPN är en egenskap för ett Active Directory-konto. Det Windows-kontot måste sedan vara förekomma i en Analysis Services-roll. Om ingen matchning hittas i Active Directory lyckas inte inloggningen. Mer information om Active Directory och namngivning av användare finns i [Attribut för namngivning av användare](https://msdn.microsoft.com/library/ms677605.aspx).

Du kan även [mappa ditt Power BI-inloggningsnamn med en lokal katalog-UPN](service-gateway-enterprise-manage-ssas.md#mapping-usernames-for-analysis-services-data-sources).

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Mappa användarnamn för Analysis Services-datakällor

<iframe width="560" height="315" src="https://www.youtube.com/embed/eATPS-c7YRU" frameborder="0" allowfullscreen></iframe>

Power BI tillåter mappning av användarnamn för Analysis Services-datakällor. Du kan konfigurera regler för att mappa ett användarnamn som är inloggat på Power BI till ett namn som har skickats för EffectiveUserName på Analysis Services-anslutningen. Mappningsanvändarnamnsfunktionenär till stor hjälp när användarnamnet i AAD inte matchar ett UPN i ditt lokala Active Directory. Om din e-postadress t.ex. är nancy@contoso.onmicrsoft.com, kan du mappa den till nancy@contoso.com, och det värdet skickas då till gatewayen.

Du kan mappa användarnamn för Analysis Services på två olika sätt:

* Manuell användarmappning
* Lokal Active Directory-egenskapssökning för att mappa om AAD UPN:er till Active Directory-användare (AD-sökningsmappning)

Även om det är möjligt att utföra manuell mappning med den andra metoden kan det vara tidskrävande och svårt att underhålla. Det är särskilt svårt när mönstermatchning inte räcker till, till exempel när domännamn skiljer sig mellan AAD och lokal AD, eller när namn på användarkonton skiljer sig mellan AAD och AD. Därför rekommenderas inte manuell mappning med den andra metoden.

Dessa två metoder beskrivs i turordning i följande två avsnitt.

### <a name="manual-user-name-re-mapping"></a>Manuell mappning av användarnamn

Du kan konfigurera anpassade regler för UPN (User Principal Name) för Analysis Services-datakällor. Detta hjälper dig om dina inloggningsuppgifter för Power BI-tjänsten inte överensstämmer med din lokala katalog-UPN. Om du till exempel loggar in i Power BI med john@contoso.com, men din lokala katalog-UPN är john@contoso.local, kan du konfigurera en mappningsregel för att skicka john@contoso.local till Analysis Services.

Gör följande för att komma till UPN-mappningsskärmen.

1. Gå till **kugghjulsikonen** och välj **Hantera gatewayer**.
2. Expandera den gateway som innehåller Analysis Services-datakällan. Om du inte har skapat Analysis Services-datakällan än, kan du göra det nu.
3. Välj datakällan och välj sedan fliken **Användare**.
4. Välj **Mappa användarnamn**.

    ![Skärm för UPN-mappning](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_02.png)

Därefter visas alternativen för att lägga till regler samt test för en viss användare.

> [!NOTE]
> Du kan hända att du oavsiktligt ändrar en användare som du inte hade för avsikt att ändra. Om till exempel **Ersätt (ursprungligt värde)** är <em>@contoso.com</em> och **Med (nytt namn)** är <em>@contoso.local</em>, kommer alla användare med en inloggning som innehåller <em>@contoso.com</em> att ersättas med <em>@contoso.local</em>. Om **Ersätt (ursprungligt namn)** är <em>dave@contoso.com</em> och **Med (nytt namn)** är <em>dave@contoso.local</em>, skickas en användare med inloggningen v-dave@contoso.com som v-dave<em>@contoso.local</em>.

### <a name="ad-lookup-mapping"></a>Mappning av AD-sökningar

Följ stegen i det här avsnittet om du vill mappa om AAD UPN:er till Active Directory-användare för att utföra en lokal AD-egenskapssökning. Vi börjar med att titta närmare på hur det här fungerar.

I **Power BI-tjänsten** inträffar följande:

* För varje fråga från en Power BI AAD-användare till en lokal SSAS-server skickas en UPN-sträng vidare, exempelvis: firstName.lastName@contoso.com

> [!NOTE]
> Alla manuella UPN-användarmappningar som definierats i Power BI-datakällskonfigurationen används fortfarande *innan* användarnamnssträngen skickas till den lokala datagatewayen.

Gör följande på den lokala datagatewayen med konfigurerbar anpassad användarmappning:

1. Hitta Active Directory för att söka (automatiskt eller konfigurerbart).
2. Leta upp attributet för AD-personen (till exempel *e-post*) baserat på inkommande UPN-sträng (”firstName.lastName@contoso.com”) från **Power BI-tjänsten**.
3. Om AD-sökningen misslyckas, försöker den använda den vidareskickade UPN:en som EffectiveUser till SSAS.
4. Om AD-sökningen lyckas, hämtas *UserPrincipalName* för AD-personen.
5. Den vidarebefordrar e-postadress för *UserPrincipalName* som *EffectiveUser* till SSAS, exempelvis <em>Alias@corp.on-prem.contoso</em>.

Så här konfigurerar du gatewayen för att utföra AD-sökningen:

1. [Ladda ned och installera den senaste gatewayen](/data-integration/gateway/service-gateway-install).

2. I gatewayen behöver du ändra den **lokala datagatewaytjänsten** för att köras med ett domänkonto (i stället för ett lokalt tjänstkonto – annars fungerar inte AD-sökningen vid körning). Gå till [appen för lokal datagateway](/data-integration/gateway/service-gateway-app) på datorn och gå sedan till **Tjänstinställningar > Byt servicekonto**. Kontrollera att du har återställningsnyckeln för gatewayen eftersom du behöver återställa den på samma dator om du inte vill skapa en ny gateway i stället. Du måste starta om gatewaytjänsten för att ändringen ska börja gälla.

3. Gå till gatewayens installationsmappen, *C:\Program Files\On-premises data gateway* som administratör, så att du har skrivbehörighet, och öppna filen *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

4. Redigera följande två konfigurationsvärden enligt *dina* Active Directory-attributkonfigurationer för AD-användarna. Konfigurationsvärdena nedan är bara exempel – du måste ange dem baserat på din Active Directory-konfiguration. De här konfigurationerna är skiftlägeskänsliga, så se till att de matchar värdena i Active Directory.

    ![Azure Active Directory-inställningar](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_03.png)

    Om inget värde har angetts för ADServerPath-konfigurationen använder gatewayen standardvärdet, Global katalog. Du kan också ange flera värden för ADServerPath. Varje värde måste vara avgränsat med semikolon som i följande exempel.

    ```xml
    <setting name="ADServerPath" serializeAs="String">
        <value> >GC://serverpath1; GC://serverpath2;GC://serverpath3</value>
    </setting>
    ```

    Gatewayen parsar värdena för ADServerPath från vänster till höger tills den hittar en matchning. Om ingen matchning hittas används ursprungligt UPN. Kontrollera att det konto som kör gatewaytjänsten (PBIEgwService) har behörighet att skicka frågor till alla AD-servrar som du angett i ADServerPath.

    Gatewayen stöder två typer av ADServerPath, som i följande exempel.

    **WinNT**

    ```xml
    <value="WinNT://usa.domain.corp.contoso.com,computer"/>
    ```

    **GC**

    ```xml
    <value> GC://USA.domain.com </value>
    ```

5. Du måste starta om den **lokala datagatewaytjänsten** för att konfigurationsändringen ska börja gälla.

### <a name="working-with-mapping-rules"></a>Arbeta med mappningsregler

För att skapa en mappningsregel anger du ett värde för **Ursprungligt namn** och **Nytt namn** och väljer sedan **Lägg till**.

| Fält | Beskrivning |
| --- | --- |
| Ersätt (ursprungligt namn) |Den e-postadress som du loggade in i Power BI med. |
| Med (nytt namn) |Det värde som du vill ersätta det med. Resultatet av ersättningen är vad som skickas till egenskapen *EffectiveUserName* för Analysis Services-anslutningen. |

![Skapa en mappningsregel](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-effective-user-names.png)

När du markerar ett objekt i listan kan du välja att ordna om det med hjälp av **sparrikonerna** eller **Ta bort** posten.

![Ändra ordning på ett objekt i listan](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-entry-selected.png)

### <a name="using-wildcard-"></a>Använda jokertecken (\*)

Du kan använda ett jokertecken för din sträng **Ersätt (ursprungligt namn)** . Det kan bara användas på egen hand och inte med någon annan strängdel. På så vis kan du ta med alla användare och skicka ett enda värde till datakällan. Detta är användbart när du vill att alla användare i din organisation ska använda samma användare i den lokala miljön.

### <a name="test-a-mapping-rule"></a>Testa en mappningsregel

Du kan verifiera vad ett ursprungligt namn kommer att ersättas med genom att ange ett värde för **Ursprungligt namn** och välja **Testa regel**.

![Testa en mappningsregel](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-test-mapping-rule.png)

> [!NOTE]
> Det tar några minuter för tjänsten att börja använda de regler som sparas. I webbläsaren fungerar regeln omedelbart.

### <a name="limitations-for-mapping-rules"></a>Begränsningar för mappningsregler

Mappningen gäller för den specifika datakälla som konfigureras. Det är inte en global inställning. Om du har flera Analysis Services-datakällor måste du mappa användarna för varje datakälla.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autentisering till en levande Analysis Services-datakälla

Varje gång en användare interagerar med Analysis Services skickas det effektiva användarnamnet till en gateway och sedan vidare till den lokala Analysis Services-servern. Användarens huvudnamn (UPN), vanligtvis den e-postadress du loggar in på molnet med, är det vi skickar till Analysis Services som den gällande användaren. UPN skickas i anslutningsegenskapen EffectiveUserName. E-postadressen måste matcha en definierad UPN inom den lokala Active Directory-domänen. UPN-namnet är en egenskap för ett Active Directory-konto. Det Windows-kontot måste sedan vara närvarande för att en Analysis Services-roll ska ha åtkomst till servern. Om ingen matchning hittas i Active Directory lyckas inte inloggningen.

Analysis Services kan också tillhandahålla filtrering baserat på det här kontot. Filtrering kan uppstå med rollbaserad säkerhet eller säkerhet på radnivå.

## <a name="role-based-security"></a>Rollbaserad säkerhet

Modeller tillhandahåller säkerhet utifrån användarroller. Roller definieras för ett visst modellprojekt under redigering i SQL Server Data Tools – Business Intelligence (SSDT BI), eller efter det att en modell har distribuerats med SQL Server Management Studio (SSMS). Roller innehåller medlemmar efter Windows-användarnamn eller Windows-grupp. Rollerna definierar de behörigheter för en användare har när det gäller att fråga eller utföra åtgärder i modellen. De flesta användare hör till en roll med läsbehörighet. Andra roller är avsedda för administratörer med behörighet att bearbeta objekt, hantera databasfunktioner och hantera andra roller.

## <a name="row-level-security"></a>Säkerhet på radnivå

Säkerhet på radnivå är specifik för Analysis Services-säkerhet på radnivå. Modeller kan tillhandahålla dynamisk säkerhet på radnivå. Till skillnad från att ha minst en roll som användarna tillhör, så krävs inte dynamisk säkerhet för tabellmodeller. På hög nivå definierar dynamisk säkerhet en användares läsbehörighet för data direkt ned till en viss rad i en viss tabell. I likhet med roller så bygger dynamisk säkerhet på radnivå på en användares Windows-användarnamn.

En användare möjlighet att fråga och visa modelldata bestäms i första hand genom vilka roller användarens Windows-användarkonto är medlem i, och i andra hand den dynamiska säkerheten på radnivå, om sådan har konfigurerats.

Rollimplementering och dynamisk säkerhet på radnivå i modeller ligger utanför den här artikelns fokus. Mer information finns i [Roller (SSAS Tabular)](https://msdn.microsoft.com/library/hh213165.aspx) och [Säkerhetsroller (Analysis Services – flerdimensionella Data)](https://msdn.microsoft.com/library/ms174840.aspx) på MSDN. Och om du vill ha riktigt djup förståelse av säkerhet för tabellmodeller kan du ladda ned och läsa [white paper om BI-semantikmodellen för tabeller](https://msdn.microsoft.com/library/jj127437.aspx).

## <a name="what-about-azure-active-directory"></a>Vad är Azure Active Directory?

Microsofts molntjänster använder [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) för att hantera autentiseringen av användare. Azure Active Directory är den klient som innehåller användarnamn och säkerhetsgrupper. Normalt är den e-postadress som en användare loggar in med densamma som kontots UPN-namn.

Vilken är mitt lokala Active Directorys roll?

För att Analysis Services ska kunna avgöra om en användare som ansluter tillhör en roll med behörighet att läsa data, så måste servern konvertera det effektiva användarnamn som skickades från AAD till gatewayen och vidare till Analysis Services-servern. Analysis Services-servern skickar det effektiva användarnamnet till en Windows Active Directory-domänkontrollant (DC). Active Directory-domänkontrollanten verifierar sedan att det effektiva användarnamnet är ett giltigt UPN för ett lokalt konto, och returnerar användarens Windows-användarnamn till Analysis Services-servern.

EffectiveUserName kan inte användas på en Analysis Services-server som inte är domänansluten. Analysis Services-servern måste vara ansluten till en domän, så att eventuella fel vid inloggningen undviks.

### <a name="how-do-i-tell-what-my-upn-is"></a>Hur vet jag vilken UPN jag har?

Du kanske inte vet vilken din UPN är, och du är kanske inte domänadministratör. Du kan använda följande kommando från din arbetsstation för att ta reda på ditt kontos UPN.

    whoami /upn

Resultatet ser ut ungefär som en e-postadress, men detta är det UPN som finns på ditt domänkonto. Om du använder en Analysis Services-datakälla för live-anslutningar, och om denna inte stämmer överens med den e-postadress som du loggar in i Power BI med, kan du titta närmare på hur det går till att [mappa användarnamn](#mapping-usernames-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Synkronisera ett lokalt Active Directory med Azure Active Directory

Dina lokala Active Directory-konton bör matcha Azure Active Directory om du ska använda Analysis Services live-anslutningar. Liksom att UPN-namnet måste matcha mellan kontona.

Molntjänsterna känner bara till konton i Azure Active Directory. Det spelar ingen roll om du har lagt till ett konto i ditt lokala Active Directory, eftersom det inte kan användas ifall det inte finns i AAD. Det finns olika sätt på vilka du kan matcha dina lokala Active Directory-konton med Azure Active Directory.

1. Du kan lägga till konton manuellt till Azure Active Directory.

   Du kan skapa ett konto på Azure-portalen eller i administrationscentret för Microsoft 365, och kontonamnet matchar UPN-namnet för det lokala Active Directory-kontot.

2. Du kan använda [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis)-verktyget för att synkronisera lokala konton med din Azure Active Directory-klient.

   Azure AD Connect-verktyget erbjuder alternativ för katalogsynkronisering och hur du konfigurerar autentisering, inklusive hash-synkronisering av lösenord, direktautentisering och federation. Om du inte är klientadministratör eller lokal domänadministratör behöver du kontakta IT-administratören om du vill få detta konfigurerat.

Med Azure AD Connect säkerställer du att UPN-namnet matchar mellan AAD och ditt lokala Active Directory.

> [!NOTE]
> När du synkroniserar konton med Azure AD Connect-verktyget skapas nya konton i AAD-klienten.

## <a name="using-the-data-source"></a>Använda datakällan

När du har skapat datakällan går den att använda med live-anslutningar eller med schemalagd uppdatering.

> [!NOTE]
> Server- och databasnamnen måste överensstämma mellan Power BI Desktop och datakällan i den lokala datagatewayen.

Länken mellan din datauppsättning och datakällan i gatewayen är baserad på servernamnet och databasnamnet. Dessa måste stämma överens. Om du exempelvis anger en IP-adress för servernamnet i Power BI Desktop måste du använda den IP-adressen för datakällan i gatewaykonfigurationen. Om du använder *SERVER\INSTANS* i Power BI Desktop måste du använda samma i den datakälla som konfigureras för gatewayen.

Detta gäller för både realtidsanslutningar och schemalagd uppdatering.

### <a name="using-the-data-source-with-live-connections"></a>Använda datakällan med realtidsanslutningar

Du behöver se till att server- och databasnamnet överensstämmer mellan Power BI Desktop och den konfigurerade datakällan för gatewayen. Du behöver även kontrollera att användaren finns med på fliken **Användare** för datakällan för att datamängder med realtidsanslutning ska kunna publiceras. Valet rörande realtidsanslutningar sker i Power BI Desktop när du importerar data för första gången.

Efter din publicering, antingen från Power BI Desktop eller från **Hämta data**, ska dina rapporter börja fungera. Det kan ta ett par minuter efter att du har skapat datakällan i gatewayen innan anslutningen kan användas.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Använda datakällan med schemalagd uppdatering

Om du finns med på fliken **Användare** för den datakälla som konfigurerats i gatewayen, och om server- och databasnamnen matchar, visas gatewayen som ett alternativ för användning med schemalagd uppdatering.

![Visa användarna](media/service-gateway-enterprise-manage-ssas/powerbi-gateway-enterprise-schedule-refresh.png)

### <a name="limitations-of-analysis-services-live-connections"></a>Begränsningar för Analysis Services realtidsanslutningar

Du kan använda en realtidsanslutning för tabellinstanser eller flerdimensionella instanser.

| **Serverversion** | **Obligatorisk SKU** |
| --- | --- |
| 2012 SP1 CU4 eller senare |Business Intelligence och Enterprise SKU |
| 2014 |Business Intelligence och Enterprise SKU |
| 2016 |Standard-SKU eller högre |

* Formatering på cellnivå och översättningsfunktioner stöds inte.
* Åtgärder och namngivna mängder exponeras inte för Power BI, men du kan fortfarande ansluta till flerdimensionella kuber som också innehåller åtgärder eller namngivna mängder och skapa visuella objekt och rapporter.

## <a name="next-steps"></a>Nästa steg

* [Felsökning av den lokala datagatewayen](/data-integration/gateway/service-gateway-tshoot)
* [Felsöka gatewayer – Power BI](service-gateway-onprem-tshoot.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

