---
title: Kopiera rapporter från andra arbetsytor (förhandsversion) – Power BI
description: Lär dig hur du delar en datamängd med användare i organisationen. De kan sedan skapa rapporter baserat på din datamängd på sina egna arbetsytor.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 9c7cbd895a913b76a9c0b87155f7800c5538ab28
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75223846"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Kopiera rapporter från andra arbetsytor (förhandsversion)

När du har hittat en rapport som du gillar på en arbetsyta eller i en app kan du göra en kopia av den och sedan spara den på en annan arbetsyta. Du kan sedan ändra din kopia av rapporten genom att lägga till eller ta bort visuella objekt och andra element. Du behöver inte tänka på att skapa datamodellen. Den har redan skapats. Och det är mycket enklare att ändra en befintlig rapport än att börja från början. Men när du skapar en app från den nya arbetsytan kan du ibland inte publicera din kopia av rapporten i appen. Mer information finns i [Överväganden och begränsningar i artikeln ”Använda datamängder mellan arbetsytor”](service-datasets-across-workspaces.md#considerations-and-limitations).

> [!NOTE]
> För att göra en kopia behöver du en Pro-licens, även om den ursprungliga rapporten finns på en arbetsyta i en Premium-kapacitet.

## <a name="save-a-copy-of-a-report"></a>Skapa en kopia av en rapport

1. I en app eller på en arbetsyta går du till listvyn Rapporter.

1. Under **Åtgärder** väljer du **Spara en kopia**.

    ![Skapa en kopia av en rapport](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    Du ser endast ikonen **Spara en kopia** om rapporten är på en arbetsyta med ny arbetsytefunktion och du har [skapa-behörighet](service-datasets-build-permissions.md). Även om du har åtkomst till arbetsytan måste du ha skapa-behörighet för datauppsättningen.

3. I **Spara en kopia av den här rapporten** ger du rapporten ett namn och väljer mål för arbetsytan.

    ![Dialogrutan Spara en kopia](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    Vilken arbetsyta du kan spara till beror på var du kopierar från. När du kopierar från en arbetsyta kan du spara rapporten på den aktuella arbetsytan eller en annan i Power BI-tjänsten. Du kan bara se arbetsytor som är arbetsytor med den nya funktionen och där du är medlem. När du kopierar från en app kan du spara rapporten till Min arbetsyta.
  
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

## <a name="delete-a-report-and-its-shared-dataset"></a>Ta bort en rapport och dess delade datauppsättning

Du kan bestämma att du inte längre vill ha kvar rapporten och dess associerade delade datauppsättning på arbetsytan.

1. Ta bort rapporten. I listan över rapporter på arbetsytan väljer du ikonen **Ta bort**.

    ![Ta bort rapportikonen](media/service-datasets-across-workspaces/power-bi-datasets-delete-report.png)

2. I listan över datauppsättningar ser du att de delade datamängder inte har ikoner för att **Ta bort**. Uppdatera sidan eller gå till en annan sida och återvänd. Datauppsättningen kommer att vara borta. Om inte, kontrollera **Visa relaterade**. Det kan vara relaterat till en annan tabell på din arbetsyta.

    ![Ikonen Visa relaterade](media/service-datasets-across-workspaces/power-bi-dataset-view-related-icon.png)

    > [!NOTE]
    > Om du tar bort den delade datauppsättningen på den här arbetsytan tas den inte bort. Det är endast referensen till den som tas bort.


## <a name="next-steps"></a>Nästa steg

- [Använda datamängder mellan arbetsytor (förhandsversion)](service-datasets-across-workspaces.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
