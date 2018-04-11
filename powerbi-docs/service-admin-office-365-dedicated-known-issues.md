---
title: Office 365-dedikerade kunder – kända problem
description: Support för Office 365-dedikerade kunder – kända problem. I det här avsnittet beskrivs problem som är specifika för en Office 365-dedikerad kund. Detta innefattar begränsningar i gruppfunktionen samt iPhone-appen med anpassade domäner.
services: powerbi
documentationcenter: ''
author: mgblythe
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 06/28/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 4ba9aaf309e7cc749ee9293b0bb906a26b81e59c
ms.sourcegitcommit: 8552a34df8e6141eb704314c1a019992901d6e78
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2018
---
# <a name="office-365-dedicated-customers---known-issues"></a>Office 365-dedikerade kunder – kända problem
Power BI har nu stöd för Office 365-dedikerade kunder.  Om du är en O365-dedikerad kund kan du logga in med ett konto från den klienten och använda Power BI. Det finns för närvarande två kända problem.

## <a name="groups"></a>Grupper
När du väljer **Medlemmar** eller **Kalender** i snabbmenyn Grupp omdirigeras du till e-postappen i stället.  **Filer** och **Konversationer** fungerar som förväntat.

![](media/service-admin-office-365-dedicated-known-issues/group-menu.png)

## <a name="iphone-app---sign-in-with-vanity-domain-leads-to-error"></a>iPhone-app – Inloggning med en anpassad domän leder till fel
När du loggar in på iPhone-appen med en anpassad domän kan det uppstå ett fel.

*Inloggningsfel*  
*Ett oväntat internt fel har uppstått. Försök igen.*

Undvik problemet genom att logga in med e-postadressen som visas när du klickar på användarikonen i Power BI-tjänsten, i stället för med den anpassade domänen.

![](media/service-admin-office-365-dedicated-known-issues/sign-in-address.png)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

