---
title: Ändringslogg för Power BI-rapportservern
description: Den här ändringsloggen är avsedd för Power BI-rapportservern och visar nya objekt tillsammans med felkorrigeringar för varje utgiven version.
ms.author: jtarquino
author: jtarquino
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 03/31/2018
ms.openlocfilehash: 3897464cbc2a233f7b1aa6ee2f0fd70d39ff16aa
ms.sourcegitcommit: 3a05f34dbeabac62ea8c35c12a045284271971bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/03/2019
ms.locfileid: "58872511"
---
# <a name="changelog-for-power-bi-report-server"></a>Ändringslogg för Power BI-rapportservern

Den här ändringsloggen är avsedd för Power BI-rapportservern och visar nya objekt tillsammans med felkorrigeringar för varje utgiven version.

Detaljerad information om nya funktioner finns [Nyheter i Power BI-rapportserver](whats-new.md). 

## <a name="january-2019"></a>Januari 2019

- **Power BI-rapportserver**          
    - *Version 1.4.7024.16477 (version 15.0.1102.299), publicerad: 28 mars 2019*
        - Felkorrigeringar
            - Power BI-rapporter
                - Korrigering av problem med grundläggande autentiseringsuppgifter vid användning av Direct Query för SAP Hana och SAP BW
                - Korrigering av uppdatering av OData-feeddata som misslyckas på grund av att det inte gick att läsa in filen eller sammansättningen Microsoft.OData.Core.NetFX35.V7

- **Power BI-rapportserver**            
    - *Version 1.4.6969.7395 (version 15.0.1102.235), publicerad: 30 januari 2019*
        - Felkorrigeringar
            - Power BI-rapporter
                - Korrigering av problem med grundläggande autentiseringsuppgifter vid användning av Direct Query
                - Korrigering för dubbelriktade relationer när säkerhetsfilter på radnivå tillämpas
                - Korrigering för inaktuella data när en modell har uppdaterats i en utskalningsmiljö
                - Korrigering för dubbel rullningslist för tabell/matris i Firefox 63+
                - Korrigering för ikonstorlek +/- i Internet Explorer
            - Sidnumrerade rapporter
                - Korrigering för problem med uppdatering av användningen av en delad datakälla för en rapport

    - *Version 1.4.6960.38798 (version 15.0.1102.222), publicerad: 22 januari 2019*
        - Funktioner
            - Power BI-rapporter 
                - Stöd för säkerhet på radnivå
                - Expandera eller komprimera på matrisens radrubriker
                - Kopiera och klistra in mellan .pbix-filer
                - Smarta justeringsstödlinjer
                - Stöd för SAP BW 2.0 Connector
            - Administratörer
                - Möjlighet att begränsa tillägg av resurser som kan laddas upp till rapportservern
                - Möjlighet att begränsa hyperlänkscheman som stöds
            - Programmerbarhet
                - Ny webb-API: / PowerBIReports({Id})/DataModelRoles (GET)
                - Ny webb-API: /PowerBIReports({Id})/DataModelRoleAssignments (GET & PUT)
                - Se [REST API för Power BI-rapportserver](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0) för mer information.
        - Felkorrigeringar
            - Säkerhetsrisk för HTML-inmatning
            - Exportera till PDF visar inte eurotecken
            - När du sparar ett lösenord med flera datakällor i Power BI-rapporter blir icke-ändrade lösenord ogiltiga
            - Problem med visuella objekt i Power BI Mobile-appen efter inaktivitet

- **Power BI Desktop (optimerad för Power BI-rapportservern)**
    - *Version: 2.65.5313.1562 (januari 2019), publicerad: 30 januari 2019*
        - Genväg och fästa ikoner finns kvar efter avinstallation av Power BI-rapportservern
        - Korrigering av svart text på svart ikon då man fäster Power BI-rapportservern på start-menyn

    - *Version: 2.65.5313.1421 (januari 2019), publicerad: 22 januari 2019*
        - Innehåller ändringar som krävs för anslutning till Power BI-rapportservern (januari 2019)  

## <a name="august-2018"></a>Augusti 2018

