---
title: Skapa-behörighet för delade datamängder
description: Läs om hur du kan styra åtkomsten till data med hjälp av behörigheten Skapa.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 84f6a9d152151c6d6f44bcbad9e0a4d54fc0c293
ms.sourcegitcommit: 5e5a7e15cdd55f71b0806016ff91256a398704c1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/22/2020
ms.locfileid: "83792996"
---
# <a name="build-permission-for-shared-datasets"></a>Skapa-behörighet för delade datamängder

När du skapar en rapport i Power BI Desktop lagras data i rapporten i en *datamodell*. När du publicerar dina rapporter till Power BI-tjänsten publicerar du även data som en *datamängd*. Du kan ge andra *behörigheten Skapa* för rapporten så att de kan identifiera och återanvända den datamängd du har delat. I den här artikeln går vi igenom hur du kan styra åtkomsten till data med hjälp av behörigheten Skapa.

Behörigheten Skapa gäller för datamängder. När du ger användare behörigheten Skapa kan de skapa nytt innehåll i datamängden, som rapporter, instrumentpaneler, fästa paneler från Frågor och svar och Insights Discovery. 

Användare behöver också behörigheten Skapa för att arbeta med data *utanför* Power BI:

- till att exportera underliggande data
- till att skapa nytt innehåll i datamängden, som med [Analysera i Excel](../collaborate-share/service-analyze-in-excel.md)
- till att komma åt data via XMLA-slutpunkten.

## <a name="ways-to-give-build-permission"></a>Sätt att ge skapa-behörighet

Du ger skapa-behörighet för en datauppsättning på några olika sätt:

- Medlemmar i en arbetsyta med minst en deltagarroll har automatiskt skapa-behörighet för datauppsättningar i den arbetsytan och behörighet att kopiera en rapport.
 
- Medlemmar i arbetsytan där datauppsättningen finns kan tilldela behörighet till specifika användare eller säkerhetsgrupper i behörighetscentret. Om du är medlem i arbetsytan väljer du **Fler alternativ** (…) bredvid en datauppsättning > **Hantera behörigheter**.

    ![Välj ellipsen](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

    Då öppnas behörighetscentret för den datamängden, där du kan ange och ändra behörigheter.

    ![Behörighetscentret](media/service-datasets-build-permissions/power-bi-dataset-remove-permissions-no-callouts.png)

- En administratör eller medlem i den arbetsyta där datamängden finns kan under publicering av app bestämma att användare med behörighet för den appen även får skapa-behörighet för de underliggande datamängderna. Se [Dela en datauppsättning](service-datasets-share.md) för mer information.

- Anta att du har vidaredelnings- och skapa-behörigheter för en datauppsättning. När du delar en rapport eller instrumentpanel som skapats ovanpå den datauppsättningen kan du ange att mottagaren även får skapa-behörighet för den underliggande datauppsättningen.

    ![Skapa-behörighet](media/service-datasets-build-permissions/power-bi-share-report-allow-users.png)

Du kan ta bort en persons skapa-behörighet för en datauppsättning. Om du gör det kan de fortfarande se den rapport som skapats på den delade datamängden, men de kan inte längre redigera den. Mer information finns i nästa avsnitt.

## <a name="remove-build-permission-for-a-dataset"></a>Ta bort skapa-behörighet för en datauppsättning

Du kan behöva ta bort skapa-behörighet för vissa användare av en delad datauppsättning. 

1. I en arbetsyta går du till sidan med **datauppsättningar**-listan. 
1. Välj **Fler alternativ** (...) bredvid datauppsättningen > **Hantera behörighet**.

    ![Hantera behörigheter](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

1. Välj **Fler alternativ** (...) bredvid ett namn > **Ta bort skapa**.

    ![Ta bort skapa-behörighet](media/service-datasets-build-permissions/power-bi-dataset-remove-build-permissions.png)

    De kan fortfarande se den rapport som skapats med den delade datauppsättningen, men de kan inte längre redigera den.

### <a name="remove-build-permission-for-a-dataset-in-an-app"></a>Ta bort skapa-behörighet för en datauppsättning i en app

Anta att du har distribuerat en app från en arbetsyta till en grupp med personer. Senare bestämmer du dig för att ta bort åtkomsten till appen för vissa personer. Om du tar bort deras åtkomst till appen tar det inte automatiskt bort deras bygg- och återdelnings-behörigheter. Det är ett extra steg. 

1. På en sida med en arbetytelista väljer du **Uppdatera appen**. 

    ![Uppdatera app](media/service-datasets-build-permissions/power-bi-app-update.png)

1. På fliken **Behörigheter** trycker du på **X** för att ta bort personen eller gruppen. 

    ![Tryck på X](media/service-datasets-build-permissions/power-bi-app-delete-user.png)
1. Välj **Uppdatera app**.

    Ett meddelande visas som förklarar att du måste gå till **Hantera behörigheter** för att ta bort skapa-behörighet för användare med befintlig åtkomst. 

    ![Hantera behörigheter-meddelande](media/service-datasets-build-permissions/power-bi-dataset-app-remove-message.png)

1. Välj **Uppdatera**.

1. I arbetsytan går du till sidan med **Satauppsättningar**-listan. 
1. Välj **Fler alternativ** (...) bredvid datauppsättningen > **Hantera behörighet**.

    ![Hantera behörigheter](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

1. Välj **Fler alternativ** (...) bredvid namnet > **Ta bort skapa**.

    ![Ta bort skapa-behörighet](media/service-datasets-build-permissions/power-bi-dataset-remove-build-permissions.png)

    De kan fortfarande se den rapport som skapats med den delade datauppsättningen, men de kan inte längre redigera den.

## <a name="more-granular-permissions"></a>Mer granulära behörigheter

Power BI introducerade skapa-behörigheten juni 2019 som ett komplement till de befintliga behörigheterna Läsa och Dela vidare. Alla användare som redan hade läsbehörighet för datauppsättningar via appbehörigheter, delning eller arbetsyteåtkomst vid den tidpunkten fick även skapa-behörighet för samma datauppsättningar. De fick skapa-behörighet automatiskt eftersom läsbehörighet redan gav den rätt att skapa nytt innehåll ovanpå datamängden med hjälp av Analysera i Excel eller export.

Med den här mer granulära skapa-behörigheten kan du välja vilka som endast kan se innehållet i den befintliga rapporten eller instrumentpanelen samt vilka som kan skapa innehåll som är kopplat till de underliggande datamängderna.

Om din datamängd används av en rapport utanför datamängdens arbetsyta kan du inte ta bort den datamängden. I stället visas ett felmeddelande.

Du kan ta bort skapa-behörigheter. Om du gör detta kan de personer vars behörigheter du har återkallat fortfarande se rapporten, men de kan inte längre redigera den eller exportera underliggande data. Användare med enbart läsbehörighet kan fortfarande exportera sammanfattade data. 

## <a name="next-steps"></a>Nästa steg

- [Använda datamängder på arbetsytor](service-datasets-across-workspaces.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
