---
title: DirectQuery och SAP Business Warehouse (BW) i Power BI
description: Att tänka på när du använder DirectQuery med SAP Business Warehouse (BW)
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 61de19e50437cf8cb5920d2a413821e325da2a1a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61304414"
---
# <a name="directquery-and-sap-business-warehouse-bw"></a>DirectQuery och SAP Business Warehouse (BW)
Du kan ansluta till **SAP Business Warehouse (BW)** -datakällor direkt med **DirectQuery**. På grund av SAP BW:s OLAP/flerdimensionella natur så finns det många viktiga skillnader mellan DirectQuery över SAP BW jämfört med relationella källor som SQL Server. Dessa skillnader kan sammanfattas på följande sätt:

* I **DirectQuery** över relationella källor, finns det en uppsättning frågor (som de definieras i dialogrutan **Hämta Data** eller **Frågeredigeraren**) som logiskt definierar de data som finns tillgängliga i fältlistan. Detta är *inte* fallet när du ansluter till en OLAP-källa, till exempel SAP BW. Vid anslutning till SAP-servern med **Hämta Data**, är det istället bara Infocube eller BEx Query som är markerat. Alla nyckelfigurer och -dimensioner för den valda Infocube/BEx Query kommer då finnas tillgängliga i fältlistan.   
* På liknande sätt, finns det ingen **Frågeredigerare** vid anslutning till SAP BW. Inställningarna för datakälla (till exempel servernamn) kan ändras genom att välja **Redigera frågor > Inställningar för datakälla**. Inställningarna för alla parametrar kan ändras genom att välja **Redigera frågor > Hantera parametrar**.
* På grund av den unika naturen för OLAP-källor finns ytterligare begränsningar (både när det gäller modellering och visualiseringar) som gäller utöver de normala begränsningar som tillämpas för DirectQuery. Dessa begränsningar beskrivs senare i den här artikeln.

Det är dessutom *mycket viktigt* att förstå att det finns många funktioner för SAP BW som inte stöds i Power BI och att på grund av det offentliga gränssnittet till SAP BW så finns det viktiga fall där resultaten som visas i Power BI inte matchar de som visas när du använder ett SAP-verktyg. Dessa begränsningar beskrivs senare i den här artikeln. Dessa begränsningar och skillnader i beteende bör granskas noggrant för att säkerställa att resultaten som visas i Power BI som de returneras av det offentliga SAP-gränssnittet tolkas korrekt.  

> [!NOTE]
> Möjligheten att använda DirectQuery över SAP BW fanns som förhandsversion fram till uppdateringen från mars 2018 av Power BI Desktop. Under förhandsversionen ledde feedback och förslag på förbättringar till en ändring som påverkar rapporter som har skapats med den förhandsversionen. Nu när allmän tillgänglighet (GA) för DirectQuery över SAP BW har lanserats *måste* du ta bort alla befintliga (förhandsversionsbaserade) rapporter med DirectQuery över SAP BW som har skapats med före-GA-versionen. I rapporter som har skapats med före-GA-versionen av DirectQuery över SAP BW uppstår fel med de före-GA-rapporterna vid anrop av uppdatering, på grund av försök att uppdatera metadata med ändringar av den underliggande SAP BW-kuben. Återskapa de rapporterna från en tom rapport med GA-versionen av DirectQuery över SAP BW. 

## <a name="additional-modeling-restrictions"></a>Ytterligare modelleringsbegränsningar
Den primära ytterligare modelleringsbegränsningen vid anslutning till SAP BW med DirectQuery i Power BI är följande:

* **Inget stöd för beräknade kolumner:** Möjligheten att skapa beräknade kolumner är inaktiverad. Det innebär också att gruppering och klustring, som skapar beräknade kolumner, inte är tillgängligt.
* **Ytterligare begränsningar för mått:** Det finns ytterligare begränsningar av de DAX-uttryck som kan användas i mått för att återspegla den supportnivå som erbjuds av SAP BW.
* **Inget stöd för att definiera relationer:** Relationerna är inbyggda i den externa SAP-källan och ytterligare relationer kan inte definieras i modellen.
* **Ingen datavy:** **Datavyn** visar normalt detaljerade nivådata i tabellerna. På grund av naturen för OLAP-källor som SAP BW, är den här vyn inte tillgänglig via SAP BW.
* **Information om kolumner och mått är fasta:** Listan över kolumner och mått som visas i fältlistan korrigeras i den underliggande källan och kan inte modifieras. Det går till exempel inte att ta bort en kolumn eller ändra dess datatyp (det går däremot att byta namn på den).
* **Ytterligare begränsningar i DAX:** Det finns ytterligare begränsningar för DAX som kan användas i måttdefinitioner när man vill återspegla begränsningar i källan. Det är till exempel inte möjligt att använda en mängdfunktion via en tabell.

