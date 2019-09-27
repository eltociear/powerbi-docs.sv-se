---
title: Konfigurera enkel inloggning – Kerberos
description: Konfigurera din gateway med Kerberos för att aktivera SSO (enkel inloggning) från Power BI till lokala datakällor
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 9958059fcf0d86323fc95f44f6fcfcb08fe7b52b
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71100452"
---
# <a name="configure-kerberos-based-sso-from-power-bi-service-to-on-premises-data-sources"></a>Konfigurera Kerberos-baserad enkel inloggning från Power BI-tjänsten till lokala datakällor

Använd [Kerberos-begränsad delegering](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) för att aktivera sömlös anslutning med enkel inloggning. När enkel inloggning aktiveras blir det enkelt för Power BI-rapporter och instrumentpaneler att uppdatera data från lokala källor.

Flera objekt måste konfigureras för att Kerberos-begränsad delegering ska fungera korrekt, inklusive _Tjänsternas huvudnamn_ (SPN) och delegeringsinställningar på tjänstkonton.

### <a name="prerequisite-1-install-and-configure-the-microsoft-on-premises-data-gateway"></a>Förutsättning 1: Installera och konfigurera den lokala Microsoft-datagatewayen

Den lokala datagatewayen stöder en uppgradering på plats samt _inställningsövertagande_ för befintliga gatewayer.

### <a name="prerequisite-2-run-the-gateway-windows-service-as-a-domain-account"></a>Förutsättning 2: Kör gatewayens Windows-tjänst som ett domänkonto

I en standardinstallation körs gatewayen som ett datorlokalt tjänstkonto (mer specifikt _NT Service\PBIEgwService_), vilket visas i följande bild:

![Skärmbild av tjänstkonto](media/service-gateway-sso-kerberos/service-account.png)

För att aktivera Kerberos-begränsad delegering måste gatewayen köras som ett domänkonto, såvida inte din Azure Active Directory-instans redan har synkroniserats med din lokala Active Directory-instans (med Azure AD DirSync/Connect). Information om hur du växlar till ett domänkonto finns i [ändra gatewaytjänstkontot](/data-integration/gateway/service-gateway-service-account).

> [!NOTE]
> Om Azure AD Connect har konfigurerats och användarkonton har synkroniserats behöver inte gatewaytjänsten utföra några lokala Azure AD-sökningar vid körningen. I stället kan du helt enkelt använda lokalt tjänst-SID för gatewaytjänsten till att slutföra all nödvändig konfiguration i Azure Active Directory. De konfigurationssteg för Kerberos-begränsad delegering som beskrivs i den här artikeln motsvarar de konfigurationssteg som krävs i Azure Active Directory-kontexten. De tillämpas helt enkelt på gatewayens datorobjekt (enligt identifiering av lokalt tjänst-SID) i Azure AD, i stället för på domänkontot.

### <a name="prerequisite-3-have-domain-admin-rights-to-configure-spns-setspn-and-kerberos-constrained-delegation-settings"></a>Förutsättning 3: Ha domänadministratörsbehörighet för att konfigurera SPN:er (SetSPN) och Kerberos-begränsade delegeringsinställningar

Vi rekommenderar inte att en domänadministratör tillfälligt eller permanent beviljar behörighet till någon annan för att konfigurera SPN:er och inställningar för Kerberos-delegering, utan att kräva att den personen har behörighet som domänadministratör. I följande avsnitt beskriver vi de rekommenderade konfigurationsstegen i detalj.

## <a name="configure-kerberos-constrained-delegation-for-the-gateway-and-data-source"></a>Konfigurera Kerberos-begränsad delegering för gatewayen och datakällan

Som domänadministratör konfigurerar du ett SPN för gatewaytjänstens domänkonto (om så krävs) och delegeringsinställningarna för gatewaytjänstens domänkonto.

### <a name="configure-an-spn-for-the-gateway-service-account"></a>Konfigurera ett SPN för gatewaytjänstkontot

Börja med att kontrollera om ett SPN redan har skapats för det domänkonto som används som gatewayens tjänstkonto:

1. Starta **Active Directory-användare och datorer** som domänadministratör.

2. Högerklicka på domänen, välj **Sök** och ange kontonamnet för gatewayens tjänstkonto.

3. Högerklicka på gatewayens tjänstkonto i sökresultatet och välj **Egenskaper**.

