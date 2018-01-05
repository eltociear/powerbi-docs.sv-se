---
title: "Självstudier: Facebook-analyser med hjälp av Power BI Desktop"
description: "Självstudier: Facebook-analyser med hjälp av Power BI Desktop"
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 3642a252467d504b61eb81f82d0b96f64a24f22b
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="tutorial-facebook-analytics-using-power-bi-desktop"></a>Självstudier: Facebook-analyser med hjälp av Power BI Desktop
I den här kursen får du lära dig hur du importerar och visualiserar data från **Facebook**. Under kursen lär du dig att ansluta till en viss Facebook-sida (Power BI-sida), använd datatransformationssteg och skapa vissa visuella objekt.

Du kommer att få göra följande:

* **Aktivitet 1:** Ansluta till Facebook-sida
* **Aktivitet 2**: Skapa visualiseringar med rapportvyn
  
  * **Steg 1:** Skapa en trädkartsvisualisering
* **Aktivitet 3:** Utforma data i frågevyn
  
  * **Steg 1**: Dela datum-tid-kolumnen i två
  * **Steg 2**: Lägga till ett samlat värde från en relaterad tabell
* **Aktivitet 4**: Skapa fler visualiseringar med rapportvyn
  
  * **Steg 1:** Läsa in frågan i din rapport
  * **Steg 2**: Skapa ett linjediagram och ett stapeldiagram

## <a name="task-1-connect-to-a-facebook-page"></a>**Aktivitet 1: Ansluta till Facebook-sida**
I den här uppgiften får du importera data från platsen [Microsoft Power BI Facebook](https://www.facebook.com/microsoftbi) (här är webbadressen: *https://www.facebook.com/microsoftbi)*.

Vem som helst kan ansluta till sidan och följa de här stegen - inga särskilda autentiseringsuppgifter (andra än ditt eget Facebook-konto som du använder i det här steget) krävs.

![](media/desktop-tutorial-facebook-analytics/1.png)

1. I dialogrutan **Komma igång** eller på menyfliksområdet **Start** väljer du **Hämta data.**
2. Dialogrutan **Hämta data** visas så att du kan välja från alla typer av datakällor. Välj **Facebook** från gruppen **Andra**.
   
   ![](media/desktop-tutorial-facebook-analytics/t_fb_getdataother.png)
   
   När du väljer **Anslut**, visas en dialogruta för att varna dig om riskerna med att använda en tjänst från tredje part.
   
   ![](media/desktop-tutorial-facebook-analytics/t_fb_connectingtotps.png)
3. När du väljer Fortsätt visas **Facebook**-dialogrutan där du kan klistra in sidonamnet (**microsoftbi**) i textrutan **Användarnamn**. Välj **Inlägg** från listrutan **Anslutning**.
   
   ![](media/desktop-tutorial-facebook-analytics/2.png)
4. Klicka på **OK**.
5. När du tillfrågas om autentiseringsuppgifter, logga in med Facebook-konto och ge Power BI åtkomst till ditt konto.
   
   ![](media/desktop-tutorial-facebook-analytics/facebookcredentials.png)

När du har anslutits till sidan ser du data som läses in i modellen. 

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loadpreview.png)

Därifrån visar **Frågeredigeraren** dina data. **Frågeredigeraren** är en del av Power BI Desktop men startar i ett separat fönster där du genomför alla transformationer på dina dataanslutningar.

![](media/desktop-tutorial-facebook-analytics/t_fb_1-intoqueryeditor.png)

När du är nöjd med dina data kan du överföra dem till Power BI Desktop. Välj **Läs in och stäng** från menyfliksområdet **Start**.

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)

Du ser en dialogruta som visar förloppet för att läsa in data i Power BI Desktop-datamodellen.

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loading.png)

När dina data har överförts, vidarebefordras du till **Rapportvyn** där kolumner från tabellen listas i listan **Fält** till höger.

![](media/desktop-tutorial-facebook-analytics/fbdesigner1.png)

