---
title: Öka och minska detaljnivån i ett visuellt objekt
description: Den här artikeln beskriver hur du ökar detaljnivån i ett visuellt objekt i Microsoft Power BI-tjänsten.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 21d663b2f29a8090e6cfb7013d16c739ef0a29b3
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73851462"
---
# <a name="drill-mode-in-a-visual-in-power-bi"></a>Granskningsläge i ett visuellt objekt i Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Den här artikeln beskriver hur du ökar detaljnivån i ett visuellt objekt i Microsoft Power BI-tjänsten. Genom att öka och minska detaljnivån för dina datapunkter, kan du utforska detaljerad information om dina data. 

## <a name="drill-requires-a-hierarchy"></a>Detaljgranskning kräver en hierarki

När en visualisering har en hierarki kan du öka detaljnivån till att visa ytterligare information. Du kan till exempel ha ett visuellt objekt som kontrollerar OS-medaljantal enligt en hierarki som består av sport, gren och evenemang. Som standard visar det visuellt objektet medaljantal efter sport: gymnastik, skidåkning, vattensport osv. Men eftersom den har en hierarki, skulle val av ett av de visuella elementen (till exempel ett stapel-, linje- eller bubbeldiagram), visa en allt mer detaljerad bild. Om du väljer elementet **vattensporter** visas data för simning, simhopp och vattenpolo.  Om du väljer elementet **simhopp** visas detaljer för trampolin, plattform och synkroniserade simhopp.

Datum är en unik typ av hierarki.  Rapportdesigners lägger ofta till datum-hierarkier i visuella objekt. En vanlig datumhierarki kan till exempel innehålla år, kvartal, månad och dag. 

## <a name="figure-out-which-visuals-can-be-drilled"></a>Räkna ut vilka visuella objekt som kan detaljgranskas
Är du osäker på vilka visuella Power BI-objekt som innehåller en hierarki? Hovra över ett visuellt objekt. Om du ser en kombination av dessa granskningskontroller längst upp har det visuella objektet en hierarki.

![Skärmbild av granskningsikonerna.](./media/end-user-drill/power-bi-drill-icons.png)  

## <a name="learn-how-to-drill-down-and-up"></a>Lär dig hur du ökar/minskar detaljnivån

I det här exemplet använder vi en trädkarta som har en hierarki som består av område, stad, postnummer och butiksnamn. Trädkartan visar, före granskningen, hur många enheter som sålts totalt den här året per område. 

![Skärmbild av trädkartan och dess filter.](./media/end-user-drill/power-bi-treemaps.png)  


### <a name="two-ways-to-access-the-drill-features"></a>Tre sätt att få åtkomst till granskningsfunktioner

Det finns två sätt att få åtkomst till funktioner för att öka och minska detaljnivån samt expandera för visuella objekt som har hierarkier. Prova dem och använd den som du gillar mest.

- Det första sättet: Hovra över ett visuellt objekt för att se och använda ikonerna.  

    ![Skärmbild av hovringsexemplet.](./media/end-user-drill/power-bi-hover.png)

- Det andra sättet: Högerklicka på ett visuellt objekt för att visa och använda menyn.

    ![Skärmbild av högerklicksexemplet.](./media/end-user-drill/power-bi-drill-menu.png)



## <a name="drill-pathways"></a>Sökvägar för granskning

### <a name="drill-down-all-fields-at-once"></a>Öka detaljnivån för alla fält på en gång
![Ikonen för att öka detaljnivån](./media/end-user-drill/power-bi-drill-icon3.png)

Det finns olika sätt att granska det visuella objektet mer detaljerat. Om du väljer ikonen för att öka detaljnivån kommer du till nästa nivå i hierarkin. Om du tittar på nivån **Område** för Kentucky och Tennessee kan du öka detaljnivån till stadsnivån för båda delstaterna, sedan postnummernivån för båda delstaterna och slutligen butiknamnsnivån för båda delstaterna. Varje steg i sökvägen visar nya uppgifter.

![Diagram som visar dina olika sökvägar för ökad detaljnivå](./media/end-user-drill/power-bi-drill-path.png)

Välj ikonen för att minska detaljnivån ![Ikonen för att minska detaljnivån](./media/end-user-drill/power-bi-drill-icon5.png) tills du kommer tillbaka till ”Totalt antal enheter i år efter område”.

### <a name="expand-all-fields-at-once"></a>Expandera alla fält samtidigt
![Ikonen för att expandera](./media/end-user-drill/power-bi-drill-icon6.png)

**Expandera** lägger till ytterligare en hierarkinivå i den aktuella vyn. Så om du tittar på nivån **Område** kan du expandera och lägga till ort, postnummer och namn i din trädkarta. Varje steg i sökvägen visar samma information och lägger till en nivå med ny information.

![Diagram som visar sökvägen för expansion](./media/end-user-drill/power-bi-expand-path.png)

Du kan också välja att öka detaljnivån för eller expandera ett fält i taget.


### <a name="drill-down-one-field-at-a-time"></a>Öka detaljnivån ett fält i taget


