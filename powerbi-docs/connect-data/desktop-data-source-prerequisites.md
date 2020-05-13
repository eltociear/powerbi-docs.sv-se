---
title: Krav på Power BI-datakälla
description: Krav på Power BI-datakälla
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 498636d61f61764cfaef29db32454f55f1328243
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83293615"
---
# <a name="power-bi-data-source-prerequisites"></a>Krav på Power BI-datakälla
Power BI stöder en specifik providerversion för varje dataleverantör när det gäller objekt. Läs mer om datakällor som är tillgängliga för Power BI i [Datakällor](desktop-data-sources.md). I följande tabell beskrivs dessa krav.

| Datakälla | Provider | Lägsta providerversion | Lägsta version för datakälla | Datakällobjekt som stöds | Nedladdningslänk |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.net (inbyggt i .Net Framework) |.NET Framework 3.5 (endast) |SQL Server 2005+ |Tabeller/vyer, skalärfunktioner, tabellfunktioner |Ingår i .NET Framework 3.5 eller senare |
| Access |Microsoft Access-databasmotor (ACE) |ACE 2010 SP1 |Ingen begränsning |Tabeller/vyer |[Nedladdningslänk](https://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Excel (endast .xls-filer) (se kommentar 1) |Microsoft Access-databasmotor (ACE) |ACE 2010 SP1 |Ingen begränsning |Tabeller, blad |[Nedladdningslänk](https://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Oracle (se kommentar 2) |ODP.NET |ODAC 11.2 version 5 (11.2.0.3.20) |9.x+ |Tabeller/vyer |[Nedladdningslänk](https://go.microsoft.com/fwlink/?linkid=272376&clcid=0x409) |
| | System.Data.OracleClient (inbyggd i .NET Framework) |.NET Framework 3.5 |9.x+ |Tabeller/vyer |Ingår i .NET Framework 3.5 eller senare |
| IBM DB2 |ADO.Net-klient från IBM (del av drivrutinspaket för IBM-dataserver) |10.1 |9.1+ |Tabeller/vyer |[Nedladdningslänk](https://go.microsoft.com/fwlink/?linkid=274911&clcid=0x409) |
| MySQL |Anslutning/nät |6.6.5 |5.1 |Tabeller/vyer, skalärfunktioner |[Nedladdningslänk](https://go.microsoft.com/fwlink/?linkid=278885&clcid=0x409) |
| PostgreSQL |NPGSQL ADO.NET-provider (levereras med Power BI Desktop) |4.0.10 |9.4 |Tabeller/vyer |[Nedladdningslänk](https://go.microsoft.com/fwlink/?linkid=282716&clcid=0x409) |
| Teradata |.NET Data Provider för Teradata |14+ |12+ |Tabeller/vyer |[Nedladdningslänk](https://go.microsoft.com/fwlink/?linkid=278886&clcid=0x409) |
| SAP Sybase SQL Anywhere |iAnywhere.Data.SQLAnywhere för .NET 3.5 |16+ |16+ |Tabeller/vyer |[Nedladdningslänk](https://go.microsoft.com/fwlink/?linkid=324846) |

>[!NOTE]
>Excel-filer med filnamnstillägget .xlsx kräver inte någon separat providerinstallation.

>[!NOTE]
>Oracle-providers kräver dessutom Oracle-klientprogramvaran (version 8.1.7+).
> 
> 

