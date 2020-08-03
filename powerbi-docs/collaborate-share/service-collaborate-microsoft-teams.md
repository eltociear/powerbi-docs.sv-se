---
title: Samarbeta i Microsoft Teams med Power BI
description: Du kan enkelt dela och samarbeta med interaktivt Power BI-innehåll i Microsoft Teams kanaler och chattar.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 07/22/2020
ms.openlocfilehash: 17a0879dac416a98d214ed11861947cb2c311487
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87254218"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>Samarbeta i Microsoft Teams med Power BI

Du har flera alternativ för delning och samarbete med interaktivt Power BI-innehåll i Microsoft Teams kanaler och chattar. 

- Med **Power BI**-fliken för Microsoft Teams kan du [bädda in interaktiva rapporter i Microsoft Teams](service-embed-report-microsoft-teams.md) kanaler och chattar. **Power BI**-fliken hjälper dina kollegor att hitta teamets data och diskutera data i dina teamkanaler. 
- Skapa en [länkförhandsvisning](service-teams-link-preview.md) när du klistrar in en länk till dina rapporter, instrumentpaneler och appar i rutan för Microsoft Teams-meddelande. I länkförhandsvisningen visas information om länken. 
- Använd [Dela till Teams](service-share-report-teams.md) när du visar rapporter och instrumentpaneler i Power BI-tjänsten för att snabbt starta konversationer i Teams.
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="Skärmbild av en Power BI-rapport inbäddad i en Teams-kanal.":::

## <a name="requirements"></a>Krav

För att Power BI ska fungera i Microsoft Teams ska du i allmänhet säkerställa att följande gäller:

- Dina användare har en Power BI Pro-licens, eller att rapporten ligger i en [Power BI Premium-kapacitet (SKU:n EM eller P)](../admin/service-premium-what-is.md) med en Power BI-licens.
- Användaren har loggat in i Power BI-tjänsten och aktiverat sin Power BI-licens.
- Användaren uppfyller kraven för att använda **Power BI**-fliken i Microsoft Teams.

Säkerställ följande element om du vill använda **Power BI**-fliken i Microsoft Teams:

- Microsoft Teams har **Power BI**-fliken.
- För att kunna lägga till en rapport i Microsoft Teams med **Power BI**-fliken måste du ha minst en Deltagare-roll på arbetsytan där rapporten ska vara. Information om de olika rollerna finns i [Roller i de nya arbetsytorna](service-new-workspaces.md#roles-in-the-new-workspaces).
- För att kunna visa rapporten på **Power BI**-fliken i Microsoft Teams måste användarna ha behörighet att visa rapporten.
- Användare måste vara Microsoft Teams-användare med åtkomst till kanaler och chattar.

Kontrollera denna inställning om du vill använda funktionerna för **Dela till Teams** i Power BI:

- Power BI-administratörer har inte inaktiverat klientinställningen **Dela till Teams** i Power BI-administratörsportalen. Med den här inställningen kan organisationer dölja knapparna för **Dela till Teams**. Mer information finns i artikeln [Power BI-administratörsportalen](../admin/service-admin-portal.md#share-to-teams-tenant-setting).

## <a name="grant-access-to-reports"></a>Bevilja åtkomst till rapporter

När du bäddar in en rapport i Microsoft Teams eller skickar en länk till ett objekt får inte användarna automatiskt behörighet att visa rapporten. Du måste [tillåta att användare visar rapporten i Power BI](service-share-dashboards.md). Du kan använda en Microsoft 365-grupp för ditt team så att det blir enklare.

> [!IMPORTANT]
> Se till att granska vem som kan visa rapporten i Power BI-tjänsten och bevilja åtkomst till de som inte visas i listan.

Ett sätt att se till att alla i teamet har åtkomst till rapporterna är att placera rapporterna på en enda arbetsyta i och ge Microsoft 365-gruppen för ditt team åtkomst.

## <a name="known-issues-and-limitations"></a>Kända problem och begränsningar

- Power BI har inte stöd för samma lokaliserade språk som i Microsoft Teams. Det kan innebära att den inbäddade rapporten inte är helt lokaliserad.
- Du kan inte bädda in Power BI-instrumentpaneler på **Power BI**-fliken för Microsoft Teams.
- Användare utan någon Power BI-licens eller behörighet att visa rapporten ser meddelandet Innehållet inte är tillgängligt.
- Du kan uppleva problem om du använder Internet Explorer 10. <!--You can look at the [browsers support for Power BI](../consumer/end-user-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- [URL-filter](service-url-filters.md) stöds inte på **Power BI**-fliken för Microsoft Teams.
- I nationella moln är den nya **Power BI**-fliken inte tillgänglig. Det kan finnas en äldre version som inte stöder den nya arbetsytemiljön eller rapporter i Power BI.
- När du har sparat fliken kan du inte ändra namnet på fliken via flikinställningarna. Använd alternativet **Byt namn** för att ändra det.
- Enkel inloggning stöds inte för tjänsten för länkförhandsvisning.
- Länkförhandsvisningar fungerar inte i möteschattar eller privata kanaler.

## <a name="next-steps"></a>Nästa steg

- [Bädda in Power BI-innehåll i Microsoft Teams](service-embed-report-microsoft-teams.md)
- [Hämta en Power BI-länkförhandsvisning i Microsoft Teams](service-teams-link-preview.md)
- [Dela direkt till Teams från Power BI-tjänsten](service-share-report-teams.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/).
