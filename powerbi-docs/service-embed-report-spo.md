---
title: Bädda in med rapportwebbdel i SharePoint Online
description: Med den nya rapportwebbdelen för SharePoint Online i Power BI kan du enkelt bädda in interaktiva Power BI-rapporter i SharePoint Online-sidor.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 05/16/2019
ms.openlocfilehash: c8789d47ed1b67f9fd6808865514120457a29dfe
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051275"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Bädda in med rapportwebbdel i SharePoint Online

Med den nya rapportwebbdelen för SharePoint Online i Power BI kan du enkelt bädda in interaktiva Power BI-rapporter i SharePoint Online-sidor.

När du använder den nya **bädda in i SharePoint Online** alternativet, inbäddade rapporter är helt säkra, så du kan enkelt skapa säkra interna portaler.

## <a name="requirements"></a>Krav

För **bädda in i SharePoint Online** rapporterna ska fungera, krävs följande:

* En Power BI Pro-licens eller en [Power BI Premium-kapacitet (EM eller P SKU)](service-premium-what-is.md) med en Power BI-licens.
* Power BI-webbdelen för SharePoint Online kräver [moderna sidor](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b).

## <a name="embed-your-report"></a>Bädda in rapporten
Om du vill bädda in rapporten i SharePoint Online måste du hämta URL: en för rapporten och använda den med SharePoint Online nya Power BI-webbdelen.

### <a name="get-a-report-url"></a>Få en rapport-URL

1. Visa rapporten i Power BI.

2. Välj den **filen** och välj sedan **bädda in i SharePoint Online**.

    ![Filmenyn](media/service-embed-report-spo/powerbi-file-menu.png)