## <a name="additional-visualization-restrictions"></a>Ytterligare visualiseringsbegränsningar
De primära ytterligare begränsningarna av visualiseringar vid anslutning till SAP BW med DirectQuery i Power BI är följande:

* **Ingen sammansättning av kolumner:** Det går inte att ändra aggregeringen för en kolumn i ett visuellt objekt, och den är alltid *Sammanfatta inte*
* **Måttfiltrering är inaktiverat:** Måttfiltrering är inaktiverat för att återspegla det stöd som erbjuds av SAP BW.
* **Flera val och inkludera/exkludera:** Möjlighet att välja flera datapunkter på en visualisering är inaktiverad om punkterna motsvarar värden från fler än en kolumn. I ett stapeldiagram som visar försäljning efter land med kategori i teckenförklaringen, skulle det till exempel inte vara möjligt att välja punkten för (USA, cyklar) och (Frankrike, kläder). På samma sätt skulle det inte vara möjligt att välja punkten (USA, cyklar) och utesluta den från den visuella informationen. Bägge begränsningarna gäller för att återspegla det stöd som erbjuds av SAP BW.

## <a name="support-for-sap-bw-features"></a>Stöd för SAP BW-funktioner
I följande tabell listar alla SAP BW-funktioner som inte stöds fullt ut eller fungerar annorlunda mot när du använder Power BI.   

