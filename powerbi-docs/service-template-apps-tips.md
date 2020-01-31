---
title: Tips för att skapa mallappar i Power BI
description: Tips om hur du kan använda frågor, datamodeller, rapporter och instrumentpaneler för att skapa bra mallappar
author: teddybercovitz
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/26/2019
ms.author: tebercov
ms.openlocfilehash: 632c1f1a9f0cba3f403cae4a471df6b7e699f481
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/24/2020
ms.locfileid: "76710163"
---
# <a name="tips-for-authoring-template-apps-in-power-bi"></a>Tips för att skapa mallappar i Power BI

När du [skapar en mallapp](service-template-apps-create.md) i Power BI skapar du en arbetsyta, testar den och börjar använda den i produktionen. Andra viktiga delar är att skapa rapporten och instrumentpanelen. Vi kan bryta ned skapandeprocessen i fyra huvudsakliga delar. Att arbeta med dessa delar hjälper dig att skapa bästa möjliga mallapp:

* Med **frågor** kan du [ansluta](desktop-connect-to-data.md) och [transformera](desktop-query-overview.md) data och definiera [parametrar](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/). 
* I **datamodellen** skapar du [relationer](desktop-create-and-manage-relationships.md), [mått](desktop-measures.md) och vanliga frågor och svar om förbättringar.  
* **[Rapportsidorna](desktop-report-view.md)** innehåller visuella objekt och filter som ger insikter i dina data.  
* **[Instrumentpaneler](consumer/end-user-dashboards.md)** och [paneler](service-dashboard-create.md) ger en översikt över de analyser som ingår.
* Exempeldata medför att din app kan utforskas direkt efter installationen.

Du känner kanske till varje del som befintliga Power BI-funktioner. När du skapar en mallapp finns ytterligare saker att överväga för varje del. Se avsnitten nedan för mer information.

<a name="queries"></a>

## <a name="queries"></a>Frågor
I mallappar används frågor som skapats i Power BI Desktop för att ansluta till din datakälla och importera data. Dessa frågor krävs för att returnera ett konsekvent schema och stöds för schemalagd datauppdatering (DirectQuery stöds inte).

### <a name="connect-to-your-api"></a>Ansluta till din API
Först måste du ansluta till ditt API från Power BI Desktop så att du kan börja skapa dina frågor.

Du kan använda de datakopplingar som finns tillgängliga i Power BI Desktop för att ansluta till din API. Du kan använda Web Data Connector (Hämta data -> Webb) till att ansluta till din Rest API, eller OData-koppling (Hämta data -> OData-feed) för att ansluta till din OData-feed.

