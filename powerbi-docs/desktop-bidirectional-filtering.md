---
title: "Dubbelriktad korsfiltrering i Power BI Desktop (förhandsversion)"
description: "Aktivera korsfiltrering med hjälp av DirectQuery i Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 7946a9389897c4401e581482c0630547a764616d
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="bidirectional-cross-filtering-using-directquery-in-power-bi-desktop-preview"></a>Dubbelriktad korsfiltrering med DirectQuery i Power BI Desktop (förhandsversion)

När rapportskapare (och datamodellerare) filtrerar tabeller för att skapa en lämplig datavy kan det vara svårt att avhöra hur filtrering ska tillämpas på en rapport. Tabellens filtersammanhang på en tabell hålls på ena sidan av relationen, men inte den andra, vilket kräver komplexa DAX-formler för att få önskade resultat.

Med dubbelriktad korsfiltrering har rapportskapare (och datamodellerare) nu mer kontroll över hur filter tillämpas när du arbetar med relaterade tabeller. De kan tillämpa dessa filter på *både* sidor i en tabellrelation. Detta åstadkoms genom att låta filterkontexten spridas till en annan relaterad tabell på andra sidan av en tabellrelation.

Ett [detaljerat whitepaper](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) är tillgängligt som förklarar dubbelriktad mellan filtrering i Power BI Desktop (det omfattar även SQL Server Analysis Services 2016, som har samma funktioner).

* Hämta vårt whitepaper [dubbelriktad korsfiltrering för Power BI Desktop](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx)

### <a name="enabling-bidirectional-cross-filtering-for-directquery"></a>Aktivera dubbelriktad korsfiltrering för DirectQuery
Du måste först aktivera korsfiltrering för DirectQuery för att använda funktionen. Detta är en förhandsversionsfunktion, vilket innebär att dess tillgänglighet och beteende kan ändras i kommande versioner av Power BI Desktop.

För att aktivera korsfiltrering för DirectQuery i Power BI Desktop, välj **Arkiv > Alternativ och inställningar > Alternativ**, markera kryssrutan bredvid **aktivera korsfiltrering i båda riktningarna för DirectQuery**, som visas i följande bild.

![](media/desktop-bidirectional-filtering/bidirectional-filtering_1.png)

> [!NOTE]
> När du skapar DAX-formler för korsfiltrering i Power BI Desktop ska du använda *UserPrincipalName* (vilket är ofta samma som en användares inloggning, till exempel *joe@contoso.com*) i stället för *Användarnamn*. Därmed kan du behöva skapa en relaterad tabell som mappar *användarnamn* (eller EmployeeID, till exempel) till *UserPrincipleName*.
> 
> 

Följande måste markeras i dialogrutan **Redigera relation** för att aktivera korsredigering:

* Riktningen för **korsfiltreringen** måste anges till **både**
* **Tillämpa säkerhetsfilter i båda riktningarna** måste också vara markerad
  
  ![](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

Mer information och exempel på hur dubbelriktad korsfiltrering fungerar, ta en titt på vårt [whitepaper](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) ovan.

