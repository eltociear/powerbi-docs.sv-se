---
title: Power BI för myndigheter i USA – översikt
description: För USA. Mer information om funktioner och begränsningar för Power BI-tjänsten för amerikanska myndigheter
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: f14734f168abca1003bd5b6c773c4c70daf53d15
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75762104"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI för amerikanska myndighetskunder
**Power BI-tjänsten** har en version som är tillgänglig för amerikanska myndigheter som en del av **Office 365 US Government Community**-prenumerationer. Den version av **Power BI-tjänsten** som beskrivs i den här artikeln är utformad för kunder som tillhör amerikanska myndigheter och är separat och skiljer sig från kommersiella versioner av **Power BI-tjänsten**.

![](media/service-govus-overview/service_usgov_overview-1.png)

I följande avsnitt beskrivs de *funktioner* som är tillgängliga för i den version av **Power BI-tjänsten** som är avsedd för amerikanska myndigheter. Här klargörs även några av *begränsningarna*, här finns en lista med vanliga frågor och svar (**FAQ**), (även sådana om hur man registrerar sig) och länkar till mer information.

## <a name="features-of-power-bi-us-government"></a>Funktioner i Power BI-versionen för amerikanska myndigheter
Det är viktigt att tänka på att **Power BI för amerikanska myndigheter** endast är endast tillgänglig som en **Pro-licens**, och inte som en kostnadsfri licens. Vissa funktioner i Power BI-tjänsten är tillgängliga i den version av **Power BI** som är avsedd för amerikanska myndigheter.

Följande funktioner är tillgängliga för dem som använder **Power BI för amerikanska myndigheter**, då de även gäller **Pro**-licensfunktioner:

* Skapa och visa instrumentpaneler och rapporter
* [Datakapacitetsbegränsningar](service-admin-manage-your-data-storage-in-power-bi.md)
* [Schemalagd datauppdatering](refresh-data.md)
* Uppdateringsbara teaminstrumentpaneler
* Active Directory-grupper för delning och hantering av åtkomstkontroll
* [Importera data](service-get-data.md) och rapporter från Excel, CSV och Power BI Desktop-filer
* Data Management Gateway
* Alla data krypteras i Azure SQL- och Blob Storage för Power BI
* Ansluta till tjänster med [innehållspaket](service-connect-to-services.md)

## <a name="connectivity-between-government-and-global-azure-cloud-services"></a>Anslutningen mellan myndigheter och globala Azure-molntjänster 

Azure distribueras i flera moln. Som standard kan klientorganisationer öppna brandväggsregler till en molnspecifik instans, men nätverk mellan moln är annorlunda och kräver att du öppnar specifika brandväggsregler för kommunikation mellan tjänster. Om du är en Power BI-kund och du har befintliga SQL-instanser i det offentliga molnet som du behöver komma åt, måste du öppna specifika brandväggsregler IP-adressutrymmet för SQL till Azure Government-molnet för följande datacenter:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

