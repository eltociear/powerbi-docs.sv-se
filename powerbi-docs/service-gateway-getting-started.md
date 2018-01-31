---
title: "Kom igång med Power BI-gatewayar"
description: "Lär dig grunderna om datagatewayer för Power BI."
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
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 14c96dbc88784cd76099c25508409bcc24064e35
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="getting-started-with-power-bi-gateways"></a>Kom igång med Power BI-gatewayar
Välkommen till guiden **kom igång med Power BI-gatewayer**. I den här korta genomgången får du bekanta dig med vad en gateway gör, hur den fungerar och hur du får din egen gateway installerad, konfigurerad och klar att köras.  

![](media/service-gateway-getting-started/gw_gettingstarted_0a.png)

Gatewayar kan vara ett tekniska ämne och eftersom varje nätverks och företag skiljer sig åt, kan komplexiteten för en gateway vara betydande. För att hålla den komplexiteten stången så tar vi och börjar med grunderna.

## <a name="how-power-bi-gateways-work"></a>Så här fungerar Power BI-gatewayar
En **gateway** är programvara som möjliggör åtkomst till data som finns på ett privat, lokalt nätverk för efterföljande användning i en molnbaserad tjänst som Power BI. Den är som en grindvakt som lyssnar efter anslutningsbegäranden och ger dem bara åtkomst när en användare uppfyller vissa villkor (till exempel om de har tillåtelse att använda gatewayen). Detta gör att organisationer kan lämna databaser och informationslager på sina lokala nätverk, men ändå använda delmängder av dessa data på ett säkert sätt för att skapa övertygande rapporter och instrumentpaneler i Power BI.

En gateway skyddar också åtkomst och data genom att kryptera och komprimera alla data som skickas via den, samt eventuella lösenord som används för att ansluta till datakällor. Allt det här låter säkert väldigt enkelt, men det finns många detaljer att tänka på.

Ibland vill du ha en gateway bara för dig. Du kanske har en stor Excel-arbetsbok plus tre SQL-databaser med åratal av försäljnings- och marknadsföringsdata och du vill skapa en Power BI-instrumentpanel som visar dessa försäljningsdata från alla vinklar. Du är den enda personen som skapar rapporter, det är din Excel-arbetsbok och endast du använder databaserna för att skapa Power BI-rapporter. Du behöver bara en gateway för personligt bruk, inte för att dela datakällorna med alla andra.

En annan gång, kanske du är i en organisation med alla möjliga databastyper från olika leverantörer, inklusive Analysis Services, SAP, Oracle, IBM och olika andra datakällor och en massa människor behöver åtkomst till dem så att de kan skapa en massa rapporter. I det fallet behöver du en gateway som låter dig konfigurera åtkomst till alla dessa datakällor och sedan måste du dela den med en massa personer i din organisation. Det är en helt annan typ av gateway.

Lyckligtvis tillhandahåller Power BI två gatewayer, vilka passar de här två scenarierna väl. Dessa två gateway-erbjudanden från Power BI är som följer:

* **Lokal datagateway (personligt läge)** – tillåter en användare att ansluta till källor och kan inte delas med andra. Kan endast användas med Power BI.
* **Lokal datagateway** – flera användare kan ansluta till flera lokala datakällor och kan användas av Power BI, PowerApps, Flow och Azure Logic Apps, allt med en enda gateway-installation.

Båda gatewayerna utför en liknande funktion – de underlättar åtkomst till data som finns på ett privat lokalt nätverk så att data kan användas i molnbaserade tjänster som Power BI. Den personliga gatewayen kan användas av en person och endast av Power BI. Den **lokala datagatewayen** kan användas av många användare och av många tjänster.

Det finns tre delar, eller faser för att få en gateway att fungera:

* Installera gatewayen
* Lägg till användare till gatewayen (låter dem använda gatewayen)
* Anslut till datakällor

När du använder en gateway kan du dessutom göra något annat som kan vara viktigt:

* Uppdatera lokala data så att Power BI-rapporter kan uppdateras med nya data

Uppdatering av data innebär att Power BI-instrumentpaneler och rapporter ser nya ut och återspeglar den senaste informationen. När någon visar en rapport som du skapat med lokala data, kan den rapporten visa den senaste informationen, även om du har skapat rapporten för ett tag sedan.

