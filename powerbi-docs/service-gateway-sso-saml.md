---
title: Använda SAML för enkel inloggning (SSO) till lokala datakällor
description: Konfigurera din gateway med Security Assertion Markup Language (SAML) för att aktivera enkel inloggning (SSO) från Power BI till lokala datakällor.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 03/05/2019
LocalizationGroup: Gateways
ms.openlocfilehash: c1ca797efa2e40bf74384a1e9f2362acd26c6f8f
ms.sourcegitcommit: 883a58f63e4978770db8bb1cc4630e7ff9caea9a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/07/2019
ms.locfileid: "57555646"
---
# <a name="use-security-assertion-markup-language-saml-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>Använda Security Assertion Markup Language (SAML) för enkel inloggning (SSO) från Power BI till lokala datakällor

Använd [Security Assertion Markup Language (SAML)](https://www.onelogin.com/pages/saml) för att aktivera sömlös anslutning för enkel inloggning. När enkel inloggning aktiveras blir det enkelt för Power BI-rapporter och instrumentpaneler att uppdatera data från lokala källor.

## <a name="supported-data-sources"></a>Datakällor som stöds

Vi stöder för närvarande SAP HANA med SAML. Mer information om att installera och konfigurera enkel inloggning för SAP HANA med hjälp av SAML finns i ämnet om [SAML SSO för BI-plattform till HANA](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA) i SAP HANA-dokumentationen.

Vi har stöd för ytterligare datakällor med [Kerberos](service-gateway-sso-kerberos.md).

## <a name="configuring-the-gateway-and-data-source"></a>Konfigurera gatewayen och datakällan

Om du vill använda SAML genererar du först ett certifikat för SAML-identitetsprovidern och mappar sedan en Power BI-användare till identiteten.

1. Generera ett certifikat. Se till att du använder det fullständiga domännamnet för SAP HANA-servern när du fyller i *eget namn*. Certifikatet upphör att gälla efter 365 dagar.

    ```
    openssl req -newkey rsa:2048 -nodes -keyout samltest.key -x509 -days 365 -out samltest.crt
    ```

1. I SAP HANA Studio högerklickar du på din SAP HANA-server och navigerar sedan till **Säkerhet** > **Open Security Console (Öppna säkerhetskonsol)** > **SAML Identity Provider (SAML-identitetsprovider)** > **OpenSSL Cryptographic Library (kryptografiskt bibliotek för OpenSSL)**.

    Det är också möjligt att använda det kryptografiska SAP-biblioteket (kallas även CommonCryptoLib eller sapcrypto) istället för OpenSSL för att slutföra de här installationsstegen. Läs den officiella SAP-dokumentationen för mer information.

1. Välj **Importera**, navigera till samltest.crt och importera den.

    ![Identitetsprovidrar](media/service-gateway-sso-saml/identity-providers.png)

1. I SAP HANA Studio väljer du mappen **Säkerhet**.

    ![Mappen Säkerhet](media/service-gateway-sso-saml/security-folder.png)

1. Expandera **Användare** och välj sedan den användare som du vill mappa din Power BI-användare till.

1. Välj **SAML** och sedan **Konfigurera**.

    ![Konfigurera SAML](media/service-gateway-sso-saml/configure-saml.png)

1. Välj den identitetsprovider som du skapade i steg 2. För **Extern identitet** anger du Power BI-användarens UPN och väljer sedan **Lägg till**.

    ![Välja identitetsprovider](media/service-gateway-sso-saml/select-identity-provider.png)

Nu när du har konfigurerat certifikatet och identiteten konverterar du certifikatet till ett pfx-format och konfigurerar gatewaydatorn till att använda certifikatet.

1. Konvertera certifikatet till pfx-format genom att köra följande kommando.

    ```
    openssl pkcs12 -inkey samltest.key -in samltest.crt -export -out samltest.pfx
    ```

1. Kopiera pfx-filen till gatewaydatorn:

    1. Dubbelklicka på samltest.pfx och välj sedan **Lokal dator** > **Nästa**.

    1. Ange lösenordet och välj sedan **Nästa**.

    1. Välj **Placera alla certifikat i nedanstående arkiv**, sedan **Bläddra** > **Personligt** > **OK**.

    1. Välj **Nästa** och sedan **Slutför**.

    ![Importera certifikatet](media/service-gateway-sso-saml/import-certificate.png)

1. Bevilja gatewaytjänstkontot åtkomst till den privata nyckeln för certifikatet:

    1. På gatewaydatorn kör du Microsoft Management Console (MMC).

        ![Köra MMC](media/service-gateway-sso-saml/run-mmc.png)

    1. Under **Arkiv** väljer du **Lägg till/ta bort snapin-modul**.

        ![Lägga till snapin-modulen](media/service-gateway-sso-saml/add-snap-in.png)

    1. Välj **Certifikat** > **Lägg till** och välj sedan **Datorkonto** > **Nästa**.

    1. Välj **Lokal dator** > **Slutför** > **OK**.

    1. Expandera **Certifikat** > **Personligt** > **Certifikat** och leta upp certifikatet.

    1. Högerklicka på certifikatet och navigera till **Alla uppgifter** > **Hantera privata nycklar**.

        ![Hantera privata nycklar](media/service-gateway-sso-saml/manage-private-keys.png)

    1. Lägg till gatewaytjänstkontot till listan. Som standard är kontot **NT SERVICE\PBIEgwService**. Du kan ta reda på vilket konto som kör gatewaytjänsten genom att köra **services.msc** och leta upp **Tjänst för lokal datagateway**.

        ![Gatewaytjänst](media/service-gateway-sso-saml/gateway-service.png)

Slutligen följer du dessa steg för att lägga till tumavtrycket för certifikatet till gatewaykonfigurationen.

1. Kör följande PowerShell-kommando för att visa certifikaten på datorn.

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```
1. Kopiera tumavtrycket för det certifikat som du skapade.

1. Gå till gatewaykatalogen, vilken som standard är C:\Program Files\On-premises data gateway (Lokal datagateway).

1. Öppna PowerBI.DataMovement.Pipeline.GatewayCore.dll.config och leta upp avsnittet \*SapHanaSAMLCertThumbprint\*. Klistra in det tumavtryck som du kopierade.

1. Starta om gatewaytjänsten.

## <a name="running-a-power-bi-report"></a>Köra en Power BI-rapport

Nu kan du använda sidan **Hantera gateway** i Power BI för att konfigurera datakällan och för att under dess **Avancerade inställningar** aktivera enkel inloggning. Du kan sedan publicera rapporter och datamängder med bindning till den datakällan.

![Avancerade inställningar](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="troubleshooting"></a>Felsökning

När du har konfigurerat enkel inloggning kan följande felmeddelande visas i Power BI-portalen: ”De tillhandahållna autentiseringsuppgifterna kan inte användas för SapHana-källan.” Det här felet indikerar att SAML-autentiseringsuppgifterna avvisades av SAP HANA.

Autentiseringsspårning ger detaljerad information för felsökning av problem med autentisering på SAP HANA. Följ de här stegen för att konfigurera spårning för din SAP HANA-server.

1. Aktivera autentiseringsspårning genom att köra följande fråga på SAP HANA-servern.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. Återskapa ditt problem.

1. Öppna administrationskonsolen i HANA Studio och gå till fliken **Diagnosis Files** (diagnostikfiler).

1. Öppna den senaste spårningen av indexservern och sök efter SAMLAuthenticator.cpp.

    Du bör hitta ett detaljerat felmeddelande som anger den grundläggande orsaken, som i följande exempel.

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. När du har slutfört felsökningen kan du stänga av autentiseringsspårningen genom att köra följande fråga.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>Nästa steg

Mer information om den **lokala datagatewayen** och **DirectQuery** finns i följande resurser:

* [Lokal datagateway](service-gateway-onprem.md)
* [DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery och SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)