- **Power BI-rapportserver**
    - *Version 1.3.6816.37243 (version 15.0.2.557), publicerad: 30 augusti 2018*
        - Felkorrigeringar
            - Ett problem åtgärdades när servern uppgraderades från tidigare versioner av PBI Report Server där en bindningsomdirigering inte uppdaterades, kunderna såg detta:      
            *`
            Failed to load expression host assembly. Details: Could not load file or assembly 'Microsoft.ReportingServices.ProcessingObjectModel, Version=2018.7.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040) (rsErrorLoadingExprHostAssembly)
             `*
             
            - Programfel för dataetikettstransparens har nu åtgärdats.
            
    - *Version 1.3.6801.38816 (version 15.0.2.540), publicerad: 15 augusti 2018*
        - Funktioner
            - SAP HANA SSO Direct Query-stöd med Kerberos är nu tillgängligt för Power BI-rapporter
            - API för anpassade visuella objekt släpps med versionen 1.13.0
            - Anpassade visuella objekt kommer att återställas till en tidigare version som är kompatibel med den aktuella versionen av server-API (om tillgängligt)

- **Power BI Desktop (optimerad för Power BI-rapportservern)**
    - *Version: 2.61.5192.641 (augusti 2018), publicerad: 15 augusti 2018*
        - Innehåller ändringar som krävs för anslutning till Power BI-rapportservern (augusti 2018)         
        
## <a name="march-2018"></a>Mars 2018

- **Power BI-rapportserver**
    - *Version 1.2.6690.34729 (version 15.0.2.402), publicerad: 27 april 2018*
        - Felkorrigeringar
            - Aktivera migrering av SQL Server Reporting Services 2017-kataloger
            - För Power BI-rapporter (PBIX)
                - Rapporter kan uppdateras när en server är konfigurerad för att använda anpassad autentisering
                - Att ändra egenskaperna för en rapport återställer inte autentiseringsuppgifter för datakällor
            - För sidnumrerade rapporter (RDL)
                - Användning av `Lookup()` eller härledda funktioner såsom `LookupSet()` och `MultiLookup()` i RDL Expressions leder inte längre till `#Error`
                - Länkade rapporter respekterar sidstorleken för målrapporten vid utskrift
                - Prenumerationer kan skapas för länkade rapporter som använder sammanhängande parametrar
                - Standardinställningar för flervärdesparameter kan ändras när du använder IE11
                - Leveransalternativ för datadrivna prenumerationen kan redigeras
                - Prenumerationer kan visas och redigeras medan prenumerationen körs
                - Att ange autentiseringsuppgifterna för datakällan tar inte bort uttrycksbaserade anslutningssträngar
            - För KPI:er
                - Trendrader uppdateras när data uppdateras
            - Allmänna stabilitetsförbättringar

    - *Version 1.2.6660.39920 (version 15.0.2.389), publicerad: 28 mars 2018*
        - Felkorrigeringar
            - För Power BI-rapporter (PBIX), fungerar korrigering för Exportera data inte från Power BI-visualiseringar
            - För Power BI-rapporter (PBIX), fungerar korrigeringar för URL-filter inte
            - För sidbrytningsrapporter (RDL), visas korrigering för bilder inte korrekt i IE11 när du har uppgraderat till Power BI-rapportservern som släpptes i mars

    - *Version 1.2.6648.38132 (version 15.0.2.378), publicerad: 19 mars 2018*
        - Säkerhetsuppdateringar
        - Förbättrad användbarhet
        - Felkorrigeringar
            - För sidnumrerade rapporter har en korrigering gjorts för parametersynligheten i en länkad rapport som återställs efter redigering av dess egenskaper
            - Korrigering för webbportalen med anpassad formulärautentisering som ignorerar cookien för dynamisk förfallotid
            - Korrigering för export till Word som skapar ojämn radhöjd om raden har tomt innehåll
            - För sidnumrerade rapporter har en korrigering gjorts för uttrycksbaserade anslutningssträngar som tas bort när vi ändrar autentiseringsuppgifter för datakällor
            - Korrigering för möjligheten att använda KPI med textvärden
            - För sidnumrerade rapporter (RDL) har en korrigering gjorts för möjligheten att tilldela en ny datauppsättning till en befintlig sidnumrerad rapport
            - Andra stabilitets- och användbarhetskorrigeringar

- **Power BI Desktop (optimerad för Power BI-rapportservern)**
    - Version: 2.56.5023.1043 (mars 2018), publicerad: 19 mars 2018
        - Innehåller ändringar som krävs för anslutning till Power BI-rapportservern (mars 2018)

## <a name="october-2017"></a>Oktober 2017

