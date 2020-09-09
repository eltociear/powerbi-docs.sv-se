---
title: Distribuera till Power BI
description: Vägledning om hur du distribuerar, hanterar och övervakar innehåll när du migrerar till Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 59f340e6325cf846d1b0453a94a1015b50a987c4
ms.sourcegitcommit: ffc46032d0771227395cc38be9ec9ff1500eac70
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402012"
---
# <a name="deploy-to-power-bi"></a>Distribuera till Power BI

I den här artikeln beskrivs **steg 5**, som handlar om att distribuera, stödja och övervaka innehåll när du migrerar till Power BI.

:::image type="content" source="media/powerbi-migration-deploy-support-monitor/migrate-to-powerbi-stage-5.png" alt-text="Bild som visar stegen i en Power BI-migrering. Steg 5 framhävs för den här artikeln.":::

> [!NOTE]
> En fullständig förklaring av bilden ovan finns i [Översikt över Power BI-migrering](powerbi-migration-overview.md).

Det primära fokuset i steg 5 är att distribuera den nya Power BI-lösningen till produktion.

Utdata från det här steget är en produktionslösning som är redo att användas av verksamheten. När du arbetar med en flexibel metod kan det vara bra att ha vissa planerade förbättringar som ska levereras i en framtida iteration. Support och övervakning är också viktigt i det här skedet, och det bör ske regelbundet.

> [!TIP]
> Förutom för att köra parallellt och inaktivera de äldre rapporterna, som beskrivs nedan, gäller de avsnitt som beskrivs i den här artikeln även för ett standardprojekt för Power BI-implementering.

## <a name="deploy-to-test-environment"></a>Distribuera en testmiljö

För IT-hanterade lösningar, eller lösningar som är viktiga för affärsproduktivitet, finns det vanligtvis en test miljö. En testmiljö ligger mellan utveckling och produktion och behövs inte för alla Power BI-lösningar. En testarbetsyta kan fungera som en stabil plats, separerad från utveckling, för att acceptanstest för användare (UAT) ska inträffa innan den släpps till produktion.

