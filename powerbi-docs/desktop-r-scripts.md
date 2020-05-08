---
title: Kör R-skript i Power BI Desktop
description: Kör R-skript i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 358a61c13418bd29a9e83ed7029e8b90f9a5988e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76161573"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>Kör R-skript i Power BI Desktop

Du kan köra R-skript direkt i Power BI Desktop och importera de resulterande datamängderna till en Power BI Desktop-datamodell.

## <a name="install-r"></a>Installera R

För att kunna köra R-skript i Power BI Desktop måste du installera R på den lokala datorn. Du kan hämta och installera R kostnadsfritt från flera platser, bland annat [Microsoft R Application Network](https://mran.revolutionanalytics.com/download/) och [CRAN Repository](https://cran.r-project.org/bin/windows/base/). Den aktuella versionen stöder Unicode-tecken och blanksteg (tomma tecken) i installationssökvägen.

## <a name="run-r-scripts"></a>Kör R-skript

Med bara några få steg i Power BI Desktop kan du köra R-skript och skapa en datamodell. Med datamodellen kan du skapa rapporter och dela dem i Power BI-tjänsten. R-skript i Power BI Desktop stöder nu talformat som innehåller decimaler (.) eller kommatecken (,).

### <a name="prepare-an-r-script"></a>Förbereda ett R-skript

Om du vill köra ett R-skript i Power BI Desktop, skapa skriptet i din lokala R-utvecklingsmiljö och kontrollera att den har körts.

Kontrollera att skriptet har körts i en ny och oförändrad arbetsyta för att köra skriptet i Power BI Desktop. Det innebär att alla paket och beroenden måste läsas in och köras uttryckligen. Du kan använda `source()` för att köra beroende skript.

När du förbereder och kör ett R-skript i Power BI Desktop, finns det några begränsningar:

* Eftersom endast dataramar importeras, måste de data som du vill importera i Power BI finnas i en dataram.
* Kolumner som har skrivits som Komplex eller Vektor importeras inte och ersätts med felvärden i den skapade tabellen.
* Värden som är `N/A` översätts till `NULL`-värden i Power BI Desktop.
* Alla R-skript som körs längre än 30 minuters avbryts.
* Interaktiva anrop i R-skriptet, t.ex. att vänta på indata från användaren, avbryter körningen av skriptet.
* När du konfigurerar arbetskatalogen i R-skriptet *måste* du definiera en fullständig sökväg till arbetskatalogen i stället för en relativ sökväg.

### <a name="run-your-r-script-and-import-data"></a>Kör R-skriptet och importera data

Nu kan du köra R-skriptet för att importera data till Power BI Desktop:

1. I Power BI Desktop väljer du **Hämta data**, **Annan** > **R-skript** och sedan **Anslut**:

    ![Anslut till R-skript, kategorin Annan, dialogrutan Hämta data, Power BI Desktop](media/desktop-r-scripts/r-scripts-1.png)

2. Om R är installerat på den lokala datorn kopierar du bara ditt skript till skriptfönstret och väljer **OK**. Den senast installerade versionen visas som R-motor.

    ![Dialogrutan R-skript, Power BI Desktop](media/desktop-r-scripts/r-scripts-2.png)

3. Välj **OK** att köra R-skriptet. När skriptet har körts kan du välja vilka resulterande dataramar du vill lägga till i Power BI-modellen.

Du kan styra vilken R-installation som ska användas för att köra skriptet. Om du vill ange installationsinställningarna för R väljer du **Arkiv** > **Alternativ och inställningar** > **Alternativ** och sedan **R-skriptning**. Under **R-skriptalternativ** visas de aktuella R-installationsalternativen i listrutan **Identifierade R-startkataloger**. Om den R-installation du önskar inte visas, väljer du **Annan** och bläddrar sedan till eller anger din önskade R-installationsmapp i **Ange en R-startkatalog**.

![R-skriptalternativ, dialogrutan Alternativ, Power BI Desktop](media/desktop-r-scripts/r-scripts-4.png)

### <a name="refresh"></a>Refresh

Du kan uppdatera ett R-skript i Power BI Desktop. När du uppdaterar ett R-skript, körs Power BI Desktop R-skriptet igen i Power BI Desktop-miljön.

## <a name="next-steps"></a>Nästa steg

Ta en titt på följande extra information om R i Power BI.

* [Skapa visuella Power BI-objekt med R](desktop-r-visuals.md)
* [Använd en extern R IDE med Power BI](desktop-r-ide.md)
