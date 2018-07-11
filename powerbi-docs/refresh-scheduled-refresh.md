---
title: Konfigurera schemalagd uppdatering
description: Detta beskrivs stegen för att välja en gateway och konfigurera schemalagd uppdatering.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: 96c1709c1d85b8a960be9c96b6839b69b4f22eaa
ms.sourcegitcommit: ba447d7cc94418d7d3cf6fdcb686ec1a859258a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37145466"
---
# <a name="configuring-scheduled-refresh"></a>Konfigurera schemalagd uppdatering

>[!NOTE]
>Efter två månaders inaktivitet pausas schemalagd uppdatering för en datauppsättning. Se avsnittet [*Uppdatera schema*](#schedule-refresh) senare i den här artikeln för mer information.
> 
> 

Om din datauppsättning stöder schemalagd uppdatering med hjälp av Uppdatera nu och Uppdatera schema, finns det några krav och inställningar som är viktiga att tillämpa för att uppdateringen ska lyckas. Dessa är **Gateway-anslutning**, **Autentiseringsuppgifter för datakälla** och **Uppdatera schema**. Låt oss ta en närmare titt på var och en.

Här beskrivs tillgängliga alternativ för både [Power BI Gateway – Personal](service-gateway-personal-mode.md) och [den lokala datagatewayen](service-gateway-onprem.md).

Du kan göra följande för att komma till skärmen Uppdatera schema.

1. Välj **ellipsen (...)** bredvid en datauppsättning som visas under **Datauppsättningar**.
2. Välj **Uppdatera schema**.
   
    ![](media/refresh-scheduled-refresh/dataset-menu.png)

## <a name="gateway-connection"></a>Gatewayanslutning
Olika alternativ visas beroende på om du har en personlig eller en företagsgateway online och tillgänglig.

Om ingen gateway är tillgänglig, visas **gatewayinställningarna** som inaktiverade. Du kan även se ett meddelande om hur du installerar den personliga gatewayen.

![](media/refresh-scheduled-refresh/gateway-not-configured.png)

Om du har en personlig gateway konfigurerad blir den tillgänglig för val om den är online. Den visas som offline om den inte är tillgänglig.

![](media/refresh-scheduled-refresh/gateway-connection.png)

Du kan också välja företagsgatewayen om du har en sådan tillgänglig. En företagsgateway visas som tillgänglig endast om ditt konto finns med på fliken Användare för den datakälla som har konfigurerats för en viss gateway.

## <a name="data-source-credentials"></a>Autentiseringsuppgifter för datakälla
### <a name="power-bi-gateway---personal"></a>Power BI Gateway – Personal
Om du använder den personliga gatewayen för att uppdatera data, måste ange de autentiseringsuppgifter som användes för att ansluta till serverdatakällan. Om du har anslutit till ett innehållspaket från en onlinetjänst överförs de autentiseringsuppgifter som du har angett för att ansluta för schemalagd uppdatering.

![](media/refresh-scheduled-refresh/data-source-credentials-pgw.png)

Du måste bara logga in till datakällor första gången du tillämpar uppdatering för den aktuella datauppsättningen. När autentiseringsuppgifterna har angetts sparas de för datauppsättningen.

> [!NOTE]
> Om lösenordet som du använder för att logga in till en datakälla upphör att gälla eller har ändras, måste du för vissa autentiseringsmetoder även ändra det för datakällan i autentiseringsuppgifterna för datakällan.
> 
> 

Om något går fel beror problemet oftast antingen på att gatewayen är offline, eftersom den inte kan logga in till Windows och starta tjänsten, eller att Power BI inte kan logga in till datakällorna för att fråga efter uppdaterade data. Kontrollera datauppsättningens inställningar om uppdateringen misslyckas. Om gatewaytjänsten är offline visas felet i Status för gateway. Om Power BI inte kan logga in till datakällorna, visas ett fel i Autentiseringsuppgifter för datakälla.

### <a name="on-premises-data-gateway"></a>Lokal datagateway
Du behöver inte ange autentiseringsuppgifter som definierats för datakällan av gatewayadministratören om du använder den lokala datagatewayen för att uppdatera data.

![](media/refresh-scheduled-refresh/data-source-credentials-egw.png)

> [!NOTE]
> När du ansluter till lokala SharePoint för datauppdatering, har Power BI endast stöd för autentiseringsmekanismerna *Anonym*, *Grundläggande* och *Windows (NTLM/Kerberos)*. Power BI stöder inte *ADFS* eller *några formulärbaserade autentiserings*mekanismer för datauppdatering av lokala SharePoint-datakällor.
> 
> 

## <a name="schedule-refresh"></a>Uppdatera schema
Du definierar frekvens och tidpunkter för att uppdatera datauppsättningen i avsnittet för schemalagd uppdatering. Vissa datakällor kräver inte tillgång till en gateway för att de ska kunna konfigureras. Andra kräver en gateway.

Du måste sätta skjutreglaget **Håll dina data aktuella** på **Ja** för att konfigurera inställningarna.

> [!NOTE]
> Power BI-tjänsten har som mål att initiera uppdatering av dina data inom **15 minuter** från din schemalagda uppdateringstid.
> 
> 

![](media/refresh-scheduled-refresh/scheduled-refresh.png)

> [!NOTE]
> Efter två månaders inaktivitet pausas schemalagd uppdatering för en datauppsättning. En datauppsättning betraktas som inaktiv när ingen användare har besökt någon instrumentpanel eller rapport som bygger på datauppsättningen. Efter den tidsperioden skickas ett e-postmeddelande till datauppsättningens ägare vari det anges att den schemalagda uppdateringen har pausats och uppdateringsschemat för datauppsättningen visas som **inaktiverat**. Om du vill återuppta schemalagd uppdatering besöker du helt enkelt någon av instrumentpanelerna eller rapporterna som bygger på datauppsättningen.
> 
> 

## <a name="whats-supported"></a>Vad stöds?
Vissa datauppsättningar stöds för olika gatewayar för schemalagd uppdatering. Nedan följer en referens för att få en uppfattning om vad som är tillgängligt.

### <a name="power-bi-gateway---personal"></a>Power BI Gateway – Personal
**Power BI Desktop**

* Alla datakällor online som visas i Hämta data och Frågeredigeraren i Power BI Desktop.
* Alla lokala datakällor som visas i Hämta data och Frågeredigeraren i Power BI Desktop, förutom Hadoop-filer (HDFS) och Microsoft Exchange.

**Excel**

> [!NOTE]
> I Excel 2016 eller senare, visas nu Power Query i avsnittet Data på menyfliksområdet under Hämta & Transformera data.
> 
> 

* Alla online-datakällor som visas i Power Query.
* Alla lokala datakällor som visas i Power Query förutom Hadoop-filer (HDFS) och Microsoft Exchange.
* Alla online-datakällor som visas i Power Pivot.\*
* Alla lokala datakällor som visas i Power Query förutom Hadoop-filer (HDFS) och Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

## <a name="troubleshooting"></a>Felsökning
Ibland går det inte som förväntat att uppdatera data. Vanligtvis rör problemet en gateway. Ta en titt på artiklarna för gatewayfelsökning där du hittar verktyg och information om kända problem.

[Felsöka den lokala datagatewayen](service-gateway-onprem-tshoot.md)

[Felsöka Power BI Gateway – Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)

## <a name="next-steps"></a>Nästa steg
[Datauppdatering i Power BI](refresh-data.md)  
[Power BI Gateway – Personal](service-gateway-personal-mode.md)  
[Lokal datagateway](service-gateway-onprem.md)  
[Felsöka den lokala datagatewayen](service-gateway-onprem-tshoot.md)  
[Felsöka Power BI Gateway – Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