Om ditt innehåll har publicerats till en arbetsyta med Premium-kapacitet kan [distributionspipelines](../create-reports/deployment-pipelines-overview.md) förenkla distributionsprocessen till utvecklings-, test- och produktionsarbetsytor. Alternativt kan publicering utföras manuellt eller med [PowerShell-skript](https://powerbi.microsoft.com/blog/duplicating-workspaces-by-using-power-bi-cmdlets/).

### <a name="deploy-to-test-workspace"></a>Distribuera till testarbetsyta

Viktiga aktiviteter under en distribution till testarbetsytan omfattar vanligtvis:

- **Anslutningssträngar och parametrar:** Justera datauppsättningens anslutningssträngar om datakällan skiljer sig mellan utveckling och testning. [Parameterisering](../connect-data/service-parameters.md) kan användas för att effektivt hantera anslutningssträngar.
- **Arbetsytans innehåll:** Publicera datauppsättningar och rapporter till testarbetsytan och skapa instrumentpaneler.
- **App.** Publicera en [app](../consumer/end-user-apps.md) med hjälp av innehållet från testarbetsytan om den kommer att ingå i UAT-processen. Vanligen är appbehörigheter begränsade till ett litet antal personer som är involverade i UAT.
- **Datauppdatering:** [Schemalägg uppdatering av datauppsättningen](../connect-data/refresh-scheduled-refresh.md) för alla Import-datauppsättningar för den period då UAT inträffar aktivt.
- **Säkerhet:** Uppdatera eller verifiera [arbetsyteroller](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces). Att testa arbetsytans åtkomst involverar ett litet antal personer som är involverade i UAT.

> [!NOTE]
> Mer information om alternativ för distribution till utveckling, testning och produktion finns i avsnitt 9 i [Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/PBIEnterpriseDeploymentWP).

### <a name="conduct-user-acceptance-testing"></a>Utföra acceptanstest för användare

UAT omfattar vanligtvis affärsanvändare som är ämnesexperter. När de har verifierats ger de sitt godkännande om att det nya innehållet är korrekt, uppfyller kraven och kan distribueras för mer omfattande konsumtion av andra.

I vilken utsträckning den här UAT-processen är formell, inklusive skriftliga signeringar, beror på dina metoder för ändringshantering.

## <a name="deploy-to-production-environment"></a>Distribuera till produktionsmiljön

Det finns flera saker att tänka på när du distribuerar till produktionsmiljön.

### <a name="conduct-a-staged-deployment"></a>Utföra en mellanlagrad distribution

Om du försöker minimera risk- och användaravbrott, eller om det finns andra problem, kan du välja att utföra en mellanlagrad distribution. Den första distributionen till produktion kan omfatta en mindre grupp av pilotanvändare. Med en pilot kan feedback aktivt begäras från pilotanvändarna.

Expandera behörigheter i produktionsarbetsytan eller appen gradvis tills alla målanvändare har behörighet till den nya Power BI-lösningen.

> [!TIP]
> Använd [Power BI-aktivitetsloggen](../admin/service-admin-auditing.md) för att förstå hur konsumenter använder den nya Power BI-lösningen.

### <a name="handle-additional-components"></a>Hantera ytterligare komponenter

Under distributionsprocessen kan du behöva arbeta med dina Power BI-administratörer för att åtgärda andra krav som behövs för att stödja hela lösningen, till exempel:

- **Gatewayunderhåll:** Det kan krävas att du registrerar en [ny datakälla](../connect-data/service-gateway-data-sources.md) i datagatewayen.
- **Gateway-drivrutiner och -anslutningar:** En ny patentskyddad datakälla kan kräva installation av en ny drivrutin eller anpassad anslutning på varje server i gatewayklustret.
- **Skapa en ny Premium-kapacitet:** Du kanske kan använda en befintlig [Premium-kapacitet](../admin/service-premium-capacity-manage.md). Eller så kan det finnas situationer när en ny Premium-kapacitet är motiverad. Det kan vara fallet när du vill avgränsa en avdelnings arbetsbelastning.
- **Konfigurera ett Power BI-dataflöde:** Aktiviteter för förberedelse av data kan ställas in en gång i ett [Power BI-dataflöde](../transform-model/service-dataflows-overview.md) med Power Query Online. Det hjälper till att undvika att replikera förberedelse av data i många olika Power BI Desktop-filer.
- **Registrera ett nytt organisatoriskt visuellt objekt:** Registrering av [ett organisatoriskt visuellt objekt](../developer/visuals/power-bi-custom-visuals-organization.md) i organisationen kan göras i administrationsportalen för anpassade visuella objekt som inte härstammar från AppSource.
- **Ange aktuellt innehåll:** Det finns en klientinställning som styr vilka som kan [visa innehåll](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/) på Power BI-tjänstens startsida.
- **Ange känslighetsetiketter:** Alla [känslighetsetiketter](../admin/service-security-data-protection-overview.md) från Microsoft Information Protection.

### <a name="deploy-to-production-workspace"></a>Distribuera till produktionsarbetsyta

Viktiga aktiviteter under en distribution till produktionsarbetsytan omfattar vanligtvis:

- **Ändringshantering:** Om det behövs kan du skaffa ett godkännande för att distribuera och kommunicera till användargruppen med hjälp av standardmetoderna för ändringshantering. Det kan finnas ett fönster för godkänd ändringshantering där produktionsdistributioner tillåts. Det är vanligtvis tillämpligt på IT-hanterat innehåll och används mycket mer sällan för självbetjäningsinnehåll.
- **Återställningsplan:** Med en migrering är förväntningen att migreringen görs av en ny lösning för första gången. Om innehållet redan finns måste du ha en plan för att återgå till den tidigare versionen, om det blir nödvändigt. Att ha tidigare versioner av Power BI Desktop-filer (med SharePoint- eller OneDrive-versioner) fungerar bra för det här ändamålet.
- **Anslutningssträngar och parametrar:** Justera datauppsättningens anslutningssträngar om datakällan skiljer sig mellan testning och produktion. [Parameterisering](../connect-data/service-parameters.md) kan användas effektivt för detta ändamål.
- **Datauppdatering:** [Schemalägg datauppsättningsuppdateringar](../connect-data/refresh-scheduled-refresh.md) för alla importerade datauppsättningar.
- **Arbetsytans innehåll:** Publicera datauppsättningar och rapporter till produktionsarbetsytan och skapa instrumentpaneler. Om ditt innehåll har publicerats till arbetsytor med Premium-kapacitet kan [distributionspipelines](../create-reports/deployment-pipelines-overview.md) förenkla distributionsprocessen till utvecklings-, test- och produktionsarbetsytor.
- **App:** Om appar är en del av din strategi för innehållsdistribution publicerar du en [app](../consumer/end-user-apps.md) med hjälp av innehållet från produktionsarbetsytan.
- **Säkerhet:** Uppdatera och verifiera [arbetsyteroller](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) baserat på din strategi för innehållsdistribution och samarbete.
- **Datamängdsinställningar:** Uppdatera och verifiera inställningarna för varje datauppsättning, däribland:
  - [Bekräftelse](../connect-data/service-datasets-certify.md) (till exempel certifierad eller upphöjd)
  - Gatewayanslutning eller autentiseringsuppgifter för datakälla
  - Schemalagd uppdatering
  - [Aktuella frågor och svar](../create-reports/service-q-and-a-create-featured-questions.md)
- **Inställningar för rapporter och instrumentpanel:** Uppdatera och verifiera inställningarna för varje rapport och instrumentpanel. De viktigaste inställningarna är:
  - Beskrivning
  - Kontaktperson eller grupp
  - [Känslighetsetikett](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
  - [Aktuellt innehåll](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)
- **Prenumerationer:** Konfigurera rapportprenumerationer om det behövs.

> [!IMPORTANT]
> Du har nu nått en stor milstolpe. Fira din prestationer genom att slutföra migreringen.

### <a name="communicate-with-users"></a>Kommunicera med användare

Meddela den nya lösningen till konsumenter. Berätta för dem var de kan hitta innehållet, samt information om tillhörande dokumentation, vanliga frågor och svar och självstudier. Om du vill introducera det nya innehållet bör du överväga att vara värd för en lunch-and-learn type-session eller förbereda några videor på begäran.

Se till att ta med anvisningar om hur du man om hjälp, samt hur man ger feedback.

### <a name="conduct-a-retrospective"></a>Genomför en återblick

Överväg att utföra en återblick för att undersöka vad som gått bra med migreringen och vad som kan göras bättre vid nästa migrering.

## <a name="run-in-parallel"></a>Kör parallellt

I många situationer körs den nya lösningen parallellt med den äldre lösningen för en fördefinierad tid. Fördelar med att köra parallellt är:

- Riskminskning, särskilt om rapporterna betraktas som verksamhetskritiska.
- Gör det möjligt för användare att vänja sig vid den nya Power BI-lösningen.
- Gör det möjligt för informationen som visas i Power BI att korsrefereras till äldre rapporter.

## <a name="decommission-the-legacy-report"></a>Inaktivera den äldre rapporten

Vid något tillfälle bör de rapporter som migrerats till Power BI inaktiveras på den äldre BI-plattformen. Inaktivering av äldre rapporter kan inträffa när:

- Den förväntade tiden för parallell körning – som bör ha kommunicerats till användargruppen – har upphört att gälla. Det är vanligtvis 30–90 dagar.
- Alla användare av det äldre systemet har tillgång till den nya Power BI-lösningen.
- Betydande aktivitet inträffar inte längre i den äldre rapporten.
- Inga problem har uppstått med den nya Power BI-lösningen som kan påverka användarnas produktivitet.

## <a name="monitor-the-solution"></a>Övervaka lösningen

Händelser från [Power BI-aktivitetsloggen](../admin/service-admin-auditing.md) kan användas för att förstå användningsmönster för den nya lösningen (eller [-körningsloggen](/sql/reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view?view=sql-server-ver15) för innehåll som distribuerats till Power BI-rapportservern). Om du analyserar aktivitetsloggen kan du få hjälp med att avgöra om den faktiska användningen skiljer sig från förväntningarna. Det kan också verifiera att lösningen stöds tillräckligt.

Här är några frågor som kan åtgärdas genom att granska aktivitetsloggen:

- Hur ofta visas innehållet?
- Vem visar innehållet?
- Visas innehållet vanligtvis via en app eller en arbetsyta?
- Använder de flesta användare en webbläsare eller ett mobilprogram?
- Används prenumerationer?
- Skapas nya rapporter som baseras på den här lösningen?
- Uppdateras innehållet ofta?
- Hur definieras säkerhet?
- Inträffar problem regelbundet, till exempel datauppdateringsfel?
- Sker oroande aktiviteter (till exempel betydande exportaktivitet eller flera enskilda rapportresurser) som kan innebära att ytterligare utbildning behövs?

> [!IMPORTANT]
> Se till att någon regelbundet granskar aktivitetsloggen. Att bara hämta den och lagra historiken är viktigt i gransknings- och efterlevnadssyfte. Det verkliga värdet är dock när förebyggande åtgärder kan vidtas.

## <a name="support-the-solution"></a>Stödja lösningen

Även om migreringen är slutförd är perioden efter migreringen viktig för att lösa problem och hantera eventuella prestandaproblem. Med tiden kommer den migrerade lösningen förmodligen att genomgå ändringar när affärsbehoven utvecklas.

Supporten kan vara lite olika beroende på hur BI av självbetjäningstyp hanteras i hela organisationen. Power BI-experter i hela affärsenheterna fungerar ofta som förstahandssupport. Även om det är en informell roll är den viktigt och bör uppmuntras.

Att ha en formell supportprocess som är bemannad med supportbegäran, är också avgörande för hantering av rutinmässiga systemorienterade förfrågningar och för eskalering.

Du kan också ha ett [Center för utmärkthet (COE)](center-of-excellence-establish.md) som fungerar som interna konsulter som stöder, utbildar och styr Power BI i organisationen. En COE kan vara ansvarig för att granska användbart Power BI-innehåll i en intern portal.

Slutligen bör det vara klart för innehållskonsumenter att veta vem som ska kontaktas angående frågor om innehållet och för att få en mekanism för att ge feedback om problem eller förbättringar.

## <a name="next-steps"></a>Nästa steg

I den [sista artikeln i den här serien](powerbi-migration-learn-from-customers.md) lär du dig av kunder när de migrerar till Power BI.

Andra användbara resurser är:

- [Microsoft BI-omvandling](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)

Våra erfarna Power BI-partners finns där och kan hjälpa din organisation att lyckas med migreringsprocessen. Om du vill kontakta en Power BI-partner går du till [partnerportalen för Power BI](https://powerbi.microsoft.com/partners/).
