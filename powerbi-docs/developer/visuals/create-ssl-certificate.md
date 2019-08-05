---
title: Skapa SSL-certifikat
description: Instruktioner med tillfällig lösning för att skapa certifikat manuellt för utvecklarserver
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 3287e8a7eb1c36c3f0d8a1fc24faa0442de2dddf
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425446"
---
# <a name="creating-ssl-certificate"></a>Skapa SSL-certifikat

Kör följande kommando för att generera certifikatet med hjälp av PowerShell New-SelfSignedCertificate-cmdlet:en i Windows 8 eller senare.

Verktyget kräver OpenSSL-installation för **Windows** **7**. Verktyget `openssll` måste vara tillgängligt från kommandoraden.

För att installera OpenSSL besöker du [https://www.openssl.org](https://www.openssl.org) eller [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-mac-os-x"></a>Skapa certifikat (Mac OS X)

Vanligtvis är OpenSSL-verktyg tillgängliga i operativsystemen Linux eller Mac OS X.

Annars kan du installera från

*Brew*-pakethanteraren

```cmd
brew install openssl
brew link openssl --force
```

eller med hjälp av *MacPorts*

```cmd
sudo port install openssl
```

Efter installation av OpenSSL för att generera nytt certifikatanrop:

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-linux"></a>Skapa certifikat (Linux)

OpenSSL-verktyg är inte tillgängliga i ditt Linux-operativsystem. Du kan installera med följande kommandon.

För *APT*-pakethanteraren:

```cmd
sudo apt-get install openssl
```

För *Yellowdog-uppdateraren*:

```cmd
yum install openssl
```

För *Redhat-pakethanteraren*:

```cmd
rpm install openssl
```

Om OpenSSl redan är tillgängligt i ditt operativsystem anropar du

```cmd
pbiviz --create-cert
```

för att generera ett nytt certifikat.

Eller så hämtar du från [https://www.openssl.org](https://www.openssl.org) eller [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

## <a name="generate-certificate-manually"></a>Generera certifikat manuellt

Du kan ange dina certifikat som genereras av verktyg.

Om du har OpenSSL installerat på datorn kan du köra följande kommando för att generera ett nytt certifikat

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

Vanligtvis finns certifikat för PowerBI-visuals-tools-webbservern på

```cmd
%appdata%\npm\node_modules\PowerBI-visuals-tools\certs
```

för den globala instansen av verktygen

eller

```cmd
<custom visual project root>\node_modules\PowerBI-visuals-tools\certs
```

för den lokala instansen av verktygen.

Du bör spara certifikatfilen som `PowerBICustomVisualTest_public.cer` och den privata nyckeln som `PowerBICustomVisualTest_public.key` om du använder PEM-format.
Spara certifikatfilen som `PowerBICustomVisualTest_public.pfx` om du använder PFX-formatet.

Om PFX-certifikatfilen kräver lösenfras bör du ange följande i

```cmd
\PowerBI-visuals-tools\config.json
```

serveravsnittet:

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