## <a name="task-2-create-visualizations-using-the-report-view"></a>**Aktivitet 2: Skapa visualiseringar med rapportvyn**
Nu när du har överfört data från sidan kan du snabbt och få enkelt insikter om dina data med visuella objekt.

**Steg 1:** Skapa en trädkartsvisualisering

Det är enkelt att skapa en visualisering, vi bara drar ett fält från **fältlistan** och släpp det på **rapportarbetsytan.**

Dra fältet **Typ** till arbetsytan **Rapport**. Power BI Desktop skapar ett nytt visuellt objekt på **rapportarbetsytan**. Dra därefter **typ** från **Fält** (samma fält som du precis har dragit till **rapport**arbetsytan) till området **Värde** för att skapa ett  **Stapeldiagram**.

![](media/desktop-tutorial-facebook-analytics/fbdesigner2.png)

Vi kan enkelt ändra visualiseringstyp genom att klicka på en annan ikon i fönstret **Visualisering**. Nu ska vi ändra typen till en **Trädkarta** genom att välja ikonen från **Visualiseringar**, enligt följande bild.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3.png)

Nu ska vi lägga till en förklaring och sedan ändra färgen på en datapunkt. Välj ikonen **Format** i fönstret **Visualiseringar**. **Format**-ikonen som ser ut som ett penselverktyg.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3a.png)

När du väljer nedåtpilen bredvid **Förklaring** expanderas området och visar hur du anpassar förklaringen för den valda visualiseringen. I detta fall har vi gjort följande val:

* flyttat skjutreglaget **Förklaring** till **På** så visas en förklaring
* valt **höger** från listrutan **LegendPosition**
* flyttat skjutreglaget **rubrik** till **På**, så att en rubrik för förklaringen visas
* skrivit i **typ** för rubriken för förklaringen

I följande bild, är dessa inställningar redan utförda och visas i visualiseringen.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3b.png)

Nu ska vi ändra färg på en av datapunkterna. Datapunkten med en länk bör vara blå, så att den liknar standardfärger för hyperlänkar.

Välj pilen bredvid **Datafärger** för att expandera avsnittet. Datapunkter visas med markeringspilarna bredvid varje färg som gör att vi kan välja en annan färg för varje datapunkt.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3c.png)

När du klickar på nedåtpilen för färgrutan bredvid varje datapunkt visas färgvalsdialogrutan för låta dig välja din färg. I så fall väljer du ljusblått.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3d.png)

Det är bättre. I följande bild, kan du se hur färgen används på datapunkten i visualiseringen och att förklaringen uppdateras automatiskt, liksom dess färg i området **Datafärger**.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3e.png)

## <a name="task-3-shape-data-in-the-table"></a>**Aktivitet 3: Utforma data i tabellen**
Nu när du har importerat den valda tabellen och du börja visualisera den märker du kanske behöver du utföra olika dataformnings- och rensningssteg för att få ut mesta möjliga av dina data.

**Steg 1**: Dela datum-tid-kolumnen i två

I det här steget kan du dela upp den **skapade\_tid** kolumnen för att hämta värden för både datum och tid. När du arbetar i Power BI Desktop och du vill ändra en befintlig fråga måste du starta **frågeredigeraren**. För att göra det väljer du **redigera frågor** från fliken **Start**.

![](media/desktop-tutorial-facebook-analytics/t_fb_editquery.png)

1. I rutnätet i **frågeredigeraren** rullar du åt höger tills du hittar kolumnen **skapad\_tid**
2. Högerklicka på en kolumnrubrik i rutnätet i **Förhandsvisning av frågan** och klicka på **Dela kolumn \> med avgränsare** för att dela kolumnerna. Välj **Anpassad** i listrutan för avgränsare och ange **”T”** Observera att åtgärden också är tillgänglig i menyfliksområdet **Start** i gruppen **Hantera** kolumner.
   
   ![](media/desktop-tutorial-facebook-analytics/9.png)
   
   ![](media/desktop-tutorial-facebook-analytics/10.png)
