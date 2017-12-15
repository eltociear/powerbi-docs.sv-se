---
title: "Fästa en panel på en Power BI-instrumentpanel från Excel"
description: "Fäst en panel på en Power BI-instrumentpanel från Excel i OneDrive för företag. Fästa intervall, diagram, tabeller"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: l8JoB7w0zJA
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/26/2017
ms.author: mihart
ms.openlocfilehash: 855ecbe74fa4bf4ab1b1f81f22f2bab278adddb9
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="pin-a-tile-to-a-power-bi-dashboard-from-excel"></a>Fästa en panel på en Power BI-instrumentpanel från Excel
Innan du kan fästa en panel från Excel-arbetsboken, ansluter du arbetsboken till Power BI-tjänsten (app.powerbi.com). Att ansluta en arbetsbok innebär i stort sett att använda en länkad skrivskyddad version av arbetsboken i Power BI-tjänsten för att du ska kunna fästa intervall på instrumentpaneler. Du kan även fästa ett helt kalkylblad på en instrumentpanel.  
Om en arbetsbok har delats med dig kan du visa panelerna som ägaren fäst, men du kan inte skapa några instrumentpaneler själv. 

Detaljerad information om hur Excel och Power BI fungerar tillsammans finns i [Hämta data från Excel-arbetsböcker](http://go.microsoft.com/fwlink/?LinkID=521962).

Se när Will visar flera olika sätt att importera data från och ansluta till Excel-arbetsböcker.

<iframe width="560" height="315" src="https://www.youtube.com/embed/l8JoB7w0zJA" frameborder="0" allowfullscreen></iframe>

## <a name="connect-your-excel-workbook-from-onedrive-for-business-to-power-bi"></a>Anslut din Excel-arbetsbok från OneDrive för företag till Power BI
När du väljer **Anslut** visas arbetsboken i Power BI precis som den skulle ha gjort i Excel Online. Men till skillnad från i Excel Online har du några bra funktioner som hjälper dig fästa element från kalkylbladen direkt på instrumentpanelerna.

Du kan inte redigera din arbetsbok i Power BI. Men om du behöver göra ändringar kan du välja pennikonen på fliken **Arbetsböcker** i arbetsytan och sedan välja att redigera din arbetsbok i Excel Online eller öppna den i Excel på datorn. Alla ändringar du gör sparas i arbetsboken på OneDrive.

1. Ladda upp din arbetsbok till ditt OneDrive för företag.
2. [Anslut till arbetsboken](service-excel-workbook-files.md) från Power BI.
3. Arbetsboken läggs till på fliken **Arbetsböcker** på arbetsytan i Power BI.  Ikonen ![](media/service-dashboard-pin-tile-from-excel/pbi_workbookicon.png) visar att det är en Excel-arbetsbok och en gul asterisk visar att den är ny.
   
    Ändringar som du gör i arbetsboken i Power BI sparas inte och påverkar inte den ursprungliga arbetsboken på OneDrive för företag. Om du sorterar, filtrerar eller ändrar värden i Power BI kommer ändringarna inte att sparas eller fästas. Välj pennikonen för att öppna den i Excel Online om du vill uppdatera arbetsboken. Det kan ta några minuter innan ändringar i arbetsboken i Excel Online uppdateras i panelerna.     
   
   ![](media/service-dashboard-pin-tile-from-excel/power-bi-workbooks.png)
4. Öppna arbetsboken i Power BI genom att välja arbetsbokens namn.
   
   ![](media/service-dashboard-pin-tile-from-excel/power-bi-opened.png)

## <a name="pin-a-range-of-cells-to-a-dashboard"></a>Fästa ett cellområde på en instrumentpanel
Ett sätt att lägga till en ny [instrumentpanel](service-dashboard-tiles.md) är från en Excel-arbetsbok i Power BI. Områden kan fästas från Excel-arbetsböcker som har sparats i OneDrive för företag eller andra gruppdelade dokumentbibliotek. Områdena kan innehålla data, diagram, tabeller, pivottabeller, pivotdiagram och andra delar av Excel.

1. Markera de celler som du vill fästa på en instrumentpanel.
   
    ![](media/service-dashboard-pin-tile-from-excel/pbi_selectrange.png)
2. Välj fästikonen ![](media/service-dashboard-pin-tile-from-excel/pbi_pintile_small.png). 
3. Fäst panelen på en befintlig eller ny instrumentpanel. 
   
   * Befintlig instrumentpanel: Välj instrumentpanelens namn i listrutan.
   * Ny instrumentpanel: Skriv instrumentpanelens namn.
   
   ![](media/service-dashboard-pin-tile-from-excel/pbi_dashdialog1.png)
4. Välj **Fäst**. Genom ett meddelande (nära det övre högra hörnet) får du reda på att området har lagts till som en panel på instrumentpanelen. 
   
    ![](media/service-dashboard-pin-tile-from-excel/power-bi-go-to-dashboard.png)
5. Välj **Gå till instrumentpanelen**. Härifrån kan du [byta namn, ändra storlek, länka och flytta](service-dashboard-edit-tile.md) den fastsatta visualiseringen. Som standard öppnar den fastsatta panelen arbetsboken i Power BI.

## <a name="pin-an-entire-table-or-pivot-chart-to-a-dashboard"></a>Fästa en hel tabell eller ett pivotschema på en instrumentpanel
Följ stegen ovan, men i stället för att markera ett cellområde väljer du en hel tabell eller en pivottabell.

Markera hela intervallet för tabellen för att fästa en tabell och inkludera rubrikerna.  Om du ska fästa en pivottabell bör du vara noga med att allt synligt i pivottabellen tas med, inklusive filter om det har använts.

 ![](media/service-dashboard-pin-tile-from-excel/pbi_selecttable.png)

En panel som skapas från en tabell eller pivottabell visar hela tabellen.  Om du lägger till/tar bort/filtrerar rader eller kolumner i den ursprungliga arbetsboken, kommer de också att läggas till/tas bort/filtreras i panelen.

## <a name="view-the-workbook-linked-to-the-tile"></a>Visa arbetsboken som är länkad till panelen
Om du väljer en panel i arbetsboken öppnas den länkade arbetsboken i Power BI. Eftersom arbetsboksfilen finns på ägarens OneDrive för företag, måste du ha läsbehörighet för arbetsboken för att kunna se den. Om du inte har behörighet visas ett felmeddelande.  

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
Funktioner som inte stöds: Power BI använder Excel Services till att hämta arbetsbokens paneler. Eftersom vissa funktioner från Excel inte stöds i Excel Services REST API, kan de därför inte visas på panelerna i Power BI. Till exempel: Miniatyrdiagram, ikonen Ange villkorsstyrd formatering och tidsutsnitt. En fullständig lista med funktioner som inte stöds finns i [Funktioner som inte stöds i Excel Services REST API](http://msdn.microsoft.com/library/office/ff394477.aspx)

## <a name="next-steps"></a>Nästa steg
[Dela en instrumentpanel med länkar till en Excel-arbetsbok](service-share-dashboard-that-links-to-excel-onedrive.md)

[Hämta data från Excel-arbetsböcker](service-excel-workbook-files.md)

[Instrumentpaneler i Power BI](service-dashboards.md)

Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

