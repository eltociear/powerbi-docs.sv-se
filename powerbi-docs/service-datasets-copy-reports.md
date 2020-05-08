---
title: Kopiera rapporter från andra appar eller arbetsytor (förhandsversion) – Power BI
description: Lär dig att skapa en kopia av en rapport och spara den på din egen arbetsyta.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/16/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 8716a304e5b117c027d75db149ebcc8d95efebfe
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76268901"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Kopiera rapporter från andra arbetsytor (förhandsversion)

När du har hittat en rapport som du gillar på en arbetsyta eller i en app kan du göra en kopia av den och sedan spara den på en annan arbetsyta. Du kan sedan ändra din kopia av rapporten genom att lägga till eller ta bort visuella objekt och andra element. Du behöver inte tänka på att skapa datamodellen. Den har redan skapats. Och det är mycket enklare att ändra en befintlig rapport än att börja från början. När du skapar en app från arbetsytan kan du ibland inte publicera din kopia av rapporten i appen. Mer information finns i [Överväganden och begränsningar i artikeln ”Använda datamängder mellan arbetsytor”](service-datasets-across-workspaces.md#considerations-and-limitations).

> [!NOTE]
> För att göra en kopia behöver du en Pro-licens, även om den ursprungliga rapporten finns på en arbetsyta i en Premium-kapacitet.

## <a name="save-a-copy-of-a-report-in-a-workspace"></a>Spara en kopia av en rapport på en arbetsyta

1. I arbetsytan går du till listvyn Rapporter.

    ![Listvyn Rapporter](media/service-datasets-copy-reports/power-bi-report-list-view.png)

1. Under **Åtgärder** väljer du **Spara en kopia**.

    ![Skapa en kopia av en rapport](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    Du ser endast ikonen **Spara en kopia** om rapporten är på en arbetsyta med ny arbetsytefunktion och du har [skapa-behörighet](service-datasets-build-permissions.md). Även om du har åtkomst till arbetsytan måste du ha skapa-behörighet för datauppsättningen.

3. I **Spara en kopia av den här rapporten** ger du rapporten ett namn och väljer mål för arbetsytan.

    ![Dialogrutan Spara en kopia](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    Du kan spara rapporten på den aktuella arbetsytan eller en annan i Power BI-tjänsten. Du kan bara se arbetsytor som är arbetsytor med den nya funktionen och där du är medlem. 
  
4. Välj **Spara**.

    Power BI skapar automatiskt kopia av rapporten och en post i listan med datamängder, om rapporten baseras på en datamängd utanför arbetsytan. Ikonen för den här datamängden skiljer sig från ikonen för datamängder på arbetsytan: ![Ikon för delad datamängd](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)
    
    På så sätt kan medlemmar i arbetsytan se vilka rapporter och instrumentpaneler som använder datamängder som är utanför arbetsytan. Posten visas information om datamängden och vissa utvalda åtgärder.

    ![Datamängdsåtgärder](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

    Mer information om rapporten och relaterad datamängd finns i [Din kopia av rapporten](#your-copy-of-the-report) i den här artikeln.

## <a name="copy-a-report-in-an-app"></a>Kopiera en rapport i en app

1. I appen öppnar du den rapport som du vill kopiera.
2. I menyraden väljer du **Fler alternativ** ( **...** ) > **Spara en kopia**.

    ![Spara en kopia av rapporten](media/service-datasets-copy-reports/power-bi-save-copy.png)

    Du ser bara alternativet **Spara en kopia** om rapporten är på en arbetsyta och du har [Skapa-behörighet](service-datasets-build-permissions.md).

3. Ge rapporten ett namn > **Spara**.

    ![Namnge din kopia av rapporten](media/service-datasets-copy-reports/power-bi-save-report-from-app.png)

    Din kopia sparas automatiskt på Min arbetsyta.

4. Välj **Gå till rapport** för att öppna din kopia.

## <a name="your-copy-of-the-report"></a>Din kopia av rapporten

När du sparar en kopia av rapporten skapar du en live-anslutning till datamängden, och du kan öppna funktionen för rapportskapande med hela datamängden tillgänglig. 

![Redigera din kopia av rapporten](media/service-datasets-copy-reports/power-bi-edit-report-copy.png)

Du har inte gjort en kopia av datamängden. Datamängden finns fortfarande på dess ursprungliga plats. Du kan använda alla tabeller och mått i datamängden i din egen rapport. Begränsningar gällande säkerhet på radnivå (RLS) för datamängden gäller, så du ser endast data som du har behörighet att se baserat på din RLS-roll.

## <a name="view-related-datasets"></a>Visa relaterade datamängder

När du har en rapport på en arbetsyta som baseras på en datamängd på en annan arbetsyta, kan du behöva veta mer om den datamängd som den baseras på.

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
