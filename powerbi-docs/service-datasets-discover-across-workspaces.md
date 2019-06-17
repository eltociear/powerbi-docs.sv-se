---
title: Skapa rapporter baserat på datamängder från olika arbetsytor (förhandsversion) – Power BI
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
ms.openlocfilehash: 99769b78060756c557223dd366da550ad3e11056
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461291"
---
# <a name="create-reports-based-on-datasets-from-different-workspaces-preview"></a>Skapa rapporter baserat på datamängder från olika arbetsytor (förhandsversion)

Lär dig hur du skapar rapporter på dina egna arbetsytor baserat på datamängder på andra arbetsytor. Om du vill skapa en rapport ovanpå en befintlig datamängd kan du starta från Power BI Desktop eller Power BI-tjänsten i Min arbetsyta eller i en [ny arbetsytefunktion](service-create-the-new-workspaces.md).

- I Power BI-tjänsten: **Hämta data** > **Publicerade datamängder**.
- I Power BI Desktop: **Hämta data** > **Power BI-datamängder**.

    ![Ansluta till en befintlig datamängd](media/service-datasets-across-workspaces/power-bi-connect-dataset-pk.png)
   
I båda fallen börjar funktionen för identifiering av datamängd i den här dialogrutan, **Välj en datamängd för att skapa en rapport**. Du kan se alla datamängder som du har åtkomst till, oavsett var de är:

![Skapa en datamängd](media/service-datasets-across-workspaces/power-bi-select-dataset.png)

Den första är märkt med **Promoted** (Upphöjd). Vi går igenom det i [Hitta en rekommenderad datamängd](#find-an-endorsed-dataset) senare i artikeln.

De datamängder som du ser i den här listan uppfyller minst ett av följande villkor:

- Datamängden finns i en av arbetsytorna med ny arbetsytefunktion, och du är medlem i den arbetsytan. Se [Överväganden och begränsningar](service-datasets-across-workspaces.md#considerations-and-limitations).
- Du har behörigheten skapa-behörighet för datamängden, som finns på en arbetsyta med ny arbetsytefunktion.
- Datamängden finns i Min arbetsyta.

> [!NOTE]
> Om du använder den kostnadsfria versionen ser du endast datamängder i Min arbetsyta eller datamängder som du har skapa-behörighet för och som finns på arbetsytor för Premium-kapacitet.

När du klickar på **Skapa** så skapar du en live-anslutning till datamängden, funktionen för rapportskapande öppnas med hela datamängden tillgänglig. Du har inte gjort en kopia av datamängden. Datamängden finns fortfarande på dess ursprungliga plats. Du kan använda alla tabeller och mått i datamängden för att skapa egna rapporter. Begränsningar gällande säkerhet på radnivå (RLS) för datamängden gäller, så du ser endast data som du har behörighet att se baserat på din RLS-roll.

Du kan spara rapporten på den aktuella arbetsytan i Power BI-tjänsten eller publicera rapporten till en arbetsyta från Power BI Desktop. Power BI skapar automatiskt en post i listan över datamängder om rapporten baseras på en datamängd utanför arbetsytan. Ikonen för den här datamängden skiljer sig från ikonen för datamängder på arbetsytan: ![Ikon för delad datamängd](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)

På så sätt kan medlemmar i arbetsytan se vilka rapporter och instrumentpaneler som använder datamängder som är utanför arbetsytan. Posten visas information om datamängden och vissa utvalda åtgärder.

![Datamängdsåtgärder](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="find-an-endorsed-dataset"></a>Hitta en rekommenderad datamängd

Det finns två olika typer av rekommenderade datamängder. Datamängdsägare kan *höja upp* en datamängd som de rekommenderar till dig. Power BI-klientorganisationsadministratörer kan utse experter i din organisation som kan *certifiera* datamängder som alla kan använda. Både rekommenderade och certifierade datamängd visar *märken* som du ser både när du letar efter en datamängd och i listan över datamängder på en arbetsyta. 

- I Power BI-tjänsten: **Hämta data** > **Publicerade datamängder**.
- I Power BI Desktop: **Hämta data** > **Power BI-datamängder**.

    I dialogrutan **Välj en datamängd** visas rekommenderade datamängder överst i listan som standard. 

    ![Upphöjd datamängd](media/service-datasets-certify-promote/power-bi-dataset-promoted.png)

## <a name="next-steps"></a>Nästa steg

- [Använda datamängder mellan arbetsytor (förhandsversion)](service-datasets-across-workspaces.md)
- Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)