3. Byt namn på kolumnerna som har skapats till **skapad\_datum** och **skapad\_tid**.
4. Välj den nya kolumnen, **skapad\_tid**, *** och i bandet **Frågevy** navigerar du till fliken **Lägg till kolumn** och markerar **Tid\>Timme** under gruppen **från datum och tid**. Detta lägger till en ny kolumn som isolerar värdet för timme för tiden.
   
   ![](media/desktop-tutorial-facebook-analytics/11.png)
5. Ändra typen för den nya kolumnen **Timme** till **Heltal** genom att navigera till fliken **Start** och markera listrutan **Datatyp** eller genom att högerklicka på kolumnen och välja **Transformera\>Heltal**.
   
   ![](media/desktop-tutorial-facebook-analytics/12.png)

**Steg 2**: Lägga till ett samlat värde från en relaterad tabell

I det här steget kan du lägga till antalet resurser från det kapslade värdet så att du kan använda det i visualiseringar.

1. Fortsätta bläddra till höger tills du ser kolumnen **resurser**. Det kapslade värdet indikerar att vi måste transformera om för att få de faktiska värdena.
2. Längst upp till höger på kolumnrubriken väljer du ikonen ![](media/desktop-tutorial-facebook-analytics/14.png) för att öppna verktyget **Expandera/aggregering**. Välj **antal** och därefter **OK**. Detta lägger till antalet resurser för varje rad i vår tabell.
   
   ![](media/desktop-tutorial-facebook-analytics/15.png)
   
   När data har lästs in, byter du namn på kolumnen till **resurser** genom att dubbelklicka på kolumnnamnet. Högerklicka på kolumnen eller i menyfliksområdet **Frågevy** och välj **Byt namn** under fliken **Transformera** och gruppen **Valfri kolumn**.
3. Slutligen ändra typen av den nya kolumnen **resurser** till **Heltal**. När kolumnen har markerats kan typen ändras genom att högerklicka på kolumnen och välja **Transformera\>Heltal** eller **** genom att navigera till **Start**-fliken och välja rullgardinsmenyn **Datatyp** eller.

### <a name="query-steps-created"></a>Frågesteg som skapats
När du utför omvandlingar i frågevyn skapas och visas frågesteg i rutan **frågeinställningar** i listan **TILLÄMPADE STEG**. Varje frågesteg har en motsvarande frågeformel, även kallat ”M”-språk.

![](media/desktop-tutorial-facebook-analytics/16.png)