1. Välj ikonen för ökad detaljnivå för att aktivera den ![Skärmbild av aktiverad ikon för ökad detaljnivå på/av.](./media/end-user-drill/power-bi-drill-icon2.png).

    Nu kan du öka detaljnivån **ett fält i taget** genom att välja ett visuellt element. Exempel på visuella element är: stapel-, bubbel- eller lövdiagram.

    ![Skärmbild av ett visuellt objekt med en pil som pekar på den aktiverade ikonen för ökad detaljnivå på/av.](media/end-user-drill/power-bi-drill-icon-selected.png)

    Om du inte slår på ökad detaljnivå på, visas inte en ökad detaljnivå när du väljer ett visuellt element (till exempel ett stapel-, bubbel- eller lövdiagram). I stället korsfiltrerar det de övriga diagrammen på rapportsidan.

1. Välj lövnod för **TN**. Din trädkarta visar nu alla städer och områden i Tennessee som har en butik.

    ![Skärmbild av trädkartan som visar data för endast TN.](media/end-user-drill/power-bi-drill-down-one.png)

1. Nu kan du:

    1. Fortsätta öka detaljnivån för Tennessee.

    1. Öka detaljnivån för en viss stad i Tennessee.

    1. Expandera i stället.

    Låt oss nu fortsätta att öka detaljnivån ett fält i taget.  Välj **Knoxville, TN**. Din trädkarta visar nu postnumren för dina butiker i Knoxville.

    ![Skärmbild av trädkartan som visar postnummer 37919.](media/end-user-drill/power-bi-drill-two.png)

    Observera att rubriken ändras när du ändrar detaljnivån ner och upp igen.

### <a name="expand-all-and-expand-one-field-at-a-time"></a>Expandera alla och expandera ett fält i taget

En trädkarta som bara visar postnummer är inte användbar.  Så låt oss *expandera* en nivå ned i hierarkin.  

1. Välj ikonen för att expandera ned *expandera ned* med trädkartan aktiverad. ![Skärmbild av ikonen för att expandera ned.](./media/end-user-drill/power-bi-drill-icon6.png) Två nivåer av vår hierarki visas nu i din trädkarta: postnummer och butiksnamn.

    ![Skärmbild av trädkartan som visar postnummer butiksnamn](./media/end-user-drill/power-bi-expand-one.png)

1. För att se alla fyra hierarkinivåer av data för Tennessee väljer du pilen för att minska detaljnivån tills du når den andra nivån, **totalt antal enheter i år efter område och stad**, för din trädkarta.

    ![Skärmbild av trädkartan som visar alla data för TN.](media/end-user-drill/power-bi-expand-two.png)

1. Se till att ökning av detaljnivån fortfarande är aktiverat. ![Skärmbild av aktiverad ikon för ökad detaljnivå på/av.](./media/end-user-drill/power-bi-drill-icon2.png) och välj ikonen för att *expandera ned* ![Skärmbild av ikonen för att expandera ned.](./media/end-user-drill/power-bi-drill-icon6.png) Din trädkarta visar nu samma antal löv (rutor), men varje löv har ytterligare information. Istället för att bara visa stad och stat, visas nu även postnumret.

    ![Skärmbild av det visuella objektet med visning av stad, stat och postnummer.](./media/end-user-drill/power-bi-expand-three.png)

1. Välj ikonen *expandera ned* en gång till för att visa alla fyra hierarkinivåer i detalj för Tennessee i din trädkarta. Hovra över en lövnod för att se ytterligare information.

    ![Skärmbild av trädkartan som visar en knappbeskrivning med lövspecifika data.](./media/end-user-drill/power-bi-expand-all.png)

## <a name="show-the-data-as-you-drill"></a>Visa data medan du ändrar detaljnivå
Använd **Visa data** för att se vad som händer bakom kulisserna. Varje gången du ökar detaljnivån eller expanderar visas de data som används för att bygga det visuella objektet när du använder **Visa data**. Detta kan hjälpa dig att förstå hur visuella objekt byggs upp genom en samverkan av hierarkier, detaljgranskning och expansion. 

Välj **Fler alternativ** (...) uppe till höger och sedan **Visa data**. 

![Skärmbild av ellipsmenyn.](./media/end-user-drill/power-bi-ellipses.png)

I följande tabell visas resultatet av en ökning av detaljnivån för alla fält samtidigt, från område till butiksnamn.  


![Skärmbild som visar data för alla fyra detaljnivåer.](./media/end-user-drill/power-bi-show-data.png)

Observera att summorna är desamma för **Stad**, **Postnummer** och **Namn**. Detta är inte alltid fallet.  Men för dessa data finns endast en butik i varje postnummer och i varje stad.  



## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
Som standard filtreras inte andra visuella objekt i rapporten när du ändrar detaljnivån. Rapportdesignern kan dock ändra detta standardbeteende. Medan du ändrar detaljnivå ser du om de andra visuella objekten på sidan korsfiltreras eller korsmarkeras.


## <a name="next-steps"></a>Nästa steg

[Visuella objekt i Power BI-rapporter](../visuals/power-bi-report-visualizations.md)

[Power BI-rapporter](end-user-reports.md)

[Power BI – grundläggande begrepp](end-user-basic-concepts.md)

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
