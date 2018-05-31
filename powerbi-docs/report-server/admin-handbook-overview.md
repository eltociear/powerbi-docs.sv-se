---
title: Administratörsöversikt, Power BI-rapportserver
description: Den här artikel är administratörsöversikten för Power BI-rapportservern, en lokal plats för att lagra och hantera dina mobila Power BI-rapporter och sidnumrerade rapporter.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 05/07/2018
ms.author: maghan
ms.openlocfilehash: 228402dd2137f0cf2f3d480ff1acee10d2f28c51
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34296398"
---
# <a name="admin-overview-power-bi-report-server"></a>Administratörsöversikt, Power BI-rapportserver
Den här artikel är administratörsöversikten för Power BI-rapportservern, en lokal plats för att lagra och hantera dina mobila Power BI-rapporter och sidnumrerade rapporter. Den här artikeln beskriver begrepp för att planera, distribuera och hantera din Power BI-rapportservern, med länkar till mer information.

![](media/admin-handbook-overview/admin-handbook.png)



## <a name="installing-and-migration"></a>Installation och migrering
Du behöver installera Power BI-rapportservern för att börja använda den. Vi har information som gör att du kan hantera den här uppgiften.

Innan du börjar installera, uppgradera eller migrera till Power BI-rapportservern, bör du ta en titt på rapportserverns [systemkrav](system-requirements.md).

### <a name="installing"></a>Installera
Om du distribuerar en ny Power BI-rapportserver kan du använda följande dokument som hjälp. 

[Installera Power BI-rapportserver](install-report-server.md)

### <a name="migration"></a>Migrering
Det finns ingen uppgradering på plats för SQL Server Reporting Services. Om du har en befintlig SQL Server Reporting Services-instans som du vill göra till en Power BI-rapportserver måste du migrera den. Det finns också andra orsaker till varför du kanske skulle vilja utföra en migrering. Läs igenom migreringsdokumentet för mer information.

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

