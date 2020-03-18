---
title: Skapa ett SSL-certifikat
description: Instruktioner med tillfällig lösning för att skapa certifikat manuellt för utvecklarserver
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: fab40863d7beae4892a56975aa5e92c4fe5486ac
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380282"
---
# <a name="create-an-ssl-certificate"></a>Skapa ett SSL-certifikat

I den här artikeln beskrivs hur du skapar ett SSL-certifikat.

Generera certifikatet med hjälp av PowerShell `New-SelfSignedCertificate`-cmdleten i Windows 8 eller senare genom att köra följande kommando:

```cmd
pbiviz --install-cert
```

Verktyget kräver en OpenSSL-installation för Windows 7. OpenSSL-verktyget måste vara tillgängligt från kommandoraden.

Du installerar OpenSSL genom att gå till webbplatsen för [OpenSSL](https://www.openssl.org) eller [OpenSSL-binärfiler](https://wiki.openssl.org/index.php/Binaries).

## <a name="create-a-certificate-mac-os-x"></a>Skapa ett certifikat (Mac OS X)

Vanligtvis är OpenSSL-verktyget tillgängligt i operativsystemet Linux eller Mac OS X.

Du kan även installera verktyget genom att köra något av följande kommandon:

* Från *Brew*-pakethanteraren:

    ```cmd
    brew install openssl
    brew link openssl --force
    ```

* Med hjälp av *MacPorts*:

    ```cmd
    sudo port install openssl
    ```

När du har installerat OpenSSL-verktyget för att generera ett nytt certifikat kör du följande kommando:

```cmd
pbiviz --install-cert
```

## <a name="create-a-certificate-linux"></a>Skapa ett certifikat (Linux)

Om OpenSSL-verktyget inte är tillgängligt i ditt Linux-operativsystem kan du installera det med ett av de följande kommandona:

* För *APT*-pakethanteraren:

    ```cmd
    sudo apt-get install openssl
    ```

* För *Yellowdog-uppdateraren*:

    ```cmd
    yum install openssl
    ```

* För *Redhat-pakethanteraren*:

    ```cmd
    rpm install openssl
    ```

Om OpenSSL-verktyget redan är tillgängligt i ditt operativsystem genererar du ett nytt certifikat genom att köra följande kommando:

```cmd
pbiviz --install-cert
```

Eller så kan du hämta OpenSSL-verktyget genom att gå till webbplatsen för [OpenSSL](https://www.openssl.org) eller [OpenSSL-binärfiler](https://wiki.openssl.org/index.php/Binaries).

## <a name="generate-the-certificate-manually"></a>Generera certifikatet manuellt

Du kan ange att dina certifikat ska genereras av valfria verktyg.

Om OpenSSL-verktyget redan är installerat i systemet genererar du ett nytt certifikat genom att köra följande kommandon:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

Du kan vanligtvis hitta certifikat för PowerBI-visuals-tools-webbservern genom att köra något av följande:

* För den globala instansen av verktygen:

    ```cmd
    %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
    ```

* För den lokala instansen av verktygen:

    ```cmd
    <custom visual project root>\node_modules\PowerBI-visuals-tools\certs
    ```

Om du använder PEM-formatet sparar du certifikatfilen som *PowerBICustomVisualTest_public.crt* och sparar privateKey som *PowerBICustomVisualTest_public.key*.

Om du använder PFX-formatet sparar du certifikatfilen som *PowerBICustomVisualTest_public.pfx*.

Om PFX-certifikatfilen kräver en lösenfras gör du följande:
1. I konfigurationsfilen anger du:

    ```cmd
    \PowerBI-visuals-tools\config.json
    ```

1. I avsnittet `server` anger du lösenfrasen genom att ersätta platshållaren "*YOUR PASSPHRASE*":

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBICustomVisualTest_private.key",
        "certificate":"certs/PowerBICustomVisualTest_public.crt",
        "pfx":"certs/PowerBICustomVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"YOUR PASSPHRASE"
    }
    ```