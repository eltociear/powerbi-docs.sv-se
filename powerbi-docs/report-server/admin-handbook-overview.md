---
title: Administratörsöversikt, Power BI-rapportserver
description: Den här artikeln är administratörsöversikten för Power BI-rapportservern, en lokal plats där du kan lagra och hantera dina mobila Power BI-rapporter och sidnumrerade rapporter.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 05/18/2018
ms.author: maghan
ms.openlocfilehash: 1dbca883bc4df2bde743963db7994361616be192
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2018
ms.locfileid: "34721925"
---
# <a name="admin-overview-power-bi-report-server"></a>Administratörsöversikt, Power BI-rapportserver
Den här artikeln är administratörsöversikten för Power BI-rapportservern, en lokal plats där du kan lagra och hantera dina mobila Power BI-rapporter och sidnumrerade rapporter. Den här artikeln beskriver begrepp för att planera, distribuera och hantera din Power BI-rapportservern, med länkar till mer information.

![](media/admin-handbook-overview/admin-handbook.png)



## <a name="installing-and-migration"></a>Installation och migrering
Du måste installera Power BI-rapportservern för att kunna använda den. Vi har artiklar som förklarar hur du gör.

Innan du börjar installera, uppgradera eller migrera till Power BI-rapportservern rekommenderar vi att du går igenom [systemkraven](system-requirements.md) för rapportservern.

### <a name="installing"></a>Installera
Om du distribuerar en ny Power BI-rapportserver kan du använda följande dokument som hjälp. 

[Installera Power BI-rapportserver](install-report-server.md)

### <a name="migration"></a>Migrering
Det finns ingen uppgradering på plats för SQL Server Reporting Services. Om du har en befintlig SQL Server Reporting Services-instans som du vill göra till en Power BI-rapportserver måste du migrera den. Det kan också finnas andra anledningar till varför du vill migrera. Läs igenom migreringsdokumentet för mer information.

[Migrera en rapportserverinstallation](migrate-report-server.md)

## <a name="configuring-your-report-server"></a>Konfigurera rapportservern
Du har flera alternativ att välja mellan när du ska konfigurera rapportservern. Ska du använda SSL? Konfigurerar du en e-postserver? Vill du interagera med Power BI-tjänsten för att fästa visualiseringar?

Merparten av din konfiguration sker i rapportserverns konfigurationshanterare. Titta närmare på [konfigurationshanterarens](https://docs.microsoft.com/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode) dokumentationen för mer information.

## <a name="security"></a>Säkerhet
Säkerhet och skydd är viktigt för alla organisationer. Du kan lära dig om autentisering, auktorisering, roller och behörigheter i dokumentationen om [säkerhet](https://docs.microsoft.com/sql/reporting-services/security/reporting-services-security-and-protection).

## <a name="next-steps"></a>Nästa steg
[Installera Power BI-rapportserver](install-report-server.md)  
[Hitta rapportserverns produktnyckel](find-product-key.md)  
[Installera Power BI Desktop som har optimerats för Power BI-rapportservern](install-powerbi-desktop.md)  
[Installera Report Builder](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Ladda ned SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

