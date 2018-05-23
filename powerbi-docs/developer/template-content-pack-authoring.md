---
title: Redigera mallinnehållspaket i Power BI
description: Mall för att redigera innehållspaket
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 10/09/2017
ms.author: maghan
ms.openlocfilehash: f3f3343122857cbf06c0004d2a3e5e5247f07e48
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="author-template-content-packs-in-power-bi"></a>Redigera mallinnehållspaket i Power BI
När du redigerar ett mallinnehållspaket använder du Power BI Desktop och PowerBI.com. Det finns fyra komponenter i ditt innehållspaket:

* Med frågor kan du [ansluta](../desktop-connect-to-data.md) och [transformera](../desktop-query-overview.md) data, samt definiera [parametrar](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)  
* Datamodell för att skapa förbättringar av [relationer](../desktop-create-and-manage-relationships.md), [mått](../desktop-measures.md) och frågor och svar  
* På rapport[sidor](../desktop-report-view.md) finns visuella objekt och filter som ger analyser av dina data  
* Med [instrumentpanel](../service-dashboards.md) och [paneler](../service-dashboard-create.md) får du en översikt över de analyser som ingår  

Du känner kanske till varje del som befintliga Power BI-funktioner. När du skapar ett innehållspaket finns det några saker att fundera över för varje del – se avsnitten nedan för mer information.

<a name="queries"></a>

## <a name="queries"></a>Frågor
I mallinnehållspaket används frågor som utvecklats i Power BI Desktop till att ansluta till din datakälla och importera data. Dessa frågor krävs för att returnera ett konsekvent schema och stöds för schemalagd datauppdatering (Direct Query stöds inte).

Mallinnehållspaketen stöder endast en datakälla per innehållspaket, så du bör definiera frågorna noggrant. En enda datakälla definieras som en källa som kräver samma autentisering. Du kan göra flera API-anrop i olika frågor om alla anrop sker till samma API-slutpunkt och använder samma autentisering. Power BI-innehållspaket stöder inte flera källor som kräver olika autentiseringar.

### <a name="connect-to-your-api"></a>Ansluta till din API
För att komma igång måste du ansluta till ditt API från Power BI Desktop för att börja skapa dina frågor.

Du kan använda de datakopplingar som finns tillgängliga i Power BI Desktop till att ansluta till ditt API. Du kan använda Web Data Connector (Hämta data -> Webb) till att ansluta till din Rest API, eller OData-koppling (Hämta data -> OData-feed) för att ansluta till din OData-feed. Observera att dessa kopplingar endast fungerar om din API stöder grundläggande autentisering.

