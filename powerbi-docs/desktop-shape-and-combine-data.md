---
title: Forma och kombinera data från flera källor
description: I den här självstudien får du lära dig hur du formar och kombinerar data i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: f39f5ae569c757072a55647becb5697c881abbe2
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54285679"
---
# <a name="tutorial-shape-and-combine-data-in-power-bi-desktop"></a>Självstudie: Forma och kombinera data i Power BI Desktop

Med **Power BI Desktop**, kan du ansluta till flera olika typer av datakällor och sedan forma data så att de uppfyller dina behov, så att du kan skapa visuella rapporter som du kan dela med andra. *Formatera* data innebär att du omvandlar data – till exempel byter namn på kolumner eller tabeller, ändrar text till tal, tar bort rader, anger den första raden som rubrik och så vidare. *Kombinera* data innebär att kopplar till två eller flera datakällor, formar dem efter behov och sammanfogar dem i en användbar fråga.

I den här självstudien lär du dig att:

* Formen data med hjälp av **Frågeredigeraren**
* Anslut till en datakälla
* Anslut till en annan datakälla
* Kombinera dessa datakällor och skapa en datamodell som ska användas i rapporter

Den här självstudien beskriver hur du utformar en fråga med Power BI Desktop och visar några av de vanligaste uppgifterna. Frågan som används här beskrivs i detalj, inklusive hur du skapar en fråga från början, i [Komma igång med Power BI Desktop](desktop-getting-started.md).

Det är bra att veta att **frågeredigeraren** i Power BI Desktop använder högerklicksmenyer och menyfliksområdet. Merparten av det som du kan välja i menyfliksområdet **Transformera** är också tillgängligt genom att högerklicka på ett objekt (till exempel en kolumn) och välja från menyn som visas.

## <a name="shape-data"></a>Forma data
När du formar data i frågeredigeraren ger du stegvisa-instruktioner (som frågeredigeraren utför) för att justera de data som frågeredigeraren hämtar och presenterar. Den ursprungliga datakällan påverkas inte utan det är endast den här datavyn som justeras eller *formas*.

De steg som du anger (till exempel när du byter namn på en tabell, transformerar datatypen eller tar bort kolumner) registreras av frågeredigeraren och varje gång den här frågan ansluter till datakällan utförs dessa steg så att data alltid utformas på det sätt som du anger. Den här processen inträffar när du använder funktionen Query Editor i Power BI Desktop eller för alla som använder din delade fråga, till exempel på **Power BI**-tjänsten. De här stegen fångas i ordning i fönstret **Frågeinställningar** under **Tillämpade steg**.

Följande bild visar fönstret **Frågeinställningar** för en fråga som har formats – vi ska gå igenom de här stegen i följande stycken.

![](media/desktop-shape-and-combine-data/shapecombine_querysettingsfinished2.png)

Vi använder pensioneringsdata från [Komma igång med Power BI Desktop](desktop-getting-started.md), vilket vi hämtade genom att ansluta till en webbdatakälla, som vi ska forma efter våra behov.

Till att börja med ska vi lägga till en egen kolumn för att beräkna rankningen baserat på alla data som har samma faktorer och jämföra detta med den befintliga kolumnen _Rankning_.  Här är menyfliken **Lägg till kolumn**, med en pil som pekar mot knappen **Anpassad kolumn**, vilken låter dig lägga till en egen kolumn.

![](media/desktop-shape-and-combine-data/shapecombine_customcolumn.png)

