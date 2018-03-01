---
title: "Power BI Premium – vad är det?"
description: "Power BI Premium är dedikerad kapacitet för din organisation eller ditt team som ger mer tillförlitlig prestanda och större datavolymer utan att du behöver köpa licenser per användare."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/05/2018
ms.author: maghan
LocalizationGroup: Premium
ms.openlocfilehash: 11cfdfdfbc4b918d00633b78ec0bdafabfe99cd6
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="power-bi-premium---what-is-it"></a>Power BI Premium – vad är det?
Power BI Premium innehåller resurser som är dedikerade för att köra Power BI-tjänsten för din organisation eller ditt team, vilket ger dig mer tillförlitlig prestanda och större datavolymer. Premium möjliggör också frekvent distribution av innehåll utan att du behöver köpa licenser per användare för tittare.

Du kan dra nytta av Power BI Premium genom att tilldela arbetsytor till en Premium-kapacitet. *Premium-kapacitet* är en resurs som är dedikerad för din organisation. Arbetsytor som inte tilldelas en premium-kapacitet kommer att finnas i en delad kapacitet.

*Delad kapacitet* är den upplevelse du är van att arbeta med i Power BI, där dina arbetsbelastningar körs på dataresurser som delas av andra kunder. I delad kapacitet finns fler gränser för enskilda användare för att säkerställa kvaliteten på upplevelsen för alla användare.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="capacity-tiers"></a>Kapacitetsnivåer
Det finns två typer av kapaciteter i Power BI. Delad kapacitet och Power BI Premium-kapacitet. Här tar vi en titt på skillnaderna är mellan dem.

|  | Delad kapacitet | Power BI Premium-kapacitet |
| --- | --- | --- |
| **Uppdateringsintervall** |8/dag |Inte begränsad |
| **Isolering med dedikerad maskinvara** |![](media/service-premium/not-available.png "Inte tillgänglig") |![](media/service-premium/available.png "Tillgänglig") |
| **Företagsdistribution till** ***alla användare*** | | |
| Appar |![](media/service-premium/not-available.png "Inte tillgänglig") |![](media/service-premium/available.png "Tillgänglig")<sup>1</sup> |
| Inbäddad API och kontroller |![](media/service-premium/not-available.png "Inte tillgänglig") |![](media/service-premium/available.png "Tillgänglig")<sup>2</sup> |
| **Publicera Power BI-rapporter lokalt** |![](media/service-premium/not-available.png "Inte tillgänglig") |![](media/service-premium/available.png "Tillgänglig") |

*<sup>1</sup> Kostnadsfri användarkonsumtion i appar inkluderar tittarinnehåll i webben och mobilt, med hjälp av frågor och svar, Quick Insights, Cortana, exportera till CSV, Excel och PowerPoint. En Pro-licens krävs för andra aktiviteter som inte visas, till exempel att skapa rapporter på delade datauppsättningar och analysera i Excel. Lär dig mer om funktioner i [Power BI kostnadsfritt kontra Pro](service-free-vs-pro.md).*  
*<sup>2</sup> Framtida förbättringar kommer till Power BI Premium efter GA.*

### <a name="premium-capacity"></a>Premiumkapacitet
Om du vill börja använda en Power BI Premium-kapacitet, måste du tilldela en arbetsyta till en kapacitet. Mer information om hur du tilldelar en arbetsyta till en premiumkapacitet finns i [Hantera Power BI Premium](service-admin-premium-manage.md).

När en arbetsyta backas upp av premiumkapacitet, får du fördelarna med Power BI Premium.

* Schemalagda uppdateringar: användare var tidigare begränsade till 8 x per dag för schemalagd uppdatering av importerade modeller. Den här begränsningen hävs för datamängder i Premium-arbetsytor. Detta gäller inte för schemalagda uppdateringar för cachelagring av för DirectQuery. De är de samma för Premium och delade kapaciteter.
* Isolering med dedikerad maskinvara – vid delad kapacitet kan prestanda för rapporter och instrumentpaneler påverkas av resurskrav från andra arbetsbelastningar i kapaciteten, trots vårt skydd mot det. Premium innehåller däremot mer konsekvent och tillförlitlig prestanda för arbetsbelastningar genom att isolera dem från orelaterade arbetsbelastningar.

