---
title: Lokal datagateway – på djupet
description: Den här artikeln ger en djupgående beskrivning av den lokala gatewayen. Här beskrivs hur tjänsten fungerar med Azure Active Directory och ditt lokala Active Directory när du arbetar med Analysis Services
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 8b0121dbfe633eca9c438dfd272d3aeb56fd59a4
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34298583"
---
# <a name="on-premises-data-gateway-in-depth"></a>Lokal datagateway – på djupet
Det är möjligt för användare i din organisation att ha åtkomst till lokala data (till vilka de redan har åtkomstauktorisering), men innan dessa användare kan ansluta till den lokala datakällan, så måste en lokal datagateway ha installerats och konfigurerats. Gatewayen underlättar snabb och säker dold kommunikation mellan en användare i molnet till din lokala datakälla och sedan tillbaka till molnet.

Installation och konfiguration av en gateway görs vanligtvis av en administratör. Det kan kräva särskilda kunskaper om dina lokala servrar och i vissa fall kan det även krävas serveradministratörsbehörigheter.

Den här artikeln ger inte stegvisa anvisningar om hur du installerar och konfigurerar gatewayen. Sådan information hittar du i [Lokal datagateway](service-gateway-onprem.md). Den här artikeln är avsedd att ge dig en djup förståelse av hur gatewayen fungerar. Vi ska också i detalj diskutera användarnamn och säkerhet i både Azure Active Directory och Analysis Services, och hur molntjänsten använder den e-postadress en användare loggar in med, gatewayen och Active Directory för att ansluta säkert till och fråga din lokala data.

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-how-it-works-include.md)]

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="sign-in-account"></a>Inloggningskonto
Användarna kan logga in med antingen ett arbets- eller skolkonto. Det här är ditt organisationskonto. Om du har registrerat dig för ett Office 365-erbjudande och inte angav din faktiska e-postadress till arbetet, kan det se ut så här nancy@contoso.onmicrosoft.com. Ditt konto, inom en molntjänst, lagras i en klient i Azure Active Directory (AAD). Kontot AAD UPN kommer i de flesta fall att matcha e-postadressen.

## <a name="authentication-to-on-premises-data-sources"></a>Autentisering till lokala datakällor
Lagrade autentiseringsuppgifter används för att ansluta till lokala datakällor från gatewayen med undantag för Analysis Services. Oavsett den enskilda användaren så använder gatewayen lagrade autentiseringsuppgifter för att ansluta.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autentisering till en levande Analysis Services-datakälla
Varje gång en användare interagerar med Analysis Services skickas det effektiva användarnamnet till en gateway och sedan vidare till den lokala Analysis Services-servern. Användarens huvudnamn (UPN), vanligtvis den e-postadress du loggar in på molnet med, är vad vi skickar till Analysis Services som den effektiva användaren. UPN skickas i anslutningsegenskapen EffectiveUserName. E-postadressen måste matcha en definierad UPN inom den lokala Active Directory-domänen. UPN-namnet är en egenskap för ett Active Directory-konto. Det Windows-kontot måste sedan vara närvarande för att en Analysis Services-roll ska ha åtkomst till servern. Om ingen matchning hittas i Active Directory lyckas inte inloggningen.

Analysis Services kan också tillhandahålla filtrering baserat på det här kontot. Filtrering kan uppstå med rollbaserad säkerhet eller säkerhet på radnivå.

## <a name="role-based-security"></a>Rollbaserad säkerhet
Modeller tillhandahåller säkerhet utifrån användarroller. Roller definieras för ett visst modellprojekt under redigering i SQL Server Data Tools – Business Intelligence (SSDT BI), eller efter det att en modell har distribuerats med SQL Server Management Studio (SSMS). Roller innehåller medlemmar efter Windows-användarnamn eller Windows-grupp. Rollerna definierar de behörigheter för en användare har när det gäller att fråga eller utföra åtgärder i modellen. De flesta användare hör till en roll med läsbehörighet. Andra roller är avsedda för administratörer med behörighet att bearbeta objekt, hantera databasfunktioner och hantera andra roller.

