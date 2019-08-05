---
title: Aktivera kryptering för SAP HANA
description: Lär dig hur du krypterar anslutningen vid anslutning till en HANA-Server från Power BI med hjälp av enkel inloggning med SAML.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/26/2019
ms.author: mblythe
LocalizationGroup: Connect to data
ms.openlocfilehash: 9047ae7f74a7589d242531a5af18f6094c2b03a6
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/26/2019
ms.locfileid: "68523951"
---
# <a name="enable-encryption-for-sap-hana"></a>Aktivera kryptering för SAP HANA

Vi rekommenderar att du krypterar anslutningar till en SAP HANA-Server från Power BI Desktop och Power BI-tjänsten. Du kan aktivera HANA-kryptering med hjälp av både OpenSSL och SAP:s egenutvecklade CommonCryptoLib-bibliotek (tidigare kallat sapcrypto). SAP rekommenderar att du använder CommonCryptoLib, men grundläggande krypteringsfunktioner är tillgängliga med endera biblioteket.

Den här artikeln innehåller en översikt av hur du aktiverar kryptering med hjälp av OpenSSL och refererar till vissa områden i SAP-dokumentationen. Vi uppdaterar innehåll och länkar regelbundet, men för omfattande instruktioner och support bör du alltid läsa den officiella SAP-dokumentationen. Om du vill konfigurera kryptering med hjälp av CommonCryptoLib i stället för OpenSSL läser du [Så konfigurerar du TLS/SSL i SAP HANA 2.0](https://blogs.sap.com/2018/11/13/how-to-configure-tlsssl-in-sap-hana-2.0/) Steg för att migrera från OpenSSL till CommonCryptoLib finns i [SAP-anteckningen 2093286](https://launchpad.support.sap.com/#/notes/2093286) (s-användare krävs).

> [!NOTE]
> De konfigurationssteg som beskrivs i den här artikeln överlappar med konfigurationsstegen för enkel inloggning med SAML. Oavsett om du väljer OpenSSL eller CommonCryptoLib som din HANA-servers krypteringsalgoritm bör du se till att valet är konsekvent mellan SAML- och krypteringskonfigurationerna.

Det finns fyra steg för att aktivera kryptering för SAP HANA med hjälp av OpenSSL. Vi går igenom de här faserna härnäst.  Mer information finns i [Skydda kommunikationen mellan SAP HANA Studio och SAP HANA-server via SSL](https://blogs.sap.com/2015/09/28/securing-the-communication-between-sap-hana-studio-and-sap-hana-server-through-ssl/).

## <a name="use-openssl"></a>Använda OpenSSL

Se till att din HANA-server är konfigurerad att använda OpenSSL som kryptografiprovider. Ersätt den saknade sökvägsinformationen nedan med Server-ID (sid) för din HANA-server.

![Kryptografisk OpenSSL-provider](media/desktop-sap-hana-encryption/ssl-crypto-provider.png)

## <a name="create-a-certificate-signing-request"></a>Skapa en begäran om certifikatsignering

Skapa en begäran om X509-certifikatsignering för HANA-servern.

1. Med SSH ansluter du till den Linux-dator som HANA-servern körs på som \<sid\>adm.

1. Gå till startkatalogen _/__usr/sap/\<sid\>/home_.

1. Skapa en dold katalog med namnet _.__ssl_ om det inte redan finns en sådan.

1. Kör följande kommando:

    ```
    openssl req -newkey rsa:2048 -days 365 -sha256 -keyout Server\_Key.pem -out Server\_Req.pem -nodes
    ```

Det här kommandot skapar en begäran om certifikatsignering och en privat nyckel. När certifikatet har signerats är det giltigt i ett år (se parametern -days). När du uppmanas att ange ett eget namn (CN) anger du det fullständiga domännamnet (FQDN) för den dator där HANA-servern är installerad.

## <a name="get-the-certificate-signed"></a>Få certifikatet signerat

Få certifikatet signerat av en certifikatutfärdare (CA) som är betrodd av de klienter som du kommer att använda för att ansluta till HANA-servern.

1. Om du redan har en betrodd företagscertifikatutfärdare (som representeras av CA\_Cert.pem och CA\_Key.pem i följande exempel) signerar du certifikatbegäran genom att köra följande kommando:

    ```
    openssl x509 -req -days 365 -in Server\_Req.pem -sha256 -extfile /etc/ssl/openssl.cnf -extensions usr\_cert -CA CA\_Cert.pem -CAkey CA\_Key.pem -CAcreateserial -out Server\_Cert.pem
    ```

    Om du inte redan har en certifikatutfärdare som du kan använda så kan du skapa en rotcertifikatutfärdare själv genom att följa de steg som beskrivs i [Skydda kommunikationen mellan SAP HANA Studio och SAP HANA-server via SSL](https://blogs.sap.com/2015/09/28/securing-the-communication-between-sap-hana-studio-and-sap-hana-server-through-ssl/).

1. Skapa HAHA-servercertifikatkedjan genom att kombinera servercertifikatet, nyckeln och certifikatutfärdarens certifikat (namnet key.pem är konventionen för SAP HANA):

    ```
    cat Server\_Cert.pem Server\_Key.pem CA\_Cert.pem \> key.pem
    ```

1. Skapa en kopia av CA\_Cert.pem med namnet trust.pem (namnet trust.pem är konventionen för SAP HANA):

    ```
    cp CA\_Cert.pem trust.pem
    ```

1. Starta om HANA-servern.

1. Verifiera förtroenderelationen mellan en klient och den certifikatutfärdare som du använde för att signera SAP HANA-serverns certifikat.

    Klienten måste ha förtroende för den certifikatutfärdare som används för att signera HANA-serverns X509-certifikat innan en krypterad anslutning kan upprättas till HANA-servern från klientens dator.

    Det finns olika sätt att se till att denna förtroenderelation finns med hjälp av Microsoft Management Console (MMC) eller kommandoraden. Du kan importera certifikatutfärdarens X509-certifikat (trust.pem) till mappen **Betrodda rotcertifikatutfärdare** för den användare som kommer att upprätta anslutningen, eller till samma mapp för själva klientdatorn om det är önskvärt.

    ![Mappen Betrodda rotcertifikatutfärdare](media/desktop-sap-hana-encryption/trusted-root-certification.png)

    Du måste först konvertera trust.pem till en .crt-fil innan du kan importera certifikatet till mappen Betrodda rotcertifikatutfärdare, till exempel genom att köra följande OpenSSL-kommando:

    ```
    openssl x509 -outform der -in your-cert.pem -out your-cert.crt
    ```
    
    Information om hur du använder OpenSSL för konverteringen finns i [OpenSSL-dokumentationen](https://www.openssl.org/docs/manmaster/man1/x509.html).

## <a name="test-the-connection"></a>Testa anslutningen

Testa anslutningen i Power BI Desktop eller Power BI-tjänsten.

1. I Power BI Desktop eller på sidan **Hantera gatewayer** i Power BI-tjänsten kontrollerar du att **Validera servercertifikatet** är aktiverat innan du försöker upprätta en anslutning till SAP HANA-servern. För **SSL-kryptografiprovider** väljer du mscrypto om du har följt konfigurationsstegen för OpenSSL, och commoncrypto om du har konfigurerat det biblioteket som kryptografiprovider. Låt fälten SSL-nyckellager och SSL-förtroendelager vara tomma.

    - Power BI Desktop

        ![Validera servercertifikatet – tjänsten](media/desktop-sap-hana-encryption/validate-server-certificate-service.png)

    - Power BI-tjänst

        ![Validera servercertifikatet – Desktop](media/desktop-sap-hana-encryption/validate-server-certificate-desktop.png)

1. Kontrollera att du kan upprätta en krypterad anslutning till servern med alternativet **Verifiera servercertifikatet** aktiverat genom att läsa in data i Power BI Desktop eller uppdatera en publicerad rapport i Power BI-tjänsten.
