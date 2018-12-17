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
ms.date: 10/21/2018
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: cbfee8034639a65517f9adc57cc95dd1271e6044
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53025452"
---
# <a name="what-is-microsoft-power-bi-premium"></a>Vad är Microsoft Power BI Premium?

Microsoft Power BI Premium innehåller resurser som är dedikerade för att köra Power BI-tjänsten för din organisation. Det ger dig mer tillförlitlig prestanda och större datavolymer. Premium möjliggör också omfattande distribution av innehåll, utan att varje användare behöver köpa en egen Pro-licens. Information om hur du köper Premium finns i [Så här köper du Power BI Premium](service-admin-premium-purchase.md).

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

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

I följande tabell visas en översikt över skillnaderna mellan delad kapacitet och Premium-kapacitet.

|  | Delad kapacitet | Power BI Premium-kapacitet |
| --- | --- | --- |
| **Uppdateringsintervall** |8/dag |48/dag |
| **Isolering med dedikerad maskinvara** |![Inte tillgänglig](media/service-premium/not-available.png) |![Tillgänglig](media/service-premium/available.png) |
| **Företagsdistribution till** _**alla användare**_ | | |
| Appar och delning |![Inte tillgänglig](media/service-premium/not-available.png) |![Tillgänglig](media/service-premium/available.png) |
| Inbäddad API och kontroller |![Inte tillgänglig](media/service-premium/not-available.png) |![Tillgänglig](media/service-premium/available.png)<sup>2</sup> |
| **Publicera Power BI-rapporter lokalt** |![Inte tillgänglig](media/service-premium/not-available.png) |![Tillgänglig](media/service-premium/available.png) |
| | | |

*<sup>1</sup> Mer information finns i avsnittet med [funktioner per licenstyp](service-features-license-type.md).*  
*<sup>2</sup> Framtida förbättringar för Power BI Premium.*

I [Hantera Power BI Premium](service-admin-premium-manage.md) finns mer information om hur du tilldelar arbetsytor till en Premium-kapacitet.

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Noder för premiumkapacitet