## <a name="row-level-security"></a>Säkerhet på radnivå
Säkerhet på radnivå är specifik för Analysis Services-säkerhet på radnivå. Modeller kan tillhandahålla dynamisk säkerhet på radnivå. Till skillnad från att ha minst en roll som användarna tillhör, så krävs inte dynamisk säkerhet för tabellmodeller. På hög nivå definierar dynamisk säkerhet en användares läsbehörighet för data direkt ned till en viss rad i en viss tabell. I likhet med roller så bygger dynamisk säkerhet på radnivå på en användares Windows-användarnamn.

En användare möjlighet att fråga och visa modelldata bestäms i första hand genom vilka roller användarens Windows-användarkonto är medlem i, och i andra hand den dynamiska säkerheten på radnivå, om sådan har konfigurerats.

Rollimplementering och dynamisk säkerhet på radnivå i modeller ligger utanför den här artikelns fokus.  Mer information finns i [Roller (SSAS Tabular)](https://msdn.microsoft.com/library/hh213165.aspx) och [Säkerhetsroller (Analysis Services – flerdimensionella Data)](https://msdn.microsoft.com/library/ms174840.aspx) på MSDN. Och om du vill ha riktigt djup förståelse av säkerhet för tabellmodeller, så hämta och läs [White paper om BI-semantikmodellen för tabeller](https://msdn.microsoft.com/library/jj127437.aspx).

## <a name="what-about-azure-active-directory"></a>Vad är Azure Active Directory?
Microsofts molntjänster använder [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) för att hantera autentiseringen av användare. Azure Active Directory är den klient som innehåller användarnamn och säkerhetsgrupper. Normalt är den e-postadress som en användare loggar in med densamma som kontots UPN-namn.

Vilken är mitt lokala Active Directorys roll?

För att Analysis Services ska kunna avgöra om en användare som ansluter tillhör en roll med behörighet att läsa data, så måste servern konvertera det effektiva användarnamn som skickades från AAD till gatewayen och vidare till Analysis Services-servern. Analysis Services-servern skickar det effektiva användarnamnet till en Windows Active Directory-domänkontrollant (DC). Active Directory-domänkontrollanten verifierar sedan att det effektiva användarnamnet är ett giltigt UPN för ett lokalt konto, och returnerar användarens Windows-användarnamn till Analysis Services-servern.

EffectiveUserName kan inte användas på en Analysis Services-server som inte är domänansluten. Analysis Services-servern måste vara ansluten till en domän, så att eventuella fel vid inloggningen undviks.

## <a name="how-do-i-tell-what-my-upn-is"></a>Hur vet jag vilken UPN jag har?
Du kanske inte vet vilken din UPN är, och du är kanske inte domänadministratör. Du kan använda följande kommando från din arbetsstation för att ta reda på ditt kontos UPN-namn.

    whoami /upn

Resultatet ser ut ungefär som en e-postadress, men detta är det UPN som finns på din lokala domänkonto. Om du använder en Analysis Services-datakälla för live-anslutningar måste det matcha det som skickades till EffectiveUserName från gatewayen.

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Mappa användarnamn för Analysis Services-datakällor
Power BI tillåter mappning av användarnamn för Analysis Services-datakällor. Du kan konfigurera regler för att mappa ett användarnamn som är inloggat på Power BI till ett namn som har skickats för EffectiveUserName på Analysis Services-anslutningen. Mappningsanvändarnamnsfunktionenär till stor hjälp när användarnamnet i AAD inte matchar ett UPN i ditt lokala Active Directory. Om din e-postadress t.ex. är nancy@contoso.onmicrsoft.com, kan du mappa den till nancy@contoso.com, och det värdet skickas då till gatewayen. Du kan lära dig mer om hur du [mappar användarnamn](service-gateway-enterprise-manage-ssas.md#map-user-names).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Synkronisera ett lokalt Active Directory med Azure Active Directory
Du vill förmodligen att dina lokala Active Directory-konton ska matcha Azure Active Directory om du ska använda Analysis Services live-anslutningar. Liksom att UPN-namnet måste matcha mellan kontona.

Molntjänsterna känner bara till konton i Azure Active Directory. Det spelar ingen roll om du har lagt till ett konto i ditt lokala Active Directory, eftersom det inte kan användas ifall det inte finns i AAD. Det finns olika sätt på vilka du kan matcha dina lokala Active Directory-konton med Azure Active Directory.

1. Du kan lägga till konton manuellt till Azure Active Directory.
   
   Du kan skapa ett konto på Azure Portal eller i administrationsportalen för Office 365, och kontonamnet matchar UPN-namnet för det lokala Active Directory-kontot.
2. Du kan använda [Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)-verktyget för att synkronisera lokala konton med din Azure Active Directory-klient.
   
   Azure AD Connect-verktyget erbjuder alternativ för katalogsynkronisering och hur du konfigurerar autentisering, inklusive hash-synkronisering av lösenord, direktautentisering och federation. Om du inte är klientadministratör eller lokal domänadministratör, så måste du kontakta IT-administratören om du vill få detta konfigurerat.

Med Azure AD Connect säkerställer du att UPN-namnet matchar mellan AAD och ditt lokala Active Directory.

> [!NOTE]
> När du synkroniserar konton med Azure AD Connect-verktyget skapas nya konton i AAD-klienten.
> 
> 

## <a name="now-this-is-where-the-gateway-comes-in"></a>Det är här som gatewayen kommer in i bilden
Gatewayen fungerar som en brygga mellan molnet och den lokala servern. Dataöverföring mellan molnet och gatewayen säkras via [Azure Service Bus](https://azure.microsoft.com/documentation/services/service-bus/). Service Bus skapar en säker kanal mellan molnet och den lokala servern via en utgående anslutning på gatewayen.  Det finns inga inkommande anslutningar som du behöver öppna i den lokala brandväggen.

Om du har en Analysis Services-datakälla måste du installera gatewayen på en dator som ingår i samma skog/domän som Analysis Services-servern.

Ju närmare gatewayen har till servern, desto snabbare blir anslutningen. Om du kan ha gatewayen på samma server som datakällan, så är detta det bästa sättet på vilket du kan undvika nätverksfördröjning mellan gatewayen och servern.

## <a name="what-to-do-next"></a>Vad är nästa steg?
När du har installerat gatewayen är det dags att skapa datakällor för gatewayen. Du kan lägga till datakällor på skärmen **Hantera gatewayar**. Mer information finns i följande artiklar.

[Hantera din datakälla – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Hantera din datakälla – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Hantera din datakälla – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Hantera din datakälla – Oracle](service-gateway-onprem-manage-oracle.md)  
[Hantera din datakälla – Import/schemalagd uppdatering](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>Var saker kan gå fel
Ibland kan gatewayinstallationen misslyckas. Eller så kanske gatewayen verkar ha installerats som den ska, men den fungerar inte ihop med tjänsten. I många fall kan orsaken vara något väldigt enkelt, t.ex. det lösenord för autentiseringsuppgifterna som gatewayen använder för att logga in till datakällan.

I annat fall kan det uppstå problem med den typ av e-postadress som användarna loggar in med, eller med att Analysis Services inte kan matcha ett effektivt användarnamn. Om du har flera domäner med förtroenden sinsemellan och din gateway är i en av dem och Analysis Services i en annan, så kan detta ibland orsaka vissa problem.

Istället för att diskutera gatewayfelsökning här, så har vi placerat en serie felsökningssteg i en annan artikel, nämligen [Felsökning av lokal datagateway](service-gateway-onprem-tshoot.md). Förhoppningsvis ska du inte ha några problem. Men om du råkar ut för problem, så är det en fördel om du förstår hur allt detta fungerar, och då bör felsökningsartikeln vara till stor hjälp.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

## <a name="next-steps"></a>Nästa steg
[Felsöka den lokala datagatewayen](service-gateway-onprem-tshoot.md)  
[Azure Service Bus](https://azure.microsoft.com/documentation/services/service-bus/)  
[Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)  
Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

