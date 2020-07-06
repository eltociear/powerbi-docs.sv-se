---
title: Läs mer om vilka Python-paket som stöds
description: Vilka Python-paket som stöds respektive inte stöds i Power BI
author: otarb
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/26/2020
ms.author: otarb
LocalizationGroup: Connect to data
ms.openlocfilehash: b1dc77d2ebf0803430ceeace7e14bfa62a6d2a60
ms.sourcegitcommit: e8b12d97076c1387088841c3404eb7478be9155c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785243"
---
# <a name="create-visuals-by-using-python-packages-in-the-power-bi-service"></a>Skapa visuella objekt med hjälp av Python-paket i Power BI-tjänsten
Du kan använda det kraftfulla [Python-programmeringsspråket](https://www.python.org/) för att skapa visuella objekt i Power BI-tjänsten. Många Python-paket stöds i Power BI-tjänsten, och fler läggs till hela tiden.

Följande avsnitt innehåller en alfabetisk tabell som visar vilka Python-paket som stöds i Power BI. 

## <a name="request-support-for-a-new-python-package"></a>Begära stöd för ett nytt Python-paket
De Python-paket som stöds för **Power BI-tjänsten** hittar du i avsnittet med rubriken **Paket som stöds**. Om du vill begära support för ett Python-paket som inte finns i listan kan du kontakta [Power BI Ideas](https://ideas.powerbi.com).

## <a name="requirements-and-limitations-of-python-packages"></a>Krav och begränsningar avseende Python-paket
Det finns några krav och begränsningar när det gäller Python-paket:

* Aktuell Python-körning: Python 3.7.7.
* Power BI-tjänsten stöder, för det mesta, Python-paket med kostnadsfria programlicenser med öppen källkod, som GPL-2, 3 GPL, MIT + med flera.
* Power BI-tjänsten stöder paket som publicerats i PyPI. Tjänsten stöder inte privata eller anpassade Python-paket. Användarna uppmanas att göra sina privata paket tillgängliga på PyPI innan de begär att paketen ska vara tillgängliga i Power BI-tjänsten.
* När det gäller visuella Python-objekt i **Power BI Desktop** kan du installera alla paket, inklusive anpassade Python-paket.
* Av säkerhets- och sekretesskäl stöds inte Python-paket som tillhandahåller klient/server-frågor via webben i tjänsten. Nätverket blockeras för sådana försök.
* Godkännandeprocessen för att inkludera ett nytt Python-paket har ett beroendeträd. Vissa av de beroenden som måste installeras i tjänsten stöds inte.

## <a name="python-packages-that-are-supported-in-power-bi"></a>Python-paket som stöds i Power BI
I följande tabell visas vilka paket som **stöds** i Power BI-tjänsten.


|        Paket        |   Version   |                                   Länk                                   |
|-----------------------|-------------|--------------------------------------------------------------------------|
|matplotlib|3.2.1|https://pypi.org/project/matplotlib|
|numpy|1.18.4|https://pypi.org/project/numpy|
|pandas|1.0.1|https://pypi.org/project/pandas|
|scikit-learn|0.23.0|https://pypi.org/project/scikit-learn|
|scipy|1.4.1|https://pypi.org/project/scipy|
|s eaborn|0.10.1|https://pypi.org/project/seaborn|
|statsmodels|0.11.1|https://pypi.org/project/statsmodels|
|xgboost|1.1.0|https://pypi.org/project/xgboost|

## <a name="next-steps"></a>Nästa steg
Mer information om Python i Power BI finns i följande artiklar:

* [Skapa visuella Power BI-objekt med Python](desktop-python-visuals.md)
* [Köra Python-skript i Power BI Desktop](desktop-python-scripts.md)
* [Använda Python i frågeredigeraren](desktop-python-in-query-editor.md)
