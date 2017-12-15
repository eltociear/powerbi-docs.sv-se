---
title: "Få dina data att fungera bra med Frågor och svar i Power BI"
description: "Få dina data att fungera bra med Frågor och svar i Power BI"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 09/26/2017
ms.author: mihart
ms.openlocfilehash: 499c3beca9046af9336de6dfec96994004050986
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="make-your-data-work-well-with-qa-in-power-bi"></a>Få dina data att fungera bra med Frågor och svar i Power BI
Om du är en person som skapar datamodeller eller bygger Excel-arbetsböcker som ska användas med Power BI kan du läsa på...

I Power BI kan du med vanliga frågor och svar söka efter strukturerade data och välja rätt visualisering för din fråga – det är det som gör det till ett sådant fascinerande verktyg att arbeta med.   

Frågor och svar fungerar på alla överförda Excel-filer som innehåller tabeller, intervall eller PowerPivot-modeller, men ju fler optimeringar och datarensningar du gör, desto mer robust prestandan för frågor och svar. 

## <a name="how-qa-works"></a>Så här fungerar frågor och svar
Frågor och svar har en uppsättning kärnfunktioner som förstår naturligt språk och som arbetar med dina data. Det har kontextberoende nyckelordssökning för dina Excel-tabeller, kolumner och beräknade fältnamn. Dessutom har det inbyggd kunskap för att filtrera, sortera, aggregera, gruppera och visa data. 

I exempelvis en Excel-tabell med namnet ”Försäljning” och kolumnerna ”Produkt”, ”Månad”, ”Sålda enheter”, ”Bruttoförsäljning” och ”Resultat” kan du ställa frågor om någon av dessa entiteter.  Du kan begära att försäljning eller total vinst per månad ska visas, att produkterna sorteras efter sålda enheter och mycket annat. Läs mer om de [typer av frågor som du kan ställa](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-1.aspx), och [ställ frågor med hjälp av en frågemall](service-q-and-a.md) och [de visualiseringstyper som du kan hitta genom Frågor och svar](power-bi-visualization-types-for-reports-and-q-and-a.md).

## <a name="prepare-a-workbook-for-qa"></a>Förbereda en arbetsbok för Frågor och svar
Funktionen Frågor och svar använder sig av namnen på tabeller, kolumner och beräknade fält när den besvarar dataspecifika frågor, vilket innebär att det du kallar entiteter i din arbetsbok är viktigt!

Här får du några tips om hur du kan utnyttja Frågor och svar på bästa sätt i din arbetsbok.

* Kontrollera att dina data finns i en Excel-tabell. Så här [skapar du en Excel-tabell](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664?ui=en-US&rs=en-US&ad=US).
* Kontrollera att namnen på dina tabeller, kolumner och beräknade fältet har en meningsfull betydelse på engelska.
  
  Om du t.ex. har en tabell med försäljningsdata, så anropa tabellen ”Sales”. Kolumnnamn som “Year”, “Product”, “Sales Rep”, och “Amount” fungerar väl med Frågor och svar.

> [!NOTE]
> Om arbetsboken har en Power Pivot-datamodell, kan du göra ytterligare optimeringar. Läs mer i [Avmystifiera Power BI Q&A, del 2](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-2.aspx) från vårt interna expertteam när det gäller naturligt språk.
> 
> 

## <a name="next-steps"></a>Nästa steg
[Frågor och svar i Power BI](service-q-and-a.md)  
[Självstudier: Introduktion till Frågor och svar i Power BI](power-bi-visualization-introduction-to-q-and-a.md)  
[Hämta data (för Power BI)](service-get-data.md)  
[Power BI – grundläggande begrepp](service-basic-concepts.md)

Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