I dialogrutan **Anpassad kolumn** i **Nytt kolumnnamn**, anger du _Ny rankning_, och i **Anpassad kolumnformel**, anger du följande:

    ([Cost of living] + [Weather] + [Health care quality] + [Crime] + [Tax] + [Culture] + [Senior] + [#"Well-being"]) / 8

Kontrollera att statusmeddelandet visar _”Inga syntaxfel har identifierats.”_ och klicka på **OK**.

![](media/desktop-shape-and-combine-data/shapecombine_customcolumndialog.png)

För att hålla kolumndata konsekventa, kan du omvandla de nya kolumnvärdena till heltal. Det är bara att högerklicka på kolumnrubriken och välja **Ändra typ \> Heltal** för att ändra dem. 

Om du behöver välja fler än en kolumn ska du först markera en kolumn och sedan hålla ned **SKIFT**. Välj fler intilliggande kolumner och högerklicka på en kolumnrubrik för att ändra alla valda kolumner. Använd **CTRL** när du väljer kolumner som inte är intilliggande.

![](media/desktop-shape-and-combine-data/shapecombine_changetype2.png)

Du kan också *transformera* kolumndatatyperna från menyfliken **transformera**. Här är menyfliksområdet **Omvandla** med en pil som pekar mot knappen **Datatyp**, som låter dig omvandla den aktuella datatypen till en annan.

![](media/desktop-shape-and-combine-data/queryoverview_transformribbonarrow.png)

Observera att **Tillämpade steg** i **Frågeinställningar** återspeglar eventuella formningssteg som tillämpas på informationen. Det är bara att trycka på **X** till vänster om steget om jag vill ta bort något steg från formningsprocessen. I följande bild visar **Tillämpade steg** de steg som har utförts hittills: ansluta till webbplatsen (**källa**) och välja tabellen (**navigering**). Medan frågeredigeraren hämtar tabellen ändrar den automatiskt textbaserade numeriska kolumner från *Text* till *Heltal* (**ändringstyp**). De två sista stegen visar våra tidigare åtgärder med **Lägg till egen** och **Ändrad typ1:**. 

![](media/desktop-shape-and-combine-data/shapecombine_appliedstepsearly2.png)

Innan vi kan arbeta med den här frågan måste vi utföra ett par ändringar så att dess data hamnar på rätt plats:

* *Justera rankningen genom att ta bort en kolumn* – vi har beslutat att **Levnadskostnader** är en icke-faktor för våra resultat. När vi tagit bort den här kolumnen stöter vi på problem med att data förblir oförändrade. Men det är enkelt att åtgärda med Power BI Desktop och genom att göra detta visar vi den smidiga funktionen **Tillämpade steg** i fråga.
* *Åtgärda några fel* – Eftersom vi har tagit bort en kolumn behöver vi justera våra beräkningar i kolumnen **Ny rankning**. Detta innebär att du ändrar en formel.
* *Sortera data* – Baserat på kolumnerna **Ny rankning** och **Rankning**. 
* *Ersätt data* – Vi ska fokusera på hur du ersätter ett specifikt värde och behovet av att inkludera ett **Tillämpat steg**.
* *Ändra tabellnamnet* – **Tabell 0** är inte en användbar beskrivning, men det är lätt att ändra det.

Om du vill ta bort kolumnen **Levnadskostnader** är det bara att markera den och välja fliken **Start** från menyfliken. Välj sedan **Ta bort kolumner** enligt följande bild.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumnscostofliving.png)

Observera att värdena för _Ny rankning_ inte har ändrats; detta beror på ordningen på stegen. Eftersom frågeredigeraren registrerar stegen i turordning, men oberoende av varandra, kan du flytta varje **tillämpat steg** uppåt eller nedåt i sekvensen. Högerklicka bara på något steg, så visar frågeredigeraren en meny där kan du göra följande: **Byta namn på**, **Ta bort**, **Ta bort** **tills slutet** (ta bort det aktuella steget och alla efterföljande steg för), **Flytta upp**, eller **Flytta ned**. Gå vidare och flytta upp det sista steget _Ta bort kolumner_ till precis ovanför steget _Lägg till egen_.

![](media/desktop-shape-and-combine-data/shapecombine_movestep.png)

Välj sedan steget _Lägg till egen_. Observera att data nu visar _Fel_ som vi behöver åtgärda. 

![](media/desktop-shape-and-combine-data/shapecombine_error2.png)

Det finns ett par sätt att få mer information om varje fel. Du kan markera cellen (utan att klicka på ordet **Fel**) eller klicka på ordet **Fel** direkt. Om du väljer cellen *utan* att klicka på ordet **Fel**, visar frågeredigeraren information om felet längst ned i fönstret.

![](media/desktop-shape-and-combine-data/shapecombine_errorinfo2.png)

Om du klickar på ordet *Fel* direkt, skapas ett **Tillämpat steg** i rutan **Frågeinställningar** med information om felet. Vi vill inte ta den här vägen, så välj **Avbryt**.

För att åtgärda felen, välj kolumnen _Ny rankning_ och visa dataformeln genom att öppna menyfliken **Visa** och välja kryssrutan **Formelfält**. 

![](media/desktop-shape-and-combine-data/shapecombine_formulabar.png)

Nu kan du ta bort parametern _Levnadskostnader_ och minska divisorn genom att ändra formeln till följande: 

    Table.AddColumn(#"Removed Columns", "New Rank", each ([Weather] + [Health care quality] + [Crime] + [Tax] + [Culture] + [Senior] + [#"Well-being"]) / 7)

Välj den gröna bockmarkeringen till vänster om formelfältet eller tryck på **RETUR**, så bör data ersättas med de reviderade värdena och steget **Lägg till egen** bör nu slutföras *utan fel*.

> [!NOTE]
> Du kan också **ta bort fel** (i menyfliksområdet eller på snabbmenyn), vilket tar bort alla rader som innehåller fel. I det här fallet hade vi tagit bort alla rader från våra data och vi vill inte göra det – vi gillar alla våra data och vill behålla dem i tabellen.

Nu behöver vi sortera data baserade på kolumnen **Ny rankning**. Välj först de senast tillämpade steget **Ändrad typ1:** för att få den senaste informationen. Välj sedan listrutan bredvid kolumnrubriken **Ny rankning** och välj **Sortera stigande**.

![](media/desktop-shape-and-combine-data/shapecombine_sort.png)

Observera att data nu sorteras enligt **Ny rankning**.  Men om du tittar i kolumnen **Rankning**, kommer du att märka att data inte sorteras korrekt i fall där värdet **Ny rankning** är ett oavgjort resultat. Lös problemet genom att välja kolumnen **Ny rankning** och ändra formeln i **Formelfältet** till följande:

    = Table.Sort(#"Changed Type1",{{"New Rank", Order.Ascending},{"Rank", Order.Ascending}})

Välj grön bockmarkering till vänster om formelfältet eller tryck på **RETUR**, så bör raderna nu sorteras i enlighet med både _Ny rankning_ och _Rankning_.

Dessutom kan du välja ett **Tillämpat steg** var som helst i listan och fortsätta forma data från den punkten i sekvensen. Frågeredigeraren infogar automatiskt ett nytt steg direkt efter det markerade **tillämpade steget**. Vi gör ett försök.

Först väljer du **Tillämpade steg** innan du lägger till den anpassade kolumnen. Detta är steget _Borttagna kolumnen_. Här kommer vi att ersätta värdet för rankningen _Väder_ i Arizona. Högerklicka på lämplig cell som innehåller Arizonas rankning för _Väder_ och välj *Ersätt värden...*  från menyn som visas. Observera vilket **Tillämpat steg** som är valt (steget innan steget _Lägg till egen_).

![](media/desktop-shape-and-combine-data/shapecombine_replacevalues2.png)

Eftersom vi infogar ett steg varnar frågeredigeraren oss om risken med detta – följande steg kan skada frågan. Vi måste vara försiktiga och eftertänksamma! Eftersom detta är en genomgång och vi visar en riktigt fiffig funktion hos frågeredigeraren för att demonstrera hur du kan skapa, ta bort, infoga och sortera om stegen kan vi köra på och välja **Infoga**.

![](media/desktop-shape-and-combine-data/shapecombine_insertstep.png)

Ändra värdet till _51_ så ersätts data för Arizona. När du skapar ett nytt tillämpat steg namnger frågeredigeraren steget baserat på åtgärden, i det här fallet **Ersatt värde**. När du har mer än ett steg med samma namn i din fråga lägger frågeredigeraren till en siffra (i ordning) till varje efterföljande **tillämpat steg** att åtskilja dem.

Välj nu senaste **Tillämpat steg**, _Sorterade rader_, och notera att informationen har ändrats för Arizonas nya rankning.  Detta beror på att vi infogade steget _Ersatt värde_ på rätt plats innan steget _Lägg till egen_.

Okej, det var lite komplicerat, men det var ett bra exempel på hur kraftfull och mångsidig frågeredigeraren kan vara.

Till sist vill vi ändra namnet på tabellen till en beskrivande text. När det är dags att skapa rapporter är det särskilt praktiskt att ha beskrivande namn, särskilt när vi ansluter till flera datakällor och de är listade i rutan **Fält** rutan i **Rapportvyn**.

Du kan enkelt ändra tabellnamnet: i rutan **frågeinställningar** under **Egenskaper** skriver du det nya namnet på tabellen som visas i följande bild och trycker på **Retur**. Vi kan kalla den här tabellen *Pensioneringsstatistik*.

![](media/desktop-shape-and-combine-data/shapecombine_renametable2.png)

Okej, nu har vi format dessa data efter våra behov. Nu ska vi ansluta till en annan datakälla och kombinera data.

## <a name="combine-data"></a>Kombinera data
Våra data om olika delstater är intressanta och kommer vara användbara för att skapa mer analysverktyg och -frågor. Men det finns ett problem: de flesta data använder en tvåbokstavsförkortning för delstatskoder, inte det fullständiga namnet på delstaten. Vi behöver hitta ett sätt att associera delstatsnamn med deras förkortningar.

Vi har tur: det finns en annan offentlig datakälla som gör just detta, men den måste formas en hel del innan vi kan ansluta den till vår pensionstabell. Här är webbresursen för delstatsförkortningar:

<http://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations>

Från menyfliksområdet **Start** i frågeredigeraren väljer vi **Ny källa \> Webb** och anger adressen. Välj **Anslut** och så visar Navigator vad den fann på webbplatsen.

 ![](media/desktop-shape-and-combine-data/designer_gsg_usstateabbreviationsnavigator2.png)

Vi väljer **Koder och förkortningar ...** eftersom den innehåller användbara data men det kommer att krävas en hel del omformning innan vi kan reducera tabellens data till det vi behöver.

> [!TIP]
> Finns det något snabbare eller enklare sätt att utföra stegen nedan? Ja, kan vi skapa en *relation* mellan två tabeller och forma data baserat på relationen. Följande steg är fortfarande bra om du vill bli bättre på att arbeta med tabeller, men det är bra att veta att relationer är ett snabbt sätt att använda data från flera tabeller.
> 
> 

Vi gör följande för att ordna våra data:

* Ta bort den översta raden – den är ett resultat av hur webbsidans tabell skapade och vi behöver den inte. Välj **minska rader \> Ta bort rader \> Ta bort översta rader** från menyfliksområdet **Start**.

![](media/desktop-shape-and-combine-data/shapecombine_removetoprows.png)

Fönstret **Ta bort översta rader**, där du kan ange hur många rader som du vill ta bort.

>[!NOTE]
>Om Power BI av misstag importerar tabellrubriker som en rad i datatabellen, kan du välja **Använd första raden som rubriker** från fliken **Start** eller från fliken **Transformera** i menyfliksområdet för att åtgärda tabellen.

* Ta bort de nedersta 26 raderna – de är territorier som vi inte behöver inkludera. Välj **minska rader \> Ta bort rader \> Ta bort nedersta rader** från menyfliksområdet **Start**.

![](media/desktop-shape-and-combine-data/shapecombine_removebottomrows.png)

* Eftersom tabellen Pensioneringsstatistik saknar information för Washington DC kan behöver vi filtrera det från listan. Välj listrutepilen bredvid kolumnen Regionstatus och avmarkera sedan kryssrutan bredvid **Federalt distrikt**.

![](media/desktop-shape-and-combine-data/shapecombine_filterdc.png)

* Ta bort några kolumner som inte behövs – vi behöver bara mappningen av delstaten till dess officiella tvåbokstavsförkortning så vi kan ta bort följande kolumner: **Kolumn1**, **Kolumn3**, **Kolumn4** och sedan **Kolumn6** till **Kolumn11**. Markera **Kolumn1 **och håll nere tangenten** CTRL** och markera kolumnerna som ska tas bort (kolumnerna behöver inte vara intilliggande). Välj **Ta bort kolumner \> Ta bort kolumner** från fliken Start i menyfliksområdet.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumns.png)

>[!NOTE]
>Detta är ett bra tillfälle att påpeka att *sekvensen* med tillämpade steg i frågeredigeraren är viktig och kan påverka hur data formas. Det är också viktigt att tänka på hur ett steg kan påverka andra efterföljande steg. Om du tar bort ett steg Tillämpade steg kanske efterföljande steg inte fungerar som avsett på grund av effekten på frågornas ordningsföljd.

>[!NOTE]
>När du ändrar storlek på Query Editor-fönstret för att göra bredden mindre förminskas vissa objekt i menyfliksområdet för att maximera användningen av synligt utrymme. Om du ökar bredden på Query Editor-fönstret utökas objektet i menyfliksområdet för att använda utrymmet i menyfliksområdet optimalt.

* Byt namn på kolumner och tabellen – som vanligt finns det några olika sätt att byta namn på en kolumn. Markera kolumnen först, välj sedan **Byt namn**  från fliken **Transformera** i menyfliksområdet eller högerklicka och välj **Byt namn på...** från menyn som visas. Följande bild har pilar som pekar på båda alternativen. Du behöver bara välja en.

![](media/desktop-shape-and-combine-data/shapecombine_rename.png)

Nu ska vi byta namn på dem till *Tillståndsnamn* och *Delstatskod*. Om du vill byta namn på tabellen, skriver du namnet i rutan **namn** bredvid fönstret **Frågeinställningar**. Vi kan kalla den här tabellen *Delstatskoder*.

Nu när vi har format tabellen Delstatskoder kan vi kombinera de två tabellerna, eller frågorna, till en. Eftersom tabellerna är resultatet från frågorna som vi tillämpade på våra data kallar vi dem ofta för *frågor*.

Det finns två sätt att kombinera frågor – *sammanslagning* och *bifoga*.

När du har en eller flera kolumner som du vill lägga till i en annan fråga kan du **sammanfoga** frågorna. När du har ytterligare rader med data som du vill lägga till en befintlig fråga kan du **bifoga** frågan.

I det här fallet vill vi sammanfoga frågor. För att komma igång väljer du frågan i frågeredigeraren *där du vill* att den andra frågan ska sammanfogas, i det här fallet *Pensionsstatistik*. Välj sedan **Kombinera \> Sammanfoga frågor** från fliken **Start** på menyfliksområdet.

![](media/desktop-shape-and-combine-data/shapecombine_mergequeries.png)

Du kan uppmanas att ange sekretessnivåer för att säkerställa att data kombineras utan att inkludera eller överföra data som du inte ville överföra.

Därefter visas fönstret **Sammanfoga**, där vi kan välja vilken tabell som vi vill sammanfoga i den markerade tabellen och sedan klicka på de matchande kolumnerna som ska användas för sammanfogningen. Välj Delstat från tabellen *Pensionsstatistik* (fråga). Välj sedan frågan *Delstatskoder* (enkelt i det här fallet eftersom det är enbart en annan fråga – när du ansluter till flera datakällor finns det många frågor att välja mellan). När vi väljer rätt matchande kolumner – **Delstat** från *Pensionsstatistik*, och **Delstatsnamn** från *Delstatskoder* – ser fönstret **Sammanfoga** ut ungefär så här, och knappen **OK** är aktiverad.

![](media/desktop-shape-and-combine-data/shapecombine_merge2.png)

En **NewColumn** skapas i slutet av frågan, vilket är innehållet för tabellen (frågan) som har sammanfogats med den befintliga frågan. Alla kolumner från den sammanfogade frågan ryms i **NyKolumn**, men du kan välja att **Expandera** tabellen inkludera alla kolumner du vill.

![](media/desktop-shape-and-combine-data/shapecombine_mergenewcolumn.png)

Om du vill utöka den sammanfogade tabellen och välja vilka kolumner som ska ingå, väljer du ikonen (![Expandera](media/desktop-shape-and-combine-data/icon.png)). Fönstret **Expandera** visas.

![](media/desktop-shape-and-combine-data/shapecombine_mergeexpand.png)

I det här fallet är vi bara intresserade av kolumnen **Delstatskod** så vi väljer bara den kolumnen och sedan **OK**. Vi avmarkerar kryssrutan från Använd det ursprungliga kolumnnamnet som prefix eftersom vi inte behöver eller vill använda den. Om vi lämnar som den markerad kommer den sammanfogade kolumnen heta **NyKolumn.State kod** (det ursprungliga kolumnnamnet eller **NyKolumn**, sedan en punkt och sedan namnet på kolumnen som användes i frågan).

>[!NOTE]
>Vill du experimentera med hur du hanterar **NyKolumn**-tabellen? Du kan prova dig fram och om du inte gillar resultatet är det bara att ta bort steget från listan **Tillämpade steg** i fönstret **Frågeinställningar**. Din fråga återgår till tillståndet innan du tillämpade steget **Expandera**. Det är som en gratis uppfräschning, som du kan upprepa hur många gånger som helst tills du är nöjd med expanderingsprocessen.

Nu har vi en enskild fråga (tabellen) som kombinerar två datakällor som har formats efter våra behov. Den här frågan kan fungera som bas för många intressanta dataanslutningar – till exempel statistik över bostadskostnader, demografi eller jobbmöjligheter i varje delstat.

Om du vill tillämpa ändringarna och stänga frågeredigeraren väljer du **Stäng och tillämpa** från menyfliksområdet **Start**. Den omvandlade datauppsättningen visas i Power BI Desktop och är redo för användning när du skapar rapporter.

![](media/desktop-shape-and-combine-data/shapecombine_closeandapply.png)

## <a name="next-steps"></a>Nästa steg
Det finns olika typer av saker som du kan göra med Power BI Desktop. Läs följande resurser för mer information om dess möjligheter:

* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
* [Frågeöversikt med Power BI Desktop](desktop-query-overview.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Anslut till data i Power BI Desktop](desktop-connect-to-data.md)
* [Vanliga frågeuppgifter i Power BI Desktop](desktop-common-query-tasks.md)   

