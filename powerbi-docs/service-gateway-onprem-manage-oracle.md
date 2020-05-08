---
title: Hantera din datakälla – Oracle
description: Hantera den lokala datagatewayen och datakällorna som tillhör denna gateway.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: 5641e42d380458bd1ddcdb316c56e17fafe2d71f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79207285"
---
# <a name="manage-your-data-source---oracle"></a>Hantera din datakälla – Oracle

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

När du har [installerat den lokala datagatewayen](/data-integration/gateway/service-gateway-install) behöver du [lägga till datakällor](service-gateway-data-sources.md#add-a-data-source) som kan användas med gatewayen. Den här artikeln handlar om hur du arbetar med gatewayer och Oracle-datakällor, antingen för schemalagd uppdatering eller för DirectQuery.

## <a name="install-the-oracle-client"></a>Installera Oracle-klienten

För att gatewayen ska kunna ansluta till Oracle-servern, måste Oracle Data Provider för .NET (ODP.NET) installeras och konfigureras. ODP.NET är en del av Oracle Data Access Components (ODAC).

För 32-bitars versionen av Power BI Desktop använder du följande länk för att hämta och installera 32-bitars Oracle-klient:

* [32-bitars Oracle Data Access Components (ODAC) med Oracle Developer Tools för Visual Studio (12.1.0.2.4)](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

För 64-bitars versionen av Power BI Desktop, eller den lokala datagatewayen, använder du följande länk för att hämta och installera 64-bitars Oracle-klient:

* [64-bitars ODAC 12.2c version 1 (12.2.0.1.0) för Windows x64](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

När klienten har installerats behöver du konfigurera filen tnsnames.ora med rätt information för din databas. Power BI Desktop och gatewayen utgår från net_service_name som definieras i filen tnsnames.ora. Om net_service_name inte har konfigurerats kan du inte ansluta. Standardsökvägen för tnsnames.ora är `[Oracle Home Directory]\Network\Admin\tnsnames.ora`. Mer information om hur du konfigurerar tnsnames.ora-filer finns i [Oracle: Lokala namnparametrar (tnsnames.ora)](https://docs.oracle.com/cd/B28359_01/network.111/b28317/tnsnames.htm).

### <a name="example-tnsnamesora-file-entry"></a>Exempelpost i tnsnames.ora-fil

Det här är det grundläggande formatet för en post i tnsname.ora:

```
net_service_name=
 (DESCRIPTION=
   (ADDRESS=(protocol_address_information))
   (CONNECT_DATA=
     (SERVICE_NAME=service_name)))
```

Här är ett exempel på hur server- och portinformation anges:

```
CONTOSO =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = oracleserver.contoso.com)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = CONTOSO)
    )
  )
```

## <a name="add-a-data-source"></a>Lägga till en datakälla

Mer information om hur du lägger till en datakälla finns i [Lägga till en datakälla](service-gateway-data-sources.md#add-a-data-source). Välj **Oracle** under **Typ av datakälla**.

![Lägga till Oracle-datakällan](media/service-gateway-onprem-manage-oracle/data-source-oracle.png)

När du har valt Oracle-datakälltypen fyller du i uppgifterna för datakällan, däribland **Server** och **Databas**. 

Du kan antingen välja **Windows** eller **Grundläggande** under **Autentiseringsmetod**. Välj **Grundläggande** om du planerar att använda ett konto som har skapats i Oracle i stället för Windows-autentisering. Ange sedan de autentiseringsuppgifter som ska användas för datakällan.

> [!NOTE]
> Alla frågor till datakällan kommer att köras med dessa autentiseringsuppgifter. Mer information om hur autentiseringsuppgifter lagras finns i [Lagra krypterade autentiseringsuppgifter i molnet](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud).

![Fylla i inställningarna för datakälla](media/service-gateway-onprem-manage-oracle/data-source-oracle2.png)

När du har fyllt i allt väljer du **Lägg till**. Nu kan du använda den här datakällan för schemalagd uppdatering, eller DirectQuery mot en lokal Oracle-Server. *Anslutningen lyckades* visas om anslutningen lyckades.

![Visa anslutningsstatus](media/service-gateway-onprem-manage-oracle/datasourcesettings4.png)

### <a name="advanced-settings"></a>Avancerade inställningar

Om du vill kan du konfigurera sekretessnivån för datakällan. Den här inställningen styr hur data kan kombineras. Den används endast vid schemalagd uppdatering. Sekretessnivåinställningen gäller inte för DirectQuery. Mer information om sekretessnivåer för datakälla finns i [Sekretessnivåer (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Ange sekretessnivån](media/service-gateway-onprem-manage-oracle/datasourcesettings9.png)

## <a name="use-the-data-source"></a>Använda datakällan

När du har skapat datakällan går den att använda med DirectQuery eller med schemalagd uppdatering.

> [!WARNING]
> Server- och databasnamnen måste överensstämma mellan Power BI Desktop och datakällan i den lokala datagatewayen.

Länken mellan din datauppsättning och datakällan i gatewayen är baserad på servernamnet och databasnamnet. Dessa namn måste matcha. Om du exempelvis anger en IP-adress för servernamnet i Power BI Desktop måste du använda den IP-adressen för datakällan i gatewaykonfigurationen. Det här namnet måste även matcha ett alias som har definierats i filen tnsnames.ora. Mer information om tnsnames.org-filen finns i [Installera Oracle-klienten](#install-the-oracle-client).

Det här kravet gäller både DirectQuery och schemalagd uppdatering.

### <a name="use-the-data-source-with-directquery-connections"></a>Använda datakällan med DirectQuery-anslutningar

Se till att server- och databasnamnen överensstämmer mellan Power BI Desktop och den konfigurerade datakällan för gatewayen. Du behöver även kontrollera att användaren finns med på fliken **Användare** för datakällan för att DirectQuery-datamängder ska kunna publiceras. Valet för DirectQuery uppstår i Power BI Desktop när du importerar data första gången. Mer information om hur DirectQuery används finns i [Använda DirectQuery i Power BI Desktop](desktop-use-directquery.md).

När du har publicerat, antingen från Power BI Desktop eller **Hämta Data**, borde dina rapporter fungera. Det kan ta ett par minuter efter att du har skapat datakällan i gatewayen innan anslutningen kan användas.

### <a name="use-the-data-source-with-scheduled-refresh"></a>Använda datakällan med schemalagd uppdatering

Om du finns med på fliken **Användare** för den datakälla som konfigurerats i gatewayen, och om servernamnet och databasnamnet matchar, visas gatewayen som ett alternativ för användning med schemalagd uppdatering.

![Visa användarna](media/service-gateway-onprem-manage-oracle/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="troubleshooting"></a>Felsökning

Det kn uppstå flera fel från Oracle när namnsyntaxen är felaktig eller inte har konfigurerats korrekt:

* ORA-12154: TNS: det gick inte att matcha angivet anslutnings-ID.
* ORA-12514: TNS: lyssnaren känner för närvarande inte till tjänsten som begärdes i anslutningsbeskrivningen.
* ORA-12541: TNS: det finns ingen lyssnare.
* ORA-12170: TNS: det uppstod en anslutningstimeout.
* ORA-12504: TNS: lyssnaren har inte angetts SERVICE_NAME i CONNECT_DATA.

Dessa fel kan inträffa antingen om Oracle-klienten inte är installerad eller om den inte har konfigurerats korrekt. Om den är installerad bör du kontrollera att filen tnsnames.ora är korrekt konfigurerad och att du använder rätt net_service_name. Du behöver även se till att net_service_name är samma mellan den dator som använder Power BI Desktop och den dator som kör gatewayen. Mer information finns i [Installera Oracle-klienten](#install-the-oracle-client).

> [!NOTE]
> Du kan också stöta på ett problem på grund av kompatibiliteten mellan Oracle serverversionen och Oracle-klientversionen. De två versionerna bör vanligtvis överensstämma.

Ytterligare felsökningsinformation som är relaterad till gateway finns i [Felsökning av lokal datagateway](/data-integration/gateway/service-gateway-tshoot).

## <a name="next-steps"></a>Nästa steg

* [Felsöka gatewayer – Power BI](service-gateway-onprem-tshoot.md)
* [Power BI Premium](service-premium.md)

Har du fler frågor? Fråga [Power BI Community](https://community.powerbi.com/).

