---
title: Vad är Microsoft Power BI Premium?
description: Power BI Premium är dedikerad kapacitet för din organisation eller ditt team som ger mer tillförlitlig prestanda och större datavolymer utan att du behöver köpa licenser per användare.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/28/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: cb9280f47f1f2d28ce6fabda2dbc173fbdc837ac
ms.sourcegitcommit: 364ffa1178cdfb0a20acffc0fd79922ebc892d72
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57226145"
---
# <a name="what-is-microsoft-power-bi-premium"></a>Vad är Microsoft Power BI Premium?

> [!NOTE]
> Den här artikeln håller på att uppdateras till att beskriva nya funktioner, ge mer information och förbättra läsbarheten. Den senaste informationen finns i [Distribuera och hantera Power BI Premium-kapaciteter](whitepaper-powerbi-premium-deployment.md).

Power BI Premium innehåller resurser som är dedikerade att köra Power BI-tjänsten för din organisation. Det ger dig mer tillförlitlig prestanda och större datavolymer. Premium möjliggör också omfattande distribution av innehåll, utan att varje användare behöver köpa en egen Pro-licens.  

## <a name="premium-capacity-and-shared-capacity"></a>Premium-kapacitet och delad kapacitet

Du kan dra nytta av Power BI Premium genom att tilldela arbetsytor till en *Premium-kapacitet*. En Premium-kapacitet är en resurs som är dedikerad till din organisation. Arbetsytor som inte tilldelas en Premium-kapacitet finns i en *delad kapacitet*. Med delad kapacitet körs dina arbetsbelastningar på dataresurser som delas av andra kunder.

Följande bild visar förhållandet mellan Premium-kapacitet och delad kapacitet. Organisationen Contoso används som exempel.

![Bild av Power BI Premium](media/service-premium/premium-chart.png)

| Område | Beskrivning |
| --- | --- |
| **(1)** Objekt inom en Premium-kapacitet | <ul><li>Åtkomst till apparbetsytor (som medlemmar eller administratörer) och publicering av appar kräver en licens för Power BI Pro.<li>Det krävs Pro-licens för att dela en app, men inte för att använda den.<li>Alla instrumentpanelsmottagare kan ställa in dataaviseringar, oavsett vilken licens de har tilldelats.<li>REST API:er för inbäddning använder ett tjänstkonto med Pro-licens i stället för ett användarkonto.</ul> |
| **(2)** Min arbetsyta i delad kapacitet | <ul><li>Det krävs Pro-licens både för att dela och använda en app.</ul> |
| **(3)** Apparbetsytor i delad kapacitet | <ul><li>All appanvändning kräver Pro-licens.</ul>|
| | |

I delad kapacitet har Power BI mer begränsningar för enskilda användare för att säkerställa en bra kvalitet på upplevelsen för alla användare. Din arbetsyta är som standard i delad kapacitet, inklusive *Min arbetsyta* och apparbetsytor.

Följande tabell visar en översikt över skillnaderna mellan delad kapacitet och Premium-kapacitet:

