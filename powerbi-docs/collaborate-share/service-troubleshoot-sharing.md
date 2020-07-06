---
title: Felsöka delning av instrumentpaneler och rapporter
description: Så här löser du problem med delning av Power BI-instrumentpaneler och -rapporter med kollegor i och utanför organisationen.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 06/23/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: ef78847829ef292a16856a1597a53c95e7d20708
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/27/2020
ms.locfileid: "85486814"
---
# <a name="troubleshoot-sharing-dashboards-and-reports"></a>Felsöka delning av instrumentpaneler och rapporter

Här följer några vanliga problem som kan uppstå när du delar en instrumentpanel eller rapport, eller när någon annan delar med dig. 

## <a name="dashboard-recipients-see-a-lock-icon-in-a-tile"></a>Instrumentpanelsmottagare ser en lås-ikon i en panel

De personer som du delar med kan se en låst panel på en instrumentpanel eller ett meddelande om att ”behörighet krävs” när de försöker visa en rapport.

![låst panel i Power BI](media/service-share-dashboards/power-bi-locked_tile_small.png)

I så fall behöver ge dem behörighet till den underliggande datauppsättningen.

1. Gå till fliken **Datauppsättningar** i listan med innehåll.

1. Välj ellipsen ( **...** ) intill datamängden och välj sedan **Hantera behörigheter**.

    ![Hantera behörigheter](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. Välj **Lägg till användare**.

    ![Välj Lägg till användare](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Ange fullständiga e-postadresser för enskilda användare, distributionsgrupper och säkerhetsgrupper. Du kan inte dela med dynamiska distributionslistor.

    ![Lägg till e-postadresser](media/service-share-dashboards/power-bi-add-user-dataset.png)

1. Välj **Lägg till**.

## <a name="i-cant-share-a-dashboard-or-report"></a>Jag kan inte dela en instrumentpanel eller en rapport

Om du vill dela en instrumentpanel eller rapport behöver du behörighet att dela det underliggande innehållet, det vill säga relaterade rapporter och datamängder. Om du ser ett meddelande om att du inte kan dela ber du rapportskaparen att ge dig behörighet att dela vidare för dessa rapporter och datamängder.

![Meddelande om att det inte går att dela](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)

## <a name="i-dont-have-access-to-a-dashboard-or-report"></a>Jag har inte åtkomst till en instrumentpanel eller rapport

Om du ser meddelandet Begär åtkomst när du väljer länken till en rapport eller instrumentpanel så har du inte behörighet att visa den. Du måste [begära åtkomst till den](service-request-access.md).

## <a name="next-steps"></a>Nästa steg

- [Dela Power BI-instrumentpaneler och -rapporter med kollegor och andra](service-share-dashboards.md)
- [Hur ska jag samarbeta kring och dela instrumentpaneler och rapporter?](service-how-to-collaborate-distribute-dashboards-reports.md)
-  [Dela en filtrerad Power BI-rapport](service-share-reports.md)
- Har du några frågor? [Prova Power BI Community](https://community.powerbi.com/)
