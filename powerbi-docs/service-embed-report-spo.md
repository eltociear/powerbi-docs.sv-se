---
title: Bädda in en rapportwebbdel i SharePoint Online
description: Med den nya rapportwebbdelen för SharePoint Online i Power BI kan du enkelt bädda in interaktiva Power BI-rapporter i SharePoint Online-sidor.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 04/27/2020
ms.openlocfilehash: 5b726137fae0087701833b2d713cf7b5a329f899
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82585236"
---
# <a name="embed-a-report-web-part-in-sharepoint-online"></a>Bädda in en rapportwebbdel i SharePoint Online

Med den nya rapportwebbdelen för SharePoint Online i Power BI kan du enkelt bädda in interaktiva Power BI-rapporter i SharePoint Online-sidor.

Vid användning av det nya alternativet **Bädda in i SharePoint Online** är de inbäddade rapporterna helt säkra. Du kan därför enkelt skapa säkra interna portaler.

## <a name="requirements"></a>Krav

För att rapporter med **Bädda in i SharePoint Online** ska fungera krävs följande:

* En Power BI Pro-licens eller en [Power BI Premium-kapacitet (EM eller P SKU)](service-premium-what-is.md) med en Power BI-licens.
* Power BI-webbdelen för SharePoint Online kräver [moderna sidor](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b).
* För att kunna använda en inbäddad rapport måste användare logga in på Power BI-tjänsten och aktivera sin Power BI-licens.

## <a name="embed-your-report"></a>Bädda in rapporten
För att bädda in rapporten i SharePoint Online behöver du hämta rapport-URL:en och använda den med Power BI-webbdelen i SharePoint Online.

### <a name="get-a-report-url"></a>Hämta en rapport-URL

1. Visa rapporten i Power BI.

2. På listrutemenyn **Fler alternativ (...)** väljer du **Bädda in** > **SharePoint Online**.

    ![Menyn Fler alternativ, SharePoint Online](media/service-embed-report-spo/power-bi-more-options-sharepoint-online.png)