| Funktion | Beskrivning |
| --- | --- |
| Lokala beräkningar |Lokala beräkningar som definieras i en BEx-fråga ändrar talen som de visas via verktyg som BEx Analyzer. Dessa återspeglas dock inte i de siffror som returneras från SAP, via det offentliga MDX-gränssnittet. <br/> <br/> **Därför matchar siffror som visas i en Power BI-visualisering inte nödvändigtvis de för en motsvarande visualisering i ett SAP-verktyg.**<br/> <br/>  När du till exempel ansluter till en frågekub från en BEx-fråga som anger sammansättningen att vara kumulerande (d.v.s. löpande summering), får Power BI tillbaka basnumren och ignorerar den inställningen.  En analytiker kan absolut därefter tillämpa en löpande summeringsberäkning lokalt i Power BI, men måste vara försiktig med hur siffrorna tolkas om detta inte görs. |
| Sammansättningar |I vissa fall (särskilt när du handskas med flera valutor), matchar inte de sammansatta siffrorna som returneras av det offentliga SAP-gränssnittet de som visas av SAP-verktygen. <br/> <br/> **Därför matchar siffror som visas i en Power BI-visualisering inte nödvändigtvis de för en motsvarande visualisering i ett SAP-verktyg.** <br/> <br/> Summor över olika valutor skulle till exempel visas som * i BEx Analyzer, men totalen skulle returneras av det offentliga SAP-gränssnittet, utan någon information om att ett sådant sammansatt nummer är meningslöst. Därför skulle numret (som sammansätter, säg, $, EUR och AUD) visas av Power BI. |
| Valutaformatering |Eventuella valutaformat (till exempel $2 300 eller 4 000 AUD) återspeglas inte i Power BI. |
| Måttenhet |Måttenheter (till exempel 230 KG) återspeglas inte i Power BI. |
| Nyckel kontra text (kort, medel, lång) |För en SAP BW-egenskap som CostCenter, visar fältlistan en enda kolumn kostnadscenter.  Om du använder den kolumnen så visas standardtexten.  Genom att visa dolda fält kommer det också vara möjligt att se kolumnen för unika namn (som returnerar det unika namnet som tilldelats av SAP BW och utgör grunden för unikhet).<br/> <br/>  Nyckeln och andra textfält är inte tillgängliga. |
| Flera hierarkier för en egenskap |I **SAP**, kan en egenskap ha flera hierarkier. När en egenskap sedan inkluderas i en fråga i verktyg som BEx Analyzer, kan användaren välja vilken hierarki som ska användas. <br/> <br/> I **Power BI**, kan de olika hierarkierna ses i fältlistan som olika hierarkier på samma dimension.  Att välja flera nivåer från två olika hierarkier på samma dimension, leder dock till att tomma data returneras av SAP. |
| Behandling av ojämna hierarkier |![](media/desktop-directquery-sap-bw/directquery-sap-bw_01.png) |
| Skalningsfaktor/omvänt förtecken |I SAP kan ett nyckeltal ha en skalningsfaktor (till exempel 1000) som definieras som ett formateringsalternativ, vilket innebär att all visning kommer att skalas med den faktorn. <br/> <br/> På samma sätt kan det ha en egenskapsuppsättning som byter förecknet. Om du använder ett sådant nyckeltal i Power BI (i en visualisering eller som en del av en beräkning) resulterar det i att det oskalade numret används (och förtecknet inte omvänds). Den underliggande skalningsfaktorn är inte tillgänglig. I visuell information i Power Bi så kan skalningsenheter som visas på axeln (K, M B) styras som en del av den visuella formateringen. |
| Hierarkier där nivåer visas/döljs dynamiskt |När du först ansluter till SAP BW, hämtas information om nivåer av en hierarki, vilket resulterar i en uppsättning fält i fältlistan. Detta cachelagras och om uppsättningen nivåer ändras så förändras inte fältuppsättningarna förrän uppdatera anropas. <br/> <br/> Detta är endast möjligt i **Power BI Desktop**. Sådan uppdatering för att återspegla nivåändringar kan inte anropas i Power BI-tjänsten efter publicering. |
| Standardfiltret |En BEx-fråga kan innehålla standardfilter som automatiskt tillämpas av SAP BEx Analyzer. Dessa visas inte och den motsvarande användningen i Power BI tillämpar därmed inte samma filter som standard. |
| Dolda nyckeltal |En BEx-fråga kan styra synligheten för nyckeltal och de som är dolda visas inte i SAP BEx Analyzer. Detta återspeglas inte via det offentliga API:et och därför visas fortfarande sådana dolda nyckeltal i fältlistan. De kan dock därefter döljas i Power BI. |
| Numerisk formatering |Numerisk formatering (antal decimaler, decimaltecken osv.) återspeglas inte automatiskt i Power BI. Det är dock möjligt att därefter kontrollera sådan formatering i Power BI. |
| Versionshantering av hierarkin |SAP BW tillåter att olika versioner av en hierarki upprätthålls. Till exempel hierarkin i kostnadscenter i 2007 och 2008. Endast den senaste versionen blir tillgänglig i Power BI, eftersom information om versioner inte visas av offentliga API. |
| Tidsberoende hierarkier |När du använder Power BI, utvärderas tidsberoende hierarkier vid det aktuella datumet. |
| Valutakonvertering |SAP BW stöder valutakonvertering, baserat på växlingskurser som lagras i kuben. Sådana funktioner visas inte av det offentliga API:t och är därför inte tillgängliga i Power BI. |
| Sorteringsordning |Sorteringsordningen (via text eller nyckel) för en egenskap kan definieras i SAP. Den här sorteringsordningen återspeglas inte i Power BI. Månader kan till exempel visas som april, augusti och så vidare. <br/> <br/> Det går inte att ändra den här sorteringsordningen i Power BI. |
| Tekniska namn |I **Hämta data**, kan både egenskapernas/måttens namn (beskrivningar) och tekniska namn visas. Fältlistan innehåller bara egenskapernas/måttens namn (beskrivningar). |
| Attribut |Det går inte att komma åt attributen för en egenskap i Power BI. |
| Språkinställning för slutanvändare |De nationella inställningar som används för att ansluta till SAP BW anges som en del av anslutningsinformationen och återspeglar in de nationella inställningarna för den slutliga rapportkonsumenten. |
| Textvariabler |SAP BW låter fältnamn innehålla platshållare för variabler (till exempel ”$YEAR$ faktiska”) som sedan ersätts med det valda värdet. Fältet visas till exempel som ”2016 faktiska” i BEx-verktyg, om året 2016 har valts för variabeln. <br/> <br/> Kolumnnamnet i Power BI ändras inte beroende på variabelvärdet och visas därför som ”$YEAR$ faktiska”.  Kolumnnamnet kan dock sedan ändras i Power BI. |
| Variabler för kundutgång | Variabler för kundutgång visas inte av det offentliga API:t och stöds därför inte i Power BI. |
| Karakteristiska strukturer | Alla karakteristiska strukturer i underliggande SAP BW-källa resulterar i en ”explosion” av mått som exponeras i Power BI. Till exempel med två de två måtten Sales och Costs och en karakteristisk struktur som innehåller Budget och Actual, exponeras fyra mått: Sales.Budget, Sales.Actual, Costs.Budget, Costs.Actual. |


## <a name="next-steps"></a>Nästa steg
Mer information om DirectQuery finns i följande resurser:

* [DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)