Power BI Premium är tillgängligt i nodkonfigurationer med kapaciteter för v-kärnor. Mer information om specifika SKU-erbjudanden och kostnader finns i [Priser för Power BI](https://powerbi.microsoft.com/pricing/). En [kostnadskalkylator](https://powerbi.microsoft.com/calculator/) är också tillgänglig. Mer information om kapacitetsplanering för inbäddade analyser finns i [Planera ett white paper för Power BI-företagsdistribution](https://aka.ms/pbienterprisedeploy). Sammanfattning:

* P-noder kan användas för inbäddade distributioner eller tjänstedistributioner.

* EM-noder kan endast användas för inbäddade distributioner. EM-noder saknar åtkomst till premiumfunktioner, till exempel att dela appar till användare som inte har någon Power BI Pro-licens.

>[!NOTE]
>Länkarna i den här tabellen fungerar endast korrekt för användare som har rollen som global administratör för Office 365. Andra får ett 404-fel.

| Kapacitetsnod | Totalt antal virtuella kärnor<br/>*(Serverdel + klientdel)* | Virtuella kärnor för serverdel | Virtuella kärnor för klientdel | DirectQuery/begränsningar vid liveanslutning | Max sidåtergivningar vid högbelastning | Tillgängligt |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (månad för månad)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 v-kärnor |0,5 v-kärna, 2,5 GB RAM |0.5 virtuella kärnor |3,75 per sekund |150-300 |Tillgänglig |
| [EM2 (månad för månad)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 v-kärnor |1 v-kärna, 5 GB RAM |1 v-kärnor |7,5 per sekund |301-600 |Tillgänglig |
| [EM3 (månad för månad)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 v-kärnor |2 v-kärnor, 10 GB RAM |2 v-kärnor | |601–1200 |Tillgänglig |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 v-kärnor |4 v-kärnor, 25 GB RAM |4 v-kärnor |30 per sekund |1 201–2 400 |Tillgängliga ([månad för månad](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1) är också tillgängligt) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 v-kärnor |8 v-kärnor, 50 GB RAM |8 v-kärnor |60 per sekund |2 401–4 800 |Tillgänglig |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 v-kärnor |16 v-kärnor, 100 GB RAM |16 v-kärnor |120 per sekund |4 801–9 600 |Tillgänglig |
| | | | | | | |

* Klientdelens virtuella kärnor ansvarar för webbtjänsten, instrumentpanel och hantering av rapportdokument, hantering av åtkomsträttigheter och schemaläggning av API:er, ladda upp och hämta filer, och vanligen för allt som rör användarupplevelsen.

* Serverdelens virtuella kärnor ansvarar för grovjobbet: frågebearbetning, hantering av cache, köra R-servrar, datauppdatering, bearbetning av naturligt språk, flöden i realtid och återgivning av rapporter och bilder från serversidan. Med serverdelens virtuella kärnor reserveras dessutom en viss mängd minne. Att ha tillräckligt med minne blir särskilt viktigt när du hanterar stora datamodeller eller ett stort antal aktiva datauppsättningar.

## <a name="workloads-in-premium-capacity"></a>Arbetsbelastningar i Premium-kapacitet

Tänk på en arbetsbelastning i Power BI som en av de många tjänster som du kan visa användarna. Som standard stöder kapaciteter för **Power BI Premium** och **Power BI Embedded** endast den arbetsbelastning som är associerad med Power BI-frågor som körs i molnet.

Vi erbjuder nu stöd för förhandsversioner av två ytterligare arbetsbelastningar: **Sidnumrerade rapporter** och **dataflöden**. Du aktiverar de här arbetsbelastningarna i Power BI-adminstrationsportalen eller via Power BI REST API. Du kan också ange maximalt minne varje arbetsbelastning kan använda, så att du kan styra hur de olika arbetsbelastningarna påverkar varandra. Mer information finns i [Konfigurera arbetsbelastningar](service-admin-premium-manage.md#configure-workloads).

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

Om du använder arbetsbelastningen för sidnumrerade rapporter bör du ha följande i åtanke.

* **Minnesallokering i sidnumrerade rapporter**: Med sidnumrerade rapporter kan du köra din egen kod vid rapportåtergivning (till exempel ändra textfärg dynamiskt baserat på innehåll). Det innebär att vi skyddar Power BI Premium-kapaciteten genom att köra sidnumrerade rapporter i ett inneslutet område inom kapaciteten. Vi tilldelar det maximala minne som du anger till det här området, oavsett om arbetsbelastningen är aktiv eller inte. Om du använder Power BI-rapporter eller dataflöden i samma kapacitet, bör du ange ett så lågt minne för de sidnumrerade rapporterna att det inte påverkar andra arbetsbelastningar negativt.

* **Sidnumrerade rapporter är inte tillgängliga**: I sällsynta fall kan arbetsbelastningen för sidnumrerade rapporter bli otillgänglig. I det här fallet visar arbetsbelastningen ett feltillstånd i administratörsportalen och användarna uppnår tidsgränser vid rapportåtergivning. För att lösa det här problemet kan du inaktivera arbetsbelastningen och sedan aktivera den igen.

## <a name="power-bi-report-server"></a>Power BI-rapportserver

Med Power BI Premium ingår också möjligheten att köra Power BI-rapportserver lokalt i din organisation. Läs mer i [Kom igång med Power BI-rapportserver](report-server/get-started.md).

## <a name="next-steps"></a>Nästa steg

[Vanliga frågor och svar om Power BI Premium](service-premium-faq.md)
[Så här köper du Power BI Premium](service-admin-premium-purchase.md)
[Hantera Power BI Premium](service-admin-premium-manage.md)
[White paper om Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
[Planera en företagsdistribution för Power BI (white paper)](https://aka.ms/pbienterprisedeploy)
[Administrera Power BI i din organisation](service-admin-administering-power-bi-in-your-organization.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
