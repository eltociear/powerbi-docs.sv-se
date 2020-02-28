---
title: Bädda in en rapport via fliken Power BI för Microsoft Teams
description: På fliken Power BI för Microsoft Teams kan du enkelt bädda in interaktiva rapporter i kanaler och chattar.
author: LukaszPawlowski-MS
ms.author: lukaszp
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 01/31/2020
ms.openlocfilehash: fb4846a777dda4787e1ed0be7de869367a616ea5
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530497"
---
# <a name="embed-report-with-the-power-bi-tab-for-microsoft-teams"></a>Bädda in en rapport via fliken Power BI för Microsoft Teams

På den uppdaterade fliken Power BI för Microsoft Teams kan du enkelt bädda in interaktiva rapporter i kanaler och chattar i Microsoft Teams.

Använd fliken Power BI för Microsoft Teams till att hjälpa dina kollegor att hitta de data som teamet använder och till att diskutera data i dina Teams-kanaler.

## <a name="requirements"></a>Krav

För att fliken **Power BI för Microsoft Teams** ska fungera behöver du följande:

- en Power BI Pro-licens, eller att rapporten ligger i en [Power BI Premium-kapacitet (SKU:n EM eller P)](service-premium-what-is.md) med en Power BI-licens.
- Fliken Power BI för Microsoft Teams
- Användaren måste kunna logga in i Power BI-tjänsten och aktivera sin Power BI-licens för att kunna använda rapporten.
- Användaren måste ha behörighet att visa rapporten.

## <a name="embed-your-report"></a>Bädda in rapporten
Om du vill bädda in rapporten i en kanal eller chatt i Microsoft Teams lägger du till den enligt beskrivningen nedan.

1. Öppna önskad kanal eller chatt i Microsoft Teams och välj ikonen **+** .

    ![Lägg till en flik i en kanal eller chatt](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

2. Välj fliken Power BI.

    ![Fliklistan i Microsoft Teams med Power BI](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

3. Använd alternativen som finns för att välja en rapport från en arbetsyta, en rapport som delats med dig eller från en Power BI-app

    ![Inställningar för fliken Power BI för Microsoft Teams](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

4. Namnet på fliken uppdateras automatiskt så att det matchar rapportnamnet, men du kan ändra det. 

5. Tryck på **Spara**.

## <a name="supported-reports"></a>Rapporter som stöds

Du kan bädda in följande rapporter på fliken:

- Interaktiva och sidnumrerade rapporter
- Rapporter från Min arbetsyta, den nya arbetsytemiljön och från klassiska arbetsytor
- Rapporter i Power BI-appar


## <a name="grant-access-to-reports"></a>Bevilja åtkomst till rapporter

När du bäddar in rapporter i Microsoft Teams får inte användarna automatiskt behörighet att visa rapporten – du måste [ge användarna tillåtelse att visa rapporten i Power BI](service-share-dashboards.md). Du kan använda en Office 365-grupp för ditt team så att det blir enklare. 

> [!IMPORTANT]
> Se till att granska vem som kan visa rapporten i Power BI-tjänsten och bevilja åtkomst till de som inte visas i listan.

Ett sätt att se till att alla i teamet har åtkomst till de rapporter du bäddar in är att placera dem på en enda arbetsyta i Power BI och ge Office 365-gruppen åtkomst till arbetsytan.

## <a name="known-issues-and-limitations"></a>Kända problem och begränsningar

- Power BI har inte stöd för samma språk som i Microsoft Teams. Det innebar att den inbäddade rapporten kanske inte är helt lokaliserad.
- Du kan inte bädda in Power BI-instrumentpaneler på fliken Power BI för Microsoft Teams.
- Användare utan någon Power BI-licens eller behörighet till rapporten ser ett meddelande om att innehållet inte är tillgängligt.
- Problem kan också uppstå om du använder Internet Explorer 10. <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- [URL-filter](service-url-filters.md) stöds inte på fliken Power BI för Microsoft Teams.
- Fliken Power BI är inte tillgänglig i nationella moln. Det kan finnas en äldre version tillgänglig som inte har stöd för den nya arbetsytemiljön eller rapporter i Power BI-appar. 
- När du har sparat fliken kan du inte ändra namnet på den via flikinställningarna. Använd alternativet Byt namn för att ändra det.

## <a name="next-steps"></a>Nästa steg
- [Dela en instrumentpanel med kollegor och andra](service-share-dashboards.md)  
- [Skapa och distribuera en app i Power BI](service-create-distribute-apps.md)  
- [Vad är Power BI Premium?](service-premium-what-is.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
