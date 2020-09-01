---
title: Skapa innehåll för att migrera till Power BI
description: Vägledning om hur du skapar och validerar innehåll när du migrerar till Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: a12a320b061967e9201e3513e504277a9df586b4
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803511"
---
# <a name="createcontenttomigratetopowerbi"></a>Skapa innehåll för att migrera till Power BI

I den här artikeln beskrivs **steg 4**, som handlar om att skapa och validera innehåll när du migrerar till Power BI.

:::image type="content" source="media/powerbi-migration-create-validate-content/migrate-to-powerbi-stage-4.png" alt-text="Bild som visar stegen i en Power BI-migrering. Steg 4 framhävs för den här artikeln.":::

> [!NOTE]
> En fullständig förklaring av bilden ovan finns i [Översikt över Power BI-migrering](powerbi-migration-overview.md).

Fokus i steg 4 är att utföra det faktiska arbetet att omvandla konceptbeviset (POC, Proof of Concept) till en produktionsklar lösning.

Resultatet av det här steget är en Power BI-lösning som har validerats i en utvecklingsarbetsyta och är redo att distribueras till produktion.

> [!TIP]
> De flesta ämnena som diskuteras i den här artikeln gäller även för ett Power BI-projekt med standardimplementering.

## <a name="create-the-production-solution"></a>Skapa produktionslösningen

Här kan man välja om samma person som utförde POC ska fortsätta med att göra Power BI-lösningen produktionsklar. Men någon annan kan också göra det. Om tidslinjerna inte är i farozonen är det bra att involvera de personer som ska ansvara för Power BI-utvecklingen i framtiden. På så sätt får de tillfälle att lära sig aktivt.

> [!IMPORTANT]
> Återanvänd så mycket som möjligt av arbetet från POC.

### <a name="develop-new-import-dataset"></a>Utveckla ny importdatamängd

Du kan välja att skapa en ny importdatamängd om det inte finns någon befintlig Power BI-datamängd som uppfyller dina behov, eller om den inte kan förbättras för att uppfylla dina behov.

Allra helst kan det vara bra att redan från början frikoppla utvecklingsarbetet i fråga om data och rapporter. [Att frikoppla data och rapporter](report-separate-from-model.md) gör det lättare att separera arbete och behörigheter när olika personer ansvarar för datamodellering och rapporter. Det ger en mer skalbart arbetssätt och uppmuntrar till återanvändning av data.

De viktigaste aktiviteterna vad gäller utvecklingen av en importdatamängd är följande:

- [Hämta data](../connect-data/desktop-quickstart-connect-to-data.md) från en eller flera datakällor (vilket kan vara ett Power BI-dataflöde).
- [Forma, kombinera och förbered](../connect-data/desktop-shape-and-combine-data.md) data.
- Skapa [datamängdsmodellen](../transform-model/desktop-modeling-view.md), inklusive [datumtabeller](../transform-model/desktop-date-tables.md).
- Skapa och kontrollera [modellrelationer](../transform-model/desktop-create-and-manage-relationships.md).
- Definiera [mått](../transform-model/desktop-measures.md).
- Konfigurera [säkerhet på radnivå](../admin/service-admin-rls.md), om det behövs.
- Konfigurera synonymer och [optimera frågor och svar](../natural-language/q-and-a-best-practices.md).
- Planera för skalbarhet, prestanda och samtidighet, vilket kan påverka dina beslut om datalagringslägen, till exempel att använda en [sammansatt modell](../transform-model/desktop-composite-models.md) eller [aggregeringar](../transform-model/desktop-aggregations.md).

> [!TIP]
> Om du har olika miljöer för utveckling/testning/produktion bör du överväga att [parametrisera](/power-query/power-query-query-parameters) datakällor. Det gör distributionen, som beskrivs i [steg 5](powerbi-migration-deploy-support-monitor.md), betydligt enklare.

### <a name="develop-new-reports-and-dashboards"></a>Utveckla nya rapporter och instrumentpaneler

De viktigaste aktiviteterna i fråga om utveckling av en Power BI-rapport eller -instrumentpanel är följande:

