---
title: Mallinnehållspaketsupplevelser i Power BI
description: Mallinnehållspaketsupplevelser
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/09/2017
ms.author: maggies
ms.openlocfilehash: 723aa8e1a6817551f5e8f1c0cf096d185b1e53ae
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/21/2018
ms.locfileid: "46543793"
---
# <a name="template-content-pack-experiences-in-power-bi"></a>Mallinnehållspaketsupplevelser i Power BI
Det här avsnittet beskriver en typisk upplevelse för en användare som ansluter till ett ISV-[innehållspaket](consumer/end-user-connect-to-services.md).

Testa anslutningsupplevelsen själv genom att ansluta till ett utgivet innehållspaketet på https://app.powerbi.com/getdata/services (som [GitHub-innehållspaketet](https://app.powerbi.com/getdata/services/github) vilket beskrivs nedan).

## <a name="connect"></a>Anslut
En användare kommer igång genom att bläddra genom galleriet med innehållspaketet och välja ett innehållspaket att ansluta till. Innehållspaketposten innehåller ett namn, en ikon och en beskrivande text som ger mer information till användaren.

![anslut](media/template-content-pack-experience/github_data.png)

![anslut](media/template-content-pack-experience/github_connect.png)

## <a name="parameters"></a>Parametrar
När det är valt, kommer användaren att uppmanas att ange parametrar (vid behov). Dialogrutan parametrar anges deklarativt av skaparen vid skapandet av innehållspaketet.

För tillfället är gränssnittet för parametrar väldigt grundläggande. Det finns inget sätt att räkna upp listrutor och indatavalidering är begränsad till regex.

![parametrar](media/template-content-pack-experience/github_params.png)

## <a name="credentials"></a>Autentiseringsuppgifter
Efter parametrarna uppmanas användaren att logga in.  Om källan har stöd för flera typer av autentisering, kommer användaren att välja ett alternativ. Om källan kräver OAuth, visas tjänstens inloggningsgränssnitt när användaren trycker på Logga In.  Annars kan användaren ange sina autentiseringsuppgifter i den angivna dialogrutan.

![Autentiseringsuppgifter](media/template-content-pack-experience/github_login.png)

![anslut](media/template-content-pack-experience/github_creds2.png)

## <a name="instantiation"></a>Instansiering
När inloggningen lyckas, visas artefakter som ingår i innehållspaketet, modeller, rapporter och instrumentpaneler, i navigeringsfältet.  Dessa artefakter läggs till i varje användares konto.  Datan läses in asynkront för att fylla i datauppsättningen (modell).  Användaren kan sedan använda instrumentpanelen, rapporter och modellen.

Som standard konfigureras ett dagligt uppdateringsschema för användaren som utvärderar frågorna i modellen.  Autentiseringsuppgifterna som anges för användaren måste tillåta dem att uppdatera data utan att vara närvarande.

![Instansiering](media/template-content-pack-experience/github_dashboard.png)

## <a name="exploration-and-monitoring"></a>Utforskning och övervakning
När innehållspaketet är hydrerat till användarnas konton, kan de utforska och övervaka data/insikter.

Detta omfattar vanligtvis:

* Visa och anpassa instrumentpanelen.
* Visa och anpassa rapporten.
* Ställa frågor om dina data med naturligt språk
* Använda arbetsytan utforskning för att utforska data i datamodellen

Överväganden ska göras för att tillhandahålla modellering för naturligt språk (synonymer) och ett förståeligt modellschema för att möjliggöra en bättre utforskningsupplevelse.

