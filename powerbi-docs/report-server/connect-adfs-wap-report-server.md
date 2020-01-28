---
title: Använda webbprogramproxy och Active Directory Federated services – Power BI-rapportserver
description: Lär dig hur du använder webbprogramproxy (WAP) och Active Directory Federated Services (AD FS) för att ansluta till Power BI-rapportserver och SQL Server Reporting Services (SSRS) 2016 och senare.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: 2caa96aceef90ad1d25a521cbf4a3f699a2a64e0
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/16/2020
ms.locfileid: "76042450"
---
# <a name="use-web-application-proxy-and-active-directory-federated-services---power-bi-report-server"></a>Använda webbprogramproxy och Active Directory Federated services – Power BI-rapportserver

Den här artikeln beskriver hur du använder webbprogramproxy (WAP) och Active Directory Federated Services (AD FS) för att ansluta till Power BI-rapportserver och SQL Server Reporting Services (SSRS) 2016 och senare. Med den här integrationen kan användare som inte sitter i företagsnätverket få åtkomst till sina rapporter på Power BI-rapportserver och Reporting Services från klientens webbläsare och skyddas av AD FS-förautentisering. För Power BI-mobilappar måste du också [konfigurera OAuth för att ansluta till Power BI-rapportserver och SSRS](../consumer/mobile/mobile-oauth-ssrs.md).

## <a name="prerequisites"></a>Förutsättningar

### <a name="domain-name-services-dns-configuration"></a>Konfigurationen av Domain Name Services (DNS)

- Bestäm den offentliga URL som användaren ska ansluta till. Det kan se ut ungefär som i det här exemplet: `https://reports.contosolab.com`.
- Konfigurera din DNS-post för värdnamnet, till exempel `reports.contosolab.com`, så att den pekar mot den offentliga IP-adressen för Web Application Proxy (WAP)-servern.
- Konfigurera en offentlig DNS-post för AD FS-servern. Du kan till exempel ha konfigurerat AD FS-servern med följande URL: `https://adfs.contosolab.com`.
- Du måste först konfigurera DNS-posten så att den pekar mot den offentliga IP-adressen för Web Application Proxy (WAP)-servern, till exempel `adfs.contosolab.com`. Den publiceras som en del av WAP-programmet.

### <a name="certificates"></a>Certifikat

Du måste konfigurera certifikat för både WAP-applikationen och AD FS-servern. Båda dessa certifikat måste vara en del av en giltig certifikatutfärdare som dina datorer kan identifiera.

## <a name="1-configure-the-report-server"></a>1. Konfigurera rapportservern

Vi måste se till att vi har ett giltigt SPN (Service Principal Name). Giltiga SPN gör det möjligt att utföra rätt Kerberos-autentisering och aktivera rapportservern för förhandlingsautentisering.

### <a name="service-principal-name-spn"></a>Tjänstens huvudnamn (SPN)

SPN-namnet är en unik identifierare för en tjänst som använder Kerberos-autentisering. Se till att du har ett korrekt HTTP-SPN för rapportservern.

