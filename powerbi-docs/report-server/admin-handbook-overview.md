---
title: Administratörsöversikt, Power BI-rapportserver
description: Den här artikeln är administratörsöversikten för Power BI-rapportservern, en lokal plats där du kan lagra och hantera dina mobila Power BI-rapporter och sidnumrerade rapporter.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: maggies
ms.openlocfilehash: a93b3def115aaadbc33f6d0985aeea424558f248
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73860208"
---
# <a name="admin-overview-power-bi-report-server"></a>Administratörsöversikt, Power BI-rapportserver
Den här artikeln är administratörsöversikten för Power BI-rapportservern, en lokal plats där du kan lagra och hantera dina mobila Power BI-rapporter och sidnumrerade rapporter. I den här artikeln introduceras begrepp som beskriver hur du kan planera, distribuera och hantera din Microsoft Power BI-rapportserver, med länkar till mer information.

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
[Hämta Report Builder](https://www.microsoft.com/download/details.aspx?id=53613)  
[Ladda ned SQL Server Data Tools (SSDT)](https://go.microsoft.com/fwlink/?LinkID=616714)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

