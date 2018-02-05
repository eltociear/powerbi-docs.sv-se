--rubrik: Forma och kombinera data i Power BI Desktop-beskrivning: Forma och kombinera data i Power BI Desktop-tjänster: powerbi documentationcenter: '' author: davidiseminger manager: kfile backup: '' editor: '' tags: '' qualityfocus: no qualitydate: ''''

ms.service: powerbi ms.devlang: NA ms.topic: article ms.tgt_pltfrm: NA ms.workload: powerbi ms.date: 01/30/2018 ms.author: davidi

---
# <a name="shape-and-combine-data-in-power-bi-desktop"></a>Forma och kombinera data i Power BI Desktop
Med **Power BI Desktop** kan du ansluta till flera olika typer av datakällor och sedan forma data efter dina behov. *Formatera* data innebär att du omvandlar data – till exempel byter namn på kolumner eller tabeller, ändrar text till tal, tar bort rader, anger den första raden som rubrik och så vidare. *Kombinera* data innebär att kopplar till två eller flera datakällor, formar dem efter behov och sammanfogar dem i en användbar fråga.

Det här dokumentet beskriver hur du utformar en fråga med Power BI Desktop och visar några av de vanligaste uppgifterna. Frågan som används här beskrivs i detalj, inklusive hur du skapar en fråga från början, i [Komma igång med Power BI Desktop](desktop-getting-started.md).

Det är bra att veta att **frågeredigeraren** i Power BI Desktop använder högerklicksmenyer och menyfliksområdet. Merparten av det som du kan välja i menyfliksområdet **Transformera** är också tillgängligt genom att högerklicka på ett objekt (till exempel en kolumn) och välja från menyn som visas.

## <a name="shape-data"></a>Forma data
När du formar data i frågeredigeraren ger du stegvisa-instruktioner (som frågeredigeraren utför) för att justera de data som frågeredigeraren hämtar och presenterar. Den ursprungliga datakällan påverkas inte utan det är endast den här datavyn som justeras eller *formas*.

De steg som du anger (till exempel när du byter namn på en tabell, transformerar datatypen eller tar bort kolumner) registreras av frågeredigeraren och varje gång den här frågan ansluter till datakällan utförs dessa steg så att data alltid utformas på det sätt som du anger. Den här processen inträffar när du använder funktionen Query Editor i Power BI Desktop eller för alla som använder din delade fråga, till exempel på **Power BI**-tjänsten. De här stegen avbildas i ordning i fönstret **frågeinställningar** under **Tillämpade steg**.

Följande bild visar fönstret **Frågeinställningar** för en fråga som har formats – vi ska gå igenom de här stegen i följande stycken.

![](media/desktop-shape-and-combine-data/shapecombine_querysettingsfinished.png)

Vi använder pensioneringsdata från [Komma igång med Power BI Desktop](https://powerbi.uservoice.com/knowledgebase/articles/471664), vilket vi hämtade genom att ansluta till en webbdatakälla, som vi ska forma efter våra behov.

Till att börja med var en kolumns värden inte automatiskt omvandlade från text till siffror när QueryEditor hämtade tabellen. Vi vill att de ska vara siffror. Inga problem – det är bara att högerklicka på kolumnrubriken och välja **Ändra typ \> Heltal** för att ändra dem. Om du vill välja fler än en kolumn ska du först markera en kolumn och sedan hålla ned **SKIFT**. Välj fler intilliggande kolumner och högerklicka på en kolumnrubrik för att ändra alla valda kolumner. Använd **CTRL** när du väljer kolumner som inte är intilliggande.

![](media/desktop-shape-and-combine-data/shapecombine_changetype.png)

Du kan också *omvandla* dessa kolumner från text till rubrik från menyfliksområdet **Transformera**. Här är menyfliksområdet **transformera** med en pil som pekar mot knappen **datatyp**, som gör att du kan omvandla det aktuella objektets datatyp till en annan.

![](media/desktop-shape-and-combine-data/queryoverview_transformribbonarrow.png)

Observera att **Tillämpade steg** i **Frågeinställningar** återspeglar eventuella formningssteg som tillämpas på informationen. Det är bara att trycka på **X** till vänster om steget om jag vill ta bort något steg från formningsprocessen. I följande bild visar **Tillämpade steg** de steg som har utförts hittills: ansluta till webbplatsen (**källa**) och välja tabellen (**navigering**). Medan frågeredigeraren hämtar tabellen ändrar den automatiskt textbaserade numeriska kolumner från *Text* till *Heltal* (**ändringstyp**). En kolumn med rangordning ändrades inte automatiskt till en sifferbaserad typ och vi får veta varför om några stycken.

![](media/desktop-shape-and-combine-data/shapecombine_appliedstepsearly.png)

Innan vi kan arbeta med den här frågan måste vi utföra ett par ändringar så att dess data hamnar på rätt plats:

* *Ta bort den första kolumnen* – den behövs inte, den innehåller endast överflödiga rader som säger ”Se hur din delstat är rangordnat för pensioner”, vilket är en rest från datakällan som är en webbaserad tabell
* *Åtgärda ett par fel* – en kolumn, **kvalitet på sjukvård** innehåller några bindningar i staternas rangordning, vilket observerades på webbplatsen genom att lägga till texten *(koppla)* efter deras nummer. Det fungerar bra på webbplatsen men vi måste omvandla kolumnen från text till data manuellt. Det är lätt att åtgärda detta med hjälp av Power BI Desktop med en fiffig funktion hos **Tillämpade steg** i frågan
* *Ändra tabellnamnet* – **tabell 0** är inte en användbar beskrivning, men det är lätt att ändra det

Om du vill ta bort den första kolumnen är det bara att markera den och välja fliken **Start** fliken från menyfliken. Välj sedan **ta bort kolumner** enligt följande bild.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumnsretirement.png)

Därefter måste vi hantera textkolumnen och omvandla den till siffror. Först verkar det enkelt, som om vi kan ändra typen för kolumen **sjukvårdskvalitet** kolumn från text till siffror (t.ex *heltal* eller *decimaltal*). Men när vi ändrar typen från **Text** till **Heltal** och letar genom värdena i kolumnen ser vi att frågeredigeraren rapporterar ett par fel.

![](media/desktop-shape-and-combine-data/shapecombine_error.png)

Det finns ett par sätt att få mer information om varje fel. Du kan markera cellen (utan att klicka på ordet **Fel**) eller klicka på ordet **Fel** direkt. Om du väljer cellen *utan* att klicka på ordet **Fel**, visar frågeredigeraren information om felet längst ned i fönstret.

![](media/desktop-shape-and-combine-data/shapecombine_errorinfo.png)

Om du klickar på ordet *Fel* direkt, skapas ett **Tillämpat steg** i rutan **Frågeinställningar** med information om felet.

![](media/desktop-shape-and-combine-data/shapecombine_errorselect.png)

Du måste ta bort detta steg genom att klicka på **X** intill det för att gå tillbaka till frågeredigeraren.

När vi väljer det senaste **Tillämpade steget** ser vi felet enligt följande bild.

![](media/desktop-shape-and-combine-data/shapecombine_querystep1.png)

Eftersom frågeredigeraren registrerar steg i turordning kan vi välja steget innan vi ändrade typen i **Tillämpade steg** och se värdet i cellen före transformeringen, som på följande bild.

![](media/desktop-shape-and-combine-data/shapecombine_querystep2.png)

OK! Nu kan vi fixa dessa värden och *därefter* ändra typen. Eftersom frågeredigeraren registrerar stegen i turordning, men oberoende av varandra, kan du flytta varje **tillämpat steg** uppåt eller nedåt i sekvensen. Högerklicka bara på ett steg så visar frågeredigeraren en meny där kan du göra följande: **Byt namn**, **Ta bort**, **Ta bort** **tills slutet** (ta bort det aktuella steget och alla efterföljande steg), **Flytta upp** eller **Flytta ned**.

![](media/desktop-shape-and-combine-data/shapecombine_querystepreorder.png)

Dessutom kan du välja ett **Tillämpat steg** var som helst i listan och fortsätta forma data från den punkten i sekvensen. Frågeredigeraren infogar automatiskt ett nytt steg direkt efter det markerade **tillämpade steget**. Vi gör ett försök.

Först måste vi välja det **tillämpade steget** innan du ändrar kolumnen **sjukvårdskvalitet**. Sedan ersätter vi värdena som har texten ”(koppla)” i cellen så att endast siffran kvarstår. Högerklicka på den cell som innehåller ”35 (koppla)” och välj *Ersätt värden...*  från menyn som visas. Observera vilket **Tillämpat steg** som är valt (steget innan du ändrar typen).

![](media/desktop-shape-and-combine-data/shapecombine_replacevalues.png)

Eftersom vi infogar ett steg varnar frågeredigeraren oss om risken med detta – följande steg kan skada frågan. Vi måste vara försiktiga och eftertänksamma! Eftersom detta är en genomgång och vi visar en riktigt fiffig funktion hos frågeredigeraren för att demonstrera hur du kan skapa, ta bort, infoga och sortera om stegen kan vi köra på och välja **Infoga**.

![](media/desktop-shape-and-combine-data/shapecombine_insertstep.png)

Det finns tre kopplingar så vi ersätter värdena för varje. När du skapar ett nytt tillämpat steg namnger frågeredigeraren steget baserat på åtgärden, i det här fallet **Ersatt värde**. När du har mer än ett steg med samma namn i din fråga lägger frågeredigeraren till en siffra (i ordning) till varje efterföljande **tillämpat steg** att åtskilja dem.

Följande skärmbild visar de tre stegen för **ersatta värden** i **frågeinställningar**, men du kan också se något annat som är ännu mer intressant: eftersom vi har tagit bort alla förekomster av texten ”(koppla)” från kolumne **Sjukvårdskvalitet** slutförs steget **Ändra typ** *utan fel*.

![](media/desktop-shape-and-combine-data/shapecombine_replacedvaluesok.png)

> [!NOTE]
> Du kan också **ta bort fel** (i menyfliksområdet eller på snabbmenyn), vilket tar bort alla rader som innehåller fel. I det här fallet hade vi tagit bort alla delstater med ”*(koppla)*” från våra data och vi vill inte göra det – vi gillar alla delstater och vill ha dem i tabellen.

Okej, det var lite komplicerat, men det var ett bra exempel på hur kraftfull och mångsidig frågeredigeraren kan vara.

Till sist vill vi ändra namnet på tabellen till en beskrivande text. När det är dags att skapa rapporter är det särskilt praktiskt att ha beskrivande namn, särskilt när vi ansluter till flera datakällor och de är listade i rutan **Fält** rutan i **Rapportvyn**.

Du kan enkelt ändra tabellnamnet: i rutan **frågeinställningar** under **Egenskaper** skriver du det nya namnet på tabellen som visas i följande bild och trycker på **Retur**. Vi kan kalla den här tabellen *Pensioneringsstatistik*.

![](media/desktop-shape-and-combine-data/shapecombine_renametable.png)

Okej, nu har vi format dessa data efter våra behov. Nu ska vi ansluta till en annan datakälla och kombinera data.

## <a name="combine-data"></a>Kombinera data
Våra data om olika delstater är intressanta och kommer vara användbara för att skapa mer analysverktyg och -frågor. Men det finns ett problem: de flesta data använder en tvåbokstavsförkortning för delstatskoder, inte det fullständiga namnet på delstaten. Vi behöver hitta ett sätt att associera delstatsnamn med deras förkortningar.

Vi har tur: det finns en annan offentlig datakälla som gör just detta, men den måste formas en hel del innan vi kan ansluta den till vår pensionstabell. Här är webbresursen för delstatsförkortningar:

<http://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations>

Från menyfliksområdet **Start** i frågeredigeraren vi väljer **ny källa \> Webb** och anger adressen. Välj OK och så visar Navigator vad den fann på den webbplatsen.

 ![](media/desktop-shape-and-combine-data/designer_gsg_usstateabbreviationsnavigator.png)

Vi väljer **Tabell [redigera]** eftersom den innehåller användbar data men det kommer att krävas en hel del formning innan vi kan reducera tabellens data till det vi behöver.

> [!TIP]
> Finns det något snabbare eller enklare sätt att utföra stegen nedan? Ja, kan vi skapa en *relation* mellan två tabeller och forma data baserat på relationen. Följande steg är fortfarande bra om du vill bli bättre på att arbeta med tabeller, men det är bra att veta att relationer är ett snabbt sätt att använda data från flera tabeller.
> 
> 

Vi gör följande för att ordna våra data:

* Ta bort de två översta raderna – de är ett resultat av sättet webbsidans tabell skapades och vi behöver dem inte. Välj **minska rader \> Ta bort rader \> Ta bort översta rader** från menyfliksområdet **Start**.

![](media/desktop-shape-and-combine-data/shapecombine_removetoprows.png)

Fönstret **Ta bort översta rader**, där du kan ange hur många rader som du vill ta bort.

* Ta bort de nedersta 26 raderna – de är territorier som vi inte behöver inkludera. Välj **minska rader \> Ta bort rader \> Ta bort nedersta rader** från menyfliksområdet **Start**.

![](media/desktop-shape-and-combine-data/shapecombine_removebottomrows.png)

* Eftersom tabellen Pensioneringsstatistik saknar information för Washington DC kan behöver vi filtrera det från listan. Välj listrutepilen bredvid kolumnen Regionstatus och avmarkera sedan kryssrutan bredvid **Federalt distrikt**.

![](media/desktop-shape-and-combine-data/shapecombine_filterdc.png)

* Ta bort onödiga kolumner – vi behöver bara mappningen av delstaten som dess officiella två bokstäver, så vi kan ta bort följande kolumner: **Kolumn2**, **Kolumn3** och sedan **Kolumn5**  till och med **Kolumn10**. Markera kolumn2 och håll ned tangenten **CTRL** och markera kolumnerna som ska tas bort (kolumnerna behöver inte vara intilliggande). Välj **Ta bort kolumner \> Ta bort kolumner** från fliken Start i menyfliksområdet.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumns.png)

* Använd den första raden som rubriker – eftersom vi har tagit bort de tre översta raderna är aktuella översta raden vår önskade rubrik. Du kan välja **Använd första raden som rubriker** från fliken **Start** eller från fliken **Transformera** i menyfliksområdet.

![](media/desktop-shape-and-combine-data/shapecombine_usefirstrowasheaders.png)

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

I det här fallet vill vi slå samman frågor. För att komma igång väljer du frågan i frågeredigeraren *där du vill* att den andra frågan ska sammanfogas, i det här fallet *Pensionsstatistik*. Välj sedan **Kombinera \> Sammanfoga frågor** från fliken **Start** på menyfliksområdet.

![](media/desktop-shape-and-combine-data/shapecombine_mergequeries.png)

Du kan uppmanas att ange sekretessnivåer för att säkerställa att data kombineras utan att inkludera eller överföra data som du inte ville överföra.

![](media/desktop-shape-and-combine-data/shapecombine_mergequeriesb.png)

Därefter visas fönstret **Sammanfoga**, där vi kan välja vilken tabell som vi vill sammanfoga i den markerade tabellen och sedan klicka på de matchande kolumnerna som ska användas för sammanfogningen. Välj Delstat från tabellen *Pensionsstatistik* (fråga). Välj sedan frågan *Delstatskoder* (enkelt i det här fallet eftersom det är enbart en annan fråga – när du ansluter till flera datakällor finns det många frågor att välja mellan). När vi väljer rätt matchande kolumner – **Delstat** från *Pensionsstatistik*, och **Delstatsnamn** från *Delstatskoder* – ser fönstret **Sammanfoga** ut ungefär så här, och knappen **OK** är aktiverad.

![](media/desktop-shape-and-combine-data/shapecombine_merge.png)

En **NewColumn** skapas i slutet av frågan, vilket är innehållet för tabellen (frågan) som har sammanfogats med den befintliga frågan. Alla kolumner från den sammanfogade frågan ryms i **NyKolumn**, men du kan välja att **Expandera** tabellen inkludera alla kolumner du vill.

![](media/desktop-shape-and-combine-data/shapecombine_mergenewcolumn.png)

Om du vill utöka den sammanfogade tabellen och välja vilka kolumner som ska ingå, väljer du ikonen (![Expandera](media/desktop-shape-and-combine-data/icon.png)). Fönstret **Expandera** visas.

![](media/desktop-shape-and-combine-data/shapecombine_mergeexpand.png)

I det här fallet är vi bara intresserade av kolumnen **Delstatskod** så vi väljer bara den kolumnen och sedan **OK**. Vi avmarkerar kryssrutan från Använd det ursprungliga kolumnnamnet som prefix eftersom vi inte behöver eller vill använda den. Om vi lämnar som den markerad kommer den sammanfogade kolumnen heta **NyKolumn.State kod** (det ursprungliga kolumnnamnet eller **NyKolumn**, sedan en punkt och sedan namnet på kolumnen som användes i frågan).

>[!NOTE]
>Vill du experimentera med hur du hanterar **NyKolumn**-tabellen? Du kan prova dig fram och om du inte gillar resultatet är det bara att ta bort steget från listan **Tillämpade steg** i fönstret **Frågeinställningar**. Din fråga återgår till tillståndet innan du tillämpade steget **Expandera**. Det är som en gratis uppfräschning, som du kan upprepa hur många gånger som helst tills du är nöjd med expanderingsprocessen.

Nu har vi en enskild fråga (tabellen) som kombinerar två datakällor som har formats efter våra behov. Den här frågan kan fungera som bas för många intressanta dataanslutningar – till exempel statistik över bostadskostnader, demografi eller jobbmöjligheter i varje delstat.

Om du vill tillämpa ändringarna och stänga frågeredigeraren väljer du Stäng och tillämpa från menyfliksområdet **Start**. Den omvandlade datauppsättningen visas i Power BI Desktop och är redo för användning när du skapar rapporter.

![](media/desktop-shape-and-combine-data/shapecombine_closeandapply.png)

## <a name="next-steps"></a>Nästa steg
Det finns olika typer av saker som du kan göra med Power BI Desktop. Läs följande resurser för mer information om dess möjligheter:

* [Komma igång med Power BI Desktop](desktop-getting-started.md)
* [Frågeöversikt med Power BI Desktop](desktop-query-overview.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Anslut till data i Power BI Desktop](desktop-connect-to-data.md)
* [Vanliga frågeuppgifter i Power BI Desktop](desktop-common-query-tasks.md)   