Den första delen, installera en gateway, är enkelt. Att tillåta användare att komma åt gatewayen är också enkelt – du lägga bara till dem i en dialogruta i Power BI och det är klart. Att ansluta till datakällor kan vara krångligt, eftersom det finns så många olika datakällor och var och en har sina egna anslutningskrav och egenheter. Vi tar uppdatering i en annan guide så att vi kan fokusera på gatewayen i den här artikeln.

Vi tar det enkla först och går igenom hur du installerar en gateway.

## <a name="install-the-gateway"></a>Installera gatewayen
Om du vill installera en gateway, öppnar du Power BI-tjänsten (du kan använda den här länken för att starta Power BI-tjänsten i webbläsaren och logga in) och logga in med ditt Power BI-konto. I Power BI-tjänsten, väljer du **hämtningsikonen** i det övre högra hörnet, som det visas i följande bild och väljer **datagateway**.

![](media/service-gateway-getting-started/gw_gettingstarted_01.png)

Det tar dig till hämtningssidan, där du klickar på **hämta gateway** för att starta nedladdningen.

![](media/service-gateway-getting-started/gw_gettingstarted_02.png)

Den här skärmen ger dig en extremt kondenserad förklaring av vad en gateway gör. Den ger dig också några viktiga **varningar** – när du installerar en gateway, körs den faktiskt på den dator där du utför installationen. Om den datorn stängs av så stängs även gatewayen av (så den fungerar inte när den inte körs). Det är inte heller den bästa idén att installera på en dator som använder ett trådlöst nätverk så du bör använda en dator som är ansluten till ett fast nätverk.

När du är klar, väljer du **nästa** för att fortsätta med installationen.

![](media/service-gateway-getting-started/gw_gettingstarted_03.png)

Det är här du bestämmer vilken gateway som du installerar – lokal gateway eller en personlig gateway. I den här guiden, installerar vi den **lokala datagatewayen**.

Det finns några saker att tänka på vid den här beslutspunkten:

* Båda gatewayer kräver ett 64-bitars Windows-operativsystem.
* Gatewayer kan installeras på en domänkontrollant.
* Du kan installera upp till två lokala datagateways på samma dator, en i varje läge (personlig och standard). 
* Du kan inte ha fler än en gateway som körs i samma läge på samma dator.
* Du kan installera flera lokala datagateways på olika datorer och hantera dem från samma hanteringsgränssnitt för Power BI-gatewayen (exklusive personlig, se följande punkt).
* Du kan bara ha en gateway i personligt läge som körs för varje Power BI-användare. Om du installerar en annan gateway i personligt läge för samma användare, även om det är på en annan dator, ersätter den senaste installationen den befintliga tidigare installationen.

När vi väljer **nästa**, påbörjas gatewayinstallationen. Du måste ange var den ska installeras och standardplatsen är oftast bäst.

![](media/service-gateway-getting-started/gw_gettingstarted_06.png)

Installationen går snabbt och du får se ett statusfält.

![](media/service-gateway-getting-started/gw_gettingstarted_06a.png)

När du är nästan klar, måste du identifiera kontot som ska användas med gatewayen. Det ska vara det konto (användarnamn och lösenord) som du använder för att logga in på Power BI. Gatewayen är kopplad till ditt Power BI-konto och du konfigurerar gatewayer från Power BI-tjänsten.

![](media/service-gateway-getting-started/gw_gettingstarted_07.png)

Du loggas in, enligt följande bild.

![](media/service-gateway-getting-started/gw_gettingstarted_08.png)

När du har loggat in, måste du skapa en **återställningsnyckel**. Vi pratar mer om de i en annan artikel, men för tillfället räcker det att du vet att du behöver det för att återställa eller flytta din gateway.

![](media/service-gateway-getting-started/gw_gettingstarted_09.png)

När allt gått bra, visas ett fönster som talar om att din gateway är klar.

![](media/service-gateway-getting-started/gw_gettingstarted_10.png)

Det är allt som behövs för att installera en lokal gateway. Precis som jag lovade, var det rätt enkelt. Nästa steg är att antingen **lägga till användare** eller **lägga till datakällor** – du kan göra vilken som först och lägga till den andra efter den inledande konfigurationen.