3. Kopiera rapport-URL:en från dialogrutan.

    ![Bädda in länk](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Lägga till en Power BI-rapport på en SharePoint Online-sida

1. Öppna målsidan i SharePoint Online och välj **Redigera**.

    ![SP-redigeringssida](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    Eller välj **+ Ny** i SharePoint Online för att skapa en ny modern webbplats.

    ![Ny SP-sida](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Välj listrutan **+** och välj sedan **Power BI**-webbdelen.

    ![Ny SP-webbdel](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Välj **Lägg till rapport**.

    ![Ny SP-rapport](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. Klistra in den tidigare kopierade rapport-URL:en i fönstret med **Power BI-rapportlänk**. Rapporten läses in automatiskt.

    ![Nya SP-webbdelsegenskaper](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Välj **Publicera** så att ändringen visas för användarna i SharePoint Online.

    ![SP-rapport inläst](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>Bevilja åtkomst till rapporter

Inbäddning av en rapport i SharePoint Online ger inte automatiskt användarna behörighet att visa rapporten – du behöver ange visningsbehörigheter i Power BI.

> [!IMPORTANT]
> Se till att granska vem som kan visa rapporten i Power BI-tjänsten och bevilja åtkomst till de som inte visas i listan.

Det finns två sätt att ge åtkomst till rapporter i Power BI. Det första sättet, om du använder en Office 365-grupp för att skapa SharePoint Online-teamwebbplatsen, är att ange användaren som medlem i **arbetsytan i Power BI-tjänsten** och **SharePoint-sidan**. Mer information finns i artikeln om att [hantera en arbetsyta](service-manage-app-workspace-in-power-bi-and-office-365.md).

Det andra sättet är att bädda in en rapport i en app och dela den direkt med användare:  

1. Författaren, som måste vara Pro-användare, skapar en rapport på en arbetsyta. För delning av med *användare av kostnadsfritt Power BI* måste arbetsytan anges som en *Premium-arbetsyta*.

2. Författaren publicerar och installerar appen. Författaren måste installera appen så att den har åtkomst till den rapport-URL som används för inbäddning i SharePoint Online.

3. Nu måste även alla slutanvändare installera appen. Du kan även använda funktionen **Installera appen automatiskt**, som du kan aktivera i [Power BI-administratörsportalen](service-admin-portal.md), om du vill att appen ska förinstalleras för slutanvändare.

   ![Installera appen automatiskt](media/service-embed-report-spo/install-app-automatically.png)

4. Författaren öppnar appen och går till rapporten.

5. Författaren kopierar inbäddningsrapport-URL:en från den rapport som appen installerade. Använd inte den ursprungliga rapportadressen från arbetsytan.

6. Skapa en ny gruppwebbplats i SharePoint Online.

7. Lägg till den tidigare kopierade rapport-URL:en i Power BI-webbdelen.

8. Lägg till alla användare och/eller grupper som ska använda data på SharePoint Online-sidan och i Power BI-appen som du skapade.

    > [!NOTE]
    > **Användare eller grupper behöver åtkomst till såväl sidan SharePoint Online som rapporten i Power BI-appen för att visa rapporten på SharePoint-sidan.**

Användaren kan nu gå till gruppwebbplatsen i SharePoint Online och visa rapporter på sidan.

## <a name="multi-factor-authentication"></a>Multifaktorautentisering

Om din Power BI-miljö kräver att du loggar in med multifaktorautentisering kan du uppmanas att logga in med en säkerhetsenhet för att verifiera din identitet. Detta inträffar om du inte loggade in på SharePoint Online med hjälp av multifaktorautentisering men din Power BI-miljö kräver en säkerhetsenhet för att validera ett konto.

> [!NOTE]
> Power BI stöder ännu inte multifaktorautentisering med Azure Active Directory 2.0 – användare får ett felmeddelande. Om användaren loggar in igen på SharePoint Online med hjälp av en säkerhetsenhet kan denne eventuellt visa rapporten.

## <a name="web-part-settings"></a>Inställningar för webbdel

Nedan visas de inställningar som du kan ändra för Power BI-webbdelen för SharePoint Online.

![SP-webbdelsegenskaper](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Egenskap | Beskrivning |
| --- | --- |
| Sidnamn |Anger webbdelens standardsida. Välj ett värde från listrutan. Om inga sidor visas innehåller rapporten endast en sida eller också innehåller URL:en du klistrade in ett sidnamn. Ta bort rapportdelen av URL:en för att välja en specifik sida. |
| Skärm |Justerar hur rapporten passar på SharePoint Online-sidan. |
| Visa navigeringsfönstret |Visar eller döljer sidans navigeringsfönster. |
| Visa filtreringsfönstret |Visar eller döljer filtreringsfönstret. |

## <a name="reports-that-do-not-load"></a>Rapporter som inte kan läsas in

Om rapporten inte läses in i Power BI-webbdelen kan det hända att följande meddelande visas:

![Meddelande om att det här innehållet inte är tillgängligt](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Det finns två vanliga orsaker till det här meddelandet.

1. Du har inte rapportåtkomst.
2. Rapporten har tagits bort.

Kontakta ägaren av SharePoint Online-sidan för att hjälpa dig att lösa problemet.

## <a name="licensing"></a>Licensiering

Användare som visar en rapport i SharePoint måste antingen ha en **Power BI Pro-licens** eller så måste innehållet finnas på en arbetsyta som är i en **[Power BI Premium-kapacitet (EM eller P SKU)](service-admin-premium-purchase.md)** .

## <a name="known-issues-and-limitations"></a>Kända problem och begränsningar

* Fel: "Ett fel har uppstått. Försök att logga ut och in igen och gå sedan tillbaka till den här sidan. Korrelations-ID: odefinierat, http-svarsstatus: 400, serverfelskod 10001, meddelande: Uppdateringstoken saknas"
  
  Testa något av felsökningsstegen nedan om du får detta felmeddelande.
  
  1. Logga ut från SharePoint och logga in igen. Glöm inte att stänga alla webbläsarfönster innan du loggar in igen.

  2. Om ditt konto kräver multifaktorautentisering (MFA) loggar du in på SharePoint med hjälp av din MFA-enhet (telefonapp, smartkort osv.).
  
  3. Gästanvändares konton för Azure B2B stöds inte. Användarna ser Power BI-logotypen som visas när en del blir inläst, men rapporten visas inte.

* Power BI stöder inte samma språk som SharePoint Online. Det innebar att den inbäddade rapporten kanske inte är helt lokaliserad.

* Problem kan också uppstå om du använder Internet Explorer 10. <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->

* Power BI-webbdelen är inte tillgänglig i [nationella moln](https://powerbi.microsoft.com/clouds/).

* Klassiska SharePoint Server stöds inte med den här webbdelen.

* [URL-filter](service-url-filters.md) stöds inte med SPO-webbdelen.

## <a name="next-steps"></a>Nästa steg

* [Tillåt eller förhindra att moderna webbplatssidor skapas av slutanvändare](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [Skapa och distribuera en app i Power BI](service-create-distribute-apps.md)  
* [Dela en instrumentpanel med kollegor och andra](service-share-dashboards.md)  
* [Vad är Power BI Premium?](service-premium-what-is.md)
* [Bädda in en rapport på en säker portal eller webbplats](service-embed-secure.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