IP-intervall är tillgängliga i det offentliga molnet. Du kan läsa den senaste informationen för Government-molnet i den nedladdningsbara [dokumentationen för Azure Government-tjänsten](https://www.microsoft.com/download/details.aspx?id=57063).

## <a name="limitations-of-power-bi-us-government"></a>Begränsningar av Power BI-versionen för amerikanska myndigheter
Några av de funktioner som är tillgängliga i den kommersiella versionen av **Power BI-tjänsten** är *inte* tillgängliga i **Power BI-tjänsten** för amerikanska myndigheter. Power BI-teamet arbetar aktivt med att göra dessa funktioner tillgängliga för kunder som tillhör amerikanska myndigheter och kommer att uppdatera den här artikeln när dessa funktioner blir tillgängliga.

* **Bädda in i SharePoint Online** – det går inte att bädda in innehåll i SharePoint Online med hjälp av Power BI-webbdelen. Dock fungerar inte Secure embed med webbdelen [*Bädda in*](https://docs.microsoft.com/power-bi/service-embed-secure). Du måste lägga till *app.powerbigov.us* i listan över undantag. Det gör du genom att följa anvisningarna i artikeln [Allow or restrict the ability to embed content on SharePoint pages](https://support.office.com/article/allow-or-restrict-the-ability-to-embed-content-on-sharepoint-pages-e7baf83f-09d0-4bd1-9058-4aa483ee137b) (Tillåta eller begränsa möjligheten att bädda in innehåll på SharePoint-sidor).
* **Power BI för amerikanska myndigheter** är endast tillgängligy som en **Pro**-licens. Alla referenser till kostnadsfria Power BI-licenser i en administrationsportal (eller som användare) körs i ett kommersiellt Power BI-tjänstmoln.
* **Granskning** – nu är granskning tillgängligt via Office 365-portalen för säkerhet och regelefterlevnad (från juni 2018).
* **Extern användardelning** – delning är tillåtet inom en Power BI-klientorganisation, och från juni 2018 kan du även dela med användare utanför din Power BI-klientorganisation. Läs mer i [Distribuera Power BI-innehåll till externa gästanvändare med Azure Active Directory B2B](service-admin-azure-ad-b2b.md).
* **Användningsstatistik för instrumentpaneler och rapporter** – användningsstatistik är inte tillgängligt för rapporter och instrumentpaneler. Kunder kan använda data i granskningsloggar för att få användningsinformation om innehåll i deras organisation.
* **Dataflöden** – Dataflöden är inte tillgängliga.
* **Sidnumrerade rapporter** – Sidnumrerade rapporter är för närvarande bara tillgängliga i USGov Virginia.  Vi planerar att införa stöd i USGov Texas, men det är inte färdigt ännu.
* Du kan bara bädda in Power BI-innehåll från GCC (Government Community Cloud) med en Office 365-SKU. GCC High-kunder kan använda [Office 365- eller Azure-SKU:er](developer/embedded-faq.md#what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365).

Om du har kostnadsfria **Power BI**-licenser som tilldelats ditt konto, körs dessa konton i en kommersiell version av **Power BI**-tjänsten, och ingår inte i erbjudandet om **Power BI för amerikanska myndigheter**. För dessa kostnadsfria konton kan följande problem uppstå:

* Gateway, Mobile och Desktop kan inte autentisera
* Du har inte åtkomst till kommersiella Azure-datakällor
* PBIX filer måste överföras manuellt
* Power BI-mobilappar är inte tillgängliga

Lös problemen genom att kontakta din kontorepresentant.

## <a name="frequently-asked-questions-faq-for-the-us-government-version-of-the-power-bi-service"></a>Vanliga frågor (FAQ) för US Government-versionen av Power BI-tjänsten
Följande frågor (och svar) hjälper dig att snabbt få information som du behöver om tjänsten.

**Fråga:** Hur migrerar jag mina **Power BI**-affärsdata till **Power BI-tjänsten** för amerikanska myndigheter?

**Svar:** Din administratör måste skapa en ny instans av **Power BI** under en separat prenumeration som är specifik för amerikanska myndigheter. Sedan kan du replikera dina affärsdata i **Power BI-tjänsten** för amerikanska myndigheter, ta bort din kommersiella licens och associera din befintliga domän till den nya myndighetsspecifika tjänsten.

**Fråga:** Varför kan jag inte ansluta till ett specifikt innehållspaket?

**Svar:** Du måste kontrollera att prenumerationen har aktiverats innan du ansluter till innehållspaketet.

**Fråga:** Jag är intresserad av **Power BI** för min myndighetsorganisation. Hur kommer jag igång?

**Svar:** Registrering (ofta kallat *integration*) kan variera beroende på din befintliga licens och prenumeration. Mer information finns i artikeln [Registrera dig för Power BI US Government](service-govus-signup.md).

**Fråga:** Skiljer sig URL:en för att ansluta till **Power BI** för amerikanska myndigheter Government från URL:en för den kommersiella versionen av **Power BI**? Finns det en annan URL för GCC High-kunderna (Government Community Cloud High)?

**Svar:** Ja, URL:erna skiljer sig åt. I följande tabell visas varje URL:

| URL för den kommersiella versionen | URL för US Government-versionen | URL för amerikanska myndigheter för GCC High |
| --- | --- | --- |
| https://app.powerbi.com/ |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) |

**Fråga:** Mitt konto är etablerat i mer än ett nationellt moln. Hur väljer jag vilket moln jag ska ansluta till när jag använder **Power BI Desktop**?

**Svar:** Från och med **Power BI Desktop**-versionen från juli 2018 kan du välja vilket moln du vill använda när du loggar in till **Power BI Desktop**.


## <a name="next-steps"></a>Nästa steg
Det finns olika typer av saker du kan göra med Power BI. Mer information och utbildning, inklusive en artikel som visar hur du registrerar dig för tjänsten, hittar du i följande resurser:

* [Registrera dig för Power BI för amerikanska myndigheter](service-govus-signup.md)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Demonstration av Power BI för amerikanska myndigheter</a>
* [Guidad utbildning för Power BI](guided-learning/index.yml)
* [Komma igång med Power BI-tjänsten](service-get-started.md)
* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)

