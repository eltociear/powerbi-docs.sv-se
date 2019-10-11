---
title: Använda enkel inloggning med Kerberos för enkel inloggning till SAP BW med hjälp av CommonCryptoLib (sapcrypto.dll)
description: Konfigurera din SAP BW-server för att aktivera enkel inloggning från Power BI-tjänsten med hjälp av CommonCryptoLib (sapcrypto.dll)
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 9e676d7a14a2094d2fd7a8e41f8e49dc64f96ec2
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968783"
---
# <a name="use-kerberos-single-sign-on-for-sso-to-sap-bw-using-commoncryptolib-sapcryptodll"></a>Använda enkel inloggning med Kerberos för enkel inloggning till SAP BW med hjälp av CommonCryptoLib (sapcrypto.dll)

I den här artikeln beskrivs hur du konfigurerar din SAP BW-datakälla för att aktivera enkel inloggning från Power BI-tjänsten med hjälp av CommonCryptoLib (sapcrypto.dll).

> [!NOTE]
> Slutför stegen i den här artikeln utöver stegen i [Konfigurera enkel inloggning med Kerberos](service-gateway-sso-kerberos.md) innan du försöker uppdatera en SAP BW-baserad rapport som använder enkel inloggning med Kerberos. Användning av CommonCryptoLib som ditt SNC-bibliotek möjliggör anslutningar med enkel inloggning till både SAP BW-programservrar och SAP BW-meddelandeservrar.

## <a name="configure-sap-bw-to-enable-sso-using-commoncryptolib"></a>Konfigurera SAP BW för att aktivera enkel inloggning med hjälp av CommonCryptoLib

> [!NOTE]
> Den lokala datagatewayen är 64-bitars programvara och kräver därför 64-bitarsversionen av CommonCryptoLib (sapcrypto.dll) för att utföra BW SSO. Om du planerar att testa anslutningen med enkel inloggning till din SAP BW-server i SAP-gränssnittet innan du försöker använda en anslutning med enkel inloggning via gatewayen (rekommenderas) behöver du även 32-bitarsversionen av CommonCryptoLib, eftersom SAP-gränssnittet är 32-bitars programvara.

