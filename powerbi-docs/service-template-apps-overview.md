---
title: Vad är Power BI-mallappar?
description: Den här artikeln ger en översikt över Power BI-mallappar. Lär dig hur du skapar Power BI-appar med lite eller ingen kodning och distribuerar dem till Power BI-kunder.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
ms.openlocfilehash: 466e7cb842244104b004c4f65f82dafe13dc9725
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82781327"
---
# <a name="what-are-power-bi-template-apps"></a>Vad är Power BI-mallappar?

Med de nya Power BI-*mallapparna* kan Power BI-partner skapa Power BI-appar med lite eller ingen kodning och sedan distribuera dem till Power BI-kunder.  Den här artikeln ger en översikt över Power BI-mallappar.

Som Power BI-partner kan du skapa en uppsättning färdigt innehåll för kunderna och publicera det själv.  

Du skapar mallappar som kunderna sedan kan ansluta och instantiera med sina egna konton. Som domänexperter kan de låsa upp data på ett användarvänligt sätt för företagsanvändarna.  

Du skickar en mallapp till Partnercenter. Apparna blir sedan offentligt tillgängliga i [Power BI Apps Marketplace](https://app.powerbi.com/getdata/services) och på [Microsoft AppSource](https://appsource.microsoft.com/?product=power-bi). Här ges en översikt över hur allmänt tillgängliga mallappar skapas.

## <a name="power-bi-apps-marketplace"></a>Marketplace för Power BI-appar

Med Power BI Template Apps kan Power BI Pro- eller Power BI Premium-användare få omedelbara insikter genom förpaketerade instrumentpaneler och rapporter som kan anslutas till realtidsdatakällor. Det finns många Power BI-appar som redan finns i [Power BI Apps Marketplace](https://app.powerbi.com/getdata/services).

|  |
|     :---:      |
| [![Webbappen Microsoft Project](./media/service-template-apps-overview/project-web.png)](https://app.powerbi.com/groups/me/getapps/services/pbi_msprojectonline.pbi-microsoftprojectwebapp) [![Webbappen Microsoft 365 Usage Analytics](./media/service-template-apps-overview/microsoft365-usage-analytics.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics) [![Webbappen Dynamic 365 Business Central – Sales](./media/service-template-apps-overview/dynamics-sales.png)](https://app.powerbi.com/groups/me/getapps/services/microsoftdynsmb.businesscentral_sales) [![Webbappen Microsoft Forms Pro Customer Satisfaction](./media/service-template-apps-overview/forms-pro.png)](https://app.powerbi.com/groups/me/getapps/services/msfp.formsprocustomersatisfaction) |
|  |

## <a name="process"></a>Process
Den generella processen för att utveckla och skicka in en mallapp består av flera steg. Vissa steg kan omfatta flera samtidiga aktiviteter.


| Steg | Power BI Desktop |  |Power BI-tjänst  |  |Partnercenter  |
|---|--------|--|---------|---------|---------|
| **Ett** | Skapa en datamodell och rapport i en PBIX-fil |  | Skapa en arbetsyta. Importera en PBIX-fil. Skapa en kompletterande instrumentpanel  |  | Registrera dig som en partner |
| **Två** |  |  | Skapa ett testpaket och kör en intern validering        |  | |
| **Tre** | |  | Höj upp testpaket till förproduktion för validering utanför din Power BI-klientorganisation och skicka den till AppSource  |  | Med förproduktionspaketet skapar du ett Power BI-mallapperbjudande och påbörjar valideringsprocessen |
| **Fyra** | |  | Höj upp förproduktionspaketet till produktion |  | Publicera |

## <a name="before-you-begin"></a>Innan du börjar

Du behöver behörighet för att kunna skapa en mallapp. Se mallappinställningarna i Power BI-administratörsportalen för mer information. 

För att kunna publicera en mallapp till Power BI-tjänsten och AppSource måste du uppfylla kraven för att [bli Partnercenter-utgivare](https://docs.microsoft.com/azure/marketplace/become-publisher).
 
## <a name="high-level-steps"></a>Övergripande steg

Här är de övergripande stegen. 

1. [Granska kraven](#requirements) och se till att du uppfyller dem. 

2. Skapa en rapport i Power BI Desktop. Använd parametrarna så att du kan spara den som en fil som andra kan använda. 

3. Skapa en arbetsyta för din mallapp i din klientorganisation på Power BI-tjänsten (app.powerbi.com). 

4. Importera PBIX-filen och lägg till innehåll, till exempel en instrumentpanel, i din app. 

5. Skapa ett testpaket för att testa mallappen själv inom din organisation. 

6. Höj upp testappen till förproduktion för att skicka appen för validering i AppSource och testa den utanför din klientorganisation. 

7. Skicka in innehållet till [Partnercenter](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer) för publicering. 

8. Se till att ditt erbjudande är aktivt (publicerat) i AppSource och flytta appen till produktion i Power BI.

9. Nu kan du börja utveckla nästa version i samma arbetsyta i förproduktion. 

## <a name="requirements"></a>Krav

Du behöver behörighet för att kunna skapa en mallapp. Se [mallappinställningarna i Power BI-administratörsportalen](service-admin-portal.md#template-apps-settings) för mer information.

För att kunna publicera en mallapp till Power BI-tjänsten och AppSource måste du uppfylla kraven för att [bli en Partnercenter-utgivare](https://docs.microsoft.com/azure/marketplace/become-publisher).
 > [!NOTE] 
 > Inskickade mallappar hanteras i [Partnercenter](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer). Använd samma registreringskonto för Microsoft Developer Center för att logga in. Du bör ha endast ett Microsoft-konto för alla dina AppSource-erbjudanden. Konton bör inte vara specifika för enskilda tjänster eller erbjudanden.

## <a name="tips"></a>Tips 

- Se till att din app innehåller exempeldata så att alla kan komma igång direkt. 
- Granska appen noggrant genom att installera den i din klientorganisation och i en annan klientorganisation. Kontrollera att kunderna bara kan se det som du vill att de ska se. 
- Använd AppSource som onlinebutik för din app. På så sätt kan alla som använder Power BI hitta din app. 
- Överväg att erbjuda en mallapp för separata unika scenarier. 
- Aktivera dataanpassning, till exempel stöd för anpassade anslutningar och konfiguration av parametrar i installationsprogrammet.

Se [Tips för att skapa mallappar i Power BI](service-template-apps-tips.md) för fler förslag.

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
| Visuella objekt för Power BI | Bara som offentligt tillgängliga visuella Power BI-objekt stöds. [Visuella Power BI-objekt för organisationer](developer/visuals/power-bi-custom-visuals-organization.md) stöds inte |
| Nationella moln | Mallappar är inte tillgängliga i nationella moln |

## <a name="support"></a>Support
Använd [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support) för support under utveckling. Vi övervakar och hanterar den här webbplatsen aktivt. Kundincidenter når snabbt ett lämpligt team.

## <a name="next-steps"></a>Nästa steg

[Skapa en mallapp](service-template-apps-create.md)