Information om hur du konfigurerar SPN (tjänstens huvudnamn) för rapportservern finns i [Registrera tjänstens huvudnamn (SPN) för en rapportserver](https://docs.microsoft.com/sql/reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server).

### <a name="enabling-negotiate-authentication"></a>Aktivera förhandling av autentisering

Om du vill låta en rapportserver använda Kerberos-autentisering, behöver du konfigurera autentiseringstypen för rapportservern som RSWindowsNegotiate. Du konfigurerar den i rsreportserver.config-filen.

```
<AuthenticationTypes>

    <RSWindowsNegotiate />

    <RSWindowsNTLM />

</AuthenticationTypes>
```

Mer information finns i [Ändra en Reporting Services-konfigurationsfil](https://docs.microsoft.com/sql/reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config) och [konfigurera Windows-autentisering på en rapportserver](https://docs.microsoft.com/sql/reporting-services/security/configure-windows-authentication-on-the-report-server).

## <a name="2-configure-active-directory-federation-services-ad-fs"></a>2. Konfigurera Active Directory Federation Services (AD FS)

Du måste konfigurera AD FS på en Windows 2016-server i din miljö. Konfigurationen kan göras via Serverhanteraren och genom att välja Lägg till roller och funktioner under hantera. För mer information, se [Active Directory Federation Services (AD FS)](https://docs.microsoft.com/windows-server/identity/active-directory-federation-services).

På AD FS-servern använder du AD FS-hanteringsappen och slutför de här stegen.

1. Högerklicka på **Förlitande part-förtroenden** > **Lägg till förlitande part-förtroenden**.

    ![Lägg till förlitande part-förtroenden](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust.png)

2. Följ stegen i guiden **Lägg till förlitande part-förtroende**.

    Välj alternativet **Inte anspråksmedveten** för att använda Windows-integrerad säkerhet som autentiseringsmekanism.

    ![Välkommen till guiden Lägg till förlitande part-förtroende](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust-welcome.png)

    Ange ett valfritt namn i **Ange visningsnamn** och välj **Nästa**.
    Lägg till identifierare för förlitande part-förtroende: `<ADFS\_URL>/adfs/services/trust`

    Exempel: `https://adfs.contosolab.com/adfs/services/trust`

    ![Rapportserver](media/connect-adfs-wap-report-server/report-server-adfs-configure-identifiers.png)

    Välj de **principer för åtkomstkontroll** som passar organisationens behov och välj **Nästa**.

    ![Välj åtkomstkontroll](media/connect-adfs-wap-report-server/report-server-adfs-choose-access-control.png)
    
    Välj **Nästa**och välj sedan **Slutför** för att slutföra guiden **Lägg till förlitande part-förtroende**.

    När du är klar bör egenskaperna för den förlitande partens förtroenden se ut så här.

    ![Förlitande part-förtroenden](media/connect-adfs-wap-report-server/report-server-adfs-relying-party-trusts.png)

## <a name="3-configure-web-application-proxy-wap"></a>3. Konfigurera webbprogramproxy (WAP)

Du bör aktivera Windowsrollen proxy för webbapp (roll) på en server i din miljö. Det måste vara en server med Windows 2016. Mer information finns i [Web Application Proxy i Windows Server 2016](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server) och [Publicera appar med AD FS-förautentisering](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication).

### <a name="configure-constrained-delegation"></a>Konfigurera begränsad delegering

För att övergå från formulärautentisering till Windows-autentisering behöver vi använda begränsad delegering med protokollövergång. Detta steg är en del av Kerberos-konfigurationen. Vi har redan definierat rapportserverns SPN i rapportserverkonfigurationen.

Vi måste konfigurera begränsad delegering på WAP-serverkontot inom Active Directory. Du kan behöva arbeta med en domänadministratör om du inte har åtkomstbehörighet till Active Directory.

Följ dessa steg om du vill konfigurera begränsad delegering.

1. På en dator som har Active Directory-verktygen installerade startar du **Active Directory-användare och -datorer**.
2. Hitta datorkontot för WAP-servern. Som standard sker detta i containern **Datorer**.
3. Högerklicka på servern för WAP och gå till **Egenskaper**.
4. Gå till fliken **Delegering**, välj **Lita på den här datorn enbart för delegering till angivna tjänster** och därefter **Använd valfritt autentiseringsprotokoll**.

    ![Lita på den här datorn](media/connect-adfs-wap-report-server/report-server-adfs-delegation-use-any.png)

1. Detta alternativ konfigurerar begränsad delegering för det här WAP-serverdatorkontot. Därefter måste vi konfigurera tjänsterna som den här datorn får delegera till.
2. Välj **Lägg till** under rutan med tjänster.

    ![AD FS Lägg till förtroende](media/connect-adfs-wap-report-server/report-server-adfs-trust-add.png)

1. Välj **Användare eller datorer**.
2. Ange det tjänstkonto som används för rapportservern. Det här kontot är detsamma som du använde för att lägga till HTTP-SPN i det tidigare avsnittet med [rapportserverkonfiguration](#1-configure-the-report-server). 

3. Välj HTTP SPN för rapportservern och välj sedan **OK**.

    > [!NOTE]
    > Du kan bara se NetBIOS SPN. Faktum är att både NetBIOS och FQDN väljs, om båda finns.

1. När du markerar kryssrutan **Utökad** bör resultatet se ut som följande exempel.

    ![WAP-egenskaper](media/connect-adfs-wap-report-server/report-server-wap-properties.png)

### <a name="add-wap-application"></a>Lägg till WAP-app

1. På webbprogramproxy-servern öppnar du konsolen för **Fjärråtkomsthantering** och väljer **Webbprogramproxy** i navigeringsfönstret. 

2. I fönstret **Uppgifter** väljer du **Publicera**.

2. På sidan Välkommen klickar du på **Nästa**.

    ![Välkommen till Publicera](media/connect-adfs-wap-report-server/report-server-welcome-publish-new-app-wizard.png)

3. På sidan **Förautentisering** väljer du **Active Directory Federation Services (AD FS)** och väljer sedan **Nästa**.

    ![Förautentisering](media/connect-adfs-wap-report-server/report-server-preauthentication-new-app-wizard.png)

4. Välj förautentiseringen **Webb-och MSOFBA** eftersom vi bara ska konfigurera webbläsaråtkomst för rapportservern och inte åtkomst till mobilappar.

    ![Klienter som stöds](media/connect-adfs-wap-report-server/report-server-supported-clients-publish-new-app-wizard.png)

5. Lägg till den **Förlitande part** som vi skapade på AD FS-server som visas nedan och välj sedan **Nästa**.

    ![Publicera förlitande part](media/connect-adfs-wap-report-server/report-server-relying-party-publish-new-app-wizard.png)

6. I avsnittet **Extern URL** ska du ange den offentligt tillgängliga URL som konfigurerats på WAP-servern. Lägg till URL: en som konfigurerades på rapportservern (Report Server Configuration Manager) enligt vad som visas nedan i avsnittet **Webbadress för serverdel**. Lägg till rapportserverns SPN i avsnittet **SPN för serverdel**.

    ![Publiceringsinställningar](media/connect-adfs-wap-report-server/report-server-publishing-settings-new-app-wizard.png)

7. Välj **Nästa** och **Publicera**.
8. Kör följande PowerShell-kommando för att verifiera WAP-konfigurationen.

    ```
    Get-WebApplicationProxyApplication "PBIRSBrowser" | FL
    ```

    ![PowerShell-kommando](media/connect-adfs-wap-report-server/report-server-powershell-get-webapplication.png)

## <a name="connect-to-the-report-server-through-the-browser"></a>Anslut till rapportservern via webbläsaren

Du kan sedan komma åt den offentliga WAP-URL: en, till exempel `https://reports.contosolab.com/ReportServer` för webbtjänsten och `https://reports.contosolab.com/Reports` för webbportalen från webbläsaren. När du har autentiserats kan du visa rapporterna.

![Inloggning till AD FS](media/connect-adfs-wap-report-server/report-server-adfs-sign-in.png)

## <a name="next-steps"></a>Nästa steg

* [Konfigurera OAuth för att ansluta till Power BI-rapportserver och SSRS](../consumer/mobile/mobile-oauth-ssrs.md)
*[Vad är Power BI-rapportserver?](get-started.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

