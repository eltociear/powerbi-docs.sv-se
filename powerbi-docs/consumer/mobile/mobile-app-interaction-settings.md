---
title: Konfigurera inställningar för rapportinteraktion
description: Lär dig hur du åsidosätter standardinställningarna för interaktion för rapporter.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: painbar
ms.openlocfilehash: fee89c65328b70e1f312b39fbad75d7148bd92f2
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542299"
---
# <a name="configure-report-interaction-settings"></a>Konfigurera inställningar för rapportinteraktion

## <a name="overview"></a>Översikt

Power BI-mobilappen har ett antal konfigurerbara inställningar för ”interaktion” som gör att du kan styra hur du interagerar med dina data och definiera beteendet för vissa element i Power BI-mobilappen. För närvarande finns det inställningar för
* [Enkeltryck eller dubbeltryck på visuella rapportobjekt](#single-tap)
* [Dockad eller dynamisk rapportsidfot](#docked-report-footer-android-phones) (Android)
* [Knappinitierad rapportuppdatering eller ”dra nedåt för att uppdatera”-åtgärden](#report-refresh-android-phones) (Android)

Om du vill gå till interaktionsinställningarna trycker du på din profilbild för att öppna [sidopanelen](./mobile-apps-home-page.md#header). Välj sedan **Inställningar**och leta reda på avsnittet **Interaktion**.

![Interaktionsinställningar](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-section.png)

>[!NOTE]
>Interaktionsinställningar för uppdateringsknappen och för dockning av rapportsidfoten har för närvarande ingen inverkan på rapporter för rapportservern. Detta kommer att ändras med rapportserverversionen som släpps i januari 2020.

## <a name="interaction-settings"></a>Interaktionsinställningar

### <a name="single-tap"></a>Enkeltryck
När du hämtar Power BI-mobilappen är den inställd på enkeltryck. Det innebär att när du trycker på ett visuellt objekt för att utföra en viss åtgärd, till exempel välja ett utsnittsobjekt, korsmarkera, klicka på en länk eller knapp och så vidare, så kommer både det visuella objektet att väljas och den valda åtgärden att utföras.

Om du vill kan du inaktivera interaktion med enkeltryck. I så fall används interaktion med dubbeltryck. När interaktion med dubbeltryck används trycker du först på ett visuellt objekt för att välja det och sedan en gång till i det visuella objektet för att utföra önskad åtgärd.

### <a name="docked-report-footer-android-phones"></a>Dockad rapportsidfot (Android-telefoner)

Inställningen för dockad rapportsidfot bestämmer om rapportsidfoten ska vara dockad (dvs. fäst och alltid synlig) längst ned i rapporten, eller döljas och visas på nytt beroende på dina åtgärder i rapporten, till exempel när du rullar.

I Android-telefoner är inställningen för dockad rapportsidfot **På** som standard, vilket innebär att rapportsidfoten är dockat och alltid synlig längst ned i rapporten. Ändra inställningen till **Av** om du föredrar en dynamisk rapportsidfot som visas och försvinner, beroende på dina åtgärder i rapporten.

### <a name="report-refresh-android-phones"></a>Rapportuppdatering (Android-telefoner)

Inställningen för rapportuppdatering definierar hur du initierar rapportuppdateringar. Du kan välja att antingen ha en uppdateringsknapp på alla rapportsidhuvuden eller använda ”dra nedåt för att uppdatera”-åtgärden (dra nedåt från den övre kanten till den nedre) på rapportsidan för att uppdatera rapporten. Figuren nedan visar de två alternativen. 

![Uppdateringsknapp jämfört med dra nedåt för att uppdatera](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-refresh-button-versus-pull.png)

I Android-telefoner läggs en uppdateringsknapp till som standard.

Om du vill ändra inställningen för rapportuppdatering går du till rapportuppdateringsobjektet i interaktionsinställningarna. Den aktuella inställningen visas. Tryck på värdet för att öppna ett popup-fönster där du kan välja ett nytt värde.

![Ange uppdatering](./media/mobile-app-interaction-settings/powerbi-mobile-app-interactions-set-refresh.png)

## <a name="remote-configuration"></a>Fjärrkonfiguration

Interaktioner kan också fjärrkonfigureras av en administratör med hjälp av ett MDM-verktyg med en appkonfigurationsfil. På så sätt kan du standardisera upplevelsen för rapportinteraktion i organisationen, eller för specifika grupper med användare i organisationen. Mer information finns i [Konfigurera interaktion med hantering av mobila enheter](./mobile-app-configuration.md).


## <a name="next-steps"></a>Nästa steg
* [Interagera med rapporter](./mobile-reports-in-the-mobile-apps.md#interact-with-reports)
* [Konfigurera interaktion med hjälp av hantering av mobila enheter](./mobile-app-configuration.md)
