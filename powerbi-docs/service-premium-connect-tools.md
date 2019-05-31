---
title: Ansluta till Power BI Premium datauppsättningar med program och verktyg (förhandsversion)
description: Beskriver hur du ansluter till datauppsättningar i Power BI Premium från program och verktyg.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 063f43cb2345ccb3d1fec5c414100beb8ccde451
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941519"
---
# <a name="connect-to-datasets-with-client-applications-and-tools-preview"></a>Ansluta till datauppsättningar med program och verktyg (förhandsversion)

Power BI Premium-arbetsytor och datauppsättningar stöd *skrivskyddad* anslutningar från Microsoft och tredje parts program och verktyg. 

> [!NOTE]
> Den här artikeln är avsedd endast för att introducera skrivskyddad anslutning till Power BI Premium-arbetsytor och datauppsättningar. Den *är inte* avsedd att ge detaljerad information om programmering, särskilda verktyg och program, arkitektur och hantering av arbetsytan och datauppsättningen. Ämnen som beskrivs här kräver en djupare förståelse av Analysis Services tabellmodell database-arkitektur och administration.

## <a name="protocol"></a>Protokoll

Power BI Premium använder den [XML for Analysis](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference) (XMLA)-protokoll för kommunikation mellan program och motorn som hanterar du dina arbetsytor och datauppsättningar. Dessa meddelanden är igenom vad är vanligtvis kallas XMLA-slutpunkter. XMLA är samma kommunikationsprotokoll som används av Microsoft Analysis Services-motorn, vilket under huven, körs Power BI semantiska modellering, styrning, livscykel och datahantering. 

Merparten av program och verktyg uttryckligen kommunicerar inte med motorn genom att använda XMLA-slutpunkter. I stället använda de klientbibliotek som MSOLAP, ADOMD och AMO som en mellanhand mellan klientprogrammet och motor som kommunicerar endast med hjälp av XMLA.


## <a name="supported-tools"></a>Verktyg

De här verktygen stöder skrivskyddad åtkomst till Power BI Premium-arbetsytor och datauppsättningar:

**SQL Server Management Studio (SSMS)** -stöder DAX, MDX, XMLA och TraceEvent frågor. Kräver version 18.0. Ladda ned [här](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). 

**SQL Server Profiler** -inkluderat med SSMS 18.0 (förhandsversion) är det här verktyget förser spårning och felsökning av serverhändelser. Du kan samla in och spara data om varje händelse till en fil eller en tabell för att analysera senare. Medan du officiellt inaktuell för SQL Server, fortsätter att ingå i SSMS Profiler och kvar för Analysis Services och nu Power BI Premium. Mer information finns i [SQL Server Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler).