- **Power BI-rapportserver**
    - *Version 1.1.6582.41691 (version 14.0.600.442), publicerad: 10 januari 2018*
        - Säkerhetsuppdateringar
        - Felkorrigeringar
            - Korrigering för Model.GetParameters som returnerar 400
            - Korrigering för att ställa in delad datauppsättning till befintliga sidnumrerade rapporter (RDL)
            - Korrigering för ExecutionNotFoundException när du exporterar en rapport med olika parametervärden till PDF

    - *Version 1.1.6551.5155 (version 14.0.600.438), publicerad: 11 december 2017*
        - Felkorrigeringar
            - Det gick inte att spara data efter uppdatering för vissa Power BI Desktop-rapporter.

    - *Version 1.1.6530.30789 (version 14.0.600.437), publicerad: 17 november 2017*
        - Felkorrigeringar
            - Korrigering för grundläggande autentisering 
            - Korrigering för veckodagar som inte kunde väljas på schemasidan för prenumerationer, cacheuppdateringsplaner och ögonblicksbilder av historik i portalen
            - Korrigering för rapporter med sidbrytning. När uttryck i textrutan med KanFörstoras-egenskapen ställdes in på ”falskt” resulterade detta i att värdena inte visad färger och teckensnitt korrekt
            - Korrigering för Power BI-rapporter (PBIX). Då förklaringar lades till för linjediagram återgavs ett tomt visuellt objekt

    - *Version 1.1.6514.9163 (version 14.0.600.434), publicerad: 1 november 2017*
        - Felkorrigeringar
            - Korrigering för problem med överföringstillförlitligheten för PBIX-rapporter större än 500 MB
            - Korrigering av datainläsningsproblem för PBIX-rapporter större än 1 GB

    - *Version 1.1.6513.3500 (version 14.0.600.433), publicerad: 31 oktober 2017*
        - Funktioner
            - Stöd för inbäddad datamodell
            - Excel-arbetsboksvisning (med Office Online Server-integration aktiverad)
            - Schemalagd datauppdatering (PBIX)
            - Direct Query-stöd
            - Stöd för stora filer (upp till 2 GB)
            - Offentlig REST-API
            - Delat datauppsättningsstöd i Power BI Desktop (via oData)
            - URL-parameterstöd för PBIX-filer
            - Förbättrad användbarhet

- **Power BI Desktop (optimerad för Power BI-rapportservern)**
    - *Version: 2.51.4885.3981 (oktober 2017), publicerad: 10 april 2018*
        - Säkerhetsuppdateringar

    - *Version: 2.51.4885.2501 (oktober 2017), publicerad: 10 januari 2018*
        - Säkerhetsuppdateringar

    - *Version: 2.51.4885.1423 (oktober 2017), publicerad: 17 november 2017*
        - Felkorrigeringar
            - Korrigering för 32-bitars Power BI Desktop som inte kunde köras på x86 OS
            - Korrigering för Power BI-rapporter för att visa stödlinjer för x-axeln
            - Andra mindre felkorrigeringar

    - *Version: 2.51.4885.1041 (oktober 2017), publicerad: 31 oktober 2017*
        - Funktioner
            - Innehåller ändringar som krävs för anslutning till Power BI-rapportservern (oktober 2017)

## <a name="june-2017"></a>Juni 2017

- **Power BI-rapportserver**
    - *Version 14.0.600.309, publicerad: 10 januari 2018*
        - Säkerhetsuppdateringar

    - *Version 14.0.600.305, publicerad: 19 september 2017*  
        - Felkorrigeringar
            - Uppdatering till senaste [webbkontrollen för Bing Maps](https://msdn.microsoft.com/library/mt712542.aspx)

    - *Version 14.0.600.301, publicerad: 11 juli 2017*
        - Felkorrigeringar
            - Taggen `{{UserId}}` motsvarar de lagrade autentiseringsuppgifterna istället för användaren som kör rapporten i Power BI-rapporter
            - Vissa bilder kan inte återges i Power BI-rapportserverns rapporter
            - Det går inte att ändra namnet på en Power BI-rapport i Power BI-rapportservern
            - Det gick inte att läsa in anpassade visuella objekt i Power BI- mobilappen (det krävs ominstallation av mobilappen för att rensa det lokala cacheminnet)

    - *Version 14.0.600.271, publicerad: 12 juni 2017*
        - Ursprunglig utgåva av Power BI-rapportservern

- **Power BI Desktop (optimerad för Power BI-rapportservern)**
    - *Version: 2.47.4766.4901 (juni 2017), publicerad: 10 januari 2018*
        - Säkerhetsuppdateringar

## <a name="next-steps"></a>Nästa steg

[Vad är Power BI-rapportservern? ](get-started.md) 
 [Administratörsöversikt](admin-handbook-overview.md)  
[Installera Power BI-rapportserver](install-report-server.md)  
[Ladda ned Report Builder](https://www.microsoft.com/download/details.aspx?id=53613)  
[Ladda ned SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
