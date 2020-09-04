---
title: Uppdateringsöversikt i Power BI
description: Lär dig hur du använder uppdateringsöversikten i Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/27/2020
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: 44aeb5030008d17a9998e8357f23d47524f11512
ms.sourcegitcommit: 1aaa742c239a3119cdaad698be5a7553b68801fa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/27/2020
ms.locfileid: "89040234"
---
# <a name="refresh-summaries-for-power-bi"></a>Uppdateringsöversikt i Power BI

Sidan med **översikt över uppdateringar** i Power BI-administratörsportalen ger kontroll över och insikt i dina uppdateringsscheman, kapaciteter och potentiella överlappningar i uppdateringsscheman. På sidan kan du avgöra om du behöver justera uppdateringsscheman, lära dig felkoder för uppdateringsproblem och hantera schemaläggning av datauppdatering på korrekt sätt. 

Sidan har två vyer:

* **Historik** – visar historiksammanfattning för uppdateringar för Power BI Premium-kapaciteter som du är administratör för.

* **Schema** – visar schemavyn för schemalagd uppdatering, vilket även kan avslöja problem med tider som har överlappningar.

Du kan också exportera information om en uppdateringshändelse till en CSV-fil, som kan ge viktig information och insikter om uppdateringshändelser eller fel som kan påverka prestanda eller genomförandet av schemalagda uppdateringshändelser.

I följande avsnitt tar vi en titt på var och en av dessa vyer. 

## <a name="refresh-history"></a>Uppdateringshistorik

Du kan välja vyn **Historik** genom att klicka på **Historik** på sidan med uppdateringsöversikten.

![Historikvyn i uppdateringsöversikten](media/refresh-summaries/refresh-summaries-01a.jpg)

Historiken ger en översikt över resultaten av de senaste schemalagda uppdateringarna av de kapaciteter som du har administratörsbehörighet för. Du kan sortera vyn efter valfri kolumn genom att klicka på kolumnen. Du kan välja att sortera vyn efter kolumn i stigande ordning, fallande ordning eller med textfilter.

![sortera historikvyn](media/refresh-summaries/refresh-summaries-01b.jpg)

I historikvyn baseras data för en viss uppdatering på de 60 senaste posterna för varje schemalagd uppdatering.

Du kan också exportera information för en schemalagd uppdatering till en CSV-fil som innehåller detaljerad information, till exempel felmeddelanden för varje uppdateringshändelse. Om du exporterar till en CSV-fil kan du sortera filen efterkolumner, söka efter ord, sortera efter felkoder eller ägare med mera. Följande bild visar ett exempel på en exporterad CSV-fil. 

![Exportera information om en uppdatering](media/refresh-summaries/refresh-summaries-05.jpg)

Med informationen i den exporterade filen kan du granska kapacitet, varaktighet och eventuella felmeddelanden som registrerats för uppdateringsinstansen. 


## <a name="refresh-schedule"></a>Uppdateringsschema

Du kan välja **schemavyn** genom att klicka på **Schema** i uppdateringsöversikten. I schemavyn visas schemaläggningsinformation för veckan, uppdelat i 30 minuter långa tidsperioder. 

![Schemavy](media/refresh-summaries/refresh-summaries-02a.jpg)

Schemavyn är mycket användbar för att avgöra om det är tillräckligt lång tid mellan uppdateringshändelser så att alla uppdateringar hinner slutföras utan överlappningar, eller om det finns schemalagda uppdateringshändelser som tar för lång tid och skapar konkurrens om resurser. Om du hittar konkurrens mellan resurser justerar du dina uppdateringsscheman för att undvika konflikter eller överlappningar så att de schemalagda uppdateringarna kan slutföras. 

![Schemavy](media/refresh-summaries/refresh-summaries-02.jpg)

Kolumnen *Bokad uppdateringstid (minuter)* är en beräkning av medelvärdet för upp till 60 poster för varje associerad datauppsättning. Det numeriska värdet för varje tidsperiod på 30 minuter är summan av det antal minuter som beräknats för alla uppdateringar som schemalagts att starta på den tiden **och** alla schemalagda uppdateringar som ställts in på att starta i den *föregående* tidsperioden, men vars genomsnittliga varaktighet överlappar (går in i) den valda tidsperioden.

Kolumnen *Tillgänglig uppdateringstid (minuter)* är en beräkning av hur många minuter som är tillgängliga för uppdatering vid varje tidpunkt, minus den uppdatering som redan har schemalagts för tidpunkten. Om din P2-prenumeration till exempel innehåller 12 uppdateringar som körs samtidigt, har du 12 stycken på 30 minuter. 12 uppdateringar x 30 minuter varje gång = 360 tillgängliga minuter för uppdatering inom den tiden. Om du har en schemalagd uppdatering som tar 20 minuter är *Tillgänglig uppdateringstid (minuter)* 340 minuter (360 totalt antal tillgängliga minuter, minus 20 minuter som redan är schemalagda = 340 minuter är fortfarande tillgängligt). 

Du kan välja en tid och sedan välja tillhörande **informationsknapp** om du vill se vilka schemalagda uppdateringshändelser som bidrar till den bokade uppdateringstiden, ägarna och hur lång tid de tar att slutföra.

Låt oss titta på ett exempel på hur det fungerar. Följande dialogrutan visas när vi väljer tiden 20:30 på söndag och klickar på **information**.

![Schemavy](media/refresh-summaries/refresh-summaries-04.jpg)

Det inträffar tre schemalagda uppdateringshändelser inom den här tidsperioden. 

De schemalagda uppdateringarna nummer 1 och 3 är båda schemalagda för tiden 20:30, vilket vi kan se genom att titta på värdet i kolumnen **Schemalagd tid**. Deras genomsnittliga tid är 4:39 respektive sex sekunder (0:06). Inga problem där.

Men schemalagd uppdatering nummer 2 är schemalagd för tiden 20:00, men den tar i genomsnitt över 48 minuter att slutföra (se kolumnen **Genomsnittlig varaktighet**) och uppdateringshändelsen överlappar nästa 30-minutersperiod. 

Det är inte bra. Administratören bör i det här fallet kontakta ägarna till den schemalagda uppdateringsinstansen och föreslå att de hittar en annan tidsperiod för den schemalagda uppdateringen, eller att de schemalägger om de andra uppdateringarna eller hittar någon annan lösning för att undvika överlappning. 


## <a name="next-steps"></a>Nästa steg

- [Datauppdatering i Power BI](refresh-data.md)  
- [Power BI Gateway – Personal](service-gateway-personal-mode.md)  
- [Lokal datagateway (personligt läge)](service-gateway-onprem.md)  
- [Felsöka den lokala datagatewayen](service-gateway-onprem-tshoot.md)  
- [Felsöka Power BI Gateway – Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)