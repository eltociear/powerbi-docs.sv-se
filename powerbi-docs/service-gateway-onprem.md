---
title: Lokal datagateway
description: Det här är en översikt över den lokala datagatewayen för Power BI. Du kan använda den här gatewayen för att arbeta med DirectQuery-datakällor. Du kan också använda den för att uppdatera molndatauppsättningar med lokala data.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/26/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 4eb9f8e0b8548fbecd4e5d2e2fd47c4c3acd2bd6
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34722826"
---
# <a name="on-premises-data-gateway"></a>Lokal datagateway

Den lokala datagatewayen fungerar som en brygga med snabb och säker dataöverföring mellan lokala data (data som inte finns i molnet) och tjänsterna Power BI, Microsoft Flow, Logic Apps och PowerApps.

Du kan använda en enda gateway med flera olika tjänster samtidigt. Om du använder både Power BI och PowerApps kan du använda en enda gateway för båda. Det beror på vilket konto som du loggar in med.

> [!NOTE]
> Den lokala datagatewayen implementerar datakomprimering och transportkryptering i alla lägen.
> 
> 

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-requirements-include.md)]

### <a name="limitations-of-analysis-services-live-connections"></a>Begränsningar för Analysis Services realtidsanslutningar
Du kan använda en realtidsanslutning för tabellinstanser eller flerdimensionella instanser.

| **Serverversion** | **Obligatorisk SKU** |
| --- | --- |
| 2012 SP1 CU4 eller senare |Business Intelligence och Enterprise SKU |
| 2014 |Business Intelligence och Enterprise SKU |
| 2016 |Standard-SKU eller högre |

* Formatering på cellnivå och översättningsfunktioner stöds inte.
* Åtgärder och namngivna mängder exponeras inte för Power BI, men du kan fortfarande ansluta till flerdimensionella kuber som också innehåller åtgärder eller namngivna mängder och skapa visuella objekt och rapporter.

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="download-and-install-the-on-premises-data-gateway"></a>Hämta och installera den lokala datagatewayen
Om du vill hämta gatewayen, väljer du **Datagateway** under menyn Hämtningar. Ladda ned den [lokala datagatewayen](http://go.microsoft.com/fwlink/?LinkID=820925).

![](media/service-gateway-onprem/powerbi-download-data-gateway.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-install-include](./includes/gateway-onprem-install-include.md)]

## <a name="install-the-gateway-in-personal-mode"></a>Installera gatewayen i personligt läge
> [!NOTE]
> Personal-varianten fungerar bara med Power BI.
> 
> 

När den personliga gatewayen har installerats behöver du starta **konfigurationsguiden för Power BI Gateway – Personal**.

![](media/service-gateway-onprem/personal-gateway-launch-configuration.png)

Du måste sedan logga in till Power BI för att registrera gatewayen för molntjänsten.

![](media/service-gateway-onprem/personal-gateway-signin.png)

Du måste också ange Windows-användarnamnet och -lösenordet för Windows-tjänsten. Du kan ange ett annat Windows-konto än ditt egna. Gatewaytjänsten körs med det här kontot.

![](media/service-gateway-onprem/personal-gateway-windows-service.png)

När installationen är klar behöver du gå till dina datauppsättninger i Power BI och kontrollera att autentiseringsuppgifterna har angetts för dina lokala datakällor.

<a name="credentials"></a>

## <a name="storing-encrypted-credentials-in-the-cloud"></a>Lagra krypterade autentiseringsuppgifter i molnet
När du lägger till en datakälla till gatewayen, måste du ange autentiseringsuppgifter för datakällan. Alla frågor till datakällan kommer att köras med dessa autentiseringsuppgifter. Autentiseringsuppgifterna krypteras på ett säkert sätt, med hjälp av asymmetrisk kryptering så att de inte kan dekrypteras i molnet, innan de lagras i molnet. Autentiseringsuppgifterna skickas till den dator som kör gatewayen, lokalt där de dekrypteras när datakällorna används.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

<!-- How the gateway works -->
[!INCLUDE [gateway-onprem-how-it-works-include](./includes/gateway-onprem-how-it-works-include.md)]

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
* [Azure Information Protection](https://docs.microsoft.com/en-us/microsoft-365/enterprise/protect-files-with-aip
) stöds inte för närvarande
* [Åtkomst online](https://products.office.com/en-us/access) stöds inte för närvarande

## <a name="tenant-level-administration"></a>Administration på klientorganisationsnivå 

Det finns för tillfället ingen gemensam plats där klientorganisationsadministratörerna kan hantera alla gatewayer som andra har installerat och konfigurerat.  Om du är klientorganisationsadministratör rekommenderar vi att du frågar användarna i organisationen om de kan lägga till dig som administratör för varje gateway de installerar. Då kan du hantera alla gatewayer i organisationen på sidan med gatewayinställningar eller med hjälp av [PowerShell-kommandon](https://docs.microsoft.com/power-bi/service-gateway-high-availability-clusters#powershell-support-for-gateway-clusters). 

## <a name="enabling-outbound-azure-connections"></a>Aktivera utgående Azure-anslutningar 
Den lokala datagatewayen är beroende av Azure Service Bus för molnanslutning och upprättar motsvarande utgående anslutningar till den kopplade Azure-regionen. Som standard är detta platsen för din Power BI-klientorganisation. Se [Var finns min Power BI-klient?](https://powerbi.microsoft.com/en-us/documentation/powerbi-admin-where-is-my-tenant-located/)
Om en brandvägg blockerar utgående anslutningar, måste du konfigurera brandväggen så att den tillåter utgående anslutningar från den lokala datagatewayen till den kopplade Azure-regionen. Se [IP-intervall för Microsoft Azure-datacenter](https://www.microsoft.com/en-us/download/details.aspx?id=41653) för mer information om IP-adressintervall för varje Azure-datacenter.
> [!NOTE]
> IP-adressintervall kan förändras över tid, så se till att du laddar ned den senaste informationen med jämna mellanrum. 

## <a name="troubleshooting"></a>Felsökning
Om du får problem när du installerar och konfigurerar en gateway, hittar du mer information under [Felsökning av lokal datagateway](service-gateway-onprem-tshoot.md). Om du tror att du har ett problem med brandväggen kan du läsa mer i avsnittet om [brandvägg eller proxy](service-gateway-onprem-tshoot.md#firewall-or-proxy) i felsökningsartikeln.

Gå till [Konfigurera proxyinställningar för Power BI-gatewayerna](service-gateway-proxy.md) om du tror att du har fått proxyproblem med gatewayen.

## <a name="next-steps"></a>Nästa steg
[Hantera din datakälla – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Hantera din datakälla – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Hantera din datakälla – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Hantera din datakälla – Oracle](service-gateway-onprem-manage-oracle.md)  
[Hantera din datakälla – Import/schemalagd uppdatering](service-gateway-enterprise-manage-scheduled-refresh.md)  
[Lokal datagateway – på djupet](service-gateway-onprem-indepth.md)  
[Lokala datagatewayar (personligt läge) – den nya versionen av den personliga gatewayen](service-gateway-personal-mode.md)
[Konfigurera proxyinställningar för den lokala datagatewayen](service-gateway-proxy.md)  
Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

