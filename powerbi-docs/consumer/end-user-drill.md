---
title: Öka och minska detaljnivån i en visualisering
description: Den här artikeln beskriver hur du ökar detaljnivån i en visualisering i Microsoft Power BI-tjänsten och Power BI Desktop.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: MNAaHw4PxzE
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 6/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 29823a2f1ca7f1448df54282e0ce081310974eb3
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/16/2019
ms.locfileid: "67265189"
---
# <a name="drill-mode-in-a-visualization-in-power-bi"></a>Granskningsläge i en visualisering i Power BI

Den här artikeln beskriver hur du ökar detaljnivån i en visualisering i Microsoft Power BI-tjänsten och Power BI Desktop. Power BI-rapporter innehåller ett flertal datahierarkier som ger dig maximala insikter om dina data. Genom att öka och minska detaljnivån för dina datapunkter, kan du utforska detaljerad information om dina data. Du kan till och med dra nytta av den även på dina mobila enheter, trots den lilla formfaktorn.

## <a name="drill-requires-a-hierarchy"></a>Detaljgranskning kräver en hierarki

När en visualisering har en hierarki kan du öka detaljnivån till att visa ytterligare information. Du kan till exempel ha en visualisering som kontrollerar OS-medaljantal enligt en hierarki som består av sport, gren och evenemang. Som standard visar visualiseringen medaljantal enligt sport – gymnastik, skidåkning, vattensport osv. Men eftersom den har en hierarki, medför val av ett av visualiseringselementen (till exempel ett stapel-, linje- eller bubbeldiagram), att en allt mer detaljerad bild visas. Välj elementet **vattensporter** för att se data för simning, simhopp och vattenpolo.  Välj elementet **simhopp** för att visa detaljer för trampolin, plattform och synkroniserade simhopp.

Du kan lägga till hierarkier till rapporter som du äger men inte till de rapporter som delats med dig.
Är du osäker på vilka Power BI-visualiseringar som innehåller en hierarki? Hovra över en visualisering. Om du ser dessa kontroller för ökad detaljnivå i de övre hörnen, har visualiseringen en hierarki.

![Skärmbild av ikonen för att öka detaljnivån med en nivå i taget.](./media/end-user-drill/power-bi-drill-icon4.png)  ![Skärmbild av ikonen för att slå på eller av ökning av detaljnivån med en nivå i taget.](./media/end-user-drill/power-bi-drill-icon2.png)  ![Skärmbild av ikonen för att öka detaljnivån för alla fält samtidigt. ](./media/end-user-drill/power-bi-drill-icon3.png)
 ![ikonen Granska uppåt](./media/end-user-drill/power-bi-drill-icon5.png) ![Skärmbild av ikonen för att expandera nedåt.](./media/end-user-drill/power-bi-drill-icon6.png)  

Datum är en unik typ av hierarki. När du lägger till ett datumfält i en visualisering lägger Power BI automatiskt till en tidshierarki som innehåller år, kvartal, månad och dag. Du hittar mer information genom att läsa avsnittet om [visuella hierarkier och ökad detaljnivå](../guided-learning/visualizations.yml?tutorial-step=18) eller titta på videon nedan.

<iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Om du vill lära dig mer om att skapa hierarkier med hjälp av Power BI Desktop, titta på videon [Hur du skapar och lägger till hierarkier](https://youtu.be/q8WDUAiTGeU).

## <a name="prerequisites"></a>Förutsättningar

1. I Power BI-tjänsten eller Desktop krävs en visualisering med en hierarki för ökad detaljnivå.

1. Om du vill följa med, kan du öppna [Exempel på detaljhandelsanalys](../sample-datasets.md). Skapa en **trädkartsvisualisering** som fokuserar på:

    | Område | Fält |
    | ---- | ----- |
    | Värde |Försäljning<br>\|\_ Totalt antal enheter i år |
    | Grupp | Lager<br>\|\_ Område<br>\|\_ Stad<br>\|\_ Postnummer<br>\|\_ Namn

    Trädkartan har en hierarki som består av område, stad, postnummer och stadsnamn. Varje område har en eller flera städer, varje stad har ett eller flera postnummer osv. Visualiseringen visar som standard endast områdesdata, eftersom *Område* visas först i listan.

    ![Skärmbild av visualiseringsfönstret med fältet Område framhävt.](media/end-user-drill/power-bi-hierarcy-list.png)

1. Att lära sig hur de olika detaljnivåsikonerna fungerar tillsammans kan vara förvirrande. Nu ska vi filtrera trädkartan för att visa endast två av de mindre områdena: **KY** och **TN**. Välj trädkarta och under **Visuella nivåfilter** expanderar du **Område** och väljer **KY** och **TN**.

    ![Skärmbild av visualiseringsfönstret med filter för KY och TN.](./media/end-user-drill/power-bi-filter.png)

    Nu visas bara två områden i trädkartan.

    ![Skärmbild av det visuella objektet med KY och TN framhävt.](./media/end-user-drill/power-bi-territories.png)

## <a name="three-ways-to-use-the-drill-features"></a>Tre sätt att använda detaljnivåsfunktionerna

Det finns flera sätt att få åtkomst till funktioner för att öka och minska detaljnivån samt expandera för visualiseringar som har hierarkier. Den här artikeln visar hur du använder det första alternativet nedan. När du har lär dig grunderna för att öka detaljnivån och expandera, kommer du att kunna använda alla tre. Alla åstadkommer samma saker. Prova dem och välj den som du gillar mest.

- Hovra över en visualisering för att se och använda ikonerna.  

    ![Skärmbild av hovringsexemplet.](./media/end-user-drill/power-bi-hover.png)

- Högerklicka på en visualisering för att visa och använda menyn.

    ![Skärmbild av högerklicksexemplet.](./media/end-user-drill/power-bi-drill-menu.png)

- I menyraden Power BI väljer du knappen **Utforska**.

   ![Skärmbild av att välja Utforska med visning av ikoner och alternativ för detaljnivå.](media/end-user-drill/power-bi-explore.png)

## <a name="drill-pathways"></a>Sökvägar för granskning

### <a name="drill-down"></a>Öka detaljnivån

Det finns olika sätt att granska visualiseringen mer detaljerat. **Granska nedåt** tar dig till nästa nivå i hierarkin. Om du tittar på nivån **Område** kan du öka detaljnivån till nivån Stad och sedan Postnummer och slutligen Namn. Varje steg i sökvägen visar nya uppgifter.

![Diagram som visar dina olika sökvägar för ökad detaljnivå](./media/end-user-drill/power-bi-drill-path.png)

### <a name="expand"></a>Expandera

**Expandera** lägger till ytterligare en hierarkinivå i den aktuella vyn. Så om du tittar på nivån **Område** kan du expandera och lägga till ort, postnummer och namn i din trädkarta. Varje steg i sökvägen visar samma information och lägger till en nivå med ny information.

![Diagram som visar sökvägen för expansion](./media/end-user-drill/power-bi-expand-path.png)

Du kan också välja om du vill öka detaljnivån eller expandera ett fält i taget eller alla fält på en gång.

## <a name="drill-down-all-fields-at-once"></a>Öka detaljnivån för alla fält på en gång

1. Starta på den översta nivån av trädkartan som visar data för KY och TN. Bredda din trädkarta genom att välja ett handtag och dra det till höger.

    ![Skärmbild av det visuella trädkartsobjektet som visar KY och TN](./media/end-user-drill/power-bi-drill-down.png)

1. Om du vill öka detaljnivån för *alla fält samtidigt* väljer du dubbelpilen längst upp till vänster i visualiseringen ![dubbel ikon för ökad detaljnivå](./media/end-user-drill/power-bi-drill-icon3.png). Din trädkarta visar nu stadsdata för Kentucky och Tennessee.

    ![Skärmbild av det visuella trädkartsobjektet som visar ökad detaljnivå till städer.](./media/end-user-drill/power-bi-drill-down1.png)

1. Öka detaljnivån en gång till, till postnummernivån i hierarkin.

    ![Skärmbild av det visuella trädkartsobjektet som visar ökad detaljnivå till postnummer.](./media/end-user-drill/power-bi-drill-down2.png)

1. Om du vill minska detaljnivån igen väljer du uppåtpilen i det övre vänstra hörnet av visualiseringen ![Skärmbild ikonen för att minska detaljnivån med en nivå i taget.](./media/end-user-drill/power-bi-drill-icon5.png).

## <a name="drill-down-one-field-at-a-time"></a>Öka detaljnivån ett fält i taget

Den här metoden använder ikonerna för ökad detaljnivå som visas i det övre högra hörnet i själva visualiseringen.

1. Välj ikonen för ökad detaljnivå för att aktivera den ![Skärmbild av aktiverad ikon för ökad detaljnivå på/av.](./media/end-user-drill/power-bi-drill-icon2.png).

    Nu kan du öka detaljnivån **ett fält i taget**.

    ![Skärmbild av visuellt objekt med pil som pekar på aktiverad ikon för ökad detaljnivå på/av.](media/end-user-drill/power-bi-drill-icon-new.png)

    Om du inte slår på ökad detaljnivå på, visas inte en ökad detaljnivå när du väljer ett visualiseringselement (till exempel ett stapel-, bubbel- eller lövdiagram). I stället korsfiltrerar det de övriga diagrammen på rapportsidan.

1. Välj lövnod för **TN**. Din trädkarta visar nu alla städer i Tennessee som har en butik.

    ![Skärmbild av trädkartan som visar data för endast TN.](media/end-user-drill/power-bi-drill-down-one1.png)

1. Nu kan du:

    1. Fortsätta öka detaljnivån för Tennessee.

    1. Öka detaljnivån för en viss stad i Tennessee.

    1. Expandera i stället (se **Expandera alla fält samtidigt** nedan).

    Låt oss nu fortsätta att öka detaljnivån ett fält i taget.  Välj **Knoxville, TN**. Din trädkarta visar nu postnumren för dina butiker i Knoxville.

    ![Skärmbild av trädkartan som visar postnummer 37919.](media/end-user-drill/power-bi-drill-down-one2.png)

    Observera att rubriken ändras när du ändrar detaljnivån ner och upp igen.

## <a name="expand-all-and-expand-one-field-at-a-time"></a>Expandera alla och expandera ett fält i taget

En trädkarta som bara visar postnummer är inte användbar.  Så låt oss expandera en nivå ned i hierarkin.  

1. Välj ikonen för att expandera ned *expandera ned* med trädkartan aktiverad. ![Skärmbild av ikonen för att expandera ned.](./media/end-user-drill/power-bi-drill-icon6.png) Två nivåer av vår hierarki visas nu i din trädkarta: postnummer och butiksnamn.

    ![Skärmbild av trädkartan som visar postnummer butiksnamn](./media/end-user-drill/power-bi-expand1.png)

1. För att se alla fyra hierarkinivåer av data för Tennessee väljer du pilen för att minska detaljnivån tills du når den andra nivån, **totalt antal enheter i år efter område och stad**, för din trädkarta.

    ![Skärmbild av trädkartan som visar alla data för TN.](media/end-user-drill/power-bi-drill-down-one1.png)

1. Se till att ökning av detaljnivån fortfarande är aktiverat. ![Skärmbild av aktiverad ikon för ökad detaljnivå på/av.](./media/end-user-drill/power-bi-drill-icon2.png) och välj ikonen för att *expandera ned* ![Skärmbild av ikonen för att expandera ned.](./media/end-user-drill/power-bi-drill-icon6.png) Din trädkarta visar nu viss ytterligare information. Istället för att bara visa stad och stat, visas nu även postnumret.

    ![Skärmbild av det visuella objektet med visning av stad, stat och postnummer.](./media/end-user-drill/power-bi-expand-one3.png)

1. Välj ikonen *expandera ned* en gång till för att visa alla fyra hierarkinivåer i detalj för Tennessee i din trädkarta. Hovra över en lövnod för att se ytterligare information.

    ![Skärmbild av trädkartan som visar en knappbeskrivning med lövspecifika data.](./media/end-user-drill/power-bi-expand-all.png)

## <a name="drilling-filters-other-visuals"></a>Att gå in på detalj filtrerar andra visuella objekt

När du arbetar i granskningsläget får du bestämma hur du vill gå nedåt och hur expansionen ska påverka de andra visualiseringarna på sidan.

Som standard filtreras inte andra visuella objekt i rapporten när du ändrar detaljnivån. Du kan aktivera den här funktionen i Power BI Desktop och Power BI-tjänsten.

1. I Desktop väljer du fliken **Format** och markerar kryssrutan för **Att gå in på detalj filtrerar andra visuella objekt**.

    ![Skärmbild som visar inställningen Att gå in på detalj filtrerar andra visuella objekt i Power BI Desktop](./media/end-user-drill/power-bi-drill-filters-desktop.png)

1. När du ökar eller minskar detaljnivån eller expanderar i en visualisering med en hierarki, filtrerar åtgärden nu även övriga visuella objekt på sidan.

    ![Skärmbild av resultatet i Desktop.](./media/end-user-drill/power-bi-drill-filters.png)

    ![Skärmbild av det andra resultatet i Desktop.](./media/end-user-drill/power-bi-drill-filters2.png)

> [!NOTE]
> Om du vill aktivera detta i Power BI-tjänsten, väljer du **Visuella interaktioner** > **Att gå in på detalj filtrerar andra visuella objekt** från den översta menyraden.
>
> ![Att gå in på detalj filtrerar andra visuella objekt i Power BI-tjänsten](./media/end-user-drill/power-bi-drill-filters-service.png)

## <a name="learn-about-the-hierarchy-axis-and-hierarchy-group"></a>Mer om hierarkiaxeln och hierarkigruppen

Hierarkiaxeln och hierarkigruppen är mekanismer du kan använda för att öka och minska granulariteten för data som du vill visa. Alla data som kan ordnas i kategorier och underkategorier anses ha en hierarki, exempelvis datum och tider.

Du kan skapa en visualisering i Power BI som har en hierarki genom att välja ett eller flera datafält som läggs till i området **Axel** eller **Grupp**. Lägg sedan till de data du vill granska som datafält i området **Värden**. Dina data är hierarkiska om ikonerna för *granskningsläge* visas längst upp till vänster och höger i visualiseringen.

Det enklaste är att tänka på det som två typer av hierarkiska data:

- Datum- och tidsdata – om du har ett datafält med datatypen DateTime har du redan hierarkiska data. Power BI skapar automatiskt en hierarki för alla datafält. Du kan parsa värdena i en [DateTime](https://msdn.microsoft.com/library/system.datetime.aspx)-struktur. Du behöver bara lägga till ett DateTime-fält i området **Axel** eller **Grupp**.

- Kategoridata – om Power BI hämtar dina data från samlingar som innehåller delsamlingar, eller har rader med data med gemensamma värden, har du hierarkiska data.

Med Power BI kan du expandera en eller alla delmängder. Du kan öka detaljnivån i dina data för att visa en enda delmängd på varje nivå, eller alla delmängder samtidigt på varje nivå. Du kan till exempel öka detaljnivån för ett visst år eller visa alla resultat för varje år nedåt i hierarkin.

Du kan också minska detaljnivån på samma sätt.

I avsnitten nedan beskrivs ökad detaljnivå från den högsta vyn, mellanvyn och den lägsta vyn.

### <a name="hierarchical-data-and-time-data"></a>Hierarkiska data och tidsdata

I det här exemplet:

1. Följ vårt [exempel på detaljhandelsanalys](../sample-datasets.md) och skapa en visualisering av ett staplat kolumndiagram med fokus på:

    | Område | Fält |
    | ---- | ----- |
    | Axel | Tid<br>\|\_ Månad |
    | Värden | Försäljning<br>\|\_ TotalSales |

    Även om datafältet Axel är **Månad** skapar det en **årskategori** i området **Axel**. Det beror på att Power BI ger en fullständig DateTime-struktur för alla värden som läses. Högst upp i hierarkin visas årets data.

    ![Skärmbild av den enskilda stapeln som visar data grupperade efter år](media/end-user-drill/power-bi-hierarchical-axis-datetime-1.png)

1. Med läget för ökad detaljnivå aktiverat väljer du på stapeln i diagrammet för att gå nedåt en nivå i hierarkin. Tre staplar för data för de tillgängliga kvartalen visas.

1. Bland ikonerna uppe till vänster väljer du alternativet för att **expandera allt nedåt en nivå i hierarkin**.

1. Gör det en gång till för att komma till nivån längst ned i hierarkin som visar resultaten för varje månad.

    ![Skärmbild av stapeldiagrammet för att visa stapel per månad](media/end-user-drill/power-bi-hierarchical-axis-datetime-2.png)

Förutom visualiseringen kan vi se att hierarkin återspeglas i de data som återges för varje rapport. Välj ellipsen i det övre högra hörnet och välj sedan **Visa data**. I följande tabell visas resultaten av att öka detaljnivån från en månad eller alla månader:

|Läget Expandera|År|Kvartal|Månad|Dag|
| --- |:---:|:---:|:---:|---|
|Enkel|![enskilt år](./media/end-user-drill/power-bi-hierarchical-year.png)|![enskilt kvartal](media/end-user-drill/power-bi-hierarchical-quarter.png)|![enskild månad](./media/end-user-drill/power-bi-hierarchical-one-month.png)|![enskild dag](media/end-user-drill/power-bi-hierarchical-one-day.png)|
|Alla|![alla år](./media/end-user-drill/power-bi-hierarchical-year.png)|![alla kvartal](media/end-user-drill/power-bi-hierarchical-quarter.png)|![alla månader](./media/end-user-drill/power-bi-hierarchical-all-month.png)|![alla dagar](media/end-user-drill/power-bi-hierarchical-all-day.png)|

Observera att aktuella data är desamma för **kvartals-** och **årsrapporterna**. När du ökar detaljnivån till nivån för **Värden** ser du att den enkla rapporten är mer specifik, och att rapporten för alla månader innehåller mer data.

### <a name="hierarchical-category-data"></a>Hierarkiska kategoridata

Data som har modellerats från samlingar och delsamlingar är hierarkiska.

Ett bra exempel på detta är platsdata. Anta att du har en tabell i en datakälla med kolumner för land, region, stad och postnummer. Data som delar samma land, region och stad är hierarkiska.

I det här exemplet:

1. Om du vill följa med, kan du öppna [Exempel på detaljhandelsanalys](../sample-datasets.md). Skapa en visualisering av ett staplat kolumndiagram med fokus på:

    | Område | Fält |
    | ---- | ----- |
    | Värde |Försäljning<br>\|\_ Totalt antal enheter i år |
    | Axel | Lager<br>\|\_ Område<br>\|\_ Stad – du kan behöva dra Stad från området **Förklaring** till området **Axel**.<br>\|\_ Postnummer<br>\|\_ Namn |

    ![Skärmbild av stapeldiagrammet som visar totalt antal enheter i år per område.](media/end-user-drill/power-bi-hierarchical-axis-category-1.png)

1. Se till att läget för ökad detaljnivå är aktiverat. Bland ikonerna längst upp till vänster väljer du alternativet för att **expandera allt nedåt en nivå i hierarkin** tre gånger.

    Du är nu på nivån längst ned i hierarkin, som visar resultaten för Område, Stad och Postnummer.

    ![Skärmbild av stapeldiagrammet som visar den lägsta nivån i hierarkin, den mest detaljerade.](media/end-user-drill/power-bi-hierarchical-axis-category-2.png)

Förutom visualiseringen kan vi se att hierarkin återspeglas i de data som återges för varje rapport. Välj ellipsen i det övre högra hörnet och välj sedan **Visa data**. I följande tabell visas resultatet av att öka detaljnivån för ett enskilt område eller alla områden.

| Läget Expandera|Område|Stad|Postnummer|Namn|
| ---|:---:|:---:|:---:|---|
|Enkel|![enskilt område](./media/end-user-drill/power-bi-hierarchical-territory.png)|![enskild stad](media/end-user-drill/power-bi-hierarchical-one-territory-city.png)|![enskilt postnummer](./media/end-user-drill/power-bi-hierarchical-one-territory-city-postal.png)|![enskilt namn](media/end-user-drill/power-bi-hierarchical-one-territory-city-postal-name.png)|
|Alla|![alla områden](./media/end-user-drill/power-bi-hierarchical-territory.png)|![alla städer](media/end-user-drill/power-bi-hierarchical-all-territory-city.png)|![alla postnummer](./media/end-user-drill/power-bi-hierarchical-all-territory-city-postal.png)|![alla namn](media/end-user-drill/power-bi-hierarchical-all-territory-city-postal-name.png)|

 När du ökar detaljnivån kan du se hur den **enkla** rapporten blir mer specifik och att rapporten med **alla** områden innehåller mer data.

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

Om tillägget av ett datumfält till en visualisering inte skapar en hierarki, kan det bero på att datumfältet faktiskt inte har sparats som ett datum. Om du äger datamängden:

1. Öppna den i vyn *Data* i Power BI Desktop.

1. Välj den kolumn som har datumet.

1. På fliken **Modellering** ändrar du **Datatyp** till **Datum** eller **Datum/tid**.

![Skärmbild av vyn för att välja data. I det övre högra hörnet visas datumtyp.](media/end-user-drill/power-bi-change-data-type2.png)

Om rapporten har delats med dig, kontakta ägaren om du vill begära ändringen.

## <a name="next-steps"></a>Nästa steg

[Visualiseringar i Power BI-rapporter](../visuals/power-bi-report-visualizations.md)

[Power BI-rapporter](end-user-reports.md)

[Power BI – grundläggande begrepp](end-user-basic-concepts.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