|  | Delad kapacitet | Power BI Premium-kapacitet |
| --- | --- | --- |
| **Uppdateringsintervall** |8/dag |48/dag |
| Isolering med dedikerad maskinvara |![Inte tillgänglig](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| Företagsdistribution till *alla användare* | | |
| Appar och delning |![Inte tillgänglig](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| Inbäddad API och kontroller |![Inte tillgänglig](media/service-premium/not-available.png) |![](media/service-premium/available.png)<sup>[1](#fnt1)</sup> |
| Publicera Power BI-rapporter lokalt |![Inte tillgänglig](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| | | |

<a name="fnt1">1</a> kommande förbättringar för Power BI Premium.



### <a name="premium-capacity-nodes"></a>Noder för premiumkapacitet

Power BI Premium är tillgängligt i nodkonfigurationer med kapaciteter för v-kärnor. Mer information om specifika SKU-erbjudanden och kostnader finns i [Priser för Power BI](https://powerbi.microsoft.com/pricing/). En [kostnadskalkylator](https://powerbi.microsoft.com/calculator/) är också tillgänglig. Mer information om kapacitetsplanering för inbäddade analyser finns i [Planera ett white paper för Power BI-företagsdistribution](https://aka.ms/pbienterprisedeploy). Sammanfattning:

* P-noder kan användas för inbäddade distributioner eller tjänstedistributioner.

* EM-noder kan endast användas för inbäddade distributioner. EM-noder saknar åtkomst till premiumfunktioner, till exempel att dela appar till användare som inte har någon Power BI Pro-licens.

| Kapacitetsnod | Totalt antal virtuella kärnor<br/>*(Serverdel + klientdel)*  | Virtuella kärnor för serverdel <sup>[1](#fn1)</sup> | Virtuella kärnor för klientdel <sup>[2](#fn2)</sup> | DirectQuery/begränsningar vid liveanslutning | Maximalt antal samtidiga uppdateringar |  Tillgängligt
| --- | --- | --- | --- | --- | --- | --- | --- |
| EM1 (månad för månad) |1 v-kärnor |0,5 v-kärna, 2,5 GB RAM |0.5 virtuella kärnor |3,75 per sekund |  1 | Tillgänglig |
| EM2 (månad för månad) |2 v-kärnor |1 v-kärna, 5 GB RAM |1 v-kärnor |7,5 per sekund |  2 | Tillgänglig |
| EM3 (månad för månad) |4 v-kärnor |2 v-kärnor, 10 GB RAM |2 v-kärnor | | 3 |  Tillgänglig |
| P1 |8 v-kärnor |4 v-kärnor, 25 GB RAM |4 v-kärnor |30 per sekund | 6 | Tillgängliga (månad för månad är också tillgängligt) |
| P2 |16 v-kärnor |8 v-kärnor, 50 GB RAM |8 v-kärnor |60 per sekund | 12 | Tillgänglig |
| P3 |32 v-kärnor |16 v-kärnor, 100 GB RAM |16 v-kärnor |120 per sekund | 24 | Tillgänglig |
| | | | | | | |

<a name="fn1">1</a>: Klientdelens virtuella kärnor ansvarar för webbtjänsten. Till exempel instrumentpanel och rapporthantering, hantering av åtkomsträttigheter, schemaläggning, API:er, överföringar och hämtningar och generellt sett allt som rör användarupplevelsen. 

<a name="fn2">2</a>: Serverdelens virtuella kärnor ansvarar för grovjobbet: frågebearbetning, cachehantering, köra R-servrar, datauppdatering, bearbetning av naturligt språk, flöden i realtid och återgivning av rapporter och bilder från serversidan. Med serverdelens virtuella kärnor reserveras dessutom en viss mängd minne. Att ha tillräckligt med minne blir särskilt viktigt när du hanterar stora datamodeller eller ett stort antal aktiva datauppsättningar.

## <a name="workloads-in-premium-capacity"></a>Arbetsbelastningar i Premium-kapacitet

Som standard stöder kapaciteter för **Power BI Premium** och **Power BI Embedded** endast den arbetsbelastning som är associerad med Power BI-frågor som körs i molnet. Premium stöder också ytterligare arbetsbelastningar för **AI**, **Dataflöden** och **Sidnumrerade rapporter**. Du aktiverar de här arbetsbelastningarna i Power BI-adminstrationsportalen eller via Power BI REST API. Du kan också ange maximalt minne varje arbetsbelastning kan använda, så att du kan styra hur de olika arbetsbelastningarna påverkar varandra. Mer information finns i [Konfigurera arbetsbelastningar](service-admin-premium-workloads.md).

### <a name="default-memory-settings"></a>Standardinställningar för minne

I följande tabeller visas standard- och minimivärden för minnet, baserat på de olika [kapacitetsnoder](#premium-capacity-nodes) som finns tillgängliga. Minne allokeras dynamiskt till dataflöden, men den är statiskt allokerad till sidnumrerade rapporter. Mer information finns i nästa avsnitt, [Överväganden för sidnumrerade rapporter](#considerations-for-paginated-reports).

#### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>Microsoft Office-SKU:er för SaaS-scenarier (programvara som en tjänst)

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| Sidnumrerade rapporter | Saknas | 20 % standard, 10 % minimum | 20 % standard, 5 % minimum | 20 % standard, 2,5 % minimum |
| Dataflöden | 20 % standard, 8 % minimum  | 20 % standard, 4 % minimum  | 20 % standard, 2 % minimum | 20 % standard, 1 % minimum  |
| | | | | |

#### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>Microsoft Azure-SKU:er för PaaS-scenarier (plattform som en tjänst)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| Sidnumrerade rapporter | Saknas                      | Saknas                      | Saknas                     | 20 % standard, 10 % minimum | 20 % standard, 5 % minimum | 20 % standard, 2,5 % minimum |
| Dataflöden         | 27 % standard, 27 % minimum | 20 % standard, 16 % minimum | 20 % standard, 8 % minimum | 20 % standard, 4 % minimum  | 20 % standard, 2 % minimum | 20 % standard, 1 % minimum   |

### <a name="considerations-for-paginated-reports"></a>Överväganden för sidnumrerade rapporter

Om du använder arbetsbelastningen sidnumrerade rapporter så bör du ha i åtanke att sidnumrerade rapporter låter dig köra din egen kod vid rapportåtergivning (till exempel ändra textfärg dynamiskt baserat på innehåll). Det innebär att vi skyddar Power BI Premium-kapaciteten genom att köra sidnumrerade rapporter i ett inneslutet område inom kapaciteten. Vi tilldelar det maximala minne som du anger till det här området, oavsett om arbetsbelastningen är aktiv eller inte. Om du använder Power BI-rapporter eller dataflöden i samma kapacitet, bör du ange ett så lågt minne för de sidnumrerade rapporterna att det inte påverkar andra arbetsbelastningar negativt.

I sällsynta fall kan arbetsbelastningen för sidnumrerade rapporter bli otillgänglig. I det här fallet visar arbetsbelastningen ett feltillstånd i administratörsportalen och användarna uppnår tidsgränser vid rapportåtergivning. För att lösa det här problemet kan du inaktivera arbetsbelastningen och sedan aktivera den igen.

## <a name="power-bi-report-server"></a>Power BI-rapportserver

Med Power BI Premium ingår också möjligheten att köra Power BI-rapportserver lokalt i din organisation. Läs mer i [Kom igång med Power BI-rapportserver](report-server/get-started.md).

## <a name="next-steps"></a>Nästa steg

[Distribuera och hantera Power BI Premium-kapaciteter](whitepaper-powerbi-premium-deployment.md)   
[Så här köper du Power BI Premium](service-admin-premium-purchase.md)   
[Vanliga frågor och svar om Power BI Premium](service-premium-faq.md)   



Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
