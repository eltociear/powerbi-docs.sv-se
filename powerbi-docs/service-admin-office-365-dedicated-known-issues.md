---
title: Office 365-dedikerade kunder – kända problem
description: Support för Office 365-dedikerade kunder – kända problem. I det här avsnittet beskrivs problem som är specifika för en Office 365-dedikerad kund. Detta innefattar begränsningar i gruppfunktionen samt iPhone-appen med anpassade domäner.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/28/2017
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: a5a9d080205e5f6a047ed820b8b5ed70fa9017d2
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699991"
---
# <a name="office-365-dedicated-customers---known-issues"></a>Office 365-dedikerade kunder – kända problem
Power BI har nu stöd för Office 365-dedikerade kunder.  Om du är en O365-dedikerad kund kan du logga in med ett konto från den klienten och använda Power BI. Det finns för närvarande två kända problem.

## <a name="groups"></a>Grupper
När du väljer **Medlemmar** eller **Kalender** i snabbmenyn Grupp omdirigeras du till e-postappen i stället.  **Filer** och **Konversationer** fungerar som förväntat.

![Grupp från Power BI](media/service-admin-office-365-dedicated-known-issues/group-menu.png)

## <a name="iphone-app---sign-in-with-vanity-domain-leads-to-error"></a>iPhone-app – Inloggning med en anpassad domän leder till fel
När du loggar in på iPhone-appen med en anpassad domän kan det uppstå ett fel.

*Inloggningsfel*  
*Ett oväntat internt fel har uppstått. Försök igen.*

Undvik problemet genom att logga in med e-postadressen som visas när du klickar på användarikonen i Power BI-tjänsten, i stället för med den anpassade domänen.

![E-post för inloggning](media/service-admin-office-365-dedicated-known-issues/sign-in-address.png)

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