- Bestäm om du vill använda en Live-anslutning till en befintlig datamodell eller skapa en ny datamodell
- När du skapar en ny datamodell ska du bestämma [datalagringsläge](../transform-model/desktop-storage-mode.md) för modelltabeller (Import, DirectQuery eller Sammansatt).
- Välj vilket datavisualiseringsverktyg som bäst motsvarar behoven: Power BI Desktop, Paginated Report Builder eller Excel.
- Bestäm vilka [visuella objekt](../consumer/end-user-visual-type.md) som bäst berättar det som rapporten behöver berätta och som besvarar de frågor rapporten behöver besvara.
- Se till att alla visuella objekt visar tydlig, koncis och affärsvänlig terminologi.
- Tillgodose interaktivitetskrav.
- Lägg till [mått på rapportnivå](../transform-model/desktop-tutorial-create-measures.md) om du använder Live-anslutning.
- Skapa en [instrumentpanel](../create-reports/service-dashboards.md) i Power BI-tjänsten, i synnerhet när användarna vill ha ett enkelt sätt att övervaka viktiga mått.

> [!NOTE]
> Många av de här besluten har fattats i tidigare faser av planeringen eller i den tekniska POC.

## <a name="validate-the-solution"></a>Kontrollera lösningen

Det finns fyra huvudaspekter i valideringen av en Power BI-lösning:

1. Datanoggrannhet
2. Säkerhet
3. Funktioner
4. Prestanda

### <a name="validate-data-accuracy"></a>Validera datanoggrannhet

Som ett engångsarbete måste du under migreringen se till att data i den nya rapporten matchar det som visas i den äldre rapporten. Eller – om det finns någon skillnad – kunna förklara varför. Det är vanligare än man tror att man hittar ett fel i den äldre lösningen som åtgärdas i den nya lösningen.

Som en del av det löpande datavalideringsarbetet behöver den nya rapporten den nya rapporten vanligtvis jämföras med det ursprungliga källsystemet. Vi rekommenderar att den här valideringen sker på ett upprepningsbart sätt varje gång du publicerar en rapportändring.

### <a name="validate-security"></a>Validera säkerheten

När du validerar säkerheten finns det två huvudaspekter att tänka på:

- Databehörigheter
- Åtkomst till datamängder, rapporter och instrumentpaneler

I en importdatamängd tillämpas databehörigheter genom att definiera [säkerhet på radnivå](../admin/service-admin-rls.md) (RLS, row-level security). Det är också möjligt att databehörigheter genomdrivs av källsystemet när du använder DirectQuery-lagringsläge (eventuellt med [enkel inloggning](../connect-data/service-gateway-sso-overview.md)).

De huvudsakliga sätten att bevilja åtkomst till Power BI-innehåll är följande:

