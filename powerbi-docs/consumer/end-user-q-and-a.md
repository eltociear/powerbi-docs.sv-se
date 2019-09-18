---
title: Frågor och svar för Power BI-användare
description: Dokumentationsöversikt för Power BI frågor och svar frågor med naturligt språk.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/25/2019
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 9960ebe11271eea34245250ef5701e9a94bba744
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/16/2019
ms.locfileid: "67408445"
---
# <a name="qa-for-power-bi-consumers"></a>Frågor och svar för Power BI-**användare**
## <a name="what-is-qa"></a>Vad är frågor och svar?
Ibland är det snabbaste sättet att få svar från dina data att ställa en fråga med hjälp av naturligt språk. Till exempel hur mycket sålde vi förra året.

Använd frågor och svar för att utforska dina data med hjälp av intuitiva, naturliga språkfunktioner och få svar i form av tabeller och diagram. Frågor och svar skiljer sig från en sökmotor – den ger dig bara resultat om data i Power BI.

**Power BI – Frågor och svar** är tillgängligt med en Pro- eller Premium-licens.  [Frågor och svar i Power BI-mobilappar](mobile/mobile-apps-ios-qna.md) och [Frågor och svar med Power BI Embedded](../developer/qanda.md) täcks i separata artiklar. För närvarande har **Power BI Q & A** bara stöd för att besvara frågor på naturligt språk som ställs på engelska, även om det finns en förhandsversion för spanska som kan aktiveras av Power BI-administratören.


![trädkarta som skapats med frågor och svar](media/end-user-q-and-a/power-bi-treemap.png)

Att ställa frågan är bara början.  Roa dig med att resa igenom dina data och förfina eller expandera din fråga. Hitta betrodd ny information och gå till botten med information eller zooma ut för en bredare vy. Du kommer att fascineras av de insikter och upptäckter du kan göra.

Upplevelsen är helt interaktiv... och snabb! Det drivs av en minnesintern lagring och svaret är nästan omedelbart.

## <a name="where-can-i-use-qa"></a>Var kan jag använda Frågor och svar?
Du hittar Frågor och svar på instrumentpaneler i Power BI-tjänsten och längst ned på instrumentpanelen i Power BI Mobile. Om designern inte har gett dig redigeringsbehörigheter kommer du att kunna använda Frågor och svar för att utforska data men inte för att spara visualiseringar som skapats med Frågor och svar.

![frågeruta](media/end-user-q-and-a/powerbi-qna.png)

## <a name="use-qa-on-a-dashboard-in-the-power-bi-service"></a>Använda Frågor och svar på en instrumentpanel i Power BI-tjänsten
I Power BI-tjänsten (app.powerbi.com) innehåller en instrumentpanel paneler som fästs från en eller flera datamängder så att du kan ställa frågor om data som finns i någon av datamängderna. Om du vill se vilka rapporter och datamängder som användes för att skapa instrumentpanelen, väljer du **Visa relaterade** från menyraden.

![visa relaterad knapp i den övre menyraden](media/end-user-q-and-a/power-bi-view-related.png)

## <a name="how-do-i-start"></a>Hur börjar jag?
Bekanta dig först med innehållet. Titta på de visuella objekten på instrumentpanelen och i rapporten. Få en uppfattning av de typer och intervall av data som är tillgängliga för dig. 

Till exempel:

* Om det visuella objektets axeletiketter och värden inkluderar försäljning, konto, månad och affärsmöjligheter så kan du ställa frågor som: ”Vilket *konto* har de högsta *affärsmöjligheterna*, eller visa *försäljning* per månad som ett stapeldiagram.”

* Om du har prestandadata för webbplatser i Google Analytics kan du fråga Frågor och svar om den tid som tillbringats på en webbplats, antalet unika besök och användarengagemang. Eller, om du frågar demografisk data, kan du ställa frågor om ålder om hushållets inkomst efter plats.

När du är bekant med dina data går du tillbaka till instrumentpanelen och placerar markören i frågerutan. Då öppnas skärmen med Frågor och svar.

![Skärmen med Frågor och svar](media/end-user-q-and-a/power-bi-screen.png) 

Innan du ens börjar skriva, visar frågor och svar en ny skärm med förslag för att hjälpa dig formulera din fråga. Du ser fraser och frågor som innehåller namnen på tabellerna i de underliggande datamängderna och kan även se *aktuella** frågor som har skapats av datamängdsägaren.

Du kan välja någon av dem för att lägga till dem i frågerutan och sedan förfina dem för att hitta ett visst svar. 

Ett annat sätt som Frågor och svar hjälper dig att ställa frågor på är med uppmaningar, automatisk komplettering och visuella tips. 

![video](media/end-user-q-and-a/qna4.gif) 


### <a name="which-visualization-does-qa-use"></a>Vilken visualisering använder sig frågor och svar av?
Frågor och svar väljer den bästa visualiseringen baserat på de data som visas. Ibland definieras data i de underliggande datauppsättningarna som en viss typ eller kategori och det hjälper frågor och svar att veta hur de ska visas. Om data till exempel har definierats som en datumtyp, är det troligare att de ska visas som ett linjediagram. Data som kategoriseras som en stad visas mer troligt som en karta.

Du kan också säga till Frågor och svar vilket visuellt objekt som ska användas genom att lägga till det i din fråga. Men kom ihåg att det inte alltid är möjligt för Frågor och svar att visa data i den typ av visuellt objekt som du har begärt. Frågor och svar kommer att föreslå en lista över lämpliga typer av visuella objekt.


## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
**Fråga:** Jag ser inte Frågor och svar på den här instrumentpanelen.    
**Svar 1:** Om du inte ser någon frågeruta kontrollerar du först inställningarna. Det gör du genom att välja kugghjulsikonen i det övre högra hörnet i Power BI-verktygsfältet.   
![kugghjulsikonen](media/end-user-q-and-a/power-bi-settings.png)

Välj sedan **Inställningar** > **Instrumentpaneler**. Kontrollera att det finns en bockmarkering intill **Visa sökrutan för Frågor och svar på den här instrumentpanelen**.    
![Inställningar för Frågor och svar för instrumentpanelen](media/end-user-q-and-a/power-bi-turn-on.png)  


**Svar 2**: Ibland inaktiverar instrumentpanelens *designer* eller administratören Frågor och svar. Kontakta dem och fråga om det är OK att aktivera det igen.   

**Fråga:** Jag får inte de resultat som jag vill ha när jag skriver en fråga.    
**Svar:** Kontakta instrumentpanelens *designer*. Det finns många saker som designern kan göra för att förbättra resultaten för Frågor och svar. Till exempel kan designern byta namn på kolumner i datamängden till termer som är lätta att förstå (`CustomerFirstName` i stället för `CustFN`). Designern känner till datamängden väl och kan därför ta fram användbara frågor och lägga till dem i arbetsytan för Frågor och svar.


## <a name="next-steps"></a>Nästa steg
[Frågor och svar för Power BI-användare](end-user-q-and-a.md)