Om en app backas upp av premiumkapacitet (d.v.s. den publicerades från en app-arbetsyta som har tilldelats Premium), kan den publicerade appen sedan användas av alla användare i organisationen oavsett vilken licens de tilldelats. Detta innebär att även användare av den kostnadsfria Power BI kan använda dessa publicerade appar.

### <a name="shared-capacity"></a>Delad kapacitet
Som standard är din arbetsyta i delad kapacitet. Detta inkluderar din personliga *Min arbetsyta* tillsammans med app-arbetsytor. En Delad kapacitet är den upplevelse du är van att arbeta med i Power BI, där dina arbetsbelastningar körs på dataresurser som delas av andra kunder.

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Noder för premiumkapacitet
Power BI Premium är tillgängligt i nodkonfigurationer med kapaciteter för v-kärnor. Mer information om specifika SKU-erbjudanden och kostnaden finns i [Priser för Power BI](https://powerbi.microsoft.com/pricing/). En [kostnadskalkylator](https://powerbi.microsoft.com/calculator/) är också tillgänglig. Mer information om kapacitetsplanering för inbäddade analyser finns i [Planera ett white paper för Power BI-företagsdistribution](https://aka.ms/pbienterprisedeploy).

* P-noder kan användas för inbäddade eller tjänstedistributioner
* EM-noder kan användas för inbäddade distributioner endast
* EM1 och EM2 
* Länkar i den här tabellen fungerar bara korrekt för användare som är globala administratörer för Office 365 – andra får ett 404-fel. 

| Kapacitetsnod | Totalt antal kärnor<br/>*(Serverdel + klientdel)* | Serverdelskärnor | Klientdelskärnor | DirectQuery/begränsningar vid liveanslutning | Max sidåtergivningar vid högbelastning | Tillgängligt |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (månad för månad)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 v-kärnor |,5 kärnor, 2,5 GB RAM-minne |,5 kärnor |3,75 per sekund |150-300 |Tillgänglig |
| [EM2 (månad för månad)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 v-kärnor |1 kärna, 5GB RAM-minne |1 kärna |7,5 per sekund |301-600 |Tillgänglig |
| [EM3 (månad för månad)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 v-kärnor |2 kärnor, 10 GB RAM-minne |2 kärnor | |601–1 200 |Tillgänglig |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 v-kärnor |4 kärnor, 25 GB RAM-minne |4 kärnor |30 per sekund |1 201–2 400 |Tillgängliga ([månad för månad](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1) är också tillgängligt) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 v-kärnor |8 kärnor, 50 GB RAM-minne |8 kärnor |60 per sekund |2 401–4 800 |Tillgänglig |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32-v-kärnor |16 kärnor, 100 GB RAM-minne |16 kärnor |120 per sekund |4 801–9 600 |Tillgänglig |

* Klientdelskärnorna ansvarar för webbtjänsten, instrumentpanel och hantering av rapportdokument, hantering av åtkomsträttigheter och schemaläggning av API:er, ladda upp och hämta filer, och vanligen för allt som rör användarupplevelsen.
* Serverdelskärnor ansvarar för grovjobbet: frågebearbetning, hantering av cache, köra R-servrar, datauppdatering, bearbetning av naturligt språk, flöden i realtid och återgivning av rapporter och bilder från serversidan. Med serverdelskärnor reserveras en viss mängd minne också. Att ha tillräckligt med minne blir särskilt viktigt när du hanterar stora datamodeller eller ett stort antal aktiva datauppsättningar.

## <a name="power-bi-report-server"></a>Power BI-rapportserver
Power BI Premium innehåller rättigheten att köra Power BI-rapportserver lokalt. Mer information finns i [Kom igång med Power BI-rapportserver](report-server/get-started.md).

## <a name="next-steps"></a>Nästa steg
[Vanliga frågor och svar om Power BI Premium](service-premium-faq.md)  
[Viktig information om Power BI Premium](service-premium-release-notes.md)  
[Så här köper du Power BI Premium](service-admin-premium-purchase.md)  
[Hantera Power BI Premium](service-admin-premium-manage.md)  
[Microsoft Power BI Premium – white paper](https://aka.ms/pbipremiumwhitepaper)  
[Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/pbienterprisedeploy)  
[Administrera Power BI i din organisation](service-admin-administering-power-bi-in-your-organization.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