> [!NOTE]
> Om API:t använder andra autentiseringstyper som OAuth 2.0 eller Web API-nyckel, måste du utveckla en egen datakoppling som låter Power BI Desktop ansluta och autentisera till ditt API. Mer information om hur du utvecklar din egen datakoppling för ditt innehållspaket, finns i dokumentationen om datakopplingar [här](https://aka.ms/DataConnectors). 
> 
> 

### <a name="consider-the-source"></a>Fundera över källan
Frågorna definierar vilka data som ska ingå i datamodellen. Beroende på storleken på ditt system ska dessa frågor också innehålla filter för att dina kunder ska använda en lämplig storlek som passar ditt företagsscenario.

Power BI-innehållspaket kan köra flera frågor parallellt för många användare samtidigt.  Planera din begränsnings- och samtidighetsstrategi i förväg och fråga oss om hur du ska göra ditt innehållspaket feltolerant.

### <a name="schema-enforcement"></a>Schematillämpning
Kontrollera att dina frågor är mottagliga för ändringar i ditt system, ändringar i schemat vid uppdatering kan bryta modellen. Om källan returnerar null/saknat schemaresultat för vissa frågor, bör du fundera på att returnera en tom tabell eller ett anpassat felmeddelande som ger användaren information.

### <a name="parameters"></a>Parametrar
Med [parametrar](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) i Power BI Desktop kan dina användare ange databasvärden som anpassar de data som hämtats av användaren. Se på parametrarna uppifrån för att undvika omarbete när du har lagt tid på att skapa detaljerade frågor eller rapporter.

> [!NOTE]
> Mallinnehållspaket har endast stöd för textparametrar för närvarande. Andra parametertyper kan användas under utvecklingen, men vid [testning](template-content-pack-testing.md#templates) kommer alla värden som anges av användarna vara literala.
> 
> 

### <a name="additional-query-tips"></a>Ytterligare frågetips
* Kontrollera att alla kolumner att skrivits på rätt sätt  
* Kolumnerna ska ha informativa namn (se Frågor och svar)  
* Vid delad logik kan du använda funktioner eller frågor  
* Sekretessnivåer stöds inte för närvarande i tjänsten – om du får en uppmaning om sekretessnivåer kan du behöva skriva om frågan för att använda relativa sökvägar  

## <a name="data-model"></a>Datamodell
Med en väldefinierad datamodell kan dina kunder enkelt och intuitivt interagera med innehållspaketet. Skapa datamodellen i Power BI Desktop.

> [!NOTE]
> En stor del av den grundläggande modelleringen (skriva, kolumnnamn) ska göras i [frågorna](#queries).
> 
> 

### <a name="qa"></a>Frågor och svar
Modelleringen påverkar också hur bra Frågor och svar kan visa resultat för dina kunder. Lägg till synonymer i vanligt förekommande kolumner och se till att dina kolumner har rätt namn i [frågorna](#queries).

### <a name="additional-data-model-tips"></a>Fler datamodelltips
* Alla värdekolumner har formatering tillämpat
    >[!NOTE]
    >Typer ska tillämpas i frågan.  
* Alla mått har formatering tillämpad  
* Standardsummering är inställd. I synnerhet ”Summera inte” när det är tillämpligt (ex.vis för unika värden)  
* Datakategori har angivits, när det är tillämpligt  
* Relationer har angetts, när det krävs  

## <a name="reports"></a>Rapporter
På rapportsidorna finns ytterligare analyser av de data som ingår i innehållspaketet. Använd sidorna i rapporterna för att besvara de viktiga affärsfrågor som ditt innehållspaket försöker hantera. Skapa rapporten med Power BI Desktop.

> [!NOTE]
> Endast en rapport kan ingå i ett innehållspaket och använda de olika sidorna för att anropa särskilda delar i ditt scenario.
> 
> 

### <a name="additional-report-tips"></a>Fler rapporttips
* Använda mer än ett visuellt objekt per sida för korsfiltering  
* Justera de visuella objekten noga (ingen överlappning)  
* Sidan är inställd på läget ”4:3” eller ”16:9” för layouten  
* Alla aggregeringar som visas är numeriska (genomsnitt, unika värden)  
* Utsnitten ger rationella resultat  
* Logotypen finns på den översta rapporten som ett minimum  
* Elementen är i klientens färgschema så långt det är möjligt  

<a name="dashboard"></a>

## <a name="dashboard"></a>Instrumentpanel
Instrumentpanelen är den främsta interaktionspunkten med innehållspaketet för dina kunder. Den ska innehålla en översikt av innehållet som ingår, i synnerhet viktiga mått för ditt affärsscenario.

Skapa en instrumentpanel för ditt mallinnehållspaket genom att helt enkelt ladda upp din PBIX med Hämta data > Filer eller publicera direkt från Power BI Desktop.

> [!NOTE]
> Mallinnehållspaketen kräver för närvarande en enda rapport och datauppsättning per innehållspaket. Fäst inte innehåll från flera rapporter/datauppsättningar på instrumentpanelen som används i innehållspaketet.
> 
> 

### <a name="additional-dashboard-tips"></a>Ytterligare instrumentpanelstips
* Behåll samma tema när du fäster så att panelerna på instrumentpanelen är konsekventa  
* Fäst en logotyp på temat så att kunderna ser var paketet kommer ifrån  
* Föreslagen layout för de flesta skärmupplösningarna är 5–6 små paneler på bredden  
* Alla paneler på instrumentpanelen bör ha lämpliga rubriker/underrubriker  
* Fundera över grupperingen på instrumentpanelen för olika scenarier, antingen lodrätt eller vågrätt  

<a name="restrictions"></a>

## <a name="summary-of-restrictions"></a>Sammanfattning av begränsningar
Enligt ovanstående avsnitt har mallinnehållspaketen för närvarande ett antal begränsningar:  

| Stöds | *Stöds ej* |
| --- | --- |
| Datauppsättningar som byggts i PBI Desktop |*Datauppsättningar från andra innehållspaket eller indata, som t.ex. Excel-filer* |
| Datakälla som stöds för schemalagd datauppdatering i molnet |*Direct Query eller lokal anslutning stöds inte* |
| Frågor som returnerar ett konsekvent schema eller fel när det är lämpligt |*Dynamiska eller anpassade scheman* |
| En datakälla per datauppsättning |*Flera datakällor som t.ex. kombinationsprogram eller URL:er, vilka identifieras som flera datakällor* |
| Parametrar för att skriva text |*Andra parametertyper (t.ex. datum) eller ”tillåten lista med värden”* |
| En instrumentpanel, rapport och datauppsättning |*Flera instrumentpaneler, rapporter eller datauppsättningar* |

## <a name="next-step"></a>Nästa steg
[Testa och skicka innehållspaket](template-content-pack-testing.md)