Nästa avsnitt beskriver hur du lägger till användare till gatewayen och därefter kommer vi att diskutera vart du går för att lägga till datakällorna i gatewayen.

## <a name="add-users-to-a-gateway"></a>Lägg till användare till en gateway
Nu när vi har en installerad gateway, hanterar vi gatewayen från **Power BI-tjänsten**. Gå till hanteringsskärmen för gatewayer. I Power BI-tjänsten väljer du kugghjulsikonen i det övre högra hörnet och väljer sedan **hantera gatewayer**.

![](media/service-gateway-getting-started/gw_gettingstarted_15.png)

En sida i Power BI-tjänstens arbetsyta visas där du kan hantera dina gatewayer. Sidan **gatewayinställningar** ser ut så här.

![](media/service-gateway-getting-started/gw_gettingstarted_12.png)

Om du trycker eller klickar på **administratörer**, visas följande administratörers hanteringssida. Observera att detta bara är vilka användare som kan *administrera* gatewayen och att användare av gatewayen läggs till (eller tas bort) från varje enskild datakälla med hjälp av en annan sida – som vi går igenom i nästföljande stycken.

![](media/service-gateway-getting-started/gw_gettingstarted_13.png)

När du installerar och validerar (ansluter till) en datakälla, visas den under dess associerade gateway på vänster sida av den här **hantera gatewayer**-skärmen, som det visas i följande bild. Observera att det finns två avsnitt i den högra rutan som du kan växla mellan: **inställningar för datakälla** och **användare**. Skärmen direkt efter är avsnittet **inställningar för datakälla**.

![](media/service-gateway-getting-started/gw_gettingstarted_16.png)

När du väljer **användare**, får du en textruta där du kan skriva in användare från din organisation som du vill bevilja åtkomst till den valda datakällan. I följande skärm ser du att jag har lagt till Maggie och Adam.

När du börjar skriva in en e-postadress i textrutan, visar Power BI en lista över användare vars e-post matchar det du skriver så att du kan klicka på namnet och lägga till dem i listan.

Du kan också lägga till e-postgrupper (alias) så att grupper av människor får åtkomst såväl som enskilda användare.

![](media/service-gateway-getting-started/gw_gettingstarted_17.png)

När du har valt **Lägg till**, visas de tillagda medlemmarna i rutan och du kan lägga till fler om du vill. Det är lika enkelt att ta bort användare. Markera kryssrutan bredvid användarens namn och välj sedan **ta bort**-knappen under rutan.

![](media/service-gateway-getting-started/gw_gettingstarted_18.png)

Det är allt. Kom ihåg att du behöver lägga till användare i varje datakälla som du vill bevilja åtkomst. Varje datakälla har en separat lista med användare och du måste lägga till användare i varje datakälla separat.

## <a name="adding-data-sources"></a>Lägg till datakällor
För att göra din gateway användbar vill du förstås lägga till datakällor. Det är här lite av komplexiteten i Power BI gatewayer introduceras – det finns många olika datakällor och var och en har sina egna krav (och ofta sina egna nödvändiga drivrutiner).

Men innan vi skickar dig till en annan artikel, här är en titt på hur du går tillväga för att lägga till en datakälla. När du är på sidan **hantera gatewayer** i **Power BI-tjänsten**, markerar du den gateway som du vill lägga till en datakälla till och väljer **lägg till datakälla** i det övre vänstra hörnet på sidan, ovanför listan med dina gatewayer.

När du gör det, visas panelen **inställningar för datakälla** i den högra rutan, enligt följande bild. Där kan du namnge din datakälla (anges i textrutan **namn på datakälla**) och välja dess typ från listmenyn **typ av datakälla**.

![](media/service-gateway-getting-started/gw_gettingstarted_14.png)

Nu har du en installerad gateway och är redo att lägga till datakällor. Toppen! Resurserna i följande avsnitt innehåller information om datakällor, mer information om hur du använder gatewayer och annan användbar information.

## <a name="next-steps"></a>Nästa steg
[Använd den lokala datagatewayen](service-gateway-onprem.md)  
[Lokal datagateway – på djupet](service-gateway-onprem-indepth.md)  
[Lokal datagateway (personligt läge)](service-gateway-personal-mode.md)
[Felsök den lokala datagatewayen](service-gateway-onprem-tshoot.md)  

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

