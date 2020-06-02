---
title: Power BI för amerikanska myndighetskunder – Översikt
description: Amerikanska myndighetskunder kan lägga till en Power BI Pro-prenumeration till sitt Microsoft 365-myndighetsabonnemang. Lär dig hur du registrerar och granskar funktioners tillgänglighet i den här tjänstbeskrivningen.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/07/2020
ms.author: kfollis
LocalizationGroup: Get started
ms.openlocfilehash: 9f94d6a1b99bce40d3f901dd71877da3f6b236af
ms.sourcegitcommit: 5e5a7e15cdd55f71b0806016ff91256a398704c1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/22/2020
ms.locfileid: "83792890"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI för amerikanska myndighetskunder
Den här artikeln är till för amerikanska myndighetskunder som distribuerar Power BI som en del av ett Microsoft 365-myndighetsabonnemang. Myndighetsabonnemang är utformade för de unika behoven hos organisationer som måste uppfylla amerikanska efterlevnads- och säkerhetsstandarder. Den Power BI-tjänst som har utformats för amerikanska myndighetskunder skiljer sig från den kommersiella versionen av Power BI-tjänsten. Dessa funktionsskillnader och funktioner beskrivs i följande avsnitt.

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>Lägga till Power BI i ditt Microsoft 365-myndighetsabonnemang

