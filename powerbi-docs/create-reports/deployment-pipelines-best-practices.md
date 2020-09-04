---
title: Metodtips för distributionspipelines
description: Metodtips för distributionspipelines i Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: a1a30dc09e61e29053a5a1d95cde3d5a339c5a3d
ms.sourcegitcommit: 6d7d5e6b19e11d557dfa1b79b745728b4ee02b4e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89220870"
---
# <a name="deployment-pipelines-best-practices-preview"></a>Metodtips för distributionspipelines (förhandsversion)

Den här artikeln innehåller vägledning för BI-skapare som hanterar sitt innehåll under hela livscykeln. Den fokuserar på att använda distributionspipelines som ett verktyg för livscykelhantering för BI-innehåll.

Artikeln är indelad i fyra delar:

* **Förberedelse av innehåll** – Förbered ditt innehåll för livscykelhantering.

* **Utveckling** – lär dig mer om de bästa sätten att skapa innehåll i utvecklingssteget för distributionspipelinen.

* **Testa** – förstå hur du använder teststeget för distributionspipelines för att testa din miljö.

* **Produktion** – Använd produktionssteget för distributionspipelines när du gör ditt innehåll tillgängligt för förbrukning.

## <a name="content-preparation"></a>Innehållsförberedelse

Förbered ditt innehåll för pågående hantering under hela livscykeln. Se till att granska informationen i det här avsnittet innan du gör något av följande:

* Släpp ditt innehåll till produktion

* Börja använda en distributionspipeline för en angiven arbetsyta

* Publicera ditt arbete

### <a name="treat-each-workspace-as-a-complete-package-of-analytics"></a>Behandla varje arbetsyta som ett komplett paket av analys

Vi rekommenderar att en arbetsyta innehåller en fullständig vy av en aspekt (till exempel avdelning, affärsenhet, projekt eller vertikal) av din organisation. Detta gör det enklare att hantera behörigheter för olika användare och gör att innehållsversioner för hela arbetsytan kontrolleras enligt ett planerat schema.  

Om du använder [centraliserade datauppsättningar](../connect-data/service-datasets-across-workspaces.md) som används i organisationen rekommenderar vi att du skapar två typer av arbetsytor:

* **Modeller och dataarbetsytor** – dessa arbetsytor kommer att innehålla alla centraliserade datauppsättningar

* **Arbetsytor för rapportering** – dessa arbetsytor kommer att innehålla alla beroende rapporter och instrumentpaneler

### <a name="plan-your-permission-model"></a>Planera din behörighetsmodell

