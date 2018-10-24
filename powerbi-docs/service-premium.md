---
title: Vad är Microsoft Power BI Premium?
description: Power BI Premium är dedikerad kapacitet för din organisation eller ditt team som ger mer tillförlitlig prestanda och större datavolymer utan att du behöver köpa licenser per användare.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 09/11/2018
LocalizationGroup: Premium
ms.openlocfilehash: 0723ddb57131fed499d4ac86666b3cd6d8bcbd2d
ms.sourcegitcommit: 833cf1252807721fb1b3000487bd032bfd6c8c98
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2018
ms.locfileid: "48271818"
---
# <a name="what-is-microsoft-power-bi-premium"></a>Vad är Microsoft Power BI Premium?

Microsoft Power BI Premium innehåller resurser som är dedikerade för att köra Power BI-tjänsten för din organisation eller ditt team. Det ger dig mer tillförlitlig prestanda och större datavolymer. Med Premium möjliggör också omfattande distribution av innehåll utan att de som ska visa innehållet behöver köpa Pro-licenser per användare.

Du kan dra nytta av Power BI Premium genom att tilldela arbetsytor till en *Premium-kapacitet*. En Premium-kapacitet är en resurs som är dedikerad till din organisation. Arbetsytor som inte tilldelas en Premium-kapacitet finns i en *delad kapacitet*. Med delad kapacitet körs dina arbetsbelastningar på dataresurser som delas av andra kunder. 

I delad kapacitet har Power BI mer begränsningar för enskilda användare för att säkerställa en bra kvalitet på upplevelsen för alla användare. Din arbetsyta är som standard i delad kapacitet, inklusive *Min arbetsyta* och apparbetsytor.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="capacity-tiers"></a>Kapacitetsnivåer

Här är en översikt över skillnaderna mellan delad kapacitet och Premium-kapacitet.

|  | Delad kapacitet | Power BI Premium-kapacitet |
| --- | --- | --- |
| **Uppdateringsintervall** |8/dag |48/dag |
| **Isolering med dedikerad maskinvara** |![](media/service-premium/not-available.png "Inte tillgänglig") |![](media/service-premium/available.png "Tillgänglig") |
| **Företagsdistribution till** ***alla användare*** | | |
| Appar och delning |![](media/service-premium/not-available.png "Inte tillgänglig") |![](media/service-premium/available.png "Tillgänglig")<sup>1</sup> |
| Inbäddad API och kontroller |![](media/service-premium/not-available.png "Inte tillgänglig") |![](media/service-premium/available.png "Tillgänglig")<sup>2</sup> |
| **Publicera Power BI-rapporter lokalt** |![](media/service-premium/not-available.png "Inte tillgänglig") |![](media/service-premium/available.png "Tillgänglig") |

*<sup>1</sup> Mer information finns i avsnittet med [funktioner per licenstyp](service-features-license-type.md).*  
*<sup>2</sup> Framtida förbättringar för Power BI Premium.*

Om du vill börja använda en Power BI Premium-kapacitet tilldelar du en arbetsyta till en kapacitet. När en Premium-kapacitet backar upp en arbetsyta får du:

* **Schemalagda uppdateringar**: Med delad kapacitet är schemalagda uppdateringar för importerade modelldatauppsättningar begränsade till åtta gånger per dag. För datauppsättningar i Premium-arbetsytor kan du schemalägga uppdateringar upp till 48 gånger per dag. DirectQuery-cacheuppdateringarna är fortfarande begränsade till åtta gånger per dag i en Premium-kapacitet.

* **Isolering med dedikerad maskinvara**: I delad kapacitet kan resursbehovet för andra arbetsbelastningar påverka prestanda för dina rapporter och instrumentpaneler. Premium-kapaciteten ger i stället mer konsekventa och tillförlitliga prestanda för dina arbetsbelastningar genom att de isoleras från andra orelaterade arbetsbelastningar.

Om en app backas upp av en Premium-kapacitet (det vill säga att den publicerades från en apparbetsyta som har tilldelats Premium) kan den publicerade appen sedan användas av alla användare i organisationen oavsett vilken licens de tilldelats.

