---
title: Visa Power BI-innehåll som en extern gästanvändare (Azure AD B2B)
description: Använda Power BI-appar för att visa innehåll som delats med dig från extern organisation.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/27/2019
ms.author: mshenhav
ms.openlocfilehash: a15da4349ce97e34c8321909abc862e424b2839c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61338775"
---
# <a name="view-power-bi-content-shared-with-you-from-an-external-organization"></a>Visa Power BI-innehåll som delats med dig från en extern organisation

Powerbi integrerar med Azure Active Directory business-to-business (Azure AD B2B) att tillåta säker distribution av Power BI-innehåll till gästanvändare utanför organisationen. Och externa gästanvändare kan använda Power BI-mobilappen för att få åtkomst till den Power BI-innehåll som delats med dem. 


Gäller för:

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Android-telefon](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Android-surfplatta](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhone-telefoner |iPad-surfplattor |Android-telefoner |Android-surfplattor |

## <a name="accessing-shared-content"></a>Åtkomst till delat innehåll

**Först behöver du någon från en extern organisation att dela ett objekt med dig.** När någon [delar ett objekt med dig](../../service-share-dashboards.md), antingen från samma organisation eller från en extern organisation du får ett e-postmeddelande med en länk till det delade objektet. Efter den länken i din mobila enhet öppnas Power BI-mobilappen. Om appen känner av att objektet har delats från en extern organisation kan appen ska återansluta till organisationen med din identitet. Appen läses sedan in alla objekt som har delats med dig från den organisationen.

![Powerbi öppna delade objekt från e-post ](./media/mobile-apps-b2b/mobile-b2b-open-item-email.png)

> [!NOTE]
> Om detta är det första objektet som delas med dig som en extern gästanvändare, måste du göra anspråk på inbjudan i en webbläsare. Du kan inte göra anspråk på inbjudan i Power BI-appen.

Så länge du är ansluten till en extern organisation, visas en svart rubrik i appen. Den här rubriken anger att du inte är ansluten till organisationens startsida. Avsluta från gästläge för att ansluta till organisationen hem.

![Power BI gäst användaren rubrik](./media/mobile-apps-b2b/mobile-b2b-exit-home.png)

Du kan komma åt alla objekt som har delats med dig (inte bara de objekt som du har öppnat från e-postmeddelandet) även om du behöver ha en Power BI-artefakt länk att ansluta till en extern organisation när din app växlar. Om du vill visa alla objekt som du kan komma åt i den externa organisationen, gå till app-menyn och välj **delat med mig**. Under **appar** du hittar appar som du kan använda.

![Power BI meny som externa gästanvändare](./media/mobile-apps-b2b/mobile-b2b-menu.png)

## <a name="limitations"></a>Begränsningar

- Villkorlig åtkomst och andra Intune-principer stöds inte i Azure AD B2B och i Power BI mobile. Det innebär att appen tillämpar endast home organisationens principer, om de finns.
- Push-meddelanden tas emot från webbplatsen hemorganisation (även när användaren är ansluten som en gäst till en extern organisation). Öppna meddelandet ansluter igen appen till användarens hemorganisation plats.
- Om användaren stänger av appen, när öppnas på nytt appen ansluter automatiskt till användarens hemorganisation.
- När du är ansluten till en extern organisation, vissa åtgärder är inaktiverade: favorit objekt, dataaviseringar, kommentera och dela.
- Offlinedata är inte tillgänglig när du är ansluten till en extern organisation.
- Om du har företagsportalappen installerad på din enhet måste enheten registreras.
