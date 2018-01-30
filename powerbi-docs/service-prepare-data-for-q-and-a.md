---
title: "Så här får du dina Excel-data att fungera bra med frågor och svar i Power BI"
description: "Så här får du dina data att fungera bra med frågor och svar i Power BI"
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
ms.date: 01/18/2018
ms.author: mihart
ms.openlocfilehash: 92d75bc3df3a3403f77fb350b4acfe1325e707d2
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-make-your-excel-data-work-well-with-qa-in-power-bi"></a>Så här får du dina Excel-data att fungera bra med frågor och svar i Power BI
Om du är en person som skapar datamodeller eller bygger Excel-arbetsböcker som ska användas med Power BI kan du läsa på...

I Power BI kan du med vanliga frågor och svar söka efter strukturerade data och välja rätt visualisering för din fråga – det är det som gör det till ett sådant fascinerande verktyg att arbeta med.   

Frågor och svar fungerar på alla överförda Excel-filer som innehåller tabeller, intervall eller PowerPivot-modeller, men ju fler optimeringar och datarensningar du gör, desto mer robust prestandan för frågor och svar.  Om du planerar att dela rapporter och instrumentpaneler baserat på din datauppsättning, vill du att dina kollegor lätt kan ställa frågor och få kvalitetssvar.

### <a name="how-qa-works-with-excel"></a>Så här fungerar frågor och svar med Excel
Frågor och svar har en uppsättning kärnfunktioner som förstår naturligt språk och som arbetar med dina data. Det har kontextberoende nyckelordssökning för dina Excel-tabeller, kolumner och beräknade fältnamn. Dessutom har det inbyggd kunskap för att filtrera, sortera, aggregera, gruppera och visa data. 

I exempelvis en Excel-tabell med namnet ”Försäljning” och kolumnerna ”Produkt”, ”Månad”, ”Sålda enheter”, ”Bruttoförsäljning” och ”Resultat” kan du ställa frågor om någon av dessa entiteter.  Du kan begära att försäljning eller total vinst per månad ska visas, att produkterna sorteras efter sålda enheter och mycket annat. Läs mer om de [typer av frågor som du kan ställa](power-bi-q-and-a.md) och [de visualiseringstyper som du kan ange i en Frågor och svar-fråga](power-bi-visualization-types-for-reports-and-q-and-a.md).

### <a name="prepare-an-excel-dataset-for-qa"></a>Förbered en Excel-datauppsättning för frågor och svar
Funktionen Frågor och svar använder sig av namnen på tabeller, kolumner och beräknade fält när den besvarar dataspecifika frågor, vilket innebär att det du kallar entiteter i din arbetsbok är viktigt!

Här får du några tips om hur du kan utnyttja Frågor och svar på bästa sätt i din arbetsbok.

* Kontrollera att dina data finns i en Excel-tabell. Så här [skapar du en Excel-tabell](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664?ui=en-US&rs=en-US&ad=US).
* Kontrollera att namnen på dina tabeller, kolumner och beräknade fält är logiska med naturligt språk.
  
  Om du t.ex. har en tabell med försäljningsdata, så anropa tabellen ”Sales”. Kolumnnamn som “Year”, “Product”, “Sales Rep”, och “Amount” fungerar väl med Frågor och svar.

* Om arbetsboken har en Power Pivot-datamodell, kan du göra ytterligare optimeringar. Läs mer i [Avmystifiera Power BI Q&A, del 2](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-2.aspx) från vårt interna expertteam när det gäller naturligt språk.

* Öppna datauppsättningen i Power BI Desktop och skapa nya kolumner, skapa beräknade mått, sammanfoga fält för att skapa unika värden, klassificera data efter typ (till exempel datum, strängar, geografi, bilder, URL:er), med mera.

## <a name="next-steps"></a>Nästa steg
Gå tillbaka till [Frågor och svar i Power BI](power-bi-q-and-a.md)  
[Förbered lokala datauppsättningar för frågor och svar](service-q-and-a-direct-query.md)   
[Snabbstart för frågor och svar](power-bi-visualization-introduction-to-q-and-a.md)  
[Hämta data (för Power BI)](service-get-data.md)  

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