**DAX-Studio** – öppen källkod, community-verktyg för att köra och analysera DAX-frågor mot Analysis Services. Kräver version 2.8.2 eller senare. Mer information finns i [daxstudio.org](https://daxstudio.org/).

**Pivottabeller i Excel** -Klicka och kör version av Office 16.0.11326.10000 eller senare krävs.

**Tredjeparts** – innehåller data visualisering program och verktyg som kan ansluta till, fråga och använda datauppsättningar i Power BI Premium. De flesta verktygen kräver de senaste versionerna av MSOLAP-klientbiblioteken, men vissa kan använda ADOMD.

## <a name="client-libraries"></a>Klientbibliotek

Klientbibliotek är nödvändiga för program och verktyg att ansluta till Power BI Premium-arbetsytor. Samma klientbibliotek som används för att ansluta till Analysis Services stöds även i Power BI Premium. Microsoft-klientprogram som Excel, SQL Server Management Studio (SSMS) och SQL Server Data Tools (SSDT) installera samtliga tre klientbibliotek och uppdatera dem tillsammans med regelbundna programuppdateringar. I vissa fall, särskilt med program från tredje part och verktyg, kan du behöva installera nyare version av klientbiblioteken. Klientbibliotek uppdateras varje månad. Mer information finns i [klientbibliotek för att ansluta till Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers).

## <a name="connecting-to-a-premium-workspace"></a>Ansluta till en Premium-arbetsyta

Du kan ansluta till arbetsytor som har tilldelats till Premium-dedicerad kapacitet. Arbetsytor som har tilldelats en dedikerad kapacitet har en anslutningssträng i URL-format. 

Att hämta anslutningssträngen arbetsytan i Power BI i **arbetsyteinställningarna**på den **Premium** fliken **arbetsytan anslutning**, klickar du på **kopiera**.

![Anslutningssträngen för arbetsyta](media/service-premium-connect-tools/connect-tools-workspace-connection.png)

Arbetsytan anslutningar använder följande URL-format för att åtgärda en arbetsyta som om det vore en Analysis Services-servernamn:   
`powerbi://api.powerbi.com/v1.0/[tenant name]/[workspace name]` 

Exempel: `powerbi://api.powerbi.com/v1.0/contoso.com/Sales Workspace`
> [!NOTE]
> `[workspace name]` är skiftlägeskänsliga och kan innehålla blanksteg. 

### <a name="to-connect-in-ssms"></a>Ansluta i SSMS

I **Anslut till Server** > **servertyp**väljer **Analysis Services**. I **servernamn**, ange URL: en. I **autentisering**väljer **Active Directory - Universal med stöd för MFA**, och sedan i **användarnamn**, ange din organisations användar-ID. 

När du är ansluten, visas arbetsytan som en Analysis Services-server och datauppsättningar i arbetsytan visas som databaser.  

![SSMS](media/service-premium-connect-tools/connect-tools-ssms.png)

### <a name="initial-catalog"></a>Startkatalog

Vissa verktyg, till exempel SQL Server-Profiler, du kan behöva ange en *Initial Catalog*. Ange en datauppsättning (databas) på din arbetsyta. I **Anslut till Server**, klickar du på **alternativ**. I den **Anslut till Server** dialogrutan på den **anslutningsegenskaper** fliken **Anslut till databas**, anger du datauppsättningsnamnet.

### <a name="duplicate-workspace-name"></a>Duplicera namn på arbetsyta

När du ansluter till en arbetsyta med samma namn som en annan arbetsyta, kan du få följande fel: **Det går inte att ansluta till powerbi://api.powerbi.com/v1.0/ [klientnamn] / [Arbetsytenamn].**

Ange ObjectIDGuid, vilken kan kopieras från objekt-ID för arbetsyta i URL: en för att undvika det här felet, förutom att namnet på arbetsytan. Lägg till objekt-ID till anslutningens Webbadress. Till exempel ”powerbi://api.powerbi.com/v1.0/myorg/Contoso försäljning – 9d83d204-82a9-4b36-98f2-a40099093830”

### <a name="duplicate-dataset-name"></a>Duplicera namn på datauppsättning

Lägg till guid datauppsättning till datauppsättningens namn när du ansluter till en datauppsättning med samma namn som en annan datauppsättningar på samma arbetsyta. Du kan få både namn på datauppsättning *och* guid när du är ansluten till arbetsytan i SSMS. 

### <a name="delay-in-datasets-shown"></a>Fördröjning i datauppsättningar som visas

När du ansluter till en arbetsyta, kan ändringar från nya, borttagna och omdöpt datauppsättningar ta upp till 5 minuter innan den visas. 

### <a name="unsupported-datasets"></a>Datauppsättningar som inte stöds

Följande datauppsättningar är inte tillgängliga med hjälp av XMLA-slutpunkter. Dessa datauppsättningar *inte* visas under arbetsytan i SSMS eller i andra verktyg: 

- Datauppsättningar med Live-anslutning till en Analysis Services-modeller. 
- Datauppsättningar med Push-data med hjälp av REST-API.
- Datauppsättningar för Excel-arbetsboken. 

Följande datauppsättningar stöds inte i Power BI-tjänsten:   

- Datauppsättningar med Live-anslutning till en Power BI-datauppsättning.

## <a name="audit-logs"></a>Granskningsloggar 

När klientprogram och verktyg ansluter till en arbetsyta, åtkomst via XMLA-slutpunkter loggas i Power BI-granskningsloggar under den **GetWorkspaces** igen. Mer information finns i [granska Power BI](service-admin-auditing.md).

## <a name="see-also"></a>Se också

[Analysis Services-referenser](https://docs.microsoft.com/bi-reference/#pivot=home&panel=home-all)   
[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)   
[SQL Server Analysis Services Tabular Protocol](https://docs.microsoft.com/openspecs/sql_server_protocols/ms-ssas-t/b98ed40e-c27a-4988-ab2d-c9c904fe13cf)   
[Dynamiska hanteringsvyer (DMV)](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services)   


Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
