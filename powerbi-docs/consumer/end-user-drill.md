---
title: Öka och minska detaljnivån i en visualisering
description: Det här dokumentet beskriver hur du ökar detaljnivån i en visualisering i Microsoft Power BI-tjänsten och Power BI Desktop.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: MNAaHw4PxzE
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: bc5033df204fafcc7316d6708d7b39429e8e9cba
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61053504"
---
# <a name="drill-mode-in-a-visualization-in-power-bi"></a>Granskningsläge i en visualisering i Power BI

## <a name="drill-requires-a-hierarchy"></a>Detaljgranskning kräver en hierarki
När en visualisering har en hierarki kan du öka detaljnivån till att visa ytterligare information. Du kan till exempel ha en visualisering som kontrollerar OS-medaljantal enligt en hierarki som består av sport, gren och evenemang. Som standard visar visualiseringen medaljantal enligt sport – gymnastik, skidåkning, vattensport osv. Men eftersom den har en hierarki, skulle val av ett av de visuella elementen (till exempel ett stapel-, linje- eller bubbeldiagram), visa en allt mer detaljerad bild. Välj elementet **vattensporter** för att se data för simning, simhopp och vattenpolo.  Välj elementet **simhopp** för att visa detaljer för trampolin, plattform och synkroniserade simhopp.

Du kan lägga till hierarkier till rapporter som du äger men inte till de rapporter som delats med dig.
Är du osäker på vilka Power BI-visualiseringar som innehåller en hierarki?  Hovra över en visualisering och om du ser dessa kontroller för ökad detaljnivå i de övre hörnen, har din visualiseringen en hierarki.

![gå nedåt en nivå](./media/end-user-drill/power-bi-drill-icon4.png)![aktivera nedåt och inaktivera](./media/end-user-drill/power-bi-drill-icon2.png)![detaljgranska alla fält samtidigt ikonen](./media/end-user-drill/power-bi-drill-icon3.png)
![detaljnivån ikonen](./media/end-user-drill/power-bi-drill-icon5.png) ![expandera ned-ikon](./media/end-user-drill/power-bi-drill-icon6.png)  

