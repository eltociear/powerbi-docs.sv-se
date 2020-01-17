---
title: Dubbelriktad korsfiltrering i Power BI Desktop
description: Aktivera korsfiltrering med hjälp av DirectQuery i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 8aeae0075ed32a832c27f475ef3786b7df76576c
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761782"
---
# <a name="enable-bidirectional-cross-filtering-for-directquery-in-power-bi-desktop"></a>Aktivera dubbelriktad korsfiltrering för DirectQuery i Power BI Desktop

När rapportskapare (och datamodellerare) filtrerar tabeller för att skapa en lämplig datavy kan det vara svårt att avhöra hur filtrering ska tillämpas på en rapport. Tabellens filtersammanhang på en tabell hålls på ena sidan av relationen, men inte den andra, vilket kräver komplexa DAX-formler för att få önskade resultat.

Med dubbelriktad korsfiltrering har rapportskapare (och datamodellerare) nu mer kontroll över hur filter tillämpas när du arbetar med relaterade tabeller. De kan tillämpa dessa filter på *både* sidor i en tabellrelation. Detta åstadkoms genom att låta filterkontexten spridas till en annan relaterad tabell på andra sidan av en tabellrelation.

## <a name="detailed-whitepaper-for-bidirectional-cross-filtering"></a>Detaljerat dokument för dubbelriktad korsfiltrering
Ett [detaljerat whitepaper](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) är tillgängligt som förklarar dubbelriktad mellan filtrering i Power BI Desktop (det omfattar även SQL Server Analysis Services 2016, som har samma funktioner).

* Hämta vårt whitepaper [dubbelriktad korsfiltrering för Power BI Desktop](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx)

## <a name="enabling-bidirectional-cross-filtering-for-directquery"></a>Aktivera dubbelriktad korsfiltrering för DirectQuery

Följande måste markeras i dialogrutan **Redigera relation** för att aktivera korsredigering:

* Riktningen för **korsfiltreringen** måste anges till **både**
* **Tillämpa säkerhetsfilter i båda riktningarna** måste också vara markerad

  ![](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

> [!NOTE]
> När du skapar DAX-formler för korsfiltrering i Power BI Desktop ska du använda *UserPrincipalName* (vilket är ofta samma som en användares inloggning, till exempel <em>joe@contoso.com</em>) i stället för *Användarnamn*. Därmed kan du behöva skapa en relaterad tabell som mappar *användarnamn* (eller EmployeeID, till exempel) till *UserPrincipalName*.

Mer information och exempel på hur dubbelriktad korsfiltrering fungerar, ta en titt på vårt [whitepaper](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) ovan.