En distributionspipeline är ett Power BI-objekt med sina egna [behörigheter](deployment-pipelines-process.md#permissions). Dessutom innehåller pipelinen arbetsytor som har sina egna behörigheter.

Om du vill implementera ett säkert och enkelt arbetsflöde kan du planera vem som får åtkomst till varje del av pipelinen. Några av övervägandena för att ta med i beräkningen är:

* Vem ska ha åtkomst till pipelinen?

* Vilka åtgärder ska användare med pipeline-åtkomst kunna utföra i varje steg?

* Vem granskar innehållet i teststeget?

* Ska teststegsgranskarna ha tillgång till pipelinen?

* Vem ska övervaka distributionen till produktionssteget?

* Vilken arbetsyta tilldelar du?

* Vilket steg tilldelar du arbetsytan till?

* Behöver du göra ändringar i behörigheterna för den arbetsyta som du tilldelar?

### <a name="connect-different-stages-to-different-databases"></a>Ansluta olika steg till olika databaser

En produktionsdatabas bör alltid vara stabil och tillgänglig. Det är bättre att inte överbelasta den med frågor genererade av BI-skapare för deras utvecklings- eller testdatauppsättningar. Skapa separata databaser för utveckling och testning. Detta hjälper att skydda produktionsdata och överbelastar inte utvecklingsdatabasen med hela mängden produktionsdata, vilket kan sakta ned saker.

>[!NOTE]
>Om organisationen använder [delade centraliserade datauppsättningar](../connect-data/service-datasets-share.md) kan du hoppa över den här rekommendationen.

### <a name="use-parameters-in-your-model"></a>Använda parametrar i modellen

Eftersom du inte kan redigera datakällor för datauppsättningar i Power BI-tjänsten rekommenderar vi att du använder [parametrar](https://docs.microsoft.com/power-query/power-query-query-parameters) för att lagra anslutningsinformation, till exempel instansnamn och databasnamn, i stället för att använda en statisk anslutningssträng. På så sätt kan du hantera anslutningarna via Power BI-tjänstens webbportal eller [använda API:er](https://docs.microsoft.com/rest/api/power-bi/datasets/updateparametersingroup) i ett senare steg.

I distributionspipelines kan du konfigurera parameterregler för att ange specifika värden för utvecklings-, test- och produktionssteg.

Om du inte använder parametrar för anslutningssträngen kan du definiera regler för datakällor för att ange en anslutningssträng för en specifik datauppsättning. Det här stöds dock inte för alla datakällor i distributionspipelines. För att verifiera att du kan konfigurera regler för din datakälla, se [begränsningar för datauppsättningsregler](deployment-pipelines-get-started.md#dataset-rule-limitations).

Parametrar har ytterligare användningsområden, till exempel för att göra ändringar i frågor, filter och texten som visas i rapporten.

## <a name="development"></a>Utveckling

Det här avsnittet innehåller riktlinjer för hur du arbetar med utvecklingssteget för distributionspipelines.

### <a name="use-power-bi-desktop-to-edit-your-reports-and-datasets"></a>Använd Power BI Desktop för att redigera dina rapporter och datauppsättningar

Tänk på Power BI Desktop som din lokala utvecklingsmiljö. Med Power BI Desktop kan du testa, utforska och granska uppdateringar av dina rapporter och datauppsättningar. När arbetet är färdigt kan du ladda upp den nya versionen till utvecklingssteget. På grund av följande skäl rekommenderar vi att du redigerar .pbix-filer på Desktop (och inte i Power BI-tjänsten):

* Det är enklare att samarbeta med andra skapare i samma .pbix-fil om alla ändringar utförs i samma verktyg.

 * Om du utför ändringar online, laddar ner .pbix-filen och sedan laddar upp den igen, skapas dubbletter av rapporter och datauppsättningar.

* Du kan använda versionskontroll för att se till att dina .pbix-filer är aktuella.

### <a name="version-control-for-pbix-files"></a>Versionskontroll för .pbix-filer

Om du vill hantera versionshistoriken för dina rapporter och datauppsättningar använder du [Power BI:s automatiska synkronisering med OneDrive](../connect-data/service-connect-to-files-in-app-workspace-onedrive-for-business.md). Då hålls filerna uppdaterade med den senaste versionen. Det gör även att du kan hämta äldre versioner vid behov.

>[!NOTE]
>Använd endast automatisk synkronisering med OneDrive (eller någon annan lagringsplats) med .pbix-filerna i utvecklingssteget för distributionens pipelines. Synkronisera inte .pbix-filer i test- och produktionsstegen för distributionens pipelines. Det orsakar problem med att distribuera innehåll i pipelinen.

### <a name="separate-modeling-development-from-report-and-dashboard-development"></a>Utveckling av separata modeller för rapport- och instrumentpanelsutveckling

För distributioner i företagsskala rekommenderar vi att du separerar datauppsättningar och utveckling av rapporter och instrumentpaneler. Om du endast vill skicka ändringar till en rapport eller datauppsättning använder du distributionspipelinens alternativ selektiv distribution.  

Den här metoden ska starta från Power BI Desktop genom att skapa en separat .pbix-fil för datauppsättningar och rapporter. Du kan till exempel skapa en .pbix-fil för datauppsättningen och ladda upp den till utvecklingssteget. Senare kan dina rapportförfattare bara skapa en ny .pbix för rapporten och [ansluta den till den publicerade datauppsättningen](../connect-data/service-datasets-discover-across-workspaces.md) med en liveanslutning. Med den här tekniken kan olika skapare arbeta separat med modellering och visualiseringar och distribuera dem till produktion oberoende av varandra.

Med [delade datauppsättningar](../connect-data/service-datasets-share.md) kan du också använda den här metoden i flera arbetsytor.

### <a name="manage-your-models-using-xmla-readwrite-capabilities"></a>Hantera dina modeller med XMLA läs/skriv-funktioner

Genom att separera modelleringsutveckling från rapport- och instrumentpanelsutveckling kan du använda avancerade funktioner som källkontroll, sammanfoga skillnader och automatiserade processer. Dessa ändringar bör göras i utvecklingssteget så att det slutliga innehållet kan distribueras till test- och produktionsstegen. Detta gör att ändringar kan gå igenom en enhetlig process med andra beroende objekt innan de distribueras till produktionssteget.

Du kan separera modelleringsutvecklingen från visualiseringar genom att hantera en [delad datauppsättning](../connect-data/service-datasets-share.md) i en extern arbetsyta med XMLA r/w-funktioner. Den delade datauppsättningen kan ansluta till flera rapporter i olika arbetsytor som hanteras i flera pipelines.

## <a name="test"></a>Test

Det här avsnittet innehåller riktlinjer för hur du arbetar med teststeget för distributionspipelines.

### <a name="simulate-your-production-environment"></a>Simulera produktionsmiljön

Förutom att verifiera att nya rapporter eller instrumentpaneler ser bra ut, är det också viktigt att se hur de presterar från slutanvändarens perspektiv. I teststeget för distributionspipelines kan du simulera en verklig produktionsmiljö i testsyfte.

Se till att dessa tre faktorer beaktas i testmiljön:

* Datavolym

* Användningsvolym

* En liknande kapacitet som i produktion

När du testar kan du använda samma kapacitet som i produktionssteget. Detta kan dock göra produktionen instabil vid belastningstestning. För att undvika instabil produktion bör du använda en annan kapacitet som liknar resurser i produktionskapaciteten för testning. För att undvika extra kostnader kan du använda [Azure A-kapaciteter](../developer/embedded/azure-pbie-create-capacity.md) för att endast betala för testtiden.

![Ett diagram som visar en distributionspipeline med en testmiljö som simulerar en produktionsmiljö.](media/deployment-pipelines-best-practices/deployment-pipelines-best-practices-diagram.png)

### <a name="use-dataset-rules-with-a-real-life-data-source"></a>Använda datauppsättningsregler med en verklig datakälla

Om du använder teststeget för att simulera verklig dataanvändning rekommenderar vi att du separerar datakällorna för utveckling och test. Utvecklingsdatabasen bör vara relativt liten och testdatabasen bör vara så lika som möjligt som produktionsdatabasen. Använd [regler för datakälla](deployment-pipelines-get-started.md#step-4---create-dataset-rules) för att växla datakällor i teststeget.

Att kontrollera mängden data som du importerar från datakällan är användbart om du använder en produktionsdatakälla i teststeget. Det gör du genom att lägga till en parameter i datakällans fråga i Power BI Desktop. Använd parameterregler för att styra mängden importerade data eller redigera parameterns värde.
Du kan också använda den här metoden om du inte vill överbelasta din kapacitet.

### <a name="measure-performance"></a>Mäta prestanda

När du simulerar ett produktionssteg, [kontrollerar du rapportens belastning och interaktioner](../guidance/monitor-report-performance.md) och tar reda på om ändringarna du har gjort påverkar dem.

Du behöver även [övervaka belastningen på kapaciteten](../admin/service-admin-premium-monitor-capacity.md) så att du märker extrema belastningar innan de når produktion.  

>[!NOTE]
>Vi rekommenderar att du övervakar kapacitetsbelastningar igen när du har distribuerat uppdateringar till produktionssteget.

### <a name="check-related-items"></a>Kontrollera relaterade objekt

Relaterade tider kan påverkas av ändringar i datauppsättningar eller rapporter. Under testningen verifierar du att ändringarna inte påverkar eller bryter prestandan för befintliga objekt, vilka kan vara beroende av de uppdaterade.

Du kan enkelt hitta relaterade objekt med hjälp av arbetsytans [dataursprungsvy](../collaborate-share/service-data-lineage.md).

### <a name="test-your-app"></a>Testa din app

Om du distribuerar innehåll till dina slutanvändare via en app, granskar du appens nya version innan den är i produktion. Eftersom varje distributionspipelinesteg har en egen arbetsyta kan du enkelt publicera och uppdatera appar för utvecklings- och teststeg. Detta gör att du kan testa appen från en slutanvändares synsätt.

>[!IMPORTANT]
>Distributionsprocessen omfattar inte uppdatering av appens innehåll eller inställningar. Om du vill tillämpa ändringar på innehåll eller inställningar måste du uppdatera appen manuellt i motsvarande pipelinefas.

## <a name="production"></a>Produktion

Det här avsnittet innehåller riktlinjer för hur du arbetar med produktionssteget för distributionspipelines.

### <a name="manage-who-can-deploy-to-production"></a>Hantera vem som kan distribuera till produktion

Eftersom distributionen till produktion ska hanteras varsamt, är det bra att bara låta vissa personer hantera denna känsliga åtgärd. Men du vill antagligen att alla BI-skapare för en speciell arbetsyta ska ha åtkomst till pipelinen. Detta kan hanteras med hjälp av [behörigheter för produktionsarbetsytan](deployment-pipelines-process.md#permissions).  

För att distribuera innehåll mellan steg måste användare ha antingen medlems- eller administratörsbehörighet för bägge stegen. Se till att endast de personer som du vill distribuera till produktion, kommer att ha behörigheter för produktionsarbetsytan. Andra användare kan ha deltagar- eller läsarroll i produktionsarbetsytan. De kommer att kunna se innehåll i pipelinen men kan inte distribuera.

Dessutom bör du begränsa åtkomst till pipelinen genom att endast aktivera pipelinebehörigheter till användare som är en del av den innehållsskapande processen.

### <a name="set-rules-to-ensure-production-stage-availability"></a>Ange regler för att säkerställa tillgänglighet för produktionssteget

[Datauppsättningsregler](deployment-pipelines-get-started.md#step-4---create-dataset-rules) är ett kraftfullt sätt att säkerställa att data i produktion alltid är anslutna och tillgängliga för användare. När datauppsättningsreglerna tillämpas kan distributioner köras medan du är säker på att slutanvändare kommer att se relevant information utan störningar.

Se till att ange regler för produktionsdatauppsättningar för datakällor och parametrar som definierats i datauppsättningen.

### <a name="update-the-production-app"></a>Uppdatera produktionsappen

Distribution i en pipeline uppdaterar innehållet i arbetsytan, men uppdaterar inte den associerade appen automatiskt. Om du använder en app för innehållsdistribution ska du inte glömma att uppdatera appen när du har distribuerat till produktion, så att slutanvändare omedelbart kan använda den senaste versionen.  

### <a name="quick-fixes-to-content"></a>Snabbkorrigeringar av innehåll

Om det finns buggar i produktion som kräver en snabbkorrigering bör du inte ladda upp en ny .pbix-version direkt till produktionssteget eller göra en onlineändring i Power BI-tjänsten. Det går inte att distribuera baklänges till test- och utvecklingsstegen när det redan finns innehåll i dessa steg. Dessutom är det inte en bra idé att distribuera en korrigering utan att testa den först. Det korrekta sättet att hantera det här problemet är därför att implementera korrigeringen i utvecklingssteget och pusha den genom resten av stegen i distributionspipelinen. På så sätt kan du kontrollera att korrigeringen fungerar innan du distribuerar den till produktion. Det tar bara några minuter att distribuera över pipelinen.

## <a name="next-steps"></a>Nästa steg

>[!div class="nextstepaction"]
>[Introduktion till distributionspipelines](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Kom igång med distributionspipelines](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Förstå distributionspipelineprocessen](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Felsökning av distributionspipelines](deployment-pipelines-troubleshooting.md)
