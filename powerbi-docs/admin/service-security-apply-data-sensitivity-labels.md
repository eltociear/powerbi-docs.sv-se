---
title: Så här tillämpar du känslighetsetiketter i Power BI
description: Lär dig hur du tillämpar känslighetsetiketter i Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 08/10/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: be2f98341abd581cd2df717d19b3a9110548a2ec
ms.sourcegitcommit: 9e39232cbc28d8b39dfec5496db7ece9837b5e53
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "88049217"
---
# <a name="how-to-apply-sensitivity-labels-in-power-bi"></a>Så här tillämpar du känslighetsetiketter i Power BI

Microsoft Information Protection-känslighetsetiketter på dina rapporter, instrumentpaneler, datamängder och dataflöden kan skydda känsligt innehåll mot obehörig dataåtkomst och dataläckage. När du märker dina data med rätt känslighetsetiketter ser du till att endast behöriga användare kan komma åt dem. Den här artikeln beskriver hur du tillämpar känslighetsetiketter på ditt innehåll.

Följande krav måste vara uppfyllda för att du ska kunna använda känslighetsetiketter i Power BI:
* Du måste ha en Power BI Pro-licens och redigeringsbehörighet för det innehåll som du vill märka.
* Du måste vara medlem i en säkerhetsgrupp som har behörighet att tillämpa känslighetsetiketter. Mer information finns i [Aktivera känslighetsetiketter i Power BI](./service-security-enable-data-sensitivity-labels.md).
* Alla [licensieringskrav och andra krav](./service-security-enable-data-sensitivity-labels.md#licensing-and-requirements) måste uppfyllas.

Mer information om känslighetsetiketter i Power BI finns i [Känslighetsetiketter i Power BI](service-security-sensitivity-label-overview.md).

## <a name="applying-sensitivity-labels"></a>Använda känslighetsetiketter

När dataskydd har aktiverats för din klientorganisation ser du känslighetsetiketter i känslighetskolumnen i listvyn för instrumentpaneler, rapporter, datamängder och dataflöden.

![Aktivera känslighetsetiketter](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-01.png)

**Så här tillämpar du eller ändrar en känslighetsetikett för en rapport eller instrumentpanel**
1. Klicka på **Fler alternativ (...)** .
1. Välj **inställningar**.
1. Välj lämplig känslighetsetikett i fönstret Inställningar.
1. Spara inställningarna.

Följande bild visar hur du tillämpar en känslighetsetikett på en rapport

![Ange känslighetsetiketter](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-02.png)

**Så här tillämpar du eller ändrar en känslighetsetikett för en datamängd eller ett dataflöde**

1. Klicka på **Fler alternativ (...)** .
1. Välj **inställningar**.
1. Välj lämplig känslighetsetikett i fönstret Inställningar.
1. Tillämpa inställningarna.

Följande två bilder visar hur du tillämpar en känslighetsetikett på en datauppsättning.

Välj **Fler alternativ (...)** och sedan **Inställningar**.

![Öppna datamängsinställningarna](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-05.png)

På sidan Inställningar går du till avsnittet för känslighetsetiketter, väljer önskad etikett och klickar på **Använd**.

![Välj känslighetsetikett](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-06.png)

## <a name="removing-sensitivity-labels"></a>Ta bort känslighetsetiketter
Om du vill ta bort en känslighetsetikett från en rapport, en instrumentpanel, en datamängd eller ett dataflöde följer du [samma procedur som används för att tillämpa etiketter](#applying-sensitivity-labels) men väljer **(Ingen)** när du uppmanas att klassificera känsligheten för data. 

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

I [Känslighetsetiketter i Power BI](service-security-sensitivity-label-overview.md#limitations) finns en lista med begränsningar för känslighetsetiketter i Power BI.

## <a name="next-steps"></a>Nästa steg

I den här artikeln beskrivs hur du tillämpar känslighetsetiketter i Power BI. De här artiklarna innehåller mer information om dataskydd i Power BI. 

* [Översikt av känslighetsetiketter i Power BI](./service-security-sensitivity-label-overview.md)
* [Aktivera känslighetsetiketter i Power BI](./service-security-enable-data-sensitivity-labels.md)
* [Använda Microsoft Cloud App Security-kontroller i Power BI](./service-security-using-microsoft-cloud-app-security-controls.md)