4. Om fliken **Delegering** visas i dialogrutan **Egenskaper** har ett SPN redan skapats, och du kan hoppa över till [Välja resursbaserad eller standardmässig Kerberos-begränsad delegering](#decide-on-resource-based-or-standard-kerberos-constrained-delegation).

    Om fliken **Delegering** saknas i dialogrutan **Egenskaper**, kan du manuellt skapa ett SPN på det kontot för att aktivera den. Använd [setspn-verktyget](https://technet.microsoft.com/library/cc731241.aspx) som medföljer Windows (du måste ha domänadministratörsbehörighet för att kunna skapa ett SPN).

    Tänk dig till exempel att gatewaytjänstkontot är **Contoso\GatewaySvc** och att namnet på den dator där gatewaytjänsten körs är **MyGatewayMachine**. För att ange SPN för gatewaytjänstkontot skulle du köra följande kommando:

    ![Bild av kommandot som anger ett SPN](media/service-gateway-sso-kerberos/set-spn.png)

    Du kan även ange SPN med hjälp av MMC-snapin-modulen Active Directory-användare och datorer (Microsoft Management Console).

### <a name="decide-on-resource-based-or-standard-kerberos-constrained-delegation"></a>Välja resursbaserad eller standardmässig Kerberos-begränsad delegering

Delegeringsinställningar kan konfigureras för _antingen_ resursbaserad eller standardmässig Kerberos-begränsad delegering. Använd resursbaserad delegering om datakällan tillhör en annan domän än din gateway, men observera att den här metoden kräver Windows Server 2012 eller senare. Mer information om skillnaderna mellan de två delegeringsmetoderna finns på [översiktssidan för begränsad Kerberos-delegering](/windows-server/security/kerberos/kerberos-constrained-delegation-overview).

 När du har valt metod går du _antingen_ till avsnittet [Konfigurera gatewaytjänstkontot för standardmässig Kerberos-begränsad delegering](#configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation) _eller_ till avsnittet [Konfigurera gatewaytjänstkontot för resursbaserad Kerberos-begränsad delegering](#configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation). Slutför inte båda underavsnitten.

## <a name="configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation"></a>Konfigurera gatewaytjänstkontot för standardmässig Kerberos-begränsad delegering

> [!NOTE]
> Slutför stegen i det här avsnittet om du vill aktivera standardmässig Kerberos-begränsad delegering. Om du vill aktivera resursbaserad Kerberos-begränsad delegering slutför du stegen i underavsnittet [Konfigurera gatewaytjänstkontot för resursbaserad Kerberos-begränsad delegering](#configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation).

Nu anger vi delegeringsinställningarna för gatewaytjänstkontot. Det finns flera olika verktyg som du kan använda för att utföra dessa steg. Här använder vi Active Directory-användare och datorer, vilket är en snapin-modul i Microsoft Management Console (MMC) som administrerar och publicerar information i katalogen. Den är tillgänglig på domänkontrollanterna som standard, men du kan även aktivera den via konfiguration av Windows-funktionen på andra datorer.

Vi behöver konfigurera Kerberos-begränsad delegering med protokollövergång. Med begränsad delegering måste du vara uttrycklig med vilka tjänster du vill tillåta att gatewayen presenterar delegerade autentiseringsuppgifter till. Till exempel accepterar endast SQL Server eller SAP HANA-servern delegeringsanrop från gatewayens tjänstkonto.

Det här avsnittet förutsätter att du redan har konfigurerat SPN:er för dina underliggande datakällor (till exempel SQL Server, SAP HANA, SAP BW, Teradata eller Spark). Mer information om hur du konfigurerar dessa datakällors server-SPN:er finns i den tekniska dokumentationen för respektive databasserver. Se även rubriken *What SPN does your app require?* (Vilket SPN kräver din app?) i blogginlägget [My Kerberos Checklist](https://techcommunity.microsoft.com/t5/SQL-Server-Support/My-Kerberos-Checklist-8230/ba-p/316160) (Min Kerberos-checklista).

I följande steg förutsätter vi att det finns en lokal miljö med två datorer: en gatewaydator och en databasserver som kör SQL Server som redan har konfigurerats för Kerberos-baserad enkel inloggning. Stegen kan användas för en av de andra datakällorna som stöds, förutsatt att datakällan redan har konfigurerats för Kerberos-baserad enkel inloggning. För det här exemplet förutsätter vi även att följande inställningar och namn finns:

* Active Directory-domän (NetBIOS): Contoso
* Gatewaydatorns namn: **MyGatewayMachine**
* Gatewaytjänstkonto: **Contoso\GatewaySvc**
* Datornamn för SQL Server-datakällan: **TestSQLServer**
* Tjänstkonto för SQL Server-datakällan: **Contoso\SQLService**

Så här konfigurerar du delegeringsinställningarna:

1. Öppna **Active Directory-användare och datorer** med domänadministratörsbehörighet.

2. Högerklicka på gatewaytjänstkontot (**Contoso\GatewaySvc**) och välj **Egenskaper**.

3. Välj fliken **delegering**.

4. Välj **Lita på den här datorn enbart för delegering till angivna tjänster** > **Använd valfritt autentiseringsprotokoll**.

5. Under **Tjänster som det här kontot kan ge delegerade autentiseringsuppgifter till** väljer du **Lägg till**.

6. I den nya dialogrutan väljer du **Användare eller datorer**.

7. Ange tjänstkontot för datakällan. Till exempel kan en SQL Server-datakälla ha ett tjänstkonto såsom **Contoso\SQLService**. När kontot har lagts till väljer du **OK**.

8. Välj det SPN som du skapade för databasservern. I vårt exempel börjar SPN:et med **MSSQLSvc**. Om du har lagt till både FQDN- och NetBIOS-SPN:et för din databastjänst, väljer du båda. Du kanske bara ser en.

9. Välj **OK**. Du bör nu se SPN:et i listan.

    ![Skärmbild av dialogrutan Egenskaper för gatewayanslutning](media/service-gateway-sso-kerberos/gateway-connector-properties.png)

Hoppa nu över till [Bevilja gatewaytjänstkontot lokala principrättigheter på gatewaydatorn](#grant-the-gateway-service-account-local-policy-rights-on-the-gateway-machine) för att fortsätta med installationen.

## <a name="configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation"></a>Konfigurera gatewaytjänstkontot för resursbaserad Kerberos-begränsad delegering

> [!NOTE]
> Slutför stegen i det här avsnittet om du vill aktivera resursbaserad Kerberos-begränsad delegering. Om du vill aktivera standardmässig Kerberos-begränsad delegering slutför du stegen i underavsnittet [Konfigurera gatewaytjänstkontot för standardmässig Kerberos-begränsad delegering](#configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation).

Använd [resursbaserade Kerberos-begränsad delegering](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) för att aktivera anslutning med enkel inloggning för Windows Server 2012 och senare versioner, vilket tillåter att klientdels- och serverdelstjänster finns på olika domäner. För att det här ska fungera så måste serverdelstjänstens domän lita på klientdelstjänstens domän.

I följande steg förutsätter vi att det finns en lokal miljö med två datorer i olika domäner: en gatewaydator och en databasserver som kör SQL Server som redan har konfigurerats för Kerberos-baserad enkel inloggning. Stegen kan användas för en av de andra datakällorna som stöds, förutsatt att datakällan redan har konfigurerats för Kerberos-baserad enkel inloggning. För det här exemplet så förutsätter vi även följande inställningar och namn:

* Gatewaydatorns namn: **MyGatewayMachine**
* Gatewaytjänstkonto: **ContosoFrontEnd\GatewaySvc**
* Datornamn för SQL Server-datakällan: **TestSQLServer**
* Tjänstkonto för SQL Server-datakällan: **ContosoBackEnd\SQLService**

Baserat på dessa exempelnamn och -inställningar slutför du följande konfigurationssteg:

1. På domänkontrollanten för domänen **ContosoFrontEnd** ser du till att inga delegeringsinställningar tillämpas för det gatewaytjänstkonto som använder **Active Directory-användare och datorer**, en MMC-snapin-modul (Microsoft Management Console).

    ![Egenskaper för gatewayanslutning](media/service-gateway-sso-kerberos-resource/gateway-connector-properties.png)

2. Med hjälp av **Active Directory-användare och datorer** ser du på domänkontrollanten för domänen **ContosoBackEnd** till att inga delegeringsinställningar tillämpas för serverdelstjänstkontot. Se även till att attributet **msDS-AllowedToActOnBehalfOfOtherIdentity** för det här kontot inte anges. Du hittar attributet i **Attributredigeraren** såsom det visas i följande bild:

    ![Egenskaper för SQL-tjänsten](media/service-gateway-sso-kerberos-resource/sql-service-properties.png)

3. Skapa en grupp i **Active Directory-användare och datorer** på domänkontrollanten för domänen **ContosoBackEnd**. Lägg till gatewayens tjänstkonto till den här gruppen enligt följande bild. Bilden visar en ny grupp med namnet _ResourceDelGroup_ där gatewaytjänstkontot **GatewaySvc** lagts till i den här gruppen.

    ![Gruppegenskaper](media/service-gateway-sso-kerberos-resource/group-properties.png)

4. Öppna en kommandotolk och kör följande kommandon i domänkontrollanten för domänen **ContosoBackEnd** för att uppdatera attributet **msDS-AllowedToActOnBehalfOfOtherIdentity** för serverdelstjänstkontot:

    ```powershell
    $c = Get-ADGroup ResourceDelGroup
    Set-ADUser SQLService -PrincipalsAllowedToDelegateToAccount $c
    ```

5. Du kan verifiera att uppdateringen avspeglas i fliken Attributredigeraren i egenskaperna för serverdelstjänstkontot i **Active Directory Users and Computers.**

## <a name="grant-the-gateway-service-account-local-policy-rights-on-the-gateway-machine"></a>Bevilja gatewaytjänstkontot lokala principrättigheter på gatewaydatorn

På den dator som kör gatewaytjänsten (**MyGatewayMachine** i vårt exempel) måste du slutligen bevilja det lokala gatewaytjänstkontot den lokala principen **Personifiera en klient efter autentisering** samt **Agera som en del av operativsystemet (SeTcbPrivilege)** . Du kan utföra och kontrollera den här konfigurationen med Redigeraren för lokala grupprinciper (**gpedit**).

1. På gatewaydatorn kör du: *gpedit.msc*.

2. Gå till **Lokal datorprincip** > **Datorkonfiguration** > **Windows-inställningar** > **Säkerhetsinställningar** > **Lokala principer** > **Tilldelning av användarrättigheter**.

    ![Skärmbild av mappstrukturen i Lokal datorprincip](media/service-gateway-sso-kerberos/user-rights-assignment.png)

3. I principlistan under **Tilldelning av användarrättigheter** väljer du **Personifiera en klient efter autentisering**.

    ![Skärmbild av Personifiera en klientprincip](media/service-gateway-sso-kerberos/impersonate-client.png)

    Högerklicka och öppna **Egenskaper**. Kontrollera listan med konton. Den måste innehålla gatewaytjänstkontot (**Contoso\GatewaySvc**).

4. I principlistan under **Tilldelning av användarrättigheter** väljer du **Agera som del av operativsystemet (SeTcbPrivilege)** . Se till att gatewaytjänstkontot även finns med i listan över konton.

5. Starta om den **lokala datagatewaytjänsten**.

### <a name="set-user-mapping-configuration-parameters-on-the-gateway-machine-if-required"></a>Ange konfigurationsparametrar för användarmappning på gatewaydatorn om det krävs

Om du inte har konfigurerat Azure AD Connect följer du dessa steg för att mappa en Power BI-tjänstanvändare till en lokal Azure AD-användare. Varje Active Directory-användare som mappas på det här sättet måste ha behörigheter för enkel inloggning för din datakälla. Mer information finns i den här [Guy in a Cube-videon](https://www.youtube.com/watch?v=NG05PG9aiRw).

1. Öppna konfigurationsfilen för huvudgatewayen, `Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll`. Som standard finns den här filen på C:\Program Files\On-premises data gateway (Lokal datagateway).

1. Ange **ADUserNameLookupProperty** till ett oanvänt Active Directory-attribut. Vi antar att `msDS-cloudExtensionAttribute1` används i de steg som följer, även om det här attributet endast är tillgängligt i Windows Server 2012 och senare. Ange **ADUserNameReplacementProperty** till `SAMAccountName`. Spara konfigurationsfilen.

1. På fliken **Tjänster** i Aktivitetshanteraren högerklickar du på gatewaytjänsten och väljer **Starta om**.

    ![Skärmbild av fliken för Aktivitetshanterarens tjänster](media/service-gateway-sso-kerberos/restart-gateway.png)

1. För varje Power BI-tjänstanvändare som du vill aktivera enkel inloggning med Kerberos för anger du egenskapen `msDS-cloudExtensionAttribute1` för en lokal Active Directory-användare (med behörighet för enkel inloggning till din datakälla) till det fullständiga användarnamnet för Power BI-tjänstanvändaren. Om du till exempel loggar in på Power BI-tjänsten som `test@contoso.com` och vill mappa den här användaren till en lokal Active Directory-användare med behörigheter för enkel inloggning, till exempel `test@LOCALDOMAIN.COM`, anger du `test@LOCALDOMAIN.COM`-attributet `msDS-cloudExtensionAttribute1` till `test@contoso.com`.

Du kan även ange egenskapen `msDS-cloudExtensionAttribute1` med hjälp av MMC-snapin-modulen Active Directory-användare och datorer (Microsoft Management Console).

1. Som domänadministratör startar du Active Directory-användare och datorer, en MMC-snapin-modul.

1. Högerklicka på domänen, välj Sök och ange kontonamnet för den lokala Active Directory-användare som du vill mappa till.

1. Välj fliken **Redigera attribut**.

    Leta upp `msDS-cloudExtensionAttribute1`-egenskapen och dubbelklicka på den. Ange värdet till det fullständiga användarnamnet för den användare som du använder för att logga in på Power BI-tjänsten.

1. Välj **OK**.

    ![Skärmbild av dialogrutan Redigera strängattribut](media/service-gateway-sso-kerberos/edit-attribute.png)

1. Välj **Tillämpa**. Kontrollera att rätt värde har angetts i kolumnen **Värde**.

## <a name="complete-data-source-specific-configuration-steps"></a>Slutför de datakällsspecifika konfigurationsstegen

SAP HANA och SAP BW har ytterligare datakällsspecifika konfigurationskrav och förutsättningar som behöver uppfyllas innan du kan upprätta en anslutning med enkel inloggning via gatewayen till dessa datakällor. Mer information finns på [sidan för SAP HANA-konfiguration](service-gateway-sso-kerberos-sap-hana.md) och [sidan för konfiguration av SAP BW – CommonCryptoLib (sapcrypto.dll)](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md). Det är även möjligt att [konfigurera SAP BW för användning med gx64krb5 SNC-biblioteket](service-gateway-sso-kerberos-sap-bw-gx64krb.md), men det här biblioteket rekommenderas inte av Microsoft eftersom det inte längre stöds av SAP. Du bör använda CommonCryptoLib _eller_ gx64krb5 som SNC-bibliotek. Slutför inte konfigurationsstegen för båda biblioteken.

> [!NOTE]
> Andra SNC-bibliotek kan också fungera för BW SSO, men de stöds inte officiellt av Microsoft.

## <a name="run-a-power-bi-report"></a>Köra en Power BI-rapport

När du har slutfört alla konfigurationssteg kan du använda sidan **Hantera gateway** i Power BI för att konfigurera den datakälla som du kommer att använda för enkel inloggning. Om du har flera gatewayer ska du välja den gateway som du har konfigurerat för enkel inloggning med Kerberos. Under **Avancerade inställningar** för datakällan kontrollerar du sedan att kryssrutan ”Använd enkel inloggning via Kerberos för DirectQuery-frågor” är markerad.

![Skärmbild av alternativet Avancerade inställningar](media/service-gateway-sso-kerberos/advanced-settings.png)

 Publicera en **DirectQuery-baserad** rapport från Power BI Desktop. Den här rapporten måste använda data som är tillgängliga för den användare som är mappad till den (Azure) Active Directory-användare som loggar in på Power BI-tjänsten. Du måste använda DirectQuery i stället för import på grund av hur uppdateringen fungerar. När importbaserade rapporter uppdateras använder gatewayen de autentiseringsuppgifter som du angav i fälten **Användarnamn** och **Lösenord** när du skapade datakällan. Med andra ord används **inte** enkel inloggning med Kerberos. När du publicerar bör du även välja den gateway som du har konfigurerat för enkel inloggning om du har flera gatewayer. I Power BI-tjänsten bör du nu kunna uppdatera rapporten eller skapa en ny rapport baserat på den publicerade datamängden.

Den här konfigurationen fungerar i de flesta fall. Med Kerberos kan det dock förekomma olika konfigurationer beroende på din miljö. Om rapporten fortfarande inte kan läsas in, bör du kontakta domänadministratören för att undersöka saken vidare. Om din datakälla är SAP BW kan du även läsa felsökningsavsnitten på de datakällsspecifika konfigurationssidorna för [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md#troubleshooting) och [gx64krb5/gsskrb5](service-gateway-sso-kerberos-sap-bw-gx64krb.md#troubleshooting).

## <a name="next-steps"></a>Nästa steg

Mer information om den **lokala datagatewayen** och **DirectQuery** finns i följande resurser:

* [Vad är en lokal datagateway?](/data-integration/gateway/service-gateway-getting-started)
* [DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery och SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)
