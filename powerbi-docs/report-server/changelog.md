---
title: Ändringslogg för Power BI-rapportservern
description: Den här ändringsloggen är avsedd för Power BI-rapportservern och visar nya objekt tillsammans med felkorrigeringar för varje utgiven version.
ms.author: jaimeta
author: jtarquino
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 04/08/2020
ms.openlocfilehash: ff63e38e52a3c8970edfa5b6d9e2ccabeff2e16a
ms.sourcegitcommit: e7fda395b47e404c61e961a60816b7a1b0182759
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80979809"
---
# <a name="change-log-for-power-bi-report-server"></a>Ändringslogg för Power BI-rapportservern

Den här ändringsloggen är avsedd för Power BI-rapportservern och visar nya objekt tillsammans med felkorrigeringar för varje utgiven version.

Detaljerad information om nya funktioner finns [Nyheter i Power BI-rapportserver](whats-new.md). 


## <a name="january-2020"></a>Januari 2020
- **Power BI-rapportserver**
    - *Version: 1.6.7364.4075 (version 15.0.1102.777), utgiven: 2 mars 2020*
         - Felkorrigeringar
           -  Korrigering för Power BI-rapporter kan inte överföras för vissa datakällor
           -  Korrigering för portalens hämtningsplats för Desktop-länk för Power BI-rapportservern
           -  Korrigering för DynamicImageDPI för Excel-återgivning
           -  Korrigering för Oracle-anslutningar med felaktig trådkultur i vissa scenarier med flera användare (mer information finns i [UseInstalledUICulture-dokumentationen] (https://docs.microsoft.com/power-bi/report-server/connect-data-sources) )
           -  Korrigering för CustomHeaders-standardvärdet som orsakar problem vid inbäddning av rapporter
           -  Korrigering för SQL-parameternamn som genereras felaktigt i vissa fall
    - *Version: 1.6.7327.3007 (version 15.0.1102.759), utgiven: 23 januari 2020*
         - Funktioner
            -  Exportera till Excel från Power BI-rapporter.
           -  Stöd för Power BI Premium-datauppsättning för sidnumrerade rapporter.
           -  AltText-stöd (alternativ text) för sidnumrerade rapportelement.
           -  Stöd för anpassade rubriker.
           -  Stöd för Azure SQL-hanterade instanser som katalogen.
           -  Transparent databaskryptering för katalogen.
        - Säkerhetsuppdateringar
        - Felkorrigeringar
            - Korrigeringar för hjälpmedel för skärmläsare, rapportåtergivning och tangentbordsnavigering.
            - Korrigering för att spara rapporttitlar med flera byte.
            - Korrigering för utförlig loggning som påverkar rapportserverns tillförlitlighet.
          - Korrigering för att säkerställa realtidsdata i Power BI-rapporter på mobilen.
          - Korrigering för att tillämpa korsvisualiseringsmarkeringar mellan olika visuella objekt i filtrerade exporter av Power BI-rapporter.
          - Korrigering för att skriva sidfot när du exporterar till Word med uttryck för synlighet för sidnumrerade rapporter. 
     
- **Power BI Desktop (optimerad för Power BI-rapportservern)**
    - *Version: 2.76.5678.1521 (januari 2020), publicerad: 23 januari 2020* (ny build och ny version)
        - Innehåller ändringar som krävs för anslutning till Power BI-rapportservern (januari 2020)        


## <a name="september-2019"></a>September 2019
- **Power BI-rapportserver**
    - *Version: 1.6.7236.4246 (version 15.0.1102.646), utgiven: 25 oktober 2019*
        - Säkerhetsuppdateringar
        - Felkorrigeringar
            - Korrigeringen för .net framework 4.7 är inte installerad.
            - Korrigering för sidnumrerade Teradata-rapporter med flervärdesparametrar som anger fel 110083.
            - Korrigering för att URLRoot-värdet inte fungerar om det finns flera bindningar till webbtjänstadresser och en av dem är https://+80/reportserver.
          - Korrigering för att värden för flervärdesparametrar i sidnumrerade rapporter visas utanför rapportområdet.
          
    - *Version: 1.6.7221.30698 (version 15.0.1102.620), utgiven: 9 oktober 2019*
        - Felkorrigeringar
            - Korrigering av textfilter i anpassat visuellt objekt.
            - Korrigering av de nedrullningsbara utsnittens prestanda.
            - Korrigering av Strip PII från telemetri.
          - Korrigering av att URL:er inte ska vara skiftlägeskänsliga.
          
    - *Version 1.6.7206.38019 (Build 15.0.1102.597), publicerad: 26 september 2019*
        - Säkerhetsuppdateringar
        - Felkorrigeringar
           - Sidnumrerade rapporter
             - Korrigering av tillgänglighetsproblem som uppstått vid användning av Internet Explorer och Microsoft Edge.
             - Korrigering för SAP HANA-problem vid test av anslutningen.
             - Korrigering för problem hittade när lista över e-postadresser tillhandahålls.
             - Korrigering för Power BI-rapporter som använder en DirectQuery-datakälla och integrerad autentisering.
             - Korrigering för sidnumrerade rapporter som ska återges med filterparametrar när ögonblicksbild har aktiverats.
             - Korrigering för dubbel körning av lagrade procedurer under rapportkörning.
             - Korrigering för standardtjänstkonto som beviljas SQL Server-inloggningsbehörigheter, när anpassade tjänstkonton konfigureras att köra Power BI-rapportservern.
             - Korrigering för åtkomst av modeller under uppdatering i japansk tidszon.
             - Korrigering för inaktuella modeller när en ny version laddas upp under uppdatering.
             - Korrigering för parametervärden som innehåller &-tecknet.
         - Programmerbarhet
             - Uppdaterat webb-API: /PowerBIReports({Id})/DataSources (PATCH) för att tillåta anslutningsstränguppdateringar.
         
- **Power BI Desktop (optimerad för Power BI-rapportservern)**
    - *Version: 2.73.5586.1501 (september 2019), utgiven: 25 oktober 2019*
        - Felkorrigeringar
            - Korrigering för telemetri.
            
    - *Version: 2.73.5586.1241 (september 2019), utgiven: 9 oktober 2019*
        - Felkorrigeringar
            - Korrigering av textfilter i anpassat visuellt objekt.
            - Korrigering av de nedrullningsbara utsnittens prestanda.
            - Korrigering av Strip PII från telemetri.
            
    - *Version: 2.73.5586.821 (september 2019), utgiven: september 26 2019* (ny build och ny version)
        - Innehåller ändringar som krävs för anslutning till Power BI-rapportservern (september 2019)

    
## <a name="may-2019"></a>Maj 2019

- **Power BI-rapportserver**          
    - *Version 1.5.7074.36177 (Build 15.0.1102.371), publicerad: 21 maj 2019*
        - Felkorrigeringar
            - Sidnumrerade rapporter
                - Korrigering så att inbäddning av pdf-teckensnitt alltid är aktiverad.
                - Korrigering så att cookies som skickas via https ställs in som Säkra
                - Korrigering av problem med popup-fönster som beror på skriptfel
                - Korrigering för visningsproblem med Mobilapp på Android-telefoner
                - Korrigering så att tidnavigeringen i Mobil rapport visar rätt veckonummer oavsett när räkenskapsåret startar
                - Lade till den konfigurerbara egenskapen RestrictedResourceMimeTypeForUpload så att administratörer kan ange förbjudna mime-typer
         - Funktioner
            - Lade till stöd för betrodda visuella objekt i PBIRS

- **Power BI Desktop (optimerad för Power BI-rapportservern)**
    - *Version: 2.69.5467.1801 (maj 2019), publicerad: 21 maj 2019*
        - Felkorrigeringar
            - Korrigering som gör att autentiseringsuppgifter inte behöver anges på nytt vid PBIX-överföring till PBIRS
            - Korrigering som gör att dokument med # i filnamnet kan öppnas
            - Lade till en enklare länk för bakåtnavigering i PBIRS-urvalsfönstret
            - Korrigering av högkontrastläget i PBIRS så att bakåtknappen och visuella varningsmeddelanden syns bättre.
            - Korrigering av gränssnittet i urvalsfönstret, skalning av arbetsytan.

    - *Version: 2.69.5467.5201 (maj 2019), publicerad: 30 juli 2019*
        - Felkorrigeringar
            - Korrigering för felaktig telemetriloggning

## <a name="january-2019"></a>Januari 2019

- **Power BI-rapportserver**          
    - *Version 1.4.7024.16477 (Build 15.0.1102.299), publicerad: 28 mars 2019*
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

    - *Version 1.4.6960.38798 (version 15.0.1102.222), publicerad: Den 22 januari 2019*
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

    - *Version: 2.65.5313.1421 (januari 2019), publicerad: 22 januari 2019* (ny build och ny version)
        - Innehåller ändringar som krävs för anslutning till Power BI-rapportservern (januari 2019) 
    - *Version: 2.65.5313.5141 (januari 2019), publicerad: 31 juli2019* (ny build och ny version)
        - Felkorrigeringar
            - Korrigering för felaktig telemetriloggning

## <a name="august-2018"></a>Augusti 2018

- **Power BI-rapportserver**
    - *Version 1.3.6816.37243 (build-nr 15.0.2.557), publicerad: 30 augusti 2018*
        - Felkorrigeringar
            - Ett problem åtgärdades när servern uppgraderades från tidigare versioner av PBI Report Server där en bindningsomdirigering inte uppdaterades, kunderna såg detta:      
            *`
            Failed to load expression host assembly. Details: Could not load file or assembly 'Microsoft.ReportingServices.ProcessingObjectModel, Version=2018.7.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040) (rsErrorLoadingExprHostAssembly)
             `*
             
            - Programfel för dataetikettstransparens har nu åtgärdats.
            
    - *Version 1.3.6801.38816 (build-nr 15.0.2.540), publicerad: 15 augusti 2018*
        - Funktioner
            - SAP HANA SSO Direct Query-stöd med Kerberos är nu tillgängligt för Power BI-rapporter
            - API för anpassade visuella objekt släpps med versionen 1.13.0
            - Visuella Power BI-objekt återställs till en tidigare version som är kompatibel med den aktuella versionen av server-API (om tillgängligt)

- **Power BI Desktop (optimerad för Power BI-rapportservern)**
    - *Version: 2.61.5192.641 (augusti 2018), publicerad: 15 augusti 2018*
        - Innehåller ändringar som krävs för anslutning till Power BI-rapportservern (augusti 2018)         
    - *Version: 2.61.5192.7701 (augusti 2018), publicerad: 8 augusti 2019* (ny build och ny version)
        - Felkorrigeringar
            - Korrigering för felaktig telemetriloggning
            
## <a name="march-2018"></a>Mars 2018

- **Power BI-rapportserver**
    - *Version 1.2.6690.34729 (build-nr 15.0.2.402), publicerad: 27 april 2018*
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

    - *Version 1.2.6660.39920 (build-nr 15.0.2.389), publicerad: 28 mars 28 2018*
        - Felkorrigeringar
            - För Power BI-rapporter (PBIX), fungerar korrigering för Exportera data inte från Power BI-visualiseringar
            - För Power BI-rapporter (PBIX), fungerar korrigeringar för URL-filter inte
            - För sidbrytningsrapporter (RDL), visas korrigering för bilder inte korrekt i IE11 när du har uppgraderat till Power BI-rapportservern som släpptes i mars

    - *Version 1.2.6648.38132 (build-nr 15.0.2.378), publicerad: 19 mars 2018*
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
    - *Version 1.1.6582.41691 (build-nr 14.0.600.442), publicerad: 10 januari 2018*
        - Säkerhetsuppdateringar
        - Felkorrigeringar
            - Korrigering för Model.GetParameters som returnerar 400
            - Korrigering för att ställa in delad datauppsättning till befintliga sidnumrerade rapporter (RDL)
            - Korrigering för ExecutionNotFoundException när du exporterar en rapport med olika parametervärden till PDF

    - *Version 1.1.6551.5155 (build-nr 14.0.600.438), publicerad: 11 december 2017*
        - Felkorrigeringar
            - Det gick inte att spara data efter uppdatering för vissa Power BI Desktop-rapporter.

    - *Version 1.1.6530.30789 (build-nr 14.0.600.437), publicerad: 17 november 2017*
        - Felkorrigeringar
            - Korrigering för grundläggande autentisering 
            - Korrigering för veckodagar som inte kunde väljas på schemasidan för prenumerationer, cacheuppdateringsplaner och ögonblicksbilder av historik i portalen
            - Korrigering för rapporter med sidbrytning. När uttryck i textrutan med KanFörstoras-egenskapen ställdes in på ”falskt” resulterade detta i att värdena inte visad färger och teckensnitt korrekt
            - Korrigering för Power BI-rapporter (PBIX). Då förklaringar lades till för linjediagram återgavs ett tomt visuellt objekt

    - *Version 1.1.6514.9163 (build-nr 14.0.600.434), publicerad: 1 november 2017*
        - Felkorrigeringar
            - Korrigering för problem med överföringstillförlitligheten för PBIX-rapporter större än 500 MB
            - Korrigering av datainläsningsproblem för PBIX-rapporter större än 1 GB

    - *Version 1.1.6513.3500 (build-nr 14.0.600.433), publicerad: 31 oktober 2017*
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
    - *Build-nr 14.0.600.309, publicerad: 10 januari 2018*
        - Säkerhetsuppdateringar

    - *Build-nr 14.0.600.305, publicerad: 19 september 2017*  
        - Felkorrigeringar
            - Uppdatering till senaste [webbkontrollen för Bing Maps](https://msdn.microsoft.com/library/mt712542.aspx)

    - *Build-nr 14.0.600.301, publicerad: 11 juli 2017*
        - Felkorrigeringar
            - Taggen `{{UserId}}` motsvarar de lagrade autentiseringsuppgifterna istället för användaren som kör rapporten i Power BI-rapporter
            - Vissa bilder kan inte återges i Power BI-rapportserverns rapporter
            - Det går inte att ändra namnet på en Power BI-rapport i Power BI-rapportservern
            - Det gick inte att läsa in visuella Power BI-objekt i Power BI-mobilappen (det krävs ominstallation av mobilappen för att rensa det lokala cacheminnet)

    - *Build-nr 14.0.600.271, publicerad: 12 juni 2017*
        - Ursprunglig utgåva av Power BI-rapportservern

- **Power BI Desktop (optimerad för Power BI-rapportservern)**
    - *Version: 2.47.4766.4901 (juni 2017), publicerad: 10 januari 2018*
        - Säkerhetsuppdateringar

## <a name="next-steps"></a>Nästa steg

[Vad är Power BI-rapportservern? ](get-started.md)
[Administratörsöversikt](admin-handbook-overview.md)  
[Installera Power BI-rapportserver](install-report-server.md)  
[Hämta Report Builder](https://www.microsoft.com/download/details.aspx?id=53613)  
[Ladda ned SQL Server Data Tools (SSDT)](https://go.microsoft.com/fwlink/?LinkID=616714)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
