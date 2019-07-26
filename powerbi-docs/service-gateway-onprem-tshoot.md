---
title: Felsöka gatewayer – Power BI
description: Den här artikeln innehåller olika sätt att felsöka problem hos din lokala datagateway och Power BI. Här finns lösningar på kända problem och verktyg som kan hjälpa dig.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: a013b42f1cd7cc9b2c5c24f9636683a52687ceb8
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271407"
---
# <a name="troubleshoot-gateways---power-bi"></a>Felsöka gatewayer – Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Den här artikeln beskriver några vanliga problem som kan uppstå när du använder **den lokala datagatewayen** med Power BI. Om det uppstår ett problem som inte anges nedan kan du använda webbplatsen för [Power BI-communities](http://community.powerbi.com) eller skapa en [supportbegäran](http://powerbi.microsoft.com/support).

## <a name="configuration"></a>Konfiguration

### <a name="error-power-bi-service-reported-local-gateway-as-unreachable-restart-the-gateway-and-try-again"></a>Fel: Power BI-tjänsten rapporterade att den lokala gatewayen inte gick att nå. Starta om gatewayen och försök igen

I slutet av konfigurationen anropas Power BI-tjänsten igen för att verifiera gatewayen. Power BI-tjänsten rapporterar inte gatewayen som live. Starta om Windows-tjänsten för att kommunikationen ska lyckas. Du kan samla in och granska loggarna enligt beskrivningen [Samla in loggar från appen för lokal datagateway](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app) för att få mer information.

## <a name="data-sources"></a>Datakällor

### <a name="error-unable-to-connect-details-invalid-connection-credentials"></a>Fel: Det går inte att ansluta. Details: Ogiltiga autentiseringsuppgifter för anslutning

I **Visa information** visas felmeddelandet som togs emot från datakällan. För SQL Server ser du något liknande följande.

    Login failed for user 'username'.

Kontrollera att du har rätt användarnamn och lösenord. Kontrollera också att dessa autentiseringsuppgifter kan ansluta till datakällan. Se till att kontot som används matchar **autentiseringsmetoden**.

### <a name="error-unable-to-connect-details-cannot-connect-to-the-database"></a>Fel: Det går inte att ansluta. Details: Det går inte att ansluta till databasen

Det gick att ansluta till servern men inte på den angivna databasen. Kontrollera namnet på databasen och att användarens autentiseringsuppgifter har rätt behörighet för att komma åt databasen.

I **Visa information** visas felmeddelandet som togs emot från datakällan. För SQL Server ser du något liknande följande.

    Cannot open database "AdventureWorks" requested by the login. The login failed. Login failed for user 'username'.

### <a name="error-unable-to-connect-details-unknown-error-in-data-gateway"></a>Fel: Det går inte att ansluta. Details: Okänt fel i datagateway

Det här felet kan inträffa av olika skäl. Glöm inte att verifiera att du kan ansluta till datakällan på datorn som är värd för gatewayen. Detta kan bero på att servern inte är tillgänglig.

I **Visa information** visas felkoden **DM_GWPipeline_UnknownError**.

Du kan också leta i Händelseloggarna > **Program- och tjänstloggar** > **Lokal datagateway-tjänst** för mer information.

### <a name="error-we-encountered-an-error-while-trying-to-connect-to-server-details-we-reached-the-data-gateway-but-the-gateway-cant-access-the-on-premises-data-source"></a>Fel: Ett fel påträffades vid försök att ansluta till \<server\>. Details: Vi nådde datagatewayen men gatewayen kommer inte åt den lokala datakällan.

Det gick inte att ansluta till den angivna datakällan. Glöm inte att validera informationen för datakällan.

I **Visa information** visas felkoden **DM_GWPipeline_Gateway_DataSourceAccessError**.