3. Kopiera rapport-URL: en från dialogrutan.

    ![Bädda in länk](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Lägga till en Power BI-rapport på en SharePoint Online-sida

1. Öppna sidan i SharePoint Online och välj **redigera**.

    ![SP-redigeringssida](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    Välj i Sharepoint Online, **+ ny** att skapa en ny modern webbplats.

    ![Ny SP-sida](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Välj den **+** listrutan och välj sedan den **Power BI**.

    ![Ny SP-webbdel](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Välj **Lägg till rapport**.

    ![Ny SP-rapport](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. Klistra in tidigare kopierade rapport-URL: en i den **Power BI-Rapportlänk** fönstret. Rapporten läses in automatiskt.

    ![Nya SP-webbdelsegenskaper](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Välj **Publicera** så att ändringen visas för användarna i SharePoint Online.

    ![SP-rapport inläst](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>Bevilja åtkomst till rapporter

Bädda in en rapport i SharePoint Online inte automatiskt ge användare behörighet att visa rapporten – du måste ange visningsbehörigheter i Power BI.

> [!IMPORTANT]
> Se till att granska vem som kan visa rapporten i Power BI-tjänsten och bevilja åtkomst till de som inte visas i listan.

Det finns två sätt att ge åtkomst till rapporten i Power BI. Det första sättet, om du använder en Office 365-grupp för att skapa din SharePoint Online-gruppwebbplats, är att lista användaren som en medlem i den **apparbetsytan i Power BI-tjänsten** och **SharePoint-sida**. Mer information finns i [hantera en apparbetsyta](service-manage-app-workspace-in-power-bi-and-office-365.md).

Det andra sättet är att bädda in en rapport i en app och dela den direkt med användare:  

1. Författaren (måste vara en Pro-användare) skapar en rapport i en apparbetsyta. Dela med **kostnadsfria Power BI-användare**, app-arbetsytan måste anges som en **Premium-arbetsyta**.

2. Författaren publicerar appen och installerar den. Författaren måste se till att installera appen för att ha åtkomst till den rapport-URL som används för att bädda in i SharePoint Online.

3. Nu måste även alla slutanvändare installera appen. Du kan också använda den **installera appen automatiskt** funktion som du kan aktivera på den [Power BI-administratörsportalen](service-admin-portal.md), ha appen förinstallerade för slutanvändare.

   ![Installera appen automatiskt](media/service-embed-report-spo/install-app-automatically.png)

4. Författaren öppnar appen och går till rapporten.

5. Författaren kopierar bädda in rapporten URL: en från rapporten appen är installerad. **Använd inte den ursprungliga rapport-URL: en från apparbetsytan.**

6. Skapa en ny gruppwebbplats i SharePoint Online.

7. Lägg till URL: en för tidigare kopierade rapporten i Power BI-webbdelen.

8. Lägg till alla användare och/eller grupper som ska använda data på SharePoint Online-sidan och i Power BI-appen som du skapade.

    > [!NOTE]
    > **Användare eller grupper behöver åtkomst till såväl sidan SharePoint Online som rapporten i Power BI-appen för att visa rapporten på SharePoint-sidan.**

Användaren kan nu gå till gruppwebbplatsen i SharePoint Online och visa rapporter på sidan.

## <a name="multi-factor-authentication"></a>Multifaktorautentisering

Om din Power BI-miljö kräver att du loggar in med multifaktorautentisering kan du uppmanas att logga in med en säkerhetsenhet för att verifiera din identitet. Det här inträffar om du inte logga in på SharePoint Online med hjälp av multifaktorautentisering, men din Power BI-miljö kräver en säkerhetsenhet för att verifiera ett konto.

> [!NOTE]
> Azure Active Directory 2.0 stöder inte Multi factor authentication - användare ser ett felmeddelande. Om användaren loggar in igen på SharePoint Online med hjälp av en säkerhetsenhet kan denne eventuellt visa rapporten.

## <a name="web-part-settings"></a>Inställningar för webbdel

Nedan visas de inställningar som du kan ändra för Power BI-webbdelen för SharePoint Online.

![SP-webbdelsegenskaper](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Egenskap | Beskrivning |
| --- | --- |
| Sidnamn |Anger webbdelens standardsidan. Välj ett värde från listrutan. Om inga sidor visas innehåller rapporten endast en sida eller också innehåller URL:en du klistrade in ett sidnamn. Ta bort rapportdelen av URL:en för att välja en specifik sida. |
| Skärm |Justerar hur rapporten passar in i SharePoint Online-sidan. |
| Visa navigeringsfönstret |Visar eller döljer navigeringsfönstret. |
| Visa filtreringsfönstret |Visar eller döljer filtreringsfönstret. |

## <a name="reports-that-do-not-load"></a>Rapporter som inte kan läsas in

Om rapporten inte läsa in i Power BI-webbdelen kan du se följande meddelande:

![Det här innehållet är inte tillgängliga meddelande](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Det finns två vanliga orsaker till det här meddelandet.

1. Du har inte åtkomst till rapporten.
2. Rapporten har tagits bort.

Kontakta sidan SharePoint Online ägaren för att hjälpa dig att lösa problemet.

## <a name="licensing"></a>Licensiering

Användare som visar en rapport i SharePoint måste antingen ha en **Power BI Pro-licens** eller så måste innehållet finnas på en arbetsyta som är i en  **[Power BI Premium-kapacitet (EM eller P SKU)](service-admin-premium-purchase.md)** .

## <a name="known-issues-and-limitations"></a>Kända problem och begränsningar

* Fel: "Ett fel har uppstått. Försök att logga ut och in igen och gå sedan tillbaka till den här sidan. Korrelations-ID: odefinierat, http-svarsstatus: 400, serverfelskod 10001, meddelande: Uppdateringstoken saknas"
  
  Testa något av felsökningsstegen nedan om du får detta felmeddelande.
  
  1. Logga ut från SharePoint och logga in igen. Glöm inte att stänga alla webbläsarfönster innan du loggar in igen.

  2. Om ditt konto kräver multifaktorautentisering (MFA), sedan logga in på SharePoint med enheten MFA (telefonapp, smartkort, osv.).
  
  3. Gästanvändares konton för Azure B2B stöds inte. Användarna ser Power BI-logotypen som visas när en del blir inläst, men rapporten visas inte.

* Power BI stöder inte samma språk som SharePoint Online. Det innebar att den inbäddade rapporten kanske inte är helt lokaliserad.

* Problem kan också uppstå om du använder Internet Explorer 10. Du kan titta på [webbläsarstöd för Power BI](consumer/end-user-browsers.md) och [Office 365](https://products.office.com/office-system-requirements#Browsers-section).

* Power BI-webbdelen är inte tillgänglig i [nationella moln](https://powerbi.microsoft.com/clouds/).

* Klassiska SharePoint Server stöds inte med den här webbdelen.

* [URL-filter](service-url-filters.md) stöds inte med SPO-webbdelen.

## <a name="next-steps"></a>Nästa steg

* [Tillåt eller förhindra att moderna webbplatssidor skapas av slutanvändare](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [Skapa och distribuera en app i Power BI](service-create-distribute-apps.md)  
* [Dela en instrumentpanel med kollegor och andra](service-share-dashboards.md)  
* [Vad är Power BI Premium?](service-premium-what-is.md)
* [Bädda in en rapport på en säker portal eller webbplats](service-embed-secure.md)

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)