1. Se till att din BW-server är korrekt konfigurerad för enkel inloggning med Kerberos via CommonCryptoLib. Om den är det bör du kunna använda enkel inloggning för att komma åt din BW-server (antingen direkt eller via en SAP BW-meddelandeserver) med ett SAP-verktyg såsom SAP-gränssnittet som har konfigurerats till att använda CommonCryptoLib. Mer information om konfigurationssteg finns i [Enkel inloggning med SAP: Autentisera med Kerberos/SPNEGO](https://blogs.sap.com/2017/07/27/sap-single-sign-on-authenticate-with-kerberosspnego/). BW-servern ska använda CommonCryptoLib som SNC-bibliotek och ha ett SNC-namn som börjar med "CN=", till exempel "CN=BW1". Mer information om krav för SNC-namn finns i [SNC-parametrar för Kerberos-konfiguration](https://help.sap.com/viewer/df185fd53bb645b1bd99284ee4e4a750/3.0/en-US/360534094511490d91b9589d20abb49a.html) (mer specifikt parametern snc/identity/as).

1. Om du inte redan har gjort det installerar du x64-versionen av [SAP .NET-anslutningsprogrammet](https://support.sap.com/en/product/connectors/msnet.html) på den dator där gatewayen har installerats. Du kan kontrollera om komponenten har installerats genom att försöka ansluta till din BW-server i Power BI Desktop från gatewaydatorn. Om du inte kan ansluta med 2.0-implementeringen betyder det att .NET-anslutningsprogrammet inte är installerat, eller inte har installerats på GAC.

1. Se till att SAP Secure Login Client (SLC) inte körs på den dator där gatewayen är installerad. SLC cachelagrar Kerberos-biljetter på ett sätt som kan störa gatewayens förmåga att använda Kerberos för enkel inloggning. Om SLC är installerat avinstallerar du det eller ser till att avsluta SAP Secure Login Client: högerklicka på ikonen i systemfältet och välj Logga ut och Avsluta innan du provar en anslutning med enkel inloggning med hjälp av gatewayen. SLC stöds inte för användning på Windows Server-datorer. Mer information finns i [SAP-anteckningen 2780475](https://launchpad.support.sap.com/#/notes/2780475) (s-användare krävs).

    ![SAP Secure Login Client](media/service-gateway-sso-kerberos/sap-secure-login-client.png)

    Om du avinstallerar SLC eller väljer **Logga ut** och **Avsluta** öppnar du ett kommandoradsfönster och anger `klist purge` för att rensa cachelagrade Kerberos-biljetter innan du provar en anslutning med enkel inloggning via gatewayen.

1. Ladda ned 64-bitars CommonCryptoLib (sapcrypto.dll) version **8.5.25 eller senare** från SAP Launchpad och kopiera den till en mapp på gatewaydatorn. I samma katalog dit du kopierade sapcrypto.dll skapar du en fil som heter sapcrypto.ini med följande innehåll:

    ```
    ccl/snc/enable_kerberos_in_client_role = 1
    ```

    .ini-filen innehåller konfigurationsinformation som krävs av CommonCryptoLib för att aktivera enkel inloggning i gatewayscenariot.

    > [!NOTE]
    > De här filerna måste lagras på samma plats. Med andra ord ska _/path/to/sapcrypto/_ innehålla både sapcrypto.ini och sapcrypto.dll.

    Både gatewayens tjänstanvändare och den AD-användare (Active Directory) som tjänstanvändaren kommer att personifiera behöver läs- och körningsbehörigheter för båda filerna. Vi rekommenderar att du beviljar gruppen Autentiserade användare behörigheter i både .ini- och .dll-filerna. I testsyfte kan du även uttryckligen bevilja dessa behörigheter till både gatewayens tjänstanvändare och den Active Directory-användare som du kommer att använda för testning. I skärmbilden nedan har vi beviljat gruppen Autentiserade användare **läs- &amp; körningsbehörigheter** för sapcrypto.dll:

    ![Autentiserade användare](media/service-gateway-sso-kerberos/authenticated-users.png)

1. Om du inte redan har en SAP BW-datakälla som är associerad med den gateway som du vill att anslutningen med enkel inloggning ska gå genom, lägger du till en sådan på sidan **Hantera gatewayer** i Power BI-tjänsten. Om du redan har en sådan datakälla gör du dig redo att redigera den. Välj **SAP Business Warehouse** som **Typ av datakälla** om du vill skapa en anslutning med enkel inloggning till en BW-programserver. Välj **Sap Business Warehouse Message Server** om du vill skapa en anslutning med enkel inloggning till en BW-meddelandeserver.

    För **SNC-bibliotek** väljer du antingen **SNC\_LIB- eller SNC\_LIB\_64-miljövariabel** eller **Anpassad**. Om du väljer alternativet **SNC\_LIB** måste du ange värdet för miljövariabeln **SNC\_LIB\_64** på gatewaydatorn till den absoluta sökvägen för 64-bitarskopian av sapcrypto.dll på gatewaydatorn, till exempel *C:\Användare\Test\Desktop\sapcrypto.dll*. Om du väljer **Anpassad** klistrar du in den absoluta sökvägen till sapcrypto.dll i det fält för anpassad SNC-bibliotekssökväg som visas på sidan **Hantera gatewayer**. För **SNC-partnernamn** anger du BW-serverns SNC-namn. Under **Avancerade inställningar** kontrollerar du att **Använd enkel inloggning via Kerberos för DirectQuery-frågor** är markerat. De andra fälten bör fyllas i på samma sätt som om du hade upprättat en Windows-autentiseringsanslutning från PBI Desktop.

1. Skapa en **CCL\_PROFILE**-systemmiljövariabel och peka den på sapcrypto.ini:

    ![CCL\_PROFILE-systemmiljövariabel](media/service-gateway-sso-kerberos/ccl-profile-variable.png)

    Kom ihåg att sapcrypto.dll- och .ini-filerna måste finnas på samma plats. I det exempel som visas ovan där sapcrypto.ini finns på skrivbordet bör ska sapcrypto.dll också finnas på skrivbordet.

1. Starta om gatewaytjänsten:

    ![Starta om gatewaytjänsten](media/service-gateway-sso-kerberos/restart-gateway-service.png)

1. [Köra en Power BI-rapport](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Felsökning

Om du inte kan uppdatera rapporten i Power BI-tjänsten kan du använda gatewayspårning, CPIC-spårning och CommonCryptoLib-spårning för att diagnostisera problemet. CPIC-spårning och CommonCryptoLib är SAP-produkter, så Microsoft kan inte tillhandahålla direkt support för dem. För Active Directory-användare som ska beviljas åtkomst med enkel inloggning till BW kan vissa Active Directory-konfigurationer kräva att användarna är medlemmar i gruppen Administratörer på den dator där gatewayen är installerad.

1. **Gatewayloggar:** Du reproducerar problemet genom att öppna [gatewayappen](https://docs.microsoft.com/data-integration/gateway/service-gateway-app), gå till fliken **Diagnostik** och välja **Exportera loggar**:

    ![Exportera gatewayloggar](media/service-gateway-sso-kerberos/export-gateway-logs.png)

1. **CPIC-spårning:** För att aktivera CPIC-spårning anger du två miljövariabler: **CPIC\_TRACE** och **CPIC\_TRACE\_DIR**. Den första variabeln anger spårningsnivån och den andra variabeln anger katalogen för spårningsfil. Katalogen måste vara en plats som medlemmar i gruppen Autentiserade användare kan skriva till. Ange **CPIC\_TRACE** till 3 och **CPIC\_TRACE\_DIR** till valfri katalog som du vill att spårningsfilerna ska skrivas till. Till exempel:

    ![CPIC-spårning](media/service-gateway-sso-kerberos/cpic-tracing.png)

    Återskapa problemet och kontrollera att CPIC\_TRACE\_DIR innehåller spårningsfiler.

1. **CommonCryptoLib-spårning:** Aktivera CommonCryptoLib-spårning genom att lägga till två rader i den sapcrypto.ini-fil som du skapade tidigare:

    ```
    ccl/trace/level=5
    ccl/trace/directory=<drive>:\logs\sectrace
    ```

    Se till att ändra alternativet _ccl/trace/directory_ till en plats som medlemmar i gruppen Autentiserade användare kan skriva till. Alternativt så kan du skapa en ny .ini-fil för att ändra det här beteendet. I samma katalog som sapcrypto.ini och sapcrypto.dll skapar du en fil som heter sectrace.ini med nedanstående innehåll. Ersätt alternativet **DIRECTORY** med en plats på din dator som medlemmar i gruppen **Autentiserade användare** kan skriva till:

    ```
    LEVEL = 5
    DIRECTORY = <drive>:\logs\sectrace
    ```

    Reproducera nu problemet och kontrollera att den plats som **DIRECTORY** pekar på innehåller spårningsfiler. Se till att inaktivera CPIC- och CCL-spårning när du är klar.

    Mer information om CommonCryptoLib-spårning finns i [SAP-anteckningen 2491573](https://launchpad.support.sap.com/#/notes/2491573) (s-användare krävs).

## <a name="next-steps"></a>Nästa steg

Mer information om den **lokala datagatewayen** och **DirectQuery** finns i följande resurser:

* [Vad är en lokal datagateway?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery och SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)