Om det underliggande felmeddelandet liknar det följande, innebär det att det konto som du använder för datakällan inte är en serveradministratör för den Analysis Services-instansen. [Läs mer](https://docs.microsoft.com/sql/analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance)

    The 'CONTOSO\account' value of the 'EffectiveUserName' XML for Analysis property is not valid.

Om det underliggande felmeddelandet liknar det följande kan det betyda att tjänstkontot för Analysis Services kan saknas i katalogattributet för [token-groups-global-and-universal](https://msdn.microsoft.com/library/windows/desktop/ms680300.aspx) (TGGAU).

    The username or password is incorrect.

Domäner med åtkomst för äldre operativsystem än Windows 2000-kompatibilitet har attributet TGGAU aktiverat. I de flesta fall har nya domäner inte det här attributet som standard. Läs mer om det [här](https://support.microsoft.com/kb/331951).

Du kan kontrollera detta genom att göra följande.

1. Anslut till Analysis Services-datorn i SQL Server Management Studio. Lägg till EffectiveUserName i avancerade anslutningsegenskaper för användaren i fråga och se om felet återges.
2. Du kan använda dsacls-verktyget i Active Directory för att verifiera om attributet anges. Det här är ett verktyg som finns på en domänkontrollant. Du måste känna till det unika domännamnet för kontot och skicka det till verktyget.

        dsacls "CN=John Doe,CN=UserAccounts,DC=contoso,DC=com"

    Du vill se något som liknar följande i resultaten.

            Allow BUILTIN\Windows Authorization Access Group
                                          SPECIAL ACCESS for tokenGroupsGlobalAndUniversal
                                          READ PROPERTY

För att åtgärda problemet måste du aktivera TGGAU för kontot som används för Windows-tjänsten Analysis Services.

#### <a name="another-possibility-for-username-or-password-incorrect"></a>En annan möjlighet för felaktigt användarnamn eller lösenord

Det här felet kan också bero på att Analysis Services-servern finns i en annan domän än användarna och ett dubbelriktat förtroende kan inte upprättas.

Du måste arbeta tillsammans med dina administratörer för att verifiera förtroendet mellan domäner.

#### <a name="unable-to-see-the-data-gateway-data-sources-in-the-get-data-experience-for-analysis-services-from-the-power-bi-service"></a>Det går inte att visa datagatewayens datakällor i ”Hämta data” för Analysis Services från Power BI-tjänsten

Kontrollera att ditt konto är med på fliken **Användare** i datakällan i gateway-konfigurationen. Om du inte har åtkomst till gatewayen ber du gatewayadministratören att verifiera. Endast konton i listan **Användare** kan se datakällan som visas i Analysis Services-listan.

### <a name="error-you-dont-have-any-gateway-installed-or-configured-for-the-data-sources-in-this-dataset"></a>Fel: Du har inte någon gateway installerad eller konfigurerad för datakällor i den här datauppsättningen

Se till att du har lagt till en eller flera datakällor till gatewayen enligt beskrivningen i [Lägga till en datakälla](service-gateway-data-sources.md#add-a-data-source). Om gatewayen inte visas i administratörsportalen under **Hantera gatewayer** kan du försöka att rensa webbläsarens cache eller logga ut från tjänsten och sedan logga in igen.

## <a name="datasets"></a>Datauppsättningar

### <a name="error-there-is-not-enough-space-for-this-row"></a>Fel: Otillräckligt med utrymme för den här raden

Detta inträffar om du har en enskild rad som är större än 4 MB. Du måste avgöra vad raden är utifrån din datakälla och försöka filtrera bort den eller minska dess storlek.

### <a name="error-the-server-name-provided-doesnt-match-the-server-name-on-the-sql-server-ssl-certificate"></a>Fel: Servernamnet matchar inte servernamnet på SQL Server SSL-certifikatet

Detta kan inträffa när certifikat-CN är för serverns fullständigt kvalificerade domännamn (FQDN), men du endast har angett NetBIOS-namnet för servern. Detta leder till ett matchningsfel för certifikatet. För att lösa problemet måste du göra så att servernamnet i gatewaydatakällan, och PBIX-filen, använder serverns fullständigt kvalificerade domännamn.

### <a name="i-dont-see-the-on-premises-data-gateway-present-when-configuring-scheduled-refresh"></a>Den lokala datagatewayen visas inte när jag konfigurerar en schemalagd uppdatering

Detta kan bero på ett par olika scenarier.

1. Server- och databasnamnen matchar inte mellan Power BI Desktop och den konfigurerade datakällan för gatewayen. Dessa måste vara samma värden. De är inte skiftlägeskänsliga.
2. Ditt konto är inte med på fliken **Användare** i datakällan i gateway-konfigurationen. Du måste kontakta administratören för gatewayen för att läggas till i listan.
3. Power BI Desktop-filen innehåller flera datakällor och alla datakällorna har inte konfigurerats med gatewayen. Varje datakälla måste definieras med en gateway för att gatewayen ska visas i Schemalagd uppdatering.

### <a name="error-the-received-uncompressed-data-on-the-gateway-client-has-exceeded-the-limit"></a>Fel: Mottagna okomprimerade data på gatewayklienten har överskridit gränsen

Den exakta begränsningen är 10 GB okomprimerad data per tabell. Om du stöter på problemet finns det bra alternativ för att optimera och undvika problemet. Framför allt, minska mycket konstanta, långa strängvärden och ersätt dem med en normaliserad nyckel eller ta bort kolumnen (om den inte används).

## <a name="reports"></a>Rapporter

### <a name="report-could-not-access-the-data-source-because-you-do-not-have-access-to-our-data-source-via-an-on-premises-data-gateway"></a>Rapporten kunde inte nå datakällan eftersom du inte har åtkomst till vår datakälla via en lokal datagateway

Detta beror vanligtvis på något av följande.

1. Informationen om datakällan matchar inte den underliggande datamängden. Server- och databasnamnen måste vara likadana i Power BI Desktop som i datakällan i den lokala datagatewayen. Om du använder en IP-adress i Power BI Desktop måste datakällan för den lokala datagatewayen också använda en IP-adress.
2. Det finns ingen tillgänglig datakälla på någon gateway i din organisation. Du kan konfigurera datakällan på en ny eller befintlig lokal datagateway.

### <a name="error-data-source-access-error-please-contact-the-gateway-administrator"></a>Fel: Åtkomstfel till datakälla. Kontakta gatewayadministratören

Om den här rapporten använder en Analysis Services-liveanslutning kan det hända att ett värde skickas till EffectiveUserName som antingen inte är giltigt eller som saknar behörighet på Analysis Services-datorn. Autentiseringsproblem beror vanligtvis på att värdet som skickades som EffectiveUserName inte matchar en lokal användares huvudnamn (UPN).

Du kan göra följande för att kontrollera detta.

1. Hitta det effektiva användarnamnet i [gateway-loggarna](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).
2. När du har det skickade värdet kan du bekräfta att det stämmer. Om det är din användare kan du använda följande kommando från en kommandotolk för att visa UPN-namnet. UPN-namnet ser ut som en e-postadress.

        whoami /upn

Du kan eventuellt se vad Power BI hämtar från Azure Active Directory.

1. Bläddra till [https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer).
2. Välj **Logga in** i det övre högra hörnet.
3. Kör följande fråga. Du ser ett ganska stort JSON-svar.

        https://graph.windows.net/me?api-version=1.5
4. Leta efter **UserPrincipalName**.

Om ditt Azure Active Directory-UPN inte stämmer med ditt lokala Active Directory-UPN, kan du använda funktionen [Kartlägg användarnamn](service-gateway-enterprise-manage-ssas.md#mapping-usernames-for-analysis-services-data-sources) för att ersätta det med ett giltigt värde. Du kan också be din klientadministratör eller lokala Active Directory-administratör om hjälp med att ändra ditt UPN.

## <a name="kerberos"></a>Kerberos

Om den underliggande databasservern och den lokala datagatewayen inte har konfigurerats korrekt för [Kerberos-begränsad delegering](service-gateway-sso-kerberos.md) aktiverar du [utförlig loggning](/data-integration/gateway/service-gateway-performance#slow-performing-queries) på gatewayen och börjar felsökningen genom att undersöka problemet baserat på fel/spår i gatewayens loggfiler. Information om hur du samlar in gatewayloggarna för visning finns i [Samla in loggar från appen för lokal datagateway](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).

### <a name="impersonationlevel"></a>ImpersonationLevel

ImpersonationLevel relaterar till SPN-installationsprogrammet eller den lokala principinställningen.

```
[DataMovement.PipeLine.GatewayDataAccess] About to impersonate user DOMAIN\User (IsAuthenticated: True, ImpersonationLevel: Identification)
```

**Lösning**

Följ dessa steg för att lösa problemet:

1. Konfigurera ett SPN för den lokala gatewayen.
2. Konfigurera begränsad delegering i din Active Directory (AD).

### <a name="failedtoimpersonateuserexception-failed-to-create-windows-identity-for-user-userid"></a>FailedToImpersonateUserException: Det gick inte att skapa en Windows-identitet för användarens Användar-ID

FailedToImpersonateUserException inträffar om du inte kan personifiera för en annan användares räkning. Detta kan även inträffa om det konto som du försöker personifiera kommer från en annan domän än den som gatewaytjänstdomänen är på (detta är en begränsning).

**Lösning**

* Kontrollera att konfigurationen är korrekt enligt anvisningarna i avsnittet ImpersonationLevel ovan.
* Se till att det användar-ID som den försöker att personifiera är ett giltigt AD-konto.

### <a name="general-error-1033-error-while-parsing-the-protocol"></a>Allmänt fel. 1033-fel vid parsning av protokollet

Felet 1033 returneras om ditt externa ID som har konfigurerats i SAP HANA inte matchar inloggningen om användaren personifieras med UPN (alias@domain.com). I loggarna kommer du se ”Ursprungligt UPN alias@domain.com ersatt med nytt UPN alias@domain.com” överst i felloggarna, som visas nedan.

```
[DM.GatewayCore] SingleSignOn Required. Original UPN 'alias@domain.com' replaced with new UPN 'alias@domain.com.'
```

**Lösning**

* SAP HANA kräver att den personifierade användaren använder attributet sAMAccountName i AD (användaralias). Annars returneras 1033-felet.

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount.png)

* I loggarna visas sAMAccountName (alias) och inte UPN, vilket är aliaset följt av domänen (alias@doimain.com).

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount-02.png)

```xml
      <setting name="ADUserNameReplacementProperty" serializeAs="String">
        <value>sAMAccount</value>
      </setting>
      <setting name="ADServerPath" serializeAs="String">
        <value />
      </setting>
      <setting name="CustomASDataSource" serializeAs="String">
        <value />
      </setting>
      <setting name="ADUserNameLookupProperty" serializeAs="String">
        <value>AADEmail</value>
```

### <a name="sap-aglibodbchdb-dllhdbodbc-communication-link-failure-10709-connection-failed-rte-1-kerberos-error-major-miscellaneous-failure-851968-minor-no-credentials-are-available-in-the-security-package"></a>[SAP AG][LIBODBCHDB DLL][HDBODBC] Kommunikationslänkfel 10709 Anslutningen misslyckades (RTE: [-1] Kerberos-fel. Större: Övrigt fel [851968], mindre: Inga autentiseringsuppgifter är tillgängliga i säkerhetspaketet

Du får felmeddelandet 10709 Anslutningen misslyckades om delegeringen inte har konfigurerats korrekt i AD.

**Lösning**

* Se till att du har SAP Hana-servern på delegeringsfliken i AD för gatewaytjänstkontot.

   ![delegeringsflik](media/service-gateway-onprem-tshoot/delegation-in-AD.png)

## <a name="refresh-history"></a>Uppdateringshistorik

När du använder gatewayen för schemalagd uppdatering kan du se vilka fel som har inträffat och få användbara data med **Uppdateringshistorik** om du behöver skapa en supportbegäran. Du kan visa både schemalagda uppdateringar och sådana som görs på begäran. Följande steg visar hur du går till **Uppdateringshistorik**.

1. I Power BI-navigeringsfönstret i **Datauppsättningar** väljer du en datauppsättning &gt;Öppna meny&gt; **Schemalägg uppdatering**.

    ![Så väljer du schemauppdatering](media/service-gateway-onprem-tshoot/scheduled-refresh.png)

2. I **Inställningar för...** &gt;**Schemalägg uppdatering**, väljer du **Uppdateringshistorik**.

    ![Välja uppdateringshistorik](media/service-gateway-onprem-tshoot/scheduled-refresh-2.png)

    ![Visning av uppdateringshistorik](media/service-gateway-onprem-tshoot/refresh-history.png)

Mer information om felsökning av uppdateringsscenarier finns i artikeln [Felsöka uppdateringsscenarier](refresh-troubleshooting-refresh-scenarios.md).

## <a name="fiddler-trace"></a>Fiddlerspårning

[Fiddler](http://www.telerik.com/fiddler) är ett kostnadsfritt verktyg från Telerik som övervakar HTTP-trafik. Du kan se trafiken från och till med Power BI-tjänsten från klientdatorn. Här visas fel och annan relaterad information.

![Använda Fiddler-spårning](media/service-gateway-onprem-tshoot/fiddler.png)

## <a name="next-steps"></a>Nästa steg

* [Felsöka den lokala datagatewayen](/data-integration/gateway/service-gateway-tshoot)
* [Konfigurera proxyinställningar för den lokala datagatewayen](/data-integration/gateway/service-gateway-proxy)  
* [Hantera din datakälla – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Hantera din datakälla – SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Hantera din datakälla – SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Hantera din datakälla – Import/schemalagd uppdatering](service-gateway-enterprise-manage-scheduled-refresh.md)  

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