> [!NOTE]
> För närvarande har mallappar inte stöd för anpassade anslutningsappar. Vi rekommenderar dig att utforska vidare med Odatafeed Auth 2.0 som åtgärd för några av anslutningsanvändningsfallen eller att låta certifiera din anslutningsapp. Mer information om hur du utvecklar en anslutningsapp och får den certifierad finns i [dokumentationen om datakopplingar](https://aka.ms/DataConnectors).

### <a name="consider-the-source"></a>Fundera över källan
Frågorna definierar vilka data som ingår i datamodellen. Beroende på storleken på ditt system ska dessa frågor också innehålla filter för att dina kunder ska använda en lämplig storlek som passar ditt företagsscenario.

Power BI-mallappar kan köra flera frågor parallellt för många användare samtidigt.  Planera din begränsnings- och samtidighetsstrategi i förväg och fråga oss om hur du ska göra din mallapp feltolerant.

### <a name="schema-enforcement"></a>Schematillämpning
Kontrollera att dina frågor är mottagliga för ändringar i ditt system, ändringar i schemat vid uppdatering kan bryta modellen. Om källan returnerar null eller saknat schemaresultat för vissa frågor, bör du fundera på att returnera en tom tabell eller ett anpassat felmeddelande som ger användaren information.

### <a name="parameters"></a>Parametrar
Med [parametrar](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) i Power BI Desktop kan dina användare ange databasvärden som anpassar de data som hämtats av användaren. Se på parametrarna uppifrån för att undvika omarbete när du har lagt tid på att skapa detaljerade frågor eller rapporter.

> [!NOTE]
> Mallappar stöder alla parametrar utom Any och Binary.
>

### <a name="additional-query-tips"></a>Ytterligare frågetips

* Kontrollera att alla kolumner att skrivits på rätt sätt.
* Kolumnerna ska ha informativa namn (se [Frågor och svar](#qa)).  
* Vid delad logik kan du använda funktioner eller frågor.  
* Sekretessnivåer stöds för närvarande inte i tjänsten. Om en dialogruta om sekretessnivåer visas kan du behöva skriva om frågan och använda relativa sökvägar.  

## <a name="data-models"></a>Datamodeller

Med en väldefinierad datamodell kan dina kunder enkelt och intuitivt interagera med mallappen. Skapa datamodellen i Power BI Desktop.

> [!NOTE]
> Du bör göra en stor del av den grundläggande modelleringen (skriva, kolumnnamn) i [frågorna](#queries).

### <a name="qa"></a>Frågor och svar
Modelleringen påverkar också hur bra Frågor och svar kan visa resultat för dina kunder. Lägg till synonymer i vanligt förekommande kolumner och se till att ge dina kolumner rätt namn i [frågorna](#queries).

### <a name="additional-data-model-tips"></a>Fler datamodelltips

Kontrollera att du har:

* Tillämpat formatering för alla värdekolumner. Använt typer i frågan.  
* Använt formatering för alla mått.
* Angett standardsammanfattning. I synnerhet ”Summera inte” när det är tillämpligt (t.ex. för unika värden).  
* Angett datakategori, om tillämpligt.  
* Angett relationer, vid behov.  

## <a name="reports"></a>Rapporter
På rapportsidorna finns ytterligare analyser av de data som ingår i mallappen. Använd sidorna i rapporterna för att besvara de viktiga affärsfrågor som din mallapp försöker hantera. Skapa rapporten med Power BI Desktop.


### <a name="additional-report-tips"></a>Fler rapporttips

* Använd mer än ett visuellt objekt per sida för korsfiltering.  
* Justera de visuella objekten noga (ingen överlappning).  
* Sidan är inställd på läget ”4:3” eller ”16:9” för layouten.  
* Alla aggregeringar som visas är numeriska (genomsnitt, unika värden).  
* Utsnitten ger rationella resultat.  
* Logotypen finns på den översta rapporten som ett minimum.  
* Elementen är i klientens färgschema så långt det är möjligt.  

<a name="dashboard"></a>

## <a name="dashboards"></a>Instrumentpaneler
Instrumentpanelen är den främsta interaktionspunkten med mallappen för dina kunder. Den ska innehålla en översikt av innehållet som ingår, i synnerhet viktiga mått för ditt affärsscenario.

Skapa en instrumentpanel för din mallapp genom att helt enkelt ladda upp din PBIX med Hämta data > Filer eller publicera direkt från Power BI Desktop.


### <a name="additional-dashboard-tips"></a>Ytterligare instrumentpanelstips

* Behåll samma tema när du fäster så att panelerna på instrumentpanelen är konsekventa.  
* Fäst en logotyp på temat så att kunderna ser var paketet kommer ifrån.  
* Föreslagen layout för de flesta skärmupplösningarna är fem till sex små paneler på bredden.  
* Alla paneler på instrumentpanelen bör ha lämpliga rubriker/underrubriker.  
* Fundera över grupperingen på instrumentpanelen för olika scenarier, antingen lodrätt eller vågrätt.  

## <a name="sample-data"></a>Exempeldata
Mallappar packar ihop cachedata på arbetsytan som en del av appen under processen för att skapa appen:

* Hjälper den som installerar att förstå funktionerna och syftet med appen före anslutning av data.
* Skapar en upplevelse som driver den som installerar till att utforska ytterligare appfunktioner som leder fram till anslutningen av appens datamängd.

Vi rekommenderar att du skaffar högkvalitativa exempeldata innan du skapar appen. Se till att apprapporten och instrumentpanelerna är ifyllda med data.

## <a name="publishing-on-appsource"></a>Publicera i AppSource
Mallappar kan publiceras i AppSource. Följ dessa riktlinjer innan du skickar in din app till AppSource:

* Se till att du skapar en mallapp med engagerande exempeldata som kan hjälpa den som installerar att förstå vad appen kan göra (tom rapport och instrumentpanel godkänns inte).
Mallapparna stöder bara appar med exempeldata så var noga med att markera kryssrutan för statisk app. [Läs mer](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Ha anvisningar som valideringsteamet ska följa som innehåller autentiseringsuppgifter och parametrar som krävs för att ansluta till data.
* Programmet måste innehålla en appikon i Power BI och i ditt CPP-erbjudande. [Läs mer](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Landningssida konfigurerad. [Läs mer](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Var noga med att följa dokumentationen om [Power BI-apperbjudanden](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer).
* Om en instrumentpanel ingår i appen är det viktigt att den inte är tom.
* Installera appen via applänken innan du skickar in den och se till att du kan ansluta datamängden och att appupplevelsen är som du har planerat.
* Se till att ta bort alla onödiga anslutningar innan du laddar upp din pbix till mallarbetsytan.
* Följ Power BI:s [Designmetodtips för rapporter och visuella objekt](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-best-practices) för att få högsta inverkan på användarna och bli godkänd för distribution.
<!--- * In general, only application with valuable functionality can be approved for general use on AppSource. Application with sample data content only must have either a guidance or statistical value.) -->

## <a name="create-a-download-link-for-the-app"></a>Skapa en nedladdningslänk för appen

När du har publicerat mallappen på AppSource ska du överväga att skapa en nedladdningslänk från webbplatsen till antingen:
* AppSource-nedladdningssidan – kan ses offentligt, hämta länken från din AppSource-sida.
* Power BI – kan visas av en Power BI-användare.

För att kunna omdirigera en användare till appens nedladdningslänk i Power BI kan du titta på följande kodexempel: [GitHub-lagringsplats](https://github.com/microsoft/Template-apps-examples/tree/master/src).
[![Nedladdningslänk till app](media/service-template-apps-tips/service-template-apps-tips-download.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github)



## <a name="known-limitations"></a>Kända begränsningar

| Funktion | Kända begränsningar |
|---------|---------|
|Innehåll:  Datauppsättningar   | Det ska finnas exakt en datauppsättning. Endast de datauppsättningar som finns inbyggda i Power BI Desktop (.pbix-filer) är tillåtna. <br>Stöds ej: Datauppsättningar från andra mallar, datauppsättningar mellan arbetsytor, sidnumrerade rapporter (RDL-filer), Excel-arbetsböcker |
|Innehåll: Instrumentpaneler | Realtidspaneler godkänns inte (dvs. inget stöd för push eller strömmande datamängder) |
|Innehåll: Dataflöden | Stöds ej: Dataflöden |
|Innehåll från filer | Endast PBIX-filer är tillåtna. <br>Stöds inte: RDL-filer (sidnumrerade rapporter), Excel-arbetsböcker   |
| Datakällor | Datakällor som har stöd för schemalagd datauppdatering i molnet är tillåtna. <br>Stöds ej: <li> DirectQuery</li><li>Live-anslutningar (inte Azure AS)</li> <li>Lokala datakällor (personlig gateway och företagsgateway stöds inte)</li> <li>Realtid (pushdatamängder stöds inte)</li> <li>Sammansatta modeller</li></ul> |
| Datauppsättning: över arbetsytor | Inga datauppsättningar över arbetsytor är tillåtna  |
| Frågeparametrar | Stöds ej: Parametrar av typen ”Any” eller ”Binary” blockerar uppdateringsåtgärden för datauppsättningen |
| Anpassade visuella objekt | Bara som offentligt tillgängliga anpassade visuella objekt stöds. [Anpassade visuella objekt för organisationer](developer/power-bi-custom-visuals-organization.md) stöds inte |

## <a name="next-steps"></a>Nästa steg

[Vad är Power BI-mallappar?](service-template-apps-overview.md)
