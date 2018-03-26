---
title: Ändringslogg för Power BI-rapportservern
description: Den här ändringsloggen är avsedd för Power BI-rapportservern och visar nya objekt tillsammans med felkorrigeringar för varje utgiven version.
services: powerbi
documentationcenter: ''
author: jtarquino
manager: jonhp
backup: maggies
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/11/2017
ms.author: tankas
ms.openlocfilehash: 7c460955aba71bfb3a89d94aa6000c7bdd451ac2
ms.sourcegitcommit: 0473a155495a7a9ba4b899d0815100426718b7ac
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/20/2018
---
# <a name="changelog-for-power-bi-report-server"></a>Ändringslogg för Power BI-rapportservern

Den här ändringsloggen är avsedd för Power BI-rapportservern och visar nya objekt tillsammans med felkorrigeringar för varje utgiven version.

Detaljerad information om nya funktioner finns [Nyheter i Power BI-rapportserver](whats-new.md). 

## <a name="march-2018"></a>Mars 2018
- **Power BI-rapportserver**
    - *Version 1.2.6648.38132 (build-nr 15.0.2.378), publicerad: 19 mars 2018*
        - Säkerhetsuppdateringar
        - Förbättrad användbarhet
        - Felkorrigeringar
            - För sidnumrerade rapporter har en korrigering gjorts för parametersynligheten i en länkad rapport som återställs efter redigering av dess egenskaper
            - Korrigering för webbportalen med anpassad formulärautentisering som ignorerar cookien för dynamisk förfallotid
            - Korrigering för export till Word som skapar ojämn radhöjd om raden har tomt innehåll
            - För sidnumrerade rapporter har en korrigering gjorts för uttrycksbaserade anslutningssträngar som tas bort när vi ändrar autentiseringsuppgifter för datakällor
            - Korrigering för möjligheten att använda KPI med textvärden
            - För sidnumrerade rapporter har en korrigering gjorts för möjligheten att tilldela en ny datauppsättning till en befintlig sidnumrerad rapport
            - Andra stabilitets- och användbarhetskorrigeringar

- **Power BI Desktop (optimerad för Power BI-rapportservern)**
    - Version: 2.56.5023.1043 (mars 2018), publicerad: 19 mars 2018
        - Innehåller ändringar som krävs för anslutning till Power BI-rapportservern (mars 2018)

## <a name="october-2017"></a>Oktober 2017

- **Power BI-rapportserver**
    - *Version 1.1.6582.41691 (build-nr 14.0.600.442), publicerat: 10 januari 2018*
        - Säkerhetsuppdateringar
        - Felkorrigeringar
            - Korrigering för Model.GetParameters som returnerar 400
            - Korrigering för att ställa in delad datauppsättning till befintliga sidnumrerade rapporter (RDL)
            - Korrigering för ExecutionNotFoundException när du exporterar en rapport med olika parametervärden till PDF

    - *Version 1.1.6551.5155 (Build 14.0.600.438), Utgiven: 11 december 2017*
        - Felkorrigeringar
            - Det gick inte att spara data efter uppdatering för vissa Power BI Desktop-rapporter.

    - *Version 1.1.6530.30789 (build-nr 14.0.600.437), publicerat: 17 november 2017*
        - Felkorrigeringar
            - Korrigering för grundläggande autentisering 
            - Korrigering för veckodagar som inte kunde väljas på schemasidan för prenumerationer, cacheuppdateringsplaner och ögonblicksbilder av historik i portalen
            - Korrigering för rapporter med sidbrytning. När uttryck i textrutan med KanFörstoras-egenskapen ställdes in på ”falskt” resulterade detta i att värdena inte visad färger och teckensnitt korrekt
            - Korrigering för Power BI-rapporter (PBIX). Då förklaringar lades till för linjediagram återgavs ett tomt visuellt objekt

    - *Version 1.1.6514.9163 (build-nr 14.0.600.434), publicerat: 1 november 2017*
        - Felkorrigeringar
            - Korrigering för problem med överföringstillförlitligheten för PBIX-rapporter större än 500 MB
            - Korrigering av datainläsningsproblem för PBIX-rapporter större än 1 GB

    - *Version 1.1.6513.3500 (build-nr 14.0.600.433), publicerat: 31 oktober 2017*
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
    - *Version: 2.51.4885.2501 (oktober 2017), publicerad: 10 januari 2018*
        - Säkerhetsuppdateringar

    - *Version: 2.51.4885.1423 (oktober 2017) publicerat: 17 november 2017*
        - Felkorrigeringar
            - Korrigering för 32-bitars Power BI Desktop som inte kunde köras på x86 OS
            - Korrigering för Power BI-rapporter för att visa stödlinjer för x-axeln
            - Andra mindre felkorrigeringar

    - *Version: 2.51.4885.1041 (oktober 2017) publicerat: 31 oktober 2017*
        - Funktioner
            - Innehåller ändringar som krävs för anslutning till Power BI-rapportservern (oktober 2017)

## <a name="june-2017"></a>Juni 2017

- **Power BI-rapportserver**
    - *Build-nr 14.0.600.309, publicerat: 10 januari 2018*
        - Säkerhetsuppdateringar

    - *Build-nr 14.0.600.305, publicerat: 19 september 2017*  
        - Felkorrigeringar
            - Uppdatering till senaste [webbkontrollen för Bing Maps](https://msdn.microsoft.com/library/mt712542.aspx)

    - *Build-nr 14.0.600.301, publicerat: 11 juli 2017*
        - Felkorrigeringar
            - Taggen {{UserId}} motsvarar de lagrade autentiseringsuppgifterna istället för användaren som kör rapporten i Power BI-rapporter
            - Vissa bilder kan inte återges i Power BI-rapportserverns rapporter
            - Det går inte att ändra namnet på en Power BI-rapport i Power BI-rapportservern
            - Det gick inte att läsa in anpassade visuella objekt i Power BI- mobilappen (det krävs ominstallation av mobilappen för att rensa det lokala cacheminnet)

    - *Build-nr 14.0.600.271, publicerat: 12 juni 2017*
        - Ursprunglig utgåva av Power BI-rapportservern

- **Power BI Desktop (optimerad för Power BI-rapportservern)**
    - *Version: 2.47.4766.4901 (uni 2017), publicerad: 10 januari 2018*
        - Säkerhetsuppdateringar

## <a name="next-steps"></a>Nästa steg

[Användarhandbok](user-handbook-overview.md)  
[Handbok för administratör](admin-handbook-overview.md)  
[Snabbstart: Installera Power BI-rapportserver](quickstart-install-report-server.md)  
[Installera Report Builder](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Ladda ned SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)