| Aktivitet | Frågesteg | Formel |
| --- | --- | --- |
| Ansluta till Facebook-sida |Källa |Facebook.Graph (&quot;https://graph.facebook.com/microsoftbi/posts&quot;) |
| **Dela kolumner** för att hämta de värden som du behöver |Dela upp kolumn efter avgränsare |Table.SplitColumn  (Source,&quot;created_time&quot;,Splitter.SplitTextByDelimiter(&quot;T&quot;),{&quot;created_time.1&quot;, &quot;created_time.2&quot;}) |
| **Ändra typ** med nya kolumner (automatiskt steg) |Ändrade typ |Table.TransformColumnTypes  (#&quot;Delat kolumn enligt avgränsare&quot;,{{&quot;created_time.1&quot;, type date}, {&quot;created_time.2&quot;, type time}}) |
| **Byt namn **på en kolumn**** |Kolumner med nytt namn |Table.RenameColumns  (#&quot;Changed Type&quot;,{{&quot;created_time.1&quot;, &quot;created_date&quot;}, {&quot;created_time.2&quot;, &quot;created_time&quot;}}) |
| **Infoga **en kolumn**** |Infogad timme |Table.AddColumn  (#&quot;Renamed Columns&quot;, &quot;Hour&quot;, each Time.Hour([created_time]), type number) |
| **Ändra typ ** |Ändrad typ1 |Table.TransformColumnTypes  (#&quot;Inserted Hour&quot;,{{&quot;Hour&quot;, type text}}) |
| ** Expandera ** värden i en kapslad tabell **** |Expandera resurser |Table.ExpandRecordColumn  (#&quot;Changed Type1&quot;, &quot;shares&quot;, {&quot;count&quot;}, {&quot;shares.count&quot;}) |
| ** Byt namn på ** kolumnen**** |Kolumner med nytt namn1 |Table.RenameColumns  (#&quot; Expand shares&quot;,{{&quot;shares.count&quot;, &quot;shares&quot;}}) |
| **Ändra typ** |Ändrad typ2 |Table.TransformColumnTypes  (#&quot;Renamed Columns1&quot;,{{&quot;shares&quot;, Int64.Type}}) |

## <a name="task-4-create-additional-visualizations-using-the-report-view"></a>**Aktivitet 4: Skapa fler visualiseringar med rapportvyn**
Nu när vi har konverterat datan till det format vi behöver för analysen, kan vi läsa in resulterande tabell i rapporten och skapa fler visualiseringar.

**Steg 1:** Läsa in frågan i rapporten

För att läsa in resultatet av frågan i rapporten måste vi välja **Läs in och stäng** från **frågeredigeraren**. Då läser vi in våra ändringar i Power BI Desktop och stänger **frågeredigeraren**.

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)

I Power BI Desktop vi måste vara i **rapport**vyn. Välj den översta ikonen från det vänstra fältet i Power BI Desktop.

![](media/desktop-tutorial-facebook-analytics/17.png)

**Steg 2**: Skapa ett linjediagram och ett stapeldiagram

För att kunna skapa en visualisering kan vi dra fält från **Fältlista** och släppa dem på **rapportarbetsytan**.

1. Dra fältet **resurser** till **rapportarbetsytan**, vilket skapar ett stapeldiagram. Dra sedan det skapade\_datumet till diagrammet så skapar Power BI Desktop det visuella objektet till ett **Linjediagram**.
   
   ![](media/desktop-tutorial-facebook-analytics/19.png)
2. Dra sedan fältet **Resurser** till **rapportarbetsytan**. Dra fältet **Timme** till området **Axel** under **fältlistan**.
   
   ![](media/desktop-tutorial-facebook-analytics/20.png)
3. Vi kan enkelt ändra visualiseringstyp genom att klicka på en annan ikon i fönstret **Visualisering**. Pilen i nedanstående bild pekar på ikonen **Stapeldiagram**.
   
   ![](media/desktop-tutorial-facebook-analytics/21.png)
4. Ändra visualiseringstypen till **Stapeldiagram**.
5. **Stapeldiagrammet** har skapats, men axeln är på fel plats – vi vill att den ska sorteras åt andra hållet (från högt till lågt). Välj pilen bredvid **Y-axel** för att expandera avsnittet. Du behöver ändra axeltypen **Kontinuerlig** som **Kategoriskt** så vi sorterar den som vi vill (nedanstående bild visar axeln innan vi markerar – ta en titt på nästa bild för att se hur den ska se ut).

![](media/desktop-tutorial-facebook-analytics/22.png)

Det är bättre. Och nu har vi tre visualiseringar den här sidan. Vi kan ändra sidan på dem efter hand som vi fyller på rapportsidan.

![](media/desktop-tutorial-facebook-analytics/23.png)

Som du kan se är det enkelt att anpassa visualiseringar i rapporten, för att kunna visa datan så som du vill. I Power BI Desktop är det enkelt att hämta data från en stor mängd datakällor och utforma dem efter dina analysbehov för att visualisera datan på interaktiva sätt. När rapporten är klar kan du [ladda upp den på Power BI](desktop-upload-desktop-files.md) och skapa instrumentpanelen som baseras på den, och sedan dela den med andra Power BI-användare.

Du kan hämta slutresultatet av den här kursen [här](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/FacebookAnalytics.pbix)

### <a name="where-else-can-i-get-more-information"></a>Var kan jag få mer information?
* [Läs andra Power BI Desktop-självstudier](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Se Power BI Desktop-videor](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Besök Power BI-forumet](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Läs Power BI-bloggen](http://go.microsoft.com/fwlink/?LinkID=519327)



