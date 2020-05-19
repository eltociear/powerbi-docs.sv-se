---
title: Skapa SSL-certifikat för visuella Power BI-objekt
description: Läs hur du genererar SSL-certifikat med hjälp av Power BI visuella verktyg i Windows, Mac eller Linux, eller manuellt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: 37bd8f15dcf17cd0f967e819338a719edf2a3054
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276385"
---
# <a name="create-an-ssl-certificate"></a>Skapa ett SSL-certifikat

Den här artikeln beskriver hur du skapar och installerar Secure Sockets Layer-certifikat (SSL) för visuella Power BI-objekt.

För Windows-, macOS X-och Linux-procedurer måste du ha paketet Power BI Visual Tools **pbiviz** installerat. Mer information finns i [Konfigurera utvecklingsmiljön](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#setting-up-the-developer-environment). 

## <a name="create-a-certificate-on-windows"></a>Skapa ett certifikat i Windows

Generera certifikatet med hjälp av PowerShell-cmdleten `New-SelfSignedCertificate` i Windows 8 eller senare genom att köra följande kommando:

```powershell
pbiviz --install-cert
```

För Windows 7 kräver verktyget `pbiviz` att OpenSSL-verktyget är tillgängligt från kommandoraden. Du installerar OpenSSL genom att gå till [OpenSSL](https://www.openssl.org) eller [OpenSSL-binärfiler](https://wiki.openssl.org/index.php/Binaries).

Mer information och anvisningar om hur du installerar ett certifikat finns i [Skapa och installera ett certifikat för Windows](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#windows).

## <a name="create-a-certificate-on-macos-x"></a>Skapa ett certifikat i macOS X

Vanligtvis är OpenSSL-verktyget tillgängligt i operativsystemet macOS X.

Du kan även installera OpenSSL-verktyget genom att köra något av följande kommandon:

- Från *Brew*-pakethanteraren:
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- Med hjälp av *MacPorts*:
  
  ```cmd
  sudo port install openssl
  ```

När du har installerat OpenSSL-verktyget kör du följande kommando för att generera ett nytt certifikat:

```cmd
pbiviz --install-cert
```

Mer information och anvisningar finns i [Skapa och installera ett certifikat för OS X](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#osx).

## <a name="create-a-certificate-on-linux"></a>Skapa ett certifikat i Linux

Vanligtvis är OpenSSL-verktyget tillgängligt i operativsystemet Linux.

Innan du börjar kör du följande kommandon för att kontrollera att `openssl` och `certutil` är installerade:

```sh
which openssl
which certutil
```

Om `openssl` och `certutil` inte har installerats, installerar du verktygen `openssl` och `libnss3`.

### <a name="create-the-ssl-configuration-file"></a>Skapa SSL-konfigurationsfilen

Skapa en fil med namnet */tmp/openssl.cnf* som innehåller följande text:

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>Generera rotcertifikatutfärdaren

Kör följande kommandon för att generera en rotcertifikatutfärdare (CA) för att signera lokala certifikat:

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>Generera ett certifikat för localhost 

Generera ett certifikat för `localhost` med genererad CA och *openssl.cnf* genom att köra följande kommandon:

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>Lägg till rotcertifikat

Om du vill lägga till ett rotcertifikat i Chrome-webbläsarens databas kör du:

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

Om du vill lägga till ett rotcertifikat i Mozilla Firefox-webbläsarens databas kör du:

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

För att lägga till ett rotcertifikat för hela systemet, kör du:

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>Ta bort rotcertifikat

Om du vill ta bort ett rotcertifikat, kör du:

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>Generera ett certifikat manuellt

Du kan även generera ett SSL-certifikat manuellt med OpenSSL. Du kan ange valfritt verktyg för att generera certifikaten.

Om OpenSSL-verktyget redan är installerat, genererar du ett nytt certifikat genom att köra:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

Du kan vanligtvis hitta certifikat för `PowerBI-visuals-tools`-webbservern genom att köra något av följande kommandon:

- För den globala instansen av verktygen:
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- För den lokala instansen av verktygen:
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>PEM-format

Om du använder certifikatformatet Privacy Enhanced Mail (PEM) sparar du certifikatfilen som *PowerBIVisualTest_public.crt* och sparar den privata nyckeln som *PowerBIVisualTest_private.key*.

### <a name="pfx-format"></a>PFX-format

Om du använder certifikatformatet Personal Information Exchange (PFX) sparar du certifikatfilen som *PowerBIVisualTest_public.pfx*.

Om PFX-certifikatfilen kräver en lösenfras:

1. I konfigurationsfilen anger du:
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. I avsnittet `server` anger du lösenfrasen genom att ersätta platshållaren \<YOUR PASSPHRASE>:

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>Nästa steg
- [Utveckla ett visuellt Power BI-objekt](custom-visual-develop-tutorial.md)
- [Exempel på visuella Power BI-objekt](samples.md)
- [Publicera ett visuellt Power BI-objekt till AppSource](office-store.md)