Datum är en unik typ av hierarki. När du lägger till ett datumfält i en visualisering lägger Power BI automatiskt till en tidshierarki som innehåller år, kvartal, månad och dag. Mer information finns i [Visuella hierarkier och beteende för ökad detaljnivå](../guided-learning/visualizations.yml?tutorial-step=18) eller titta på videon nedan.


  <iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Om du vill lära dig mer om att skapa hierarkier med hjälp av Power BI Desktop, titta på videon [Hur du skapar och lägger till hierarkier](https://youtu.be/q8WDUAiTGeU)
> 

## <a name="prerequisites"></a>Förutsättningar

1. I Power BI-tjänsten eller Desktop krävs en visualisering med en hierarki för ökad detaljnivå. 
   
2. För att följa med ska du [öppna exemplet för detaljhandelsanalys](../sample-datasets.md) och skapa ett trädkartediagram som kontrollerar (värdena) **totala enheter detta år** enligt (grupperna) **Område**, **Stad**, **Postnummer** och **Namn**.  Trädkartan har en hierarki som består av område, stad, postnummer och stadsnamn. Varje område har en eller flera städer, varje stad har ett eller flera postnummer osv. Visualiseringen visar som standard endast områdesdata, eftersom *Område* visas först i listan.
   
   ![Välj ”Område”](media/end-user-drill/power-bi-hierarcy-list.png)

2. Att förstå hur de olika ikonerna för detaljgranskning fungerar tillsammans kan vara förvirrande, så låt oss filtrera trädkartan så att vi bara visar 2 av de mindre områdena: **KY** och **TN**. Välj trädkarta och under **Visuella nivåfilter** expanderar du **Område** och väljer **KY** och **TN**.

    ![filtrera på KY och TN](./media/end-user-drill/power-bi-filter.png)    

   Nu visas bara två områden i trädkartan.

   ![dubbel granskningsikon](./media/end-user-drill/power-bi-territories.png)

## <a name="three-ways-to-access-the-drill-features"></a>Tre sätt att få åtkomst till granskningsfunktioner
Det finns flera sätt att få åtkomst till funktioner för att öka och minska detaljnivån samt expandera för visualiseringar som har hierarkier. Den här artikeln visar hur du använder det första alternativet nedan. När du förstår hur man ökar detaljnivån och expanderar kan du uppnå samma sak med alla tre metoderna. Prova och se vilken du föredrar att använda.

- Hovra över en visualisering för att se och använda ikonerna.  

    ![sökväg för granskning](./media/end-user-drill/power-bi-hover.png)

- Högerklicka på en visualisering för att visa och använda menyn.
    
    ![snabbmeny](./media/end-user-drill/power-bi-drill-menu.png)

- I menyraden Power BI väljer du knappen **Utforska**.

   ![Om du väljer Utforska visas ikoner för ökad detaljnivå och alternativ](media/end-user-drill/power-bi-explore.png)

## <a name="drill-pathways"></a>Sökvägar för granskning
### <a name="drill-down"></a>Ökad detaljnivå
Det finns olika sätt att granska visualiseringen mer detaljerat. ***Öka detaljnivån*** tar dig till nästa nivå i hierarkin, så om du tittar på nivån **Område** kan du öka detaljnivån till nivån Stad och sedan Postnummer och slutligen Namn. Varje steg i sökvägen visar nya uppgifter.

![sökväg för granskning](./media/end-user-drill/power-bi-drill-path.png)

### <a name="expand"></a>Expandera

***Expandera*** lägger till ytterligare en hierarkinivå i den aktuella vyn. Så om du tittar på nivån **Område** kan du expandera och lägga till ort, postnummer och namn i din trädkarta. Varje steg i sökvägen visar samma information och lägger till en nivå med ny information.

![expandera sökväg](./media/end-user-drill/power-bi-expand-path.png)

Du kan också välja om du vill öka detaljnivån eller expandera ett fält i taget eller alla fält på en gång. 

## <a name="drill-down-all-fields-at-a-time"></a>Öka detaljnivån för alla fält på en gång

1. Starta på den översta nivån av trädkartan som visar data för KY och TN. Bredda din trädkarta genom att välja ett handtag och dra det till höger. 

    ![trädkarta som visar två stater](./media/end-user-drill/power-bi-drill-down.png) .

2. Om du vill öka detaljnivån för ***alla fält samtidigt*** väljer du dubbelpilen längst upp till vänster i visualiseringen ![ dubbel granskningsikon](./media/end-user-drill/power-bi-drill-icon3.png). Din trädkarta visar nu stadsdata för Kentucky och Tennessee. 

    ![dubbel granskningsikon](./media/end-user-drill/power-bi-drill-down1.png)
   
5. Öka detaljnivån en gång till, till postnummernivån i hierarkin.

    ![dubbel granskningsikon](./media/end-user-drill/power-bi-drill-down2.png)

3. Om du vill minska detaljnivån igen väljer du uppåtpilen i det övre vänstra hörnet av visualiseringen ![ikon för att byta detaljnivå uppåt en nivå](./media/end-user-drill/power-bi-drill-icon5.png).


## <a name="drill-down-one-field-at-a-time"></a>Öka detaljnivån ett fält i taget
Den här metoden använder ikonerna för ökad detaljnivå som visas i det övre högra hörnet i själva visualiseringen. 

1. Välj ikonen för ökad detaljnivå för att aktivera den ![ökad detaljnivå aktiverad](./media/end-user-drill/power-bi-drill-icon2.png). Nu kan du öka detaljnivån ***ett fält i taget***. 
   
   ![pil som pekar på ikonen för detaljnivå ökad/minskad](media/end-user-drill/power-bi-drill-icon-new.png)

   Om du inte aktiverar den ökade detaljnivån kommer valet av ett visuellt element (t.ex. ett stapel- eller bubbeldiagram eller en lövnod) att korsfiltrera diagrammen på rapportsidan.

2. Välj *lövnod* för **TN**. Din trädkarta visar nu alla orter i Tennessee som har en butik. 

    ![trädkarta som endast visar data för Tennessee](media/end-user-drill/power-bi-drill-down-one1.png)

2. Du kan nu öka detaljnivån för Tennessee eller för en viss stad i Tennessee, eller så kan du expandera (se här för information om hur du **expanderar alla fält samtidigt** nedan). Låt oss nu fortsätta att öka detaljnivån ett fält i taget.  Välj **Knoxville, TN**. Din trädkarta visar nu postnumret för din butik i Knoxville. 

   ![trädkartan visar 37919](media/end-user-drill/power-bi-drill-down-one2.png)

    Observera att rubriken ändras när du ändrar detaljnivån ner och upp igen.  

## <a name="expand-all-and-expand-one-field-at-a-time"></a>Expandera alla och expandera ett fält i taget
En trädkarta som bara visar postnummer är inte användbar.  Så låt oss expandera en nivå ned i hierarkin.  

1. Om trädkartan är aktiverad kan du välja ikonen *för att expandera ned* ![expandera ned](./media/end-user-drill/power-bi-drill-icon6.png). Två nivåer av vår hierarki visas nu i din trädkarta: postnummer och butiksnamn. 

    ![visar postnummer och butiksnamn](./media/end-user-drill/power-bi-expand1.png)

2. För att se alla fyra hierarkinivåer av data för Tennessee väljer du pilen för att minska detaljnivån tills du når den andra nivån, **totalt antal enheter i år efter område och stad**, för din trädkarta. 

    ![trädkarta som visar alla data för Tennessee](media/end-user-drill/power-bi-drill-down-one1.png)


3. Se till att ökad detaljnivå fortfarande är aktiverat ![ökad detaljnivå aktiverat](./media/end-user-drill/power-bi-drill-icon2.png), och välj ikonen *expandera ned* ![expandera ned-ikon](./media/end-user-drill/power-bi-drill-icon6.png). Nu visas lite mer detaljer i din trädkarta. Istället för att bara visa stad och stat, visas nu även postnumret. 

    ![dubbel granskningsikon](./media/end-user-drill/power-bi-expand-one3.png)

4. Välj ikonen *expandera ned* en gång till för att visa alla fyra hierarkinivåer i detalj för Tennessee i din trädkarta. Hovra över en lövnod för att se ytterligare information.

   ![trädkarta som visar data för Tennessee](./media/end-user-drill/power-bi-expand-all.png)

## <a name="drilling-filters-other-visuals"></a>Att gå in på detalj filtrerar andra visuella objekt
När du arbetar i granskningsläget får du bestämma hur du vill gå nedåt och hur expansionen ska påverka de andra visualiseringarna på sidan. 

Som standard filtreras inte andra visuella objekt i rapporten när du ändrar detaljnivån. Men den funktionen kan aktiveras i Power BI Desktop- och Power BI-tjänsten. 

1. I Desktop väljer du fliken **Format** och markerar kryssrutan för **Att gå in på detalj filtrerar andra visuella objekt**.

    ![inställning i Power BI Desktop](./media/end-user-drill/power-bi-drill-filters-desktop.png)

2. När du ökar detaljnivån (eller minskar eller expanderar) i ett visuellt objekt med en hierarki, filtrerar åtgärden nu även övriga visuella objekt på sidan. 

    ![inställning i Desktop](./media/end-user-drill/power-bi-drill-filters.png)

    ![inställning i Desktop](./media/end-user-drill/power-bi-drill-filters2.png)

> [!NOTE]
> Om du vill aktivera detta i Power BI-tjänsten, väljer du **Visuella interaktioner > Att gå in på detalj filtrerar andra visuella objekt** från den översta menyraden.
>
> ![inställning i Power BI-tjänsten](./media/end-user-drill/power-bi-drill-filters-service.png)



## <a name="understanding-the-hierarchy-axis-and-hierarchy-group"></a>Förstå hierarkins axel och grupp
Hierarkiaxeln och hierarkigruppen är mekanismer du kan använda för att öka och minska granulariteten för data som du vill visa. Data som kan ordnas i kategorier och underkategorier anses ha en hierarki. Detta omfattar naturligtvis datum och tider.

Du kan skapa en visualisering i Power BI som har en hierarki genom att välja ett eller flera datafält som läggs till i området **Axel** eller **Grupp**, tillsammans med data som du vill granska som datafält i området **Värden**. Dina data är hierarkiska om *detaljnivåikonerna* visas längst upp till vänster och höger i visualiseringen. 

Det enklaste är att tänka på det som två typer av hierarkiska data:
- Datum- och tidsdata – om du har ett datafält med datatypen DateTime har du redan hierarkiska data. Power BI skapar automatiskt en hierarki för alla datafält vars värden kan parsas i en [DateTime](https://msdn.microsoft.com/library/system.datetime.aspx)-struktur. Du behöver bara lägga till ett DateTime-fält i området **Axel** eller **Grupp**.
- Kategoridata – om dina data hämtas från samlingar som innehåller delsamlingar, eller har rader med data med gemensamma värden, har du hierarkiska data.

Med Power BI kan du expandera en eller alla delmängder. Du kan öka detaljnivån i dina data för att visa en enda delmängd på varje nivå, eller alla delmängder samtidigt på varje nivå. Du kan till exempel öka detaljnivån för ett visst år eller visa alla resultat för varje år nedåt i hierarkin. Du kan också minska detaljnivån på samma sätt.

I avsnitten nedan beskrivs ökad detaljnivå från den högsta vyn, mellanvyn och den lägsta vyn.

### <a name="hierarchical-data-and-time-data"></a>Hierarkiska data och tidsdata
I det här exemplet kan du följa med i vårt [exempel på detaljhandelsanalys](../sample-datasets.md) och skapa en visualisering av ett stående stapeldiagram med fokus på **Månad** (Axel) och **Total försäljning** (Värden).  

Även om datafältet Axel är **Månad** skapar det en **årskategori** i området **Axel**. Det beror på att Power BI ger en fullständig DateTime-struktur för alla värden som läses. Högst upp i hierarkin visas årets data.

![Enskild stapel som visar data grupperade efter år](media/end-user-drill/power-bi-hierarchical-axis-datetime-1.png)

Med läget för ökad detaljnivå aktiverat klickar du på stapeln i diagrammet för att gå nedåt en nivå i hierarkin. Tre staplar för data för de tillgängliga kvartalen visas. Bland ikonerna uppe till vänster väljer du alternativet för att **expandera allt nedåt en nivå i hierarkin**. Upprepa detta för att komma till nivån längst ner i hierarkin som visar resultat för varje månad.

![stapeldiagram för att se fält per månad](media/end-user-drill/power-bi-hierarchical-axis-datetime-2.png)

Förutom visualiseringen kan vi se att hierarkin återspeglas i de data som återges för varje rapport. I följande tabell visas resultaten för att **Visa data** i en rapport med ökad detaljnivå från en månad eller alla månader. 

Observera att informationen är den samma för kvartals- och årsrapporter, men när du ökar detaljnivån till nivån för **Värden** ser du att den enkla rapporten är mer specifik, och att rapporten för alla månader innehåller mer data.


|Läget Expandera|År|Kvartal|Månad|Dag|
| ---|:---:|:---:|:---:|---|
|Enkel|![enskilt år](./media/end-user-drill/power-bi-hierarchical-year.png)|![enskilt kvartal](media/end-user-drill/power-bi-hierarchical-quarter.png)|![enskild månad](./media/end-user-drill/power-bi-hierarchical-one-month.png)|![enskild dag](media/end-user-drill/power-bi-hierarchical-one-day.png)|
|Alla|![alla år](./media/end-user-drill/power-bi-hierarchical-year.png)|![alla kvartal](media/end-user-drill/power-bi-hierarchical-quarter.png)|![alla månader](./media/end-user-drill/power-bi-hierarchical-all-month.png)|![alla dagar](media/end-user-drill/power-bi-hierarchical-all-day.png)|


### <a name="hierarchical-category-data"></a>Hierarkiska kategoridata
Data som har modellerats från samlingar och delsamlingar är hierarkiska. Ett bra exempel på detta är platsdata. Anta att du har en tabell i en datakälla med kolumner för land, region, stad och postnummer. Data som delar samma land, region och stad är hierarkiska.

I det här exemplet kan du följa med i [exemplet för detaljhandelsanalys](../sample-datasets.md). Skapa en visualisering av ett stående stapeldiagram med fokus på **Totalt antal enheter i år** (Värden) enligt **Område**, **Stad**, **Postnummer** och **Namn** (Grupp).  

![stapeldiagram som visar totalt antal enheter i år efter område](media/end-user-drill/power-bi-hierarchical-axis-category-1.png)

Se till att läget för ökad detaljnivå är aktiverat. Bland ikonerna längst upp till vänster väljer du alternativet för att **expandera allt nedåt en nivå i hierarkin** tre gånger.
Du ska nu vara på nivån längst ner i hierarkin, som visar resultat för område, stad och postnummer.

![stapeldiagram som visar den lägsta nivån i hierarkin, största detaljnivån](media/end-user-drill/power-bi-hierarchical-axis-category-2.png)

Förutom visualiseringen kan vi se att hierarkin återspeglas i de data som återges för varje rapport. I följande tabell visas resultaten för att **Visa data** i en rapport med ökad detaljnivå för ett område och alla områden. När du ökar detaljnivån kan du se hur den enkla rapporten blir mer specifik och att rapporten med alla områden innehåller mer data.


| Läget Expandera|Område|Stad|Postnummer|Namn|
| ---|:---:|:---:|:---:|---|
|Enkel|![enskilt område](./media/end-user-drill/power-bi-hierarchical-territory.png)|![enskild stad](media/end-user-drill/power-bi-hierarchical-one-territory-city.png)|![enskilt postnummer](./media/end-user-drill/power-bi-hierarchical-one-territory-city-postal.png)|![enskilt namn](media/end-user-drill/power-bi-hierarchical-one-territory-city-postal-name.png)|
|Alla|![alla områden](./media/end-user-drill/power-bi-hierarchical-territory.png)|![alla städer](media/end-user-drill/power-bi-hierarchical-all-territory-city.png)|![alla postnummer](./media/end-user-drill/power-bi-hierarchical-all-territory-city-postal.png)|![alla namn](media/end-user-drill/power-bi-hierarchical-all-territory-city-postal-name.png)|


## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
* Om tillägget av ett datumfält i en visualisering inte skapar en hierarki, kan det bero på att ”datum”-fältet faktiskt inte har sparats som ett datum. Om du äger datauppsättningen, öppna den i vyn *Data* i Power BI Desktop, välj den kolumn som innehåller datum och välj fliken Modellering och ändra **Datatyp** till **Datum** eller **Datum/Tid**. Om rapporten har delats med dig, kontakta ägaren om du vill begära ändringen.  
  
  ![välj datavy, se datumtyp längst upp till höger](media/end-user-drill/power-bi-change-data-type2.png)

## <a name="next-steps"></a>Nästa steg
[Visualiseringar i Power BI-rapporter](../visuals/power-bi-report-visualizations.md)

[Power BI-rapporter](end-user-reports.md)

[Power BI – grundläggande begrepp](end-user-basic-concepts.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