I [Hantera Power BI Premium](service-admin-premium-manage.md) finns mer information om hur du tilldelar arbetsytor till en Premium-kapacitet.

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Noder för premiumkapacitet

Power BI Premium är tillgängligt i nodkonfigurationer med kapaciteter för v-kärnor. Mer information om specifika SKU-erbjudanden och kostnader finns i [Priser för Power BI](https://powerbi.microsoft.com/pricing/). En [kostnadskalkylator](https://powerbi.microsoft.com/calculator/) är också tillgänglig. Mer information om kapacitetsplanering för inbäddade analyser finns i [Planera ett white paper för Power BI-företagsdistribution](https://aka.ms/pbienterprisedeploy).

* P-noder kan användas för inbäddade distributioner eller tjänstedistributioner.

* EM-noder kan endast användas för inbäddade distributioner. EM-noder saknar åtkomst till premiumfunktioner, till exempel att dela appar till användare som inte har någon Power BI Pro-licens.

>[!NOTE]
>Länkarna i den här tabellen fungerar endast korrekt för användare som är globala administratörer för Office 365. Andra får ett 404-fel.

| Kapacitetsnod | Totalt antal virtuella kärnor<br/>*(Serverdel + klientdel)* | Virtuella kärnor för serverdel | Virtuella kärnor för klientdel | DirectQuery/begränsningar vid liveanslutning | Max sidåtergivningar vid högbelastning | Tillgängligt |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (månad för månad)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 v-kärnor |0,5 v-kärna, 2,5 GB RAM |0.5 virtuella kärnor |3,75 per sekund |150-300 |Tillgänglig |
| [EM2 (månad för månad)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 v-kärnor |1 v-kärna, 5 GB RAM |1 v-kärnor |7,5 per sekund |301-600 |Tillgänglig |
| [EM3 (månad för månad)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 v-kärnor |2 v-kärnor, 10 GB RAM |2 v-kärnor | |601–1200 |Tillgänglig |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 v-kärnor |4 v-kärnor, 25 GB RAM |4 v-kärnor |30 per sekund |1 201–2 400 |Tillgängliga ([månad för månad](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1) är också tillgängligt) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 v-kärnor |8 v-kärnor, 50 GB RAM |8 v-kärnor |60 per sekund |2 401–4 800 |Tillgänglig |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 v-kärnor |16 v-kärnor, 100 GB RAM |16 v-kärnor |120 per sekund |4 801–9 600 |Tillgänglig |

* Klientdelens virtuella kärnor ansvarar för webbtjänsten, instrumentpanel och hantering av rapportdokument, hantering av åtkomsträttigheter och schemaläggning av API:er, ladda upp och hämta filer, och vanligen för allt som rör användarupplevelsen.

* Serverdelens virtuella kärnor ansvarar för grovjobbet: frågebearbetning, hantering av cache, köra R-servrar, datauppdatering, bearbetning av naturligt språk, flöden i realtid och återgivning av rapporter och bilder från serversidan. Med serverdelens virtuella kärnor reserveras dessutom en viss mängd minne. Att ha tillräckligt med minne blir särskilt viktigt när du hanterar stora datamodeller eller ett stort antal aktiva datauppsättningar.

## <a name="power-bi-report-server"></a>Power BI-rapportserver
Med Power BI Premium ingår också möjligheten att köra Power BI-rapportserver lokalt i din organisation. Läs mer i [Kom igång med Power BI-rapportserver](report-server/get-started.md).

## <a name="next-steps"></a>Nästa steg
[Vanliga frågor och svar om Power BI Premium](service-premium-faq.md)  
[Viktig information om Power BI Premium](service-premium-release-notes.md)  
[Så här köper du Power BI Premium](service-admin-premium-purchase.md)  
[Hantera Power BI Premium](service-admin-premium-manage.md)  
[Microsoft Power BI Premium – white paper](https://aka.ms/pbipremiumwhitepaper)  
[Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/pbienterprisedeploy)  
[Administrera Power BI i din organisation](service-admin-administering-power-bi-in-your-organization.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
