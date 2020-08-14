---
title: Power BI-administratörsportalen
description: På administratörsportalen kan du konfigurera organisationstäckande inställningar för Power BI. Du kan visa användningsstatistik, konfigurera klientinställningar, arbeta med kapacitet, visa arbetsytor, organisationsvisualiseringar och aktuellt innehåll.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/10/2020
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 19b4d64039333a18405ac57d98773e9e23857a18
ms.sourcegitcommit: 9e39232cbc28d8b39dfec5496db7ece9837b5e53
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "88049816"
---
# <a name="administering-power-bi-in-the-admin-portal"></a>Administrera Power BI i Admin-portalen

Med hjälp av administratörsportalen kan du hantera organisationens Power BI-inställningar. Portalen innehåller sådant som användningsstatistik, åtkomst till Microsoft 365-administrationscentret och klientorganisationsinställningar.

Den fullständiga administratörsportalen kan nås av globala administratörer och användare som har rollen som Power BI-tjänstadministratör. Om du inte är någon av dessa roller kan du bara se **kapacitetsinställningarna** i portalen. Läs mer om administratörsrollen för Power BI-tjänsten i [Förstå administratörsrollen för Power BI](service-admin-role.md).

## <a name="how-to-get-to-the-admin-portal"></a>Navigera till administrationsportalen

Du måste vara global administratör eller Power BI-tjänstadministratör för att få åtkomst till Power BI-administratörsportalen. Läs mer om administratörsrollen för Power BI-tjänsten i [Förstå administratörsrollen för Power BI](service-admin-role.md). Gå till Power BI-administratörsportalen genom att vidta följande steg:

