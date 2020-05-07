---
title: Hantera innehåll i webbportalen för Power BI-rapportserver
description: Läs mer om att hantera innehåll i webbportalen för Power BI-rapportserver.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/24/2018
ms.author: maggies
ms.openlocfilehash: ecc33c6176214cb8178e55d716294bf9446a7b1d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73859490"
---
# <a name="manage-content-in-the-web-portal"></a>Hantera innehåll i webbportalen 
Webbportalen för Power BI-rapportserver är en lokal plats för att visa, lagra och hantera dina Power BI, mobila och sidnumrerade rapporter och KPI:er.

![Report Server-webbportalen](media/getting-around/report-server-web-portal.png)

Du kan visa webbportalen i alla moderna webbläsare. Rapporter och KPI:er i webbportalen är uppdelade i mappar och du kan markera dem som favoriter. Du kan även lagra Excel-arbetsböcker där. Från webbportalen kan du starta de verktyg du behöver för att skapa rapporter:

* **Power BI-rapporter** skapas med Power BI Desktop: visa dem i webbportalen och Power BI-mobilapparna.
* **Sidnumrerade rapporter** skapas i Report Builder: dokument med ett modernt utseende och fast layout som är optimerade för utskrift.
* **KPI:er** skapas direkt i webbportalen.

I webbportalen kan du bläddra igenom mapparna på rapportservern eller söka efter specifika rapporter. Du kan visa en rapport, dess allmänna egenskaper och tidigare kopior av rapporten som finns i rapporthistoriken. Beroende på dina behörigheter, kan du även kunna prenumerera på rapporter för leverans till din inkorgen eller en delad mapp i filsystemet.

## <a name="web-portal-roles-and-permissions"></a>Webbportalsroller och behörigheter
Webbportalen är ett program som körs i en webbläsare. När du startar webbportalen, är de sidor, länkar och alternativ som du ser beroende av de behörigheter som du har på rapportservern. Om du har tilldelats en roll med fullständiga behörigheter, har du åtkomst till en fullständig uppsättning programmenyer och -sidor för att hantera en rapportserver. Om du har tilldelats en roll med behörigheter att visa och köra rapporter, visas bara menyer och sidor som du behöver för de aktiviteterna. Du kan ha olika rolltilldelningar för olika rapportservrar eller till och med för olika rapporter och mappar på en enda rapportserver.

## <a name="start-the-web-portal"></a>Starta webbportalen
1. Öppna din webbläsare.
   
    Se den här listan över [webbläsare och versioner som stöds](browser-support.md).
2. I adressfältet, skriver du webbportalens URL.
   
    URL:en är som standard <em>https://[ComputerName]/reports</em>.
   
    Rapportservern kan ha konfigurerats för att använda en specifik port. Exempel: <em>https://[ComputerName]:80/reports</em> eller <em>https://[ComputerName]:8080/reports</em>
   
    Du ser att webbportalen grupperar objekt i dessa kategorier:
   
   * KPI:er
   * Mobila rapporter
   * Sidnumrerade rapporter
   * Power BI Desktop-rapporter
   * Excel-arbetsböcker
   * Datamängder
   * Datakällor
   * Resurser

## <a name="manage-items-in-the-web-portal"></a>Hantera objekt i webbportalen
Power BI-rapportserver ger dig detaljerad kontroll över de objekt som du lagrar på webbportalen. Du kan till exempel konfigurera prenumerationer, cachelagring, ögonblicksbilder och säkerhet för individuella sidnumrerade rapporter.

1. Välj **Fler alternativ** (...) uppe till höger av ett objekt och sedan **Hantera**.
   
    ![Välj hantera](media/getting-around/report-server-web-portal-manage-ellipsis.png)
2. Välj egenskapen eller den andra funktionen du vill ange.
   
    ![Välj en egenskap](media/getting-around/report-server-web-portal-manage-properties.png)
3. Välj **Använd**.

Läs mer om att [arbeta med prenumerationer i webbportalen](https://docs.microsoft.com/sql/reporting-services/working-with-subscriptions-web-portal).

## <a name="next-steps"></a>Nästa steg
[Vad är Power BI-rapportservern?](get-started.md)

Fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

