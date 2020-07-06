---
title: Planerat underhåll av Power BI
description: Information för administratörer om hur planerat underhåll av Power BI påverkar deras organisation och vilka steg som de kan tänkas behöva vidta.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/19/2020
ms.author: kfollis
ms.custom: MC
ROBOTS: NOINDEX
LocalizationGroup: Admin
ms.openlocfilehash: cc9364129159b5527d309f125d42e661d0b4c206
ms.sourcegitcommit: a58d10ca62bc55e83b58cf8e8495ac01a4bd6532
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/20/2020
ms.locfileid: "85120577"
---
# <a name="power-bi-planned-maintenance"></a>Planerat underhåll av Power BI

Planerat underhåll för Power BI-tjänsten är en nödvändig del av vårt åtagande att tillhandahålla en tillförlitlig produkt till våra kunder. Under tiden som planerat underhåll pågår är Power BI-tjänst tillgängligt för din organisation. Användarna kan få problem med åtkomsten till Power BI-tjänsten och bakgrundsåtgärder kan upphöra att fungera. Efter underhållsperioden förväntas tjänsten fungera normalt och både interaktiva åtgärder och bakgrundsåtgärder ska fungera.  

Planerat underhåll görs utanför normala arbetstider, så att eventuell påverkan på din organisation minimeras. När det gäller internationella organisationer som har användare runtom i världen är vi medvetna om att "utanför normala arbetstider" har olika innebörd. Vi ber om ursäkt för de eventuella problem detta kan åsamka era användare. Vi arbetar hårt för att förbättra Power BI och minimera dessa underhållsfönster.

Om din organisation påverkas så meddelar vi dig i förväg. Microsoft 365-administratörer får ett förhandsmeddelande i Microsoft 365-meddelandecentret och via e-post. Dessutom meddelas kunder med Premier Support-kontrakt genom sina Microsoft-kontoteam.

## <a name="actions-to-take-now"></a>Åtgärder att vidta nu

* Microsoft 365-administratörer bör [söka i meddelandecentret](https://admin.microsoft.com/Adminportal/Home#/MessageCenter) efter meddelanden om planerat underhåll för Power BI. Dela meddelandet med personer som bör känna till den här informationen, men som inte har åtkomst till meddelandecentret.
* Om du inte är Microsoft 365.administratör kan du kontakta IT-avdelningen eller dina interna supportteam och ställa frågor om kommande underhåll.

## <a name="actions-to-take-when-maintenance-is-complete"></a>Åtgärder att vidta när underhållet har slutförts

* Användarna bör uppdatera alla öppna webbläsarfönster.
* Power BI Mobile App-användare måste verifiera att de använder den senaste versionen och logga ut från appen för att sedan in igen. Kontrollera din telefons App Store eller gå till vår [Power BI Mobile](https://powerbi.microsoft.com/mobile/)-sida.
* Kunder som aktivt har redigerat eller publicerat rapporter som använder visuella organisationsobjekt, oavsett om det har gjorts lokalt eller från OneDrive- eller SharePoint-platser, måste antingen importera om det visuella objektet via organisationens arkiv för visuella objekt eller ladda ned en uppdaterad PBIX innan de publicerar om. Mer information om visuella objekt i organisationer finns i [Visuella objekt i organisationer](service-admin-portal.md#organization-visuals).
* Om Excel-arbetsböcker som använder funktionen Analysera i Excel inte uppdateras, kan du behöva uppdatera anslutningssträngen eller ladda ned ODC-anslutningen på nytt för den datamängden. Mer information finns i [Analysera i Excel](../collaborate-share/service-analyze-in-excel.md#connect-to-power-bi-data).
* Länkar till Power BI Embedded i innehållet kan få problem med anslutningen när underhållet har slutförts. En inbäddad länk i SharePoint eller Teams kan t.ex. resultera i ett användarfel. För att lösa det här problemet måste du återskapa den inbäddade länken i Power BI och sedan uppdatera de platser där den används. Mer information om inbäddade länkar finns i [Bädda in en rapportwebbdel i SharePoint Online](../collaborate-share/service-embed-report-spo.md) och [Samarbeta i Microsoft Teams med Power BI](../collaborate-share/service-embed-report-microsoft-teams.md).

## <a name="next-steps"></a>Nästa steg

* [Aviseringar om tjänstavbrottsaviseringar](service-interruption-notifications.md)
* [Spåra kommande ändring i meddelandecentret](https://docs.microsoft.com/microsoft-365/admin/manage/message-center?view=o365-worldwide)
