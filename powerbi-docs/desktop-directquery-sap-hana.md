---
title: "DirectQuery för SAP HANA i Power BI"
description: "Att tänka på när du använder DirectQuery med SAP HANA"
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 2b2e59371c96928a2b7c6b23bd393a80ecc3041a
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="directquery-and-sap-hana"></a>DirectQuery och SAP HANA
Du kan ansluta till **SAP HANA**-datakällor direkt med **DirectQuery**.

När du använder **SAP HANA** är det viktigt att förstå vissa aspekter av hur dess anslutningar behandlas så att:

* Resultaten motsvarar förväntningarna när SAP HANA-vyn innehåller icke-additiva mått (till exempel olika antal, eller medelvärden, istället för enkla summor)
* De resulterande frågorna är effektiva

Det är en god idé att börja med att ägna en stund åt att förstå beteendet för en relationskälla som **SQL Server**när frågan som definierats i **Hämta data** eller **Frågeredigeraren** utför en aggregering. I exemplet som följer returnerar en fråga som definierats i **Frågeredigeraren** det genomsnittliga priset enligt **ProductID**.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

Om data som importeras till Power BI (jämfört med DirectQuery), återges följande resultat:

* Data importeras på den aggregationsnivå som definierats av frågan som skapades i **Frågeredigeraren**. Till exempel, genomsnittligt pris på produkten. Detta resulterar i en tabell med de två kolumnerna *ProductID* och *AveragePrice* som kan användas i visuella objekt.
* I ett visuellt objekt kommer all efterföljande aggregation (exempelvis *summa*, *medelvärde*, *minimivärde*, övrigt) att utföras över den importerade informationen.  Till exempel, om du inkluderar *genomsnittspris* i ett visuellt objekt kommer *summa* att användas som standard. Summa returneras över *AveragePrice* för varje  *ProductID* – vilket i detta fall är 13,67. Samma gäller för en annan mängdfunktion (t.ex *minimivärde*, *medelvärde*, osv) som används på den visuella informationen. Till exempel returnerar *medelvärde* för *genomsnittspris* medelvärdet för 6,66, 4 och 3, vilket är lika med 4,56 och *inte* medelvärdet av *Pris* från 6 poster i den underliggande tabellen, vilket är 5,17.

Om **DirectQuery** används i stället för Importera gäller samma semantik och samma resultat skapas:

* Exakt samma data presenteras på rapportnivån för samma fråga – trots att data inte importeras.
* I ett visuellt objekt kommer all efterföljande aggregation (*summa*, *medelvärde*, *minimivärde*, övrigt) att utföras över den logiska tabellen från frågan. Och igen, ett visuellt objekt med *medelvärdet* av *Genomsnittspris* returnerar 4,56 igen.

Nu ska vi ta en titt på **SAP HANA**. Power BI kan arbeta med både *Analytiska vyer* och *Beräkningsvyer* i SAP HANA och båda innehåller mått. Men i dag följer metoden för SAP HANA samma principer som vi beskriv tidigare: frågan som definierades i **Hämta data** eller **Frågeredigeraren** avgör tillgängliga data och alla efterföljande aggregeringar i visuella objekt sker över dessa data. Samma gäller för både Importera och DirectQuery.

Men HANA:s specifika egenskaper gör att frågan i den första dialogrutan i **Get Data** eller **Frågeredigeraren** alltid är en aggregeringsfråga och kommer oftast innehålla mått där den aktuella aggregationen som används definieras av HANA-vyn.

Motsvarigheten till SQL Server exemplet ovan är att det finns en HANA-vy som innehåller **ID**, **ProductID**, **DepotID** och mått inklusive  **genomsnittspris** som har definierats i vyn som **Medelvärde av priset**.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_02.png)

Om upplevelsen **Hämta data** innehåller val för måtten **ProductID** och **AveragePrice** är detta den definierande frågan för vyn som begär aggregerade data (i ovanstående exempel har pseudo-SQL använts för enkelhetens skull, även om detta inte motsvarar den exakta syntaxen hos HANA SQL). I sådant fall kommer ytterligare aggregeringar som definieras i det visuella objektet att aggregeras ytterligare till följd av en sådan fråga. Igen, enligt beskrivningen ovan för **SQL Server** gäller detta både för Import och DirectQuery. Observera att frågan från **Hämta data** eller **Frågeredigeraren** med DirectQuery är ett underordnat val inom en fråga som har skickats till HANA. Således kommer inte alla data att läsas in före nästa aggregering.

Detta ger upphov till följande viktiga överväganden när du använder DirectQuery över HANA:

* Lägg märke till all annan aggregation som utförs i visuella objekt när måttet i HANA inte är additivt (till exempel inte en enkel *summa*, *minimivärde* eller *maxvärde*).
* I **Hämta data** eller **frågeredigeraren** tas endast de obligatoriska kolumnerna med för att hämta nödvändiga data, vilket speglar det faktum att resultatet måste vara en rimlig fråga som kan skickas till HANA. Till exempel, om du väljer dussintals kolumner eftersom du tror att de kommer att behövas för efterföljande visuella objekt kommer aggregatfrågan som används i det underordnade valet för DirectQuery att innehålla dessa dussintals kolumner. De kommer att prestera under förväntan.

Låt oss ta en titt på ett exempel. Om vi väljer fem kolumner i följande exempel (CalendarQuarter, Color, LastName, ProductLine, SalesOrderNumber) i dialogrutan **Hämta data** tillsammans med måttet OrderQuantity betyder det att följande SQL-fråga ställs till HANA om vi skapar ett enkelt visuellt objekt med Min OrderQuantity (minsta beställningskvantitet). Den skuggade delen är delmarkering som innehåller frågan från **Hämta data** / **frågeredigeraren**. Om den här delmarkeringen ger ett resultat med mycket hög kardinalitet kommer resultatet från HANA antagligen vara otillfredställande.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

Därför rekommenderas det att objekt som valts i **Hämta data** eller **frågeredigeraren** bör begränsas till nödvändiga objekt för att utgöra en lämplig fråga för HANA.

### <a name="next-steps"></a>Nästa steg
Mer information om DirectQuery finns i följande resurser:

* [DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery och SAP BW](desktop-directquery-sap-bw.md)
* [Lokal datagateway](service-gateway-onprem.md)