- [Arbetsyteroller](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) (för innehållsredigerare eller tittare).
- [Appbehörigheter](../collaborate-share/service-create-distribute-apps.md#publish-your-app) som tillämpas på en paketerad uppsättning arbetsyteinnehåll (för tittare).
- [Dela](../collaborate-share/service-share-dashboards.md) en enskild rapport eller instrumentpanel (för tittare).

> [!TIP]
> Vi rekommenderar att innehållsskapare utbildas om hur säkerheten hanteras effektivt. Det är också viktigt att ha robust testning, granskning och övervakning på plats.

### <a name="validate-functionality"></a>Validera funktioner

Det är dags att kontrollera datamängdsinformation som fältnamn, formatering, sortering och standardbeteende för sammanfattningar. Interaktiva rapportfunktioner, som [utsnitt](../visuals/power-bi-visualization-slicers.md), [öka detaljnivån](../consumer/end-user-drill.md), [detaljvisning](../create-reports/desktop-drillthrough.md), [uttryck](../create-reports/desktop-conditional-format-visual-titles.md), [knappar](../create-reports/desktop-buttons.md) eller [bokmärken](../create-reports/desktop-bookmarks.md), bör också verifieras.

Under utvecklingsprocessen bör Power BI-lösningen regelbundet publiceras till en utvecklingsarbetsyta i Power BI-tjänsten. Kontrollera att alla funktioner fungerar som förväntat i tjänsten, till exempel återgivningen av anpassade visuella objekt. Det är också ett bra tillfälle för ytterligare testning. Testa [schemalagd uppdatering](../connect-data/refresh-scheduled-refresh.md), [Frågor och svar](../consumer/end-user-q-and-a.md) samt hur rapporter och instrumentpaneler ser ut på en [mobil enhet](../consumer/mobile/mobile-apps-for-mobile-devices.md).

### <a name="validate-performance"></a>Validera prestanda

Power BI-lösningens prestanda är viktigt för användarupplevelsen. De flesta rapporter bör presentera visuella objekt inom 10 sekunder. Om du har rapporter som tar längre tid att läsa in, kan du pausa och fundera på vad som kan orsaka fördröjningar. Förutom i Power BI Desktop bör rapportprestanda även utvärderas regelbundet i Power BI-tjänsten.

Många prestandaproblem uppstår på grund av [DAX (Data Analysis eXpressions)](../transform-model/desktop-quickstart-learn-dax-basics.md), dålig design av datamängden eller en icke-optimal rapportdesign (till exempel när för många visuella objekt ska återges på en sida). Problem med den tekniska miljön, till exempel nätverket, en överbelastad datagateway eller hur en Premium-kapacitet har konfigurerats, kan också bidra till prestandaproblem. Mer information finns i [Optimeringsguide för Power BI](power-bi-optimization.md) och [Felsöka rapportprestanda i Power BI](report-performance-troubleshoot.md).

## <a name="document-the-solution"></a>Dokumentera lösningen

Det finns två huvudtyper av dokumentation som är användbara för en Power BI-lösning:

- Datamängdsdokumentation
- Rapportdokumentation

Dokumentation kan lagras där den är mest lättåtkomlig för målgruppen. Några vanliga alternativ:

- **På en SharePoint-webbplats:** Det kan finnas en SharePoint-webbplats för ditt Center för utmärkthet (COE) eller en intern Power BI-webbplats.
- **I en app:** URL:er kan konfigureras när du publicerar en Power BI-app för att dirigera användaren till mer information.
- **I enskilda Power BI Desktop-filer:** Modellelement, som tabeller och kolumner, kan definiera en beskrivning. Dessa beskrivningar visas som knappbeskrivningar i rutan **Fält** när du redigerar rapporter.

> [!TIP]
> Om du skapar en webbplats som hubb för Power BI-relaterad dokumentation bör du överväga att [anpassa Få hjälp-menyn](../admin/service-admin-portal.md#publish-get-help-information) med dess URL-plats.

### <a name="create-dataset-documentation"></a>Skapa datamängdsdokumentation

Datamängdsdokumentationen riktas till användare som ska hantera datamängden i framtiden. Det är praktiskt att ta med:

- vilka designbeslut som fattats och varför
- vem som äger, underhåller och certifierar datamängder
- krav på datauppdatering.
- anpassade affärsregler som definierats i datamängder
- särskilda krav på datamängdssäkerhet eller datasekretess
- framtida underhållsbehov
- kända, olösta problem eller uppskjutna, eftersläpande punkter.

Du kan också välja att skapa en ändringslogg som sammanfattar de viktigaste ändringarna som har gjorts i datamängden över tid.

### <a name="create-report-documentation"></a>Skapa rapportdokumentation

Rapportdokumentation, som vanligtvis är strukturerad som en genomgång riktad till rapportkonsumenter, kan hjälpa användarna att få mer värde av dina rapporter och instrumentpaneler. En kort självstudie i videoformat fungerar ofta bra.

Du kan också välja att inkludera ytterligare rapportdokumentation på en dold sida i rapporten. Den kan innehålla designbeslut och en ändringslogg.

## <a name="next-steps"></a>Nästa steg

I [nästa artikel i den här serien om Power BI-migrering](powerbi-migration-deploy-support-monitor.md) lär du dig mer om steg 5 som handlar om att distribuera, stödja och övervaka innehåll när du migrerar till Power BI.

Andra användbara resurser är:

- [Microsoft BI-omvandling](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)

Våra erfarna Power BI-partners finns där och kan hjälpa din organisation att lyckas med migreringsprocessen. Om du vill kontakta en Power BI-partner går du till [partnerportalen för Power BI](https://powerbi.microsoft.com/partners/).
