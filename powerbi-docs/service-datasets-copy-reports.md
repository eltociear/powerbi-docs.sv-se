---
title: Kopiera rapporter från andra arbetsytor (förhandsversion) – Power BI
description: Lär dig hur du delar en datamängd med användare i organisationen. De kan sedan skapa rapporter baserat på din datamängd på sina egna arbetsytor.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 507af4de9d57d2d54fe3e28bca8b1aff7da5cf30
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461475"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Kopiera rapporter från andra arbetsytor (förhandsversion)

Lär dig hur du kopierar en rapport från en arbetsyta och sparar den på en annan arbetsyta. Du kan sedan ändra rapporten för att lägga till eller ta bort visuella objekt och andra element.

När du har hittat en rapport som du gillar på en arbetsyta eller i en app kan du göra en kopia av den och sedan anpassa den efter dina behov. Du behöver inte tänka på att skapa datamodellen. Den har redan skapats. Och det är mycket enklare att ändra en befintlig rapport än att börja från början.

## <a name="save-a-copy-of-a-report"></a>Skapa en kopia av en rapport

1. I en app eller på en arbetsyta går du till listvyn Rapporter.

1. Under **Åtgärder** väljer du **Spara en kopia**.

    ![Skapa en kopia av en rapport](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    Du ser endast ikonen **Spara en kopia** om rapporten är på en arbetsyta med ny arbetsytefunktion och du har [skapa-behörighet](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Även om du har åtkomst till arbetsytan måste du ha skapa-behörighet för datamängden.

3. I **Spara en kopia av den här rapporten** ger du rapporten ett namn och väljer mål för arbetsytan.

    ![Dialogrutan Spara en kopia](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    Du kan spara rapporten på den aktuella arbetsytan eller en annan i Power BI-tjänsten. Du kan bara se arbetsytor som är arbetsytor med den nya funktionen och där du är medlem.
  
4. Välj **Spara**.

    När du sparar en kopia av rapporten skapar du en live-anslutning till datamängden, och du kan öppna funktionen för rapportskapande med hela datamängden tillgänglig. Du har inte gjort en kopia av datamängden. Datamängden finns fortfarande på dess ursprungliga plats. Du kan använda alla tabeller och mått i datamängden i din egen rapport. Begränsningar gällande säkerhet på radnivå (RLS) för datamängden gäller, så du ser endast data som du har behörighet att se baserat på din RLS-roll.

    Power BI skapar automatiskt en post i listan över datamängder om rapporten baseras på en datamängd utanför arbetsytan. Ikonen för den här datamängden skiljer sig från ikonen för datamängder på arbetsytan: ![Ikon för delad datamängd](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)


    På så sätt kan medlemmar i arbetsytan se vilka rapporter och instrumentpaneler som använder datamängder som är utanför arbetsytan. Posten visas information om datamängden och vissa utvalda åtgärder.

    ![Datamängdsåtgärder](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="view-related-datasets"></a>Visa relaterade datamängder

När du har en rapport på din arbetsyta kan du behöva känna till vilken datamängd den baseras på.

1. I listvyn Rapporter väljer du **Visa relaterade**.

    ![Ikonen Visa relaterade](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. Dialogrutan **Relaterat innehåll** visar alla relaterade objekt. I den här listan ser datamängden ut som vilken annan som helst. Det syns inte att den finns på en annan arbetsyta. Det här problemet är känt.
 
    ![Dialogrutan Relaterat innehåll](media/service-datasets-copy-reports/power-bi-dataset-related.png)


## <a name="next-steps"></a>Nästa steg

- [Använda datamängder mellan arbetsytor (förhandsversion)](service-datasets-across-workspaces.md)
- Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)