1. Logga in till [Power BI](https://app.powerbi.com) med hjälp av autentiseringsuppgifterna för ditt administratörskonto.

1. Välj **Inställningar** > **Administratörsportalen** i sidhuvudet.

    ![Inställningar för att administratörsportalen](media/service-admin-portal/powerbi-admin-settings.png)

Det finns flera avsnitt i administratörsportalen. Resten av den här artikeln innehåller information om vart och ett av dessa avsnitt.

![Navigering av administratörsportalen](media/service-admin-portal/powerbi-admin-landing-page.png)

* [Användningsstatistik](#usage-metrics)
* [Användare](#users)
* [Granskningsloggar](#audit-logs)
* [Klientinställningar](#tenant-settings)
* [Kapacitetsinställningar](#capacity-settings)
* [Bädda in koder](#embed-codes)
* [Visuella objekt för organisationer](organizational-visuals.md#organizational-visuals)
* [Azure-anslutningar (förhandsversion)](#azure-connections-preview)
* [Arbetsytor](#workspaces)
* [Anpassad varumärkesanpassning](#custom-branding)
* [Säkerhetsmått](#protection-metrics)
* [Aktuellt innehåll](#featured-content)

## <a name="usage-metrics"></a>Användningsstatistik

Med **användningsstatistik** kan du övervaka din organisations Power BI-användning. Den visar också vilka användare och grupper i din organisation som är mest aktiva i Power BI.

> [!NOTE]
> Första gången du använder instrumentpanelen eller när du kommer tillbaka efter en lång tid utan att visa instrumentpanelen visas antagligen en skärm för inläsning medan vi läser in instrumentpanelen.

När instrumentpanelerna har lästs in kan du se två områden med fönster. Det första området innehåller användningsdata för enskilda användare och det andra avsnittet har liknande information för grupper.

Här är en uppdelning av vad du kan se i varje panel:

* Tydlig räkning av alla instrumentpaneler, rapporter och datamängder på användararbetsytan.
  
    ![Separata antal instrumentpaneler, rapporter och datauppsättningar](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)


* Med använd instrumentpanel enligt antal användare med åtkomst till den. Till exempel: Du har en instrumentpanel som du har delat med tre användare. Du har också lagt till instrumentpanelen till ett innehållspaket som två olika användare är anslutna till. Instrumentpanelens antal skulle bli 6 (1 + 3 + 2).
  
    ![Mest använda instrumentpaneler](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* Det mest populära innehåll som användare är anslutna till. Innehållet skulle kunna vara något användarna kan nå genom processen Hämta data, t. ex. SaaS-innehållspaket, organisationsinnehållspaket, filer eller databaser.

  
    ![Mest använda paket](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* En vy över toppanvändarna baserat på hur många instrumentpaneler de har, såväl instrumentpaneler de skapat själva som instrumentpaneler som någon har delat med dem.
  
    ![Användare med flest – instrumentpaneler](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* En vy över toppanvändarna baserat på hur många rapporter de har.
  
    ![Användare med flest – rapporter](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

Det andra avsnittet visar samma typ av information, men baserat på grupper. I det här avsnittet kan du se vilka grupper i din organisation som är mest aktiva och vilken sorts innehåll de använder.

Med den här informationen kan du få verkliga insikter om hur användarna använder Power BI i organisationen.

## <a name="control-usage-metrics"></a>Kontrollera användningsstatistik

Användningsstatistikrapporter är en funktion som Power BI-administratören eller den globala administratören kan aktivera eller inaktivera. Administratörerna har detaljerad kontroll över vilka användare som har åtkomst till användningsstatistik. De är **På** som standard för alla användare i organisationen.

Administratörer kan också bestämma om skapare av innehåll kan se data per användare i användningsmått. 

Se [Övervaka användningsstatistik för Power BI-instrumentpaneler och rapporter](../collaborate-share/service-usage-metrics.md) för mer information om själva rapporterna.

### <a name="usage-metrics-for-content-creators"></a>Användningsstatistik för innehållsskapare

1. Välj **Klientorganisationsinställningar** > **Gransknings- och användningsinställningar** > **Anvndningsstatistik för innehållsskapare** i administratörsportalen.

    ![Användningsstatistik för inställningar för administratörsportalklienten](media/service-admin-portal/power-bi-admin-usage-metrics.png)

1. Aktivera (eller inaktivera) användningsstatistik > **Tillämpa**.

    ![Aktiverad användningsstatistik](../collaborate-share/media/service-usage-metrics/power-bi-tenant-settings-updated.png)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>Data per användare i användningsmått för innehållsskapare

Data per användare är som standard aktiverat för användningsstatistik, och kontoinformation ingår i statistikrapporten. Om du inte vill inkludera kontoinformation för vissa eller alla användare kan du inaktivera funktionen för specifika säkerhetsgrupper eller hela organisationen. Kontoinformation visas sedan i rapporten som *Namnlös*.

![Användningsdata per användare](media/service-admin-portal/power-bi-admin-per-user-usage-data.png)

### <a name="delete-all-existing-usage-metrics-content"></a>Ta bort allt befintligt innehåll för måttet

När du inaktiverar användningsstatistik för hela organisationen kan administratörer också välja ett eller båda alternativ:

- **Ta bort allt befintligt innehåll för användningsstatistik** för att ta bort alla befintliga rapporter och instrumentpaneler som har skapats med användningsstatistikrapporter och datauppsättningar. Det här alternativet tar bort all åtkomst till användningsstatistiken för alla användare i organisationen som kanske redan använder den.
- **Ta bort alla befintliga användarspecifika data i den aktuella användningsstatistiken** Det här alternativet tar bort all åtkomst till användningsstatistiken för alla användare i organisationen som kanske redan använder den. 

Var försiktig, eftersom det inte går att ångra när du har tagit bort befintligt användarspecifikt användningsstatistikinnehåll.

## <a name="users"></a>Användare

Du kan hantera Power BI-användare, grupper och administratörer i Microsoft 365 Administrationscenter. Fliken **Användare** innehåller en länk till administratörscentret.

![Gå till administrationscenter för Microsoft 365](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="audit-logs"></a>Granskningsloggar

Du kan hantera Power BI-granskningsloggar i Säkerhets- och efterlevnadscenter för Office 365. Fliken **Granskningsloggar** innehåller en länk till säkerhets- och efterlevnadscentret. Mer information finns i [Spåra användaraktiviteter i Power BI](service-admin-auditing.md).

Om du vill använda granskningsloggar, se till att inställningen [**Skapa granskningsloggar för intern aktivitetsgranskning och efterlevnad**](#create-audit-logs-for-internal-activity-auditing-and-compliance) är aktiverad.

## <a name="tenant-settings"></a>Klientinställningar

Med **Klientinställningar** kan du aktivera detaljerad kontroll av de funktioner som är tillgängliga för din organisation. Om du har frågor kring känsliga data, vissa av våra funktioner inte är lämpliga för din organisation eller om du bara vill att en viss funktion ska vara tillgänglig för en särskild grupp.

> [!NOTE]
> Klientinställningar som styr tillgängligheten för funktioner i Power BI-användargränssnittet kan hjälpa dig att upprätta styrningsprinciper, men de utgör inte någon säkerhetsåtgärd. Till exempel begränsar Inställningen **Exportera data** begränsar t. ex. inte en Power BI-användares behörigheter för en datamängd. Power BI-användare med läsbehörighet till en datamängd har behörighet att köra frågor på den här datamängden och kan spara resultaten utan att använda funktionen **Exportera data** i Power BI-användargränssnittet.

Följande bild visar flera inställningar på fliken **Klientorganisationsinställningar**.

![Klientinställningar](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> Det kan ta upp till 15 minuter de ändrade inställningarna träder i kraft för alla i organisationen.

Inställningarna kan ha ett av tre tillstånd:

* **Har inaktiverats för hela organisationen**: Ingen i din organisation kan använda den här funktionen.

    ![Inställningen inaktivera alla](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

* **Har aktiverats för hela organisationen**: Alla i din organisation kan använda den här funktionen.

    ![Inställningen aktivera alla](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

* **Har aktiverats för en undergrupp i organisationen**: I stället för att aktivera funktionen för hela organisationen kan du tillämpa inställningen för **vissa säkerhetsgrupper** i organisationen som har behörighet att använda den här funktionen.

    Du kan också aktivera funktionen för hela organisationen, **utom för specifika säkerhetsgrupper**.

    ![Aktiverad delmängdinställningen](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

    Du kan också kombinera inställningar för att aktivera funktionen för en viss grupp av användare och även inaktivera den för en grupp av användare. Med denna metod har vissa användare inte åtkomst till funktionen även om de finns i en tillåten grupp. Den mest restriktiva inställningen för en användare gäller.

    ![Aktivera undantagsinställning](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

Följande avsnitt ger en översikt över de olika typerna av inställningar för klientorganisation.

## <a name="help-and-support-settings"></a>Inställningar för hjälp och support

### <a name="publish-get-help-information"></a>Publicera Få hjälp-information

Administratörer kan ange interna URL:er för att åsidosätta länkarnas mål på Power BI-hjälpmenyn och för licensuppgraderingar. Om du konfigurerar anpassade URL:er kan användare i organisationen gå till interna hjälp- och supportresurser i stället för standardmålen. Följande resursmål kan anpassas:

* **Läs mer**. Den här hjälpmenylänken leder som standard till en [lista över alla Power BI-utbildningsvägar och -moduler](https://docs.microsoft.com/learn/browse/?products=power-bi). Om du istället vill dirigera den här länken till interna utbildningsresurser anger du en anpassad URL för **utbildningsdokumentationen**.

* **Community**. Om du vill leda användarna till ett internt forum från hjälpmenyn i stället för [Power BI-communityn](https://community.powerbi.com/) anger du en anpassad URL för **diskussionsforumet**.

* **Licensuppgraderingar**. Användare med en Power BI-licens (kostnadsfri) kan ges möjlighet att uppgradera sitt konto till Power BI Pro när de använder tjänsten. Om du anger en intern URL för **licensieringsbegäranden** omdirigeras användarna till en intern begäran och ett internt inköpsflöde, och förhindras att göra självbetjäningsköp. Om du vill hindra användare från att köpa licenser, men anser att det är OK att låta användarna starta en Power BI Pro-utvärderingsversion, bör du läsa [Tillåta användare att testa Power BI Pro](#allow-users-to-try-power-bi-pro) om hur man separerar köp- och testningsfunktionerna.

* **Få hjälp**. Om du vill leda användarna till ett internt forum från hjälpmenyn i stället för [Power BI-communityn](https://powerbi.microsoft.com/support/) anger du en anpassad URL för **diskussionsforumet**.

![Publicera Få hjälp-information](media/service-admin-portal/powerbi-admin-tenant-settings-gethelp.png)

### <a name="receive-email-notifications-for-service-outages-or-incidents"></a>Få e-postmeddelanden om tjänstavbrott eller incidenter

E-postaktiverade säkerhetsgrupper får e-postmeddelanden om den här klientorganisationen påverkas av ett avbrott i tjänsten eller en incident. Lär dig mer om [Aviseringar om tjänstavbrott](service-interruption-notifications.md).

### <a name="allow-users-to-try-power-bi-pro"></a>Låt användarna testa Power BI Pro

Inställningen att **Låt användare testa Power BI Pro** är aktiverad som standard och stärker kontrollen över hur användare får Power BI Pro-licenser. I scenarier där du har blockerat självbetjäningsköp kan du använda den här inställningen när du vill starta en Power BI Pro-utvärderingsversion. Slutanvändarupplevelsen beror på hur du kombinerar licensinställningarna. Tabellen nedan visar hur uppgraderingsmiljön från Power BI (kostnadsfri) till Power BI Pro påverkas av olika kombinationer av iställningar:

| Inställningar för självbetjäningsköp | Inställningen Låt användarna testa Power BI Pro | Slutanvändarupplevelse |
| ------ | ------ | ----- |
| Enabled | Inaktiverad | Användaren kan köpa en Pro-licens, men kan inte starta en utvärderingsversion |
| Enabled | Enabled | Användaren kan starta en kostnadsfri utvärderingsversion av Pro och kan uppgradera till en betald licens |
| Inaktiverad | Inaktiverad | Användaren ser ett meddelande om att kontakta IT-administratören för att begära en licens |
| Inaktiverad | Enabled | Användaren kan starta en Pro-utvärderingsversion, men måste kontakta IT-administratören för att få en betald licens |

> [!NOTE]
> Du kan lägga till en intern URL för licensieringsbegäranden i [hjälp- och supportinställningar](#help-and-support-settings). Om du konfigurerar URL:en åsidosätts standardköpsversionen. Användare som kan köpa en licens i de scenarier som beskrivs i tabellen ovan omdirigeras till din interna URL.

![Inställningsgränsnitt för Låt användarna testa Power BI Pro](media/service-admin-portal/allow-pro-trial.png)

Mer information finns i [Aktivera eller inaktivera registrering och inköp via självbetjäning](service-admin-disable-self-service.md).

## <a name="workspace-settings"></a>Arbetsyteinställningar

Administrationsportalen har tre avsnitt för att kontrollera arbetsytor i **Klientinställningar**:

- [Skapa de nya arbetsyteupplevelserna](#create-the-new-workspaces).
- [Använda datamängder på arbetsytor](#use-datasets-across-workspaces).
- [Blockera skapande av klassisk arbetsyta](#block-classic-workspace-creation).

### <a name="create-the-new-workspaces"></a>Skapa nya arbetsytor

Arbetsytor är platser där användarna kan samarbeta kring instrumentpaneler, rapporter och annat innehåll. Administratörer använder inställningen **Skapa arbetsytor (ny arbetsyteupplevelse)** till att indikera vilka användare i organisationen som kan skapa arbetsytor. Administratörer kan tillåta alla eller ingen i en organisation att skapa arbetsytor för nya arbetsyteupplevelser. De kan även begränsa skapandet till medlemmar eller vissa säkerhetsgrupper. Läs mer om [arbetsytor](../collaborate-share/service-new-workspaces.md).

:::image type="content" source="media/service-admin-portal/power-bi-admin-workspace-settings.png" alt-text="Skapa de nya arbetsyteupplevelserna":::

För klassiska arbetsytor baserade på Microsoft 365-grupper, sker administrationen även fortsatt i administrationsportalen och Azure Active Directory.

> [!NOTE]
> Inställningen **Skapa arbetsytor (ny arbetsyteupplevelse)** tillåter som standard endast användare som kan skapa Microsoft 365-grupper att skapa nya Power BI-arbetsytor. Glöm inte att ange ett värde i Power BI-administratörsportalen och därmed säkerställa att lämpliga användare kan skapa dem.

**Lista med arbetsytor**

Administratörsportalen har ett annat avsnitt med inställningar för arbetsytorna i din klient. I det avsnittet kan du sortera och filtrera listan över arbetsytor och visa information för varje arbetsyta. Mer information finns i [Arbetsytor](#workspaces) i den här artikeln.

**Publicera innehållspaket och appar**

I administrationsportalen styr du också vilka användare som har behörighet att distribuera appar i organisationen. Se [Publicera innehållspaket och appar för hela organisationen](#publish-content-packs-and-apps-to-the-entire-organization) i den här artikeln för mer information.

### <a name="use-datasets-across-workspaces"></a>Använda datamängder på arbetsytor

Administratörer kan styra vilka användare i organisationen som kan använda datauppsättningar på flera arbetsytor. När den här inställningen är aktiverad behöver användarna fortfarande den nödvändiga versionsbehörigheten för en speciell datauppsättning.

:::image type="content" source="media/service-admin-portal/power-bi-admin-datasets-workspaces.png" alt-text="Använda datamängder på arbetsytor":::

Mer information finns i [Introduktion till datamängder på olika arbetsytor](../connect-data/service-datasets-across-workspaces.md).

### <a name="block-classic-workspace-creation"></a>Blockera skapande av klassisk arbetsyta

Administratörer kan styra om organisationen kan skapa klassiska arbetsytor. När inställningen är aktiverad kan användare som skapar en arbetsyta bara skapa arbetsytor för den nya arbetsyteupplevelsen. 

![Blockera skapande av klassisk arbetsyta](media/service-admin-portal/power-bi-admin-block-classic-workspaces.png)

När inställningen är aktiverad visas inte nya skapade Office 365-grupper i listan över arbetsytor i Power BI. Befintliga klassiska arbetsytor visas fortfarande i listan. När inställningen är inaktiverad visas alla Office 365-grupper som användaren är medlem av i listan över arbetsytor. Läs mer om [arbetsytor för den nya arbetsyteupplevelsen](../collaborate-share/service-new-workspaces.md).

## <a name="export-and-sharing-settings"></a>Inställningar för export och delning

### <a name="share-content-with-external-users"></a>Dela innehåll med externa användare

Användare i organisationen kan dela instrumentpaneler, rapporter och appar med användare utanför organisationen. Läs mer om att [dela externt](../collaborate-share/service-share-dashboards.md#share-a-dashboard-or-report-outside-your-organization).

![Inställning för externa användare](media/service-admin-portal/powerbi-admin-sharing-external-02.png)

Följande bild visar meddelandet som visas när du delar med en extern användare.

![Dela med externa användare](media/service-admin-portal/powerbi-admin-sharing-external.png)  

> [!IMPORTANT]
> Det här alternativet styr huruvida användare i Power BI kan bjuda in externa användare att bli Azure Active Directory B2B (Azure AD B2B)-gästanvändare i din organisation via Power BI. När funktionen är aktiverad kan användare som har rollen gästanvändare i Azure AD lägga till externa e-postadresser när de delar rapporter, instrumentpaneler och Power BI-appar. Den externa mottagaren uppmanas att ansluta till din organisation som en Azure AD B2B-gästanvändare. Observera att när den här inställningen inaktiveras fortsätter externa användare som redan är Azure AD B2B-gästanvändare i din organisation att visas i användargränssnitt med personväljaren i Power BI och kan ges åtkomst till objekt, arbetsytor och appar.

### <a name="publish-to-web"></a>Publicera på webben

Som administratör för en Power BI-klientorganisation ger inställningen **Publicera på webben** alternativ för vilka användare som kan skapa inbäddningskoder för att publicera rapporter på webben. Den här funktionen gör rapporten och dess data tillgängliga för alla på webben. Mer information om att [publicera på webben](../collaborate-share/service-publish-to-web.md).

> [!NOTE]
> Endast Power BI-administratörer kan tillåta att nya inbäddningskoder för publicering på webben skapas. Organisationer kan ha befintliga inbäddningskoder. Se avsnittet [Inbäddningskoder](service-admin-portal.md#embed-codes) i administrationsportalen för att granska aktuella publicerade rapporter.

Följande bild visar menyn **Fler alternativ (...)** för en rapport när inställningen **Publicera på webben** är aktiverad.

![Publicera på webben på menyn Fler alternativ](media/service-admin-portal/power-bi-more-options-publish-web.png)

Inställningen **Publicera på webben** i administratörsportalen tillhandahåller alternativ för vilka användare kan skapa inbäddningskoder.

![Inställningen publicera på webben](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)

Administratörer kan ställa in **Publicera på webben** till **Aktiverad** och **Välj hur inbäddningskoder fungerar** till **Tillåt endast befintliga inbäddningskoder**. I detta fall kan användarna skapa inbäddningskoder, men de måste kontakta Power BI-administratören som kan tillåta dem att göra det.

![Uppmaning om att publicera på webben](../collaborate-share/media/service-publish-to-web/publish_to_web_admin_prompt.png)

Användarna ser olika alternativ i användargränssnittet baserat på vad inställningen för **Publicering på webben** är.

|Funktion |Aktiverad för hela organisationen |Inaktiverad för hela organisationen |Specifika säkerhetsgrupper   |
|---------|---------|---------|---------|
|**Publicera på webben** under rapportens **Fler alternativ (...)** -meny|Aktiverad för alla|Inte synlig för alla|Endast synlig för behöriga användare eller grupper.|
|**Hantera inbäddade koder** under **Inställningar**|Aktiverad för alla|Aktiverad för alla|Aktiverad för alla<br><br>Alternativet * **Ta bort** endast för behöriga användare eller grupper.<br>* **Hämta koder** aktiverat för alla.|
|**Inbäddade koder** i administrationsportalen|Statusen visar något av följande:<br>* Aktiv<br>* Stöds ej<br>* Blockerad|Statusen visar **Inaktiverad**|Statusen visar något av följande:<br>* Aktiv<br>* Stöds ej<br>* Blockerad<br><br>Om en användare inte har behörighet baserat på klientinställningen visas statusen **Intrång**.|
|Befintliga publicerade rapporter|Alla aktiverade|Alla inaktiverade|Rapporter fortsätta att visas för alla.|

### <a name="export-data"></a>Exportera data

Användare i organisationen kan exportera data från ett fönster eller en visualisering. Det här styr även funktionerna Analysera i Excel, exportera till .CSV, datamängdsnedladdningar och Power BI-tjänstens Live Connect-funktioner. Läs mer om hur du [exporterar data från en panel eller ett visuellt objekt](../visuals/power-bi-visualization-export-data.md).

>[!NOTE]
> Innan inställningen Exportera till Excel introducerades styrde den här inställningen även export av data till Excel-filer. Mer information finns i [anteckning om Exportera till Excel](#export-to-excel).

![Inställning för export av data](media/service-admin-portal/powerbi-admin-portal-export-data-setting.png)

Följande bild visar alternativet för att exportera data från en panel.

![Exportera data från en panel](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> När du inaktiverar **Exportera data** kan användare inte heller använda funktionen [Analysera i Excel](../collaborate-share/service-analyze-in-excel.md) eller live-anslutning till Power BI-tjänsten.

### <a name="export-to-excel"></a>Exportera till Excel

Användare i organisationen kan exportera data från en visualisering till en Excel-fil.

![Inställningen Exportera till Excel](media/service-admin-portal/powerbi-admin-portal-export-to-excel-setting.png)

>[!IMPORTANT]
> Innan inställningen Exportera till Excel introducerades styrdes export till en Excel-fil av inställningen export av data. Första gången administratörer för klientorganisationer i klientorganisationer som fanns före introduktionen av inställningen Exportera till Excel ser inställningen kommer de därför se att den har *Ej tillämpade ändringar*. De måste tillämpa dessa ändringar för att den nya inställningen ska börja gälla. Annars kommer exportering till en Excel-fil även fortsättningsvis att kontrolleras av inställningen Exportera data.

### <a name="export-reports-as-powerpoint-presentations-or-pdf-documents"></a>Exportera rapporter som PowerPoint-presentationer eller PDF-dokument

Användare i organisationen kan exportera Power BI-rapporter som PowerPoint-filer eller PDF-dokument. [Läs mer](../consumer/end-user-powerpoint.md)

Följande bild visar menyn **Arkiv** för en rapport när inställningen **Exportera rapporter som PowerPoint-presentationer eller PDF-dokument** är aktiverad.

![Exportera rapporter som PowerPoint-presentationer](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>Skriva ut instrumentpaneler och rapporter

Användare i organisationen kan skriva ut instrumentpaneler och rapporter. [Läs mer](../consumer/end-user-print.md)

Följande bild visar alternativet för att skriva ut en instrumentpanel.

![Skriv ut instrumentpanel](media/service-admin-portal/powerbi-admin-print-dashboard.png)

Följande bild visar menyn **Arkiv** för en rapport när inställningen **Skriv ut instrumentpaneler och rapporter** är aktiverad.

![Skriva ut rapporten](media/service-admin-portal/powerbi-admin-print-report.png)

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Tillåt externa gästanvändare att redigera och hantera innehåll i organisationen

Azure AD B2B-gästanvändare kan redigera och hantera innehåll i organisationen. [Läs mer](service-admin-azure-ad-b2b.md)

I följande bild visas alternativet Tillåt externa gästanvändare att redigera och hantera innehåll i organisationen.

![Tillåt externa gästanvändare att redigera och hantera innehåll i organisationen](media/service-admin-portal/powerbi-admin-tenant-settings-b2b-guest-edit-manage.png)

I administrationsportalen styr du också vilka användare som har behörighet att bjuda in externa användare till organisationen. Mer information finns i [Dela innehåll med externa användare](#export-and-sharing-settings) i den här artikeln.

### <a name="email-subscriptions"></a>E-postprenumerationer
Användare i organisationen kan skapa e-postprenumerationer. Läs mer om [prenumerationer](../collaborate-share/service-publish-to-web.md).

![Aktivera e-postprenumerationer](media/service-admin-portal/power-bi-manage-email-subscriptions.png)

### <a name="featured-content"></a>Aktuellt innehåll

Tillåt att vissa eller alla rapportförfattare i din organisation kan ha innehåll i avsnittet Aktuellt på Power BI-startsidan. Nya användare ser aktuellt innehåll överst på sin Power BI-startsida. Aktuellt innehåll flyttas ned på startsidan när användarna lägger till **favoriter**, **ofta använda**och **nya**. 

Vi rekommenderar att du börjar med en liten uppsättning kampanjdeltagare först. Att låta hela organisationen lägga upp innehåll på startsidan kan göra det svårt att hålla koll på allt aktuellt innehåll. 

När du har aktiverat aktuellt innehåll kan du också hantera det i administrationsportalen. I [Hantera aktuellt innehåll](#manage-featured-content) i den här artikeln kan du läsa om hur du styr aktuellt innehåll i din domän.

## <a name="content-pack-and-app-settings"></a>Inställningar för innehållspaket och appar

### <a name="publish-content-packs-and-apps-to-the-entire-organization"></a>Publicera innehållspaket och appar för hela organisationen

Administratörer använder den här inställningen för att bestämma vilka användare som får publicera innehållspaket och appar för hela organisationen snarare än specifika grupper. Läs mer om att [publicera appar](../collaborate-share/service-create-distribute-apps.md).

Följande bild visar alternativet **Hela min organisation** när du skapar ett innehållspaket.

![Publicera innehållspaket till organisationen](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-apps-and-organizational-content-packs"></a>Skapa mallappar och organisationsinnehållspaket

Användare i organisationen kan skapa mallappar och organisationsinnehållspaket som använder datamängder som bygger på en datakälla i Power BI Desktop. Läs mer om [mallappar](../connect-data/service-template-apps-create.md).

### <a name="push-apps-to-end-users"></a>Pusha appar till slutanvändare

Rapportskapare kan dela appar direkt med slutanvändare utan att det krävs någon installation från [AppSource](https://appsource.microsoft.com). Läs mer om [installera appar automatiskt för slutanvändare](../collaborate-share/service-create-distribute-apps.md#automatically-install-apps-for-end-users).

## <a name="integration-settings"></a>Inställningar för integrering

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>Analysera i Excel med lokala datauppsättningar

Användare i organisationen kan använda Excel för att visa och interagera med lokala Power BI-datauppsättningar. [Läs mer](../collaborate-share/service-analyze-in-excel.md)

> [!NOTE]
> När du inaktiverar **Exportera data** kan användare inte heller använda funktionen **Analysera i Excel**.

### <a name="use-arcgis-maps-for-power-bi"></a>Använd ArcGIS Maps for Power BI

Användare i organisationen kan använda ArcGIS Maps for Power BI-visualiseringen som tillhandahålls av Esri. [Läs mer](../visuals/power-bi-visualization-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>Använda global sökning för Power BI (förhandsversion)

Användare i organisationen kan använda externa sökfunktioner som förlitar sig på Azure Search.

## <a name="featured-tables-settings"></a>Aktuella tabellinställningar

Under **Klientinställningar** kan Power BI-administratörer med hjälp av klientinställningen **Tillåt anslutningar till aktuella tabeller** styra vem i organisationen som kan använda aktuella tabeller i galleriet för Excel-datatyper. 

:::image type="content" source="media/service-admin-portal/admin-allow-connections-featured-tables.png" alt-text="Alla anslutningar till aktuella tabeller":::

Anslutningar till aktuella tabeller inaktiveras också om klientinställningen **Exportera data** är inställd på **Inaktiverad**.

Läs mer om [aktuella Power BI-tabeller i Excel](../collaborate-share/service-excel-featured-tables.md).

## <a name="share-to-teams-tenant-setting"></a>Dela till Teams-klientinställning

Inställningen **Dela till Teams** finns i avsnittet **Klientinställningar** i Power BI-administratörsportalen. Med den här inställningen kan organisationer dölja knapparna för **Dela till Teams** i Power BI-tjänsten. När inställningen är inaktiverad visas inte **Dela till Teams**-knappar i åtgärdsfältet eller i snabbmenyer när de visar rapporter och instrumentpaneler i Power BI-tjänsten.

![Skärmbild av klientinställningen Dela till Teams i Power BI-administratörsportalen.](media/service-admin-portal/service-teams-share-to-teams-tenant-setting.png)

Läs mer om [delning av Power BI-innehåll till Teams](../collaborate-share/service-share-report-teams.md).

## <a name="r-visuals-settings"></a>Inställningar för R-visualisering

### <a name="interact-with-and-share-r-visuals"></a>Interagera med och dela visuell R-information

Användare i organisationen kan interagera med och dela visuella objekt som skapats med R-skript. [Läs mer](../visuals/service-r-visuals.md)

> [!NOTE]
> Den här inställningen gäller för hela organisationen och kan inte begränsas till specifika grupper.

## <a name="audit-and-usage-settings"></a>Gransknings- och användningsinställningar

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Skapa granskningsloggar för intern aktivitetsgranskning och efterlevnad

Användare i organisationen kan använda granskning för att övervaka åtgärder som vidtas i Power BI av andra användare i organisationen. [Läs mer](service-admin-auditing.md)

Den här inställningen måste vara aktiverad för att registrera granskningsloggposter. Det kan förekomma en fördröjning på upp till 48 timmar mellan det att granskning aktiveras och att granskningsdata kan visas. Om du inte ser data omedelbart kontrollerar du granskningsloggarna senare. Det kan förekomma en liknande fördröjning mellan hämtning av behörighet för att visa granskningsloggar och att komma åt loggarna.

> [!NOTE]
> Den här inställningen gäller för hela organisationen och kan inte begränsas till specifika grupper.

### <a name="usage-metrics-for-content-creators"></a>Användningsstatistik för innehållsskapare

Användarna i organisationen kan se användningsstatistik för de instrumentpaneler och rapporter som de har skapat. [Läs mer](../collaborate-share/service-usage-metrics.md)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>Data per användare i användningsmått för innehållsskapare

Om du använder mått för innehållsskapare visas visningsnamn och e-postadresser för de användare som har åtkomst till innehållet. [Läs mer](../collaborate-share/service-usage-metrics.md)

Data per användare är aktiverat för användningsstatistik som standard, och kontoinformation om innehållsskapare ingår i statistikrapporten. Om du inte vill samla in den här informationen för alla användare kan du inaktivera funktionen för specifika säkerhetsgrupper eller hela organisationen. Kontoinformationen för de exkluderade användarna visas då i rapporten som *Namnlös*.

## <a name="dashboard-settings"></a>Inställningar för instrumentpanelen

### <a name="data-classification-for-dashboards"></a>Klassificering av instrumentpanelsdata

Användare i organisationen kan tagga instrumentpaneler med klassificeringar som anger instrumentpanelens säkerhetsnivåer. [Läs mer](../create-reports/service-data-classification.md)

> [!NOTE]
> Den här inställningen gäller för hela organisationen och kan inte begränsas till specifika grupper.

## <a name="developer-settings"></a>Inställningar för utvecklare

### <a name="embed-content-in-apps"></a>Bädda in innehåll i appar

Användare i organisationen kan bädda in Power BI-instrumentpaneler och rapporter i SaaS-program (programvara som en tjänst). När du inaktiverar den här inställningen kan användare inte använda REST-API: er för att bädda in Power BI-innehåll i sina program. [Läs mer](../developer/embedded/embedding.md)

### <a name="allow-service-principals-to-use-power-bi-apis"></a>Tillåt att tjänsters huvudnamn att använda Power BI API:er

Webbappar som är registrerade i Azure Active Directory (Azure AD) använder en ett huvudnamn för tjänsten som tilldelas i syfte att få åtkomst till Power BI:s API:er utan en inloggad användare. Om du vill tillåta att en app använder autentisering med tjänstens huvudnamn måste tjänstens huvudnamn ingå i en tillåten säkerhetsgrupp. [Läs mer](../developer/embedded/embed-service-principal.md)

> [!NOTE]
> Tjänsthuvudnamn ärver behörigheterna för alla Power BI-klientinställningar för deras säkerhetsgrupp. Begränsa behörigheter genom att skapa en dedikerad säkerhetsgrupp för tjänstens huvudkonton och lägg till i listan Förutom vissa säkerhetsgrupper för de relevanta, aktiverade Power BI-inställningarna.

## <a name="dataflow-settings"></a>Dataflödesinställningar

### <a name="create-and-use-dataflows"></a>Skapa och använda dataflöden

Användare i organisationen kan skapa och använda dataflöden. I [Dataförberedelser med självbetjäning i Power BI](../transform-model/service-dataflows-overview.md) finns en översikt över dataflöden. Information om hur du aktiverar dataflöden i en Premium-kapacitet finns i [Konfigurera arbetsbelastningar](service-admin-premium-workloads.md).

> [!NOTE]
> Den här inställningen gäller för hela organisationen och kan inte begränsas till specifika grupper.

## <a name="template-apps-settings"></a>Inställningar för mallappar

Tre inställningar styr mallapparnas förmåga att publicera eller installera mallappar.

![Inställningar för mallappar i Power BI-administratörsportalen](media/service-admin-portal/power-bi-admin-portal-template-apps.png)

### <a name="publish-template-apps"></a>Publicera mallappar

Användare i organisationen kan skapa arbetsytor för mallappar. Kontrollera vilka användare som kan publicera mallappar eller distribuera dem till klienter utanför organisationen via [AppSource](https://appsource.microsoft.com) eller något annat distributionssätt.

![Power BI-administratörsportalen, inställningen Skapa mallappar](media/service-admin-portal/power-bi-admin-portal-template-app-settings.png)

### <a name="install-template-apps-listed-on-appsource"></a>Installera mallappar som finns i AppSource

Användare i organisationen kan **bara** ladda ned och installera mallappar från [AppSource](https://appsource.microsoft.com). Kontrollera vilka specifika användare eller säkerhetsgrupper som kan installera mallappar från AppSource.

![Power BI-administratörsportalen, inställningen Installera mallappar](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-appsource.png)

### <a name="install-template-apps-not-listed-on-appsource"></a>Installera mallappar som inte finns i AppSource

Kontrollera vilka användare i organisationen som kan ladda ned och installera mallappar **som inte finns i [AppSource](https://appsource.microsoft.com)** .

![Power BI-administratörsportalen, inställningen Installera mallappar](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-nonappsource.png)

## <a name="capacity-settings"></a>Kapacitetsinställningar

### <a name="power-bi-premium"></a>Power BI Premium

På fliken **Power BI Premium** kan du hantera alla premiumfunktioner för Power BI (Em eller P SKU) som har köpts för din organisation. Alla användare inom din organisation ser fliken **Power BI Premium** men kan endast se innehåll om de har angetts som antingen *kapacitetadministratör* eller en användare som har tilldelningsbehörighet. Om en användare inte har några behörigheter visas följande meddelande.

![Ingen åtkomst till Premiuminställningar](media/service-admin-portal/premium-settings-no-access.png)

### <a name="power-bi-embedded"></a>Power BI Embedded

På fliken för **Power BI Embedded** kan du visa de Power BI Embedded-kapaciteter (A SKU) som du har köpt för din kund. Eftersom du bara kan köpa SKU:er från Azure, [hanterar du inbäddade kapaciteter i Azure](../developer/embedded/azure-pbie-create-capacity.md) från **Azure-portalen**.

Mer information om hur du hanterar inställningar för Power BI Embedded (A SKU) finns i [Vad är Power BI Embedded](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md).

## <a name="embed-codes"></a>Bädda in koder

Som administratör kan du visa de inbäddningskoder som har genererats för din klient för att dela rapport offentligt. Du kan även återkalla eller ta bort koder. [Läs mer](../collaborate-share/service-publish-to-web.md)

![Bädda in koder i administrationsportalen för Power BI](media/service-admin-portal/embed-codes.png)

## <a name="organizational-visuals"></a>Visuella objekt för organisationer

Alla administrationsinställningar för visuella Power BI-objekt, inklusive klientinställningar för visuella Power BI-objekt, beskrivs i [Hantera administrationsinställningar för visuella Power BI-objekt](organizational-visuals.md).

## <a name="azure-connections-preview"></a>Azure-anslutningar (förhandsversion)

### <a name="tenant-level-storage-preview"></a>Lagring på klientorganisationsnivå (förhandsversion)

Som standard lagras data som används med Power BI i intern lagring som tillhandahålls av Power BI. Med integreringen av dataflöden och Azure Data Lake Storage Gen2 (ADLS Gen2) kan du lagra dina dataflöden på din organisations Azure Data Lake Storage Gen2 konto. Mer information finns i [Dataflöden och Azure Data Lake-integrering (förhandsversion)](../transform-model/service-dataflows-azure-data-lake-integration.md).

### <a name="workspace-level-storage-permissions-preview"></a>Lagringsbehörigheter på arbetsytenivå (förhandsversion)

Tillåt arbetsyteadministratörer att ansluta till sina egna lagringskonton. Med den här förhandsgranskningsfunktionen kan du aktivera en inställning som gör att arbetsytans administratörer kan ansluta sina egna lagringskonton.

## <a name="workspaces"></a>Arbetsytor

Som administratör kan visa du de arbetsytor som finns i din klientorganisation på fliken **Arbetsytor**. På den här fliken kan du utföra följande åtgärder:

- Uppdatera listan över arbetsytor och deras information.
- Exportera data om arbetsytorna till en .csv-fil. 
- Visa information om en arbetsyta, inklusive dess ID, dess användare och deras roller samt dess instrumentpaneler, rapporter och datamängder.
- Redigera listan över personer som har åtkomst. Detta innebär att du kan ta bort arbetsytan. Du kan lägga till dig själv på en arbetsyta som administratör och sedan öppna arbetsytan och ta bort den.
- Redigera fälten Namn och Beskrivning.

![Lista över arbetsytor](media/service-admin-portal/workspaces-list.png)

Administratörer kan också styra användarnas möjlighet att skapa nya arbetsytor och klassiska arbetsytor. Mer information finns i [Arbetsyteinställningar](#workspace-settings) i den här artikeln. 

Tabellkolumnerna på fliken **Arbetsytor** motsvarar egenskaperna som returneras av [Power BI Admin Rest-API](/rest/api/power-bi/admin) för arbetsytor. Personliga arbetsytor är av typen **PersonalGroup**, klassiska arbetsytor är av typen **Grupp** och arbetsytorna för den nya arbetsyteupplevelsen är av typen **Arbetsyta**. Mer information finns i [Organisera arbetet på de nya arbetsytorna](../collaborate-share/service-new-workspaces.md).

På fliken **Arbetsytor** visas *tillståndet* för varje arbetsyta. Följande tabell innehåller mer information om innebörden av dessa tillstånd.

|Stat  |Beskrivning  |
|---------|---------|
| **Aktiv** | En normal arbetsyta. Det indikerar ingenting om användning eller innehåll, bara att själva arbetsytan är ”normal”. |
| **Frånkopplad** | En arbetsyta utan administratörsanvändare. |
| **Borttaget** | En borttagen arbetsyta. I upp till 90 dagar behåller vi tillräckligt mycket metadata för att återställa arbetsytan om du vill. |
| **Tar bort** | En arbetsyta som håller på att tas bort men som inte är borta än. Användare kan ta bort sina egna arbetsytor, och placera saker i Tar bort och slutligen i Borttagen. |

Administratörerna kan även hantera och återställa arbetsytor med hjälp av administratörsportalen eller PowerShell-cmdletar. 

![Lista över arbetsytor](media/service-admin-portal/workspaces-list.png)

## <a name="custom-branding"></a>Anpassad varumärkesanpassning

Som administratör kan du anpassa utseendet på Power BI för hela organisationen. Det finns för närvarande tre huvudalternativ:

![Alternativ för anpassad varumärkesanpassning](media/service-admin-portal/power-bi-custom-branding.png)

* **Ladda upp logotyp**: För bästa resultat laddar du upp en logotyp som har sparats som en .png-bild som är 10 kB eller mindre och har minst 200 x 30 bildpunkter.

* **Ladda upp omslagsbild**: För bästa resultat laddar du upp en omslagsbild som har sparats som en .jpg- eller .png-bild som är 1 MB eller mindre och har minst 1920 x 160 bildpunkter.

* **Välj temafärg**: Du kan välja tema baserat på ett hex-nummer, RGB, ett värde eller från färgpaletten.


Mer information finns i [Anpassad varumärkesanpassning för din organisation](https://aka.ms/orgBranding).

## <a name="protection-metrics"></a>Skyddsmått

När du aktiverar informationsskydd för Power BI visas dataskyddsmåtten i administrationsportalen. Rapporten visar hur känslighetsetiketter bidrar till att skydda ditt innehåll.

## <a name="manage-featured-content"></a>Hantera aktuellt innehåll

Som innehavaradministratör kan du hantera alla rapporter, instrumentpaneler och appar som har lagts upp i avsnittet Aktuellt innehåll på startsidan för Power BI i hela organisationen.

- I administratörsportalen väljer du **Hantera aktuellt innehåll**.

Här visas en översikt över vem som har tillgång till innehållet, när det lades upp som aktuellt samt alla relevanta metadata. Om något ser misstänkt ut eller om du vill rensa avsnittet Aktuellt innehåll kan du ta bort aktuellt innehåll efter behov.

I [Aktuellt innehåll](#featured-content) i den här artikeln kan du läsa om hur du aktiverar aktuellt innehåll.

## <a name="next-steps"></a>Nästa steg

[Administrera Power BI i din organisation](service-admin-administering-power-bi-in-your-organization.md)  
[Förstå Power BI-administratörsrollen](service-admin-role.md)  
[Granska Power BI i din organisation](service-admin-auditing.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