Innan du kan få en Power BI-prenumeration för amerikanska myndigheter och tilldela licenser till användare, måste du registrera dig för ett Microsoft 365-myndighetsabonnemang. Om din organisation redan har ett Microsoft 365-myndighetsabonnemang kan du gå vidare till [Köpa en Power BI Pro-prenumeration](#buy-a-power-bi-pro-subscription-for-government-customers).

### <a name="enroll-in-a-microsoft-365-government-plan"></a>Registrera dig för ett Microsoft 365-myndighetsabonnemang

Om du är en ny kund måste du verifiera organisationens behörighet innan du kan registrera dig för ett Microsoft 365-myndighetsabonnemang.  Kom igång genom att fylla i [kvalificeringsformuläret för Microsoft 365-myndighetsabonnemang](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Försäkra dig om att du väljer rätt abonnemang för din organisation genom att läsa [Tjänstbeskrivning för Microsoft 365 för amerikanska myndigheter](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Om du redan har distribuerat Power BI i en kommersiell miljö och vill migrera till molnet för amerikanska myndigheter, måste du lägga till en ny Power BI Pro-prenumeration till ditt Microsoft 365-myndighetsabonnemang. Sedan replikerar du dina kommersiella data till Power BI-tjänsten för amerikanska myndigheter, tar bort kommersiella licenstilldelningar från användarkonton och tilldelar sedan användarkontona en Power BI Pro-myndighetslicens.
>
>
## <a name="government-cloud-instances"></a>Molninstanser för amerikanska myndigheter
Microsoft 365 erbjuder olika miljöer för myndigheter för att uppfylla olika krav på efterlevnad. Mer information om varje miljö finns i:

* [Microsoft 365 Government Community Cloud (GCC)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) är utformat för federala, statliga och lokala myndigheter.

* [Microsoft 365 Government Community Cloud High (GCC-High)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) har utformats för federala myndigheter, försvaret, flygbranschen och andra organisationer som innehar kontrollerad, ej hemligstämplad information. Den här miljön lämpar sig för nationella säkerhetsorganisationer och företag med ITAR-data (International Traffic in Arms Regulations) eller DFARS-krav (Defense Federal Acquisition Regulations Supplement).

* [Microsoft 365 DoD-miljön](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) är utformat uteslutande för USA:s försvarsdepartement. 

## <a name="connect-to-power-bi-for-us-government"></a>Ansluta till Power BI för amerikanska myndigheter

URL:en för att ansluta till Power BI skiljer sig åt för myndighetsanvändare och kommersiella användare. Om du vill logga in på Power BI använder du följande URL:er:

| Kommersiell version  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

Ditt konto kan ha konfigurerats i mer än ett moln. Om ditt konto har konfigurerats på det viset, så kan du välja vilket moln du ska ansluta till när du loggar in till Power BI Desktop.

## <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>Köp en Power BI Pro-prenumeration för myndighetskunder

När du har distribuerat Microsoft 365 kan du lägga till en Power BI Pro-prenumeration. Följ den stegvisa vägledningen i [Registrera din amerikanska myndighetsorganisation](service-govus-signup.md) när du ska köpa Power BI Pro-myndighetstjänsten. Köp tillräckligt många licenser för alla användare som behöver använda Power BI och tilldela sedan enskilda användarkonton dessa licenser.

> [!IMPORTANT]
> Power BI för amerikanska myndigheter är inte tillgängligt som en *kostnadsfri* licens. Varje användare måste tilldelas en *Pro*-licens för att få åtkomst till Government Community Cloud. Om ett användarkonto har tilldelats en kostnadsfri licens har användaren bara åtkomst till det kommersiella molnet och kommer att stöta på autentiserings- och åtkomstproblem. Om du har köpt Power BI Premium behöver du inte tilldela Pro-licenser för att aktivera användaråtkomst.  Alla användare i organisationen har åtkomst till rapporter som delas med dem så länge som rapporterna publiceras till en Premium-kapacitet. Information om man granskar skillnaderna mellan licenstyper finns i [Power BI-tjänstefunktioner efter licenstyp](../fundamentals/service-features-license-type.md).
>

## <a name="connect-government-and-global-azure-cloud-services"></a>Anslut myndighetstjänster och Azure-molntjänster

Azure distribueras i flera moln. Som standard kan du aktivera brandväggsregler för att öppna en anslutning till en molnbaserad instans, men molntäckande nätverk skiljer sig åt.  Om du vill kommunicera mellan tjänster i det offentliga molnet och tjänster i Government Community Cloud måste du konfigurera särskilda brandväggsregler. Om du exempelvis vill ha åtkomst till offentliga molninstanser för en SQL-databas från myndighetens molndistribution av Power BI, så behöver du en brandväggsregel i SQL-databasen. Konfigurera specifika brandväggsregler för SQL-databser som tillåter anslutningar till Azure Government Cloud för följande datacentra:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

IP-intervall är tillgängliga i det offentliga molnet. Om du vill hämta IP-intervall för amerikanska myndigheters moln laddar du ned filen [IP-intervall och tjänsttaggar för Azure – US Government-moln](https://www.microsoft.com/download/details.aspx?id=57063). 

Information om hur man konfigurerar brandväggar för SQL-databaser finns i [Skapa och hantera IP-brandväggsregler](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Tillgänglighet för Power BI-funktioner

För att tillgodose kraven hos molnkunder på myndigheter finns det vissa skillnader mellan myndighetsabonnemang och kommersiella abonnemang. I följande tabell visas vilka funktioner som är tillgängliga i respektive myndighetsmiljö.

|Funktion |   |GCC |GCC High |DoD|
|------|------|------|------|------|
|Administration|Kostnadsfria licenser|Inte tillgänglig|Inte tillgänglig|Inte tillgänglig|
|  |Fasta gränser för lagringsutrymme|Tillgänglig|Tillgänglig|Tillgänglig|
|  |Använda Active Directory-grupper för delning och åtkomstkontroll|Tillgänglig|Tillgänglig|Tillgänglig|
|  |Granskning via Office 365 Administrationscenter för säkerhet och efterlevnad|Tillgänglig|Tillgänglig|Tillgänglig|
|  |Delning med extern användare|Tillgänglig|Tillgänglig|Tillgänglig|
|  |Användningsstatistik för rapporter och instrumentpaneler|Inte tillgänglig|Inte tillgänglig|Inte tillgänglig|
|  |Azure B2B mellan GCC och kommersiellt moln|Inte tillgänglig|Inte tillgänglig|Inte tillgänglig|
|Skapa rapport|Skapa och visa instrumentpaneler och rapporter|Tillgänglig|Tillgänglig|Tillgänglig|
|  |Schemalagd datauppdatering|Tillgänglig|Tillgänglig|Tillgänglig|
|  |Uppdateringsbara teaminstrumentpaneler|Tillgänglig|Tillgänglig|Tillgänglig|
|  |Sidnumrerade rapporter|Tillgänglig|I planeringsstadiet|I planeringsstadiet|
|  |Mallappar|Inte tillgänglig|Inte tillgänglig|Inte tillgänglig|
|Ansluta till data|Importera data och rapporter från Excel|Tillgänglig|Tillgänglig|Tillgänglig|
|  |Importera data från CSV-filer|Tillgänglig|Tillgänglig|Tillgänglig|
|  |Importera data från Power BI Desktop-filer|Tillgänglig|Tillgänglig|Tillgänglig|
|  |Anslutning till CDS|Tillgänglig|Inte tillgänglig|Inte tillgänglig|
|  |Azure Data Lake Storage Gen2-anslutning|Tillgänglig|Inte tillgänglig|Inte tillgänglig|
|Datahantering|Gateway för datahantering|Tillgänglig|Tillgänglig|Tillgänglig|
|  |Datakryptering i Azure SQL Database|Tillgänglig|Tillgänglig|Tillgänglig|
|  |Datakryptering i Blob Storage för Power BI|Tillgänglig|Tillgänglig|Tillgänglig|
|Integrering mellan produkter|Bädda in i SharePoint Online med hjälp av Power BI:s webbdel|Inte tillgänglig|Inte tillgänglig|Inte tillgänglig|
|  |Bädda in i SharePoint Online med hjälp av Bädda in webbdel|Tillgänglig|Tillgänglig|Tillgänglig|
|  |Dataflöden-och AI-funktioner|Inte tillgänglig|Inte tillgänglig|Inte tillgänglig|
|  |Power Automate-anslutning för datadrivna aviseringar|Inte tillgänglig|Inte tillgänglig|Inte tillgänglig|
|  |Fliken Power BI i Teams|Tillgänglig|Inte tillgänglig|Inte tillgänglig|
|  |Automatiserad maskininlärning|Inte tillgänglig|Inte tillgänglig|Inte tillgänglig|
|  |Azure Cognitive Services|Inte tillgänglig|Inte tillgänglig|Inte tillgänglig|
|  |Azure Machine Learning|Inte tillgänglig|Inte tillgänglig|Inte tillgänglig|

## <a name="next-steps"></a>Nästa steg

* [Registrera dig för Power BI för amerikanska myndigheter](service-govus-signup.md)
* [Microsoft Power Apps US Government](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](https://docs.microsoft.com/power-automate/us-govt)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Demonstration av Power BI för amerikanska myndigheter</a>
