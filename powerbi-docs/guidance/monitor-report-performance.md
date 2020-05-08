---
title: Övervaka rapportprestanda i Power BI
description: Vägledning om hur man övervakar rapportprestanda i Power BI.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 2962d5f8504b7214cb685457c59b11f1d9d7b85e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "81525547"
---
# <a name="monitor-report-performance-in-power-bi"></a>Övervaka rapportprestanda i Power BI

Övervaka rapportprestanda i Power BI Desktop med hjälp av appen [Power BI Premium Metrics](../service-premium-metrics-app.md), lär dig var flaskhalsarna finns och hur du kan förbättra rapportprestanda.

Att övervaka prestanda är relevant i följande situationer:

- Uppdateringen av importdatamodellen är långsam.
- Dina DirectQuery- eller live-anslutningsrapporter är långsamma.
- Dina modellberäkningar är långsamma.

Fokusera på långsamma frågor eller visuella rapportobjekt i den fortsatta optimeringen.

## <a name="use-query-diagnostics"></a>Använd Frågediagnostik

Använd [Frågediagnostik](/power-query/QueryDiagnostics) i Power BI Desktop när du vill fastställa vad Power Query gör när du förhandsgranskar eller använder frågor. Du kan också använda funktionen _Diagnostisera steget_ när du vill registrera detaljerad utvärderingsinformation för respektive frågesteg. Resultaten görs tillgängliga i en Power Query och du kan tillämpa omvandlingar om du vill förstå frågekörningen bättre.

> [!NOTE]
> Frågediagnostik är för närvarande en förhandsgranskningsfunktion, så du måste aktivera den i _Alternativ och inställningar_. När du väl har aktiverat den, så är dess kommandon tillgängliga i Power Query-redigerarens fönster på menyfliken **Verktyg**.

![Bilden visar menyfliken Verktyg i Power Query-redigeraren. Menyfliksområdet visar kommandona Diagnostisera steg, Starta diagnostiken och Stoppa diagnostiken.](media/monitor-report-performance/power-query-diagnotics.png)

## <a name="use-performance-analyzer"></a>Använda Prestandaanalys

Använd [Prestandaanalys](../desktop-performance-analyzer.md) i Power BI Desktop om du vill ta reda på hur dina olika rapportelement, t.ex. visuella objekt och DAX-formler, presterar. Det är särskilt användbart att fastställa huruvida det är frågan eller den visuella återgivningen som orsakar prestandaproblem.

## <a name="use-sql-server-profiler"></a>Använd SQL Server Profiler

Du kan också använda [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler) för att identifiera frågor som är långsamma.

> [!NOTE]
> SQL Server Profiler är tillgängligt som en del av [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms).

Use SQL Server Profiler om din datakälla är någon av följande:

- SQL Server
- SQL Server Analysis Services
- Azure Analysis Services

> [!CAUTION]
> Power BI Desktop stöder anslutning till en diagnostikport. Diagnostikporten gör att andra verktyg kan ansluta och utföra spårningar i diagnostiksyfte. Det finns inte stöd för att göra ändringar i Power Desktop-datamodellen. Ändringar i datamodellen kan leda till skador och förlorade data.

Om du vill skapa en SQL Server Profiler-spårning, så gör så här:

1. Öppna din Power BI Desktop-rapport (så att du lätt kan hitta porten i nästa steg, och stäng andra eventuellt öppna rapporter).
1. Fastställ vilken port som används av Power BI Desktop geno att skriva följande kommando i PowerShell (med administratörsprivilegier) eller i kommandotolken:
    ```powershell
    netstat -b -n
    ```
    Utdata är en lista över program och deras öppna portar. Sök efter den port som används av **msmdsrv.exe** och skriv ned den så att du kan använda den senare. Det är din instans av Power BI Desktop.
1. Anslut SQL Server Profiler till din Power BI Desktop-rapport så här:
    1. Öppna SQL Server Profiler
    1. Välj _Nytt spår_ på _Arkiv_-menyn i SQL Server Profiler.
    1. Välj _Analysis Services_ som **Servertyp**.
    1. Skriv _localhost:[port som registrerats tidigare]_ i **Servernamn**.
    1. Klicka på _Kör_ – nu är SQL Server Profiler-spårningen igång, och profilerar aktivt Power BI Desktop-frågor.
1. Medan Power BI Desktop-frågorna körs kan du se deras respektive varaktigheter och CPU-tider. Beroende på vilkent datakällstypen är, så kan du eventuellt se andra händelser som indikerar hur frågan körs. Med hjälp av den här informationen kan du fastställa vilka frågor som utgör flaskhalsar.

En fördel med att använda SQL Server Profiler är att det är möjligt att spara en (relations)databasspårning i SQL Server. Spåret kan användas som indata för [Finjusteringsverktyg för databasmotorer](/sql/relational-databases/performance/start-and-use-the-database-engine-tuning-advisor). På så vis kan du få rekommendationer om hur du kan finjustera din datakälla.

## <a name="monitor-premium-metrics"></a>Övervaka Premium-mått

Du kan använda **Power BI Premium-måttappen** för Power BI Premium-funktioner när du övervakar din Power BI Premium-prenumerations hälsa och kapacitet. Mer information finns i [Power BI Premium-måttappen](../service-premium-metrics-app.md).

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Frågediagnostik](/power-query/QueryDiagnostics)
- [Prestandaanalys](../desktop-performance-analyzer.md)
- [Felsöka rapportprestanda i Power BI](report-performance-troubleshoot.md)
- [Power BI Premium-måttappen](../service-premium-metrics-app.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
