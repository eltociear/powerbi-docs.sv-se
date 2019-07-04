---
title: 'Exempel på personalfrågor: Ta en rundtur'
description: 'Exempel på personalfrågor för Power BI: Ta en rundtur'
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/20/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: ae2e4dcfe1fdcd88c3e6ff9e4942afdedf9d126b
ms.sourcegitcommit: a2c4f912af1729fdfdf20369bf3eff67c3927eec
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67349510"
---
# <a name="human-resources-sample-for-power-bi-take-a-tour"></a>Exempel på personalfrågor för Power BI: Ta en rundtur

## <a name="overview-of-the-human-resources-sample"></a>Översikt över Personalfrågeexemplet
Innehållspaketet med personalfrågeexempel innehåller en instrumentpanel, en rapport och en datamängd för en personalavdelning. I det här exemplet har personalavdelningen samma rapporteringsmodell för olika företag, även om de skiljer sig åt vad gäller bransch eller storlek. Det här exemplet granskar nya anställningar, nuvarande personal (aktiva anställda) och tidigare anställda som har lämnat företaget. Målet är att identifiera eventuella trender i anställningsstrategin. Vårt huvudmål är att förstå:

* Vem vi anställer
* Eventuella fördomar i vår anställningsstrategi
* Trender i frivilliga avgångar

![Instrumentpanel för personalfrågeexemplet](media/sample-human-resources/hr1.png)

Det här exemplet ingår i en serie som visar hur du kan använda Power BI med verksamhetsorienterade data, rapporter och instrumentpaneler. Det har skapats med verkliga data från [obviEnce](http://www.obvience.com/), som har anonymiserats. Aktuella data är tillgängliga i flera format: innehållsförpackning/-app, .pbix-fil för Power BI Desktop eller Excel-arbetsbok. Se [Exempel för Power BI](sample-datasets.md). 

De här självstudierna använder Power BI-tjänsten och innehållspaketet med personalfrågeexempel. Eftersom rapportupplevelserna är så lika kan du även följa med via Power BI Desktop och .pbix-exempelfilen. 

## <a name="prerequisites"></a>Förutsättningar

Innan du kan använda exemplet, måste du först hämta det som ett [innehållspaket](#get-the-content-pack-for-this-sample), en [.pbix-fil](#get-the-pbix-file-for-this-sample) eller en [Excel-arbetsbok](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Hämta innehållspaketet för det här exemplet

1. Öppna Power BI-tjänsten (app.powerbi.com), logga in och öppna den arbetsyta där du vill spara exemplet.

2. Längst ned i vänster hörn väljer du **Hämta data**.
   
   ![Välja Hämta data](media/sample-datasets/power-bi-get-data.png)
3. På sidan **Hämta data** väljer du **Exempel**.
   
4. Välj **Personalfrågeexempel** och sedan **Anslut**.  
   
   ![Ansluta till exempel](media/sample-human-resources/pbi_hr_sample_connect.png)

5. Power BI importerar innehållspaketet och lägger sedan till en ny instrumentpanel, rapport och datamängd till din aktuella arbetsyta.
   
   ![Inmatning av personalfrågeexempel](media/sample-human-resources/hr-sample-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Hämta .pbix-filen för det här exemplet

Du kan även ladda ned personalfrågeexemplet som en [.pbix-fil](http://download.microsoft.com/download/6/9/5/69503155-05A5-483E-829A-F7B5F3DD5D27/Human%20Resources%20Sample%20PBIX.pbix) som är avsedd för användning med Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Hämta Excel-arbetsboken för det här exemplet

Om du vill visa i datakällan för det här exemplet är det även tillgängligt som en [Excel-arbetsbok](http://go.microsoft.com/fwlink/?LinkId=529780). Arbetsboken innehåller Power View-blad som du kan visa och ändra. Om du vill se rådata aktiverar du dataanalystilläggen och väljer **Power Pivot > Hantera**. Aktivering av tilläggen för Power View och Power Pivot beskrivs i avsnittet om att [titta på Excel-exemplen inuti själva Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself).

## <a name="new-hires"></a>Nyanställda
Låt oss utforska nyanställda först.

1. På arbetsytan väljer du fliken **Instrumentpaneler** och öppnar instrumentpanelen **Personalfrågeexempel**.
2. På instrumentpanelen väljer du panelen för **Antal nyanställda, nyanställda samma period förra året, förändring för nuvarande personal år för år i % efter månad**.  

   ![Panelen Antal nyanställda](media/sample-human-resources/hr2.png)  

   Exempelrapporten för personal öppnas på sidan **Nyanställda**.  

   ![Sidan Nyanställda](media/sample-human-resources/hr3.png)

3. Titta närmare på dessa intressanta punkter:

    * Kombinationsdiagrammet för **Antal nyanställda, Nyanställda samma period förra året och Förändring för nuvarande personal år för år i % efter månad** visar att vi har anställt fler personer varje månad i år, jämfört med föregående år. Betydligt fler personer under vissa månader.
    * I kombinationsdiagrammet **Antal nyanställa och aktivt antal medarbetare per region och etnicitet** kan man notera att vi anställde färre personer i regionen **Öst**.
    * Vattenfallsdiagrammet **Varians av nyanställda på årsbasis per åldersgrupp** att vi i huvudsak anställer yngre personer. De här trenden kan bero på att tjänsterna i huvudsak är på deltid.
    * Cirkeldiagrammet **Antal nyanställda enligt kön** visar en ganska jämn fördelning.

    Hittar du fler insikter? Till exempel en region där könsfördelningen är ojämn? 

4. Välj olika ålder grupper och könen i diagram och utforska relationerna mellan ålder, kön, region och etnisk grupp.

5. Välj **Personalfrågeexempel** i det övre navigeringsfältet för att återgå till instrumentpanelen.

   ![Återgå till instrumentpanelen](media/sample-human-resources/power-bi-breadcrumbs.png)

## <a name="compare-currently-active-and-former-employees"></a>Jämföra nuvarande aktiva anställda och tidigare anställda
Låt oss utforska data för aktiva anställda och tidigare anställda som inte längre arbetar på företaget.

1. På instrumentpanelen väljer du panelen **Antal aktiva medarbetare per åldersgrupp**.

   ![Panelen Antal aktiva anställda per åldersgrupp](media/sample-human-resources/pbi_hr_sample_activepie.png)

   Exempelrapporten för personal öppnas på sidan **Aktiva anställda jämfört med. Uppsägningar**.  

   ![Aktiva anställda jämfört med Sidan Uppsägningar](media/sample-human-resources/hr5.png)

 2. Titta närmare på dessa intressanta punkter:

    * De två kombinationsdiagrammen till vänster visar förändringar år för år för aktiva anställda och uppsägningar. Vi har mer aktiva anställda i år på grund av att vi har anställt många på kort tid, men även fler uppsägningar än förra året.
    * I augusti hade vi fler uppsägningar än andra månader. Välj olika åldersgrupper, kön eller regioner för att se om du hittar några avvikare.
    * Om vi tittar på cirkeldiagrammen ser vi en tydlig köns- och åldersfördelning bland våra aktiva anställda. Välj olika åldersgrupper om du vill se hur könsfördelningen ändras i olika åldersgrupper. Har vi en ojämn könsfördelning i alla åldersgrupper?

## <a name="reasons-for-separation"></a>Orsaker till fördelning
Öppna rapporten i Redigeringsvyn. Du kan ändra cirkeldiagrammen för att visa data för personaluppsägningar istället för aktiva anställda.

1. Välj **Redigera rapporten** i det övre vänstra hörnet.

2. Välj cirkeldiagrammet **Antal aktiva medarbetare per åldersgrupp**.

3. För **Fält** markerar du **Anställda** för att expandera tabellen **Anställda**. Avmarkera **Antal aktiva anställda** för att ta bort fältet.

4. Välj **Antal uppsägningar** i tabellen **Anställda** för att lägga till det i rutan **Värden** i området **Fält**.

5. På rapportarbetsytan väljer du stapeln **Frivilligt** i stapeldiagrammet **Antal uppsägningar efter uppsägningsorsak**. 

   Den här stapeln markerar de anställda som lämnade företaget frivilligt i de övriga visuella objekten i rapporten.

6. Väj sektorn 50+ i cirkeldiagrammet **Antal uppsägningar per åldersgrupp**.

7. Titta på linjediagrammet i det nedre högra hörnet. Diagrammet är filtrerat för att visa frivilliga uppsägningar.  

   ![Uppsägning av medarbetare över 50](media/sample-human-resources/pbi_hr_sample_sepsover50.png)

   Ser du trenden i åldersgruppen 50+? Under den senare delen av året lämnar fler medarbetare över 50 frivilligt. Den här trenden behöver närmare efterforskning med mer data.

8. Du kan också följa samma steg för cirkeldiagrammet **Antal aktiva anställda efter kön** och ändra den till uppsägningar istället för nuvarande personal. Titta på data för frivillig uppsägning efter kön för att se om du kan hitta andra insikter.

9. Välj **Personalfrågeexempel** i det övre navigeringsfältet för att återgå till instrumentpanelen. Du kan välja att spara de ändringar som du har gjort i rapporten.

## <a name="bad-hires"></a>Dåliga anställningar
Det senaste området att utforska är dåliga anställningar. Dåliga anställningar definieras som medarbetare som inte stannade längre än 60 dagar. Vi anställer i hög takt, men anställer vi bra kandidater?

1. Välj instrumentpanelen **Dåliga anställningar som % av aktiva efter åldersgrupp**. Rapporten öppnas på flik tre, **Dåliga anställningar**.

   ![Panelen Dåliga anställningar som % av aktiva anställda efter åldersgrupp](media/sample-human-resources/hr7.png)  
2. Välj **Nordväst** i utsnittet **Region** till vänster och välj **Män** i ringdiagrammet **Antal dåliga anställningar efter kön**. Titta på de andra diagrammen på sidan **Dåliga anställningar**. Notera att det finns fler dåliga anställningar av män än kvinnor och många dåliga anställningar i grupp A.

   ![Dåliga anställningar i nordväst](media/sample-human-resources/pbi_hr_sample_badhirespage.png)  

3. Om du tittar på ringdiagrammet **Antal dåliga anställningar efter kön** och väljer olika regioner i utsnittet **Region**, ser du att den östra regionen är den enda regionen med fler kvinnliga än manliga dåliga anställningar.  

4. Välj namnet på instrumentpanelen från det övre navigeringsfältet för att återgå till instrumentpanelen.

## <a name="ask-a-question-in-the-dashboard-qa-box"></a>Ställa en fråga i instrumentpanelens frågeruta Frågor och svar
I [frågerutan Frågor och svar](power-bi-tutorial-q-and-a.md) på instrumentpanelen kan du ställa en fråga om dina data med hjälp av naturligt språk. Frågor och svar kan identifiera de ord du skriver och var svaret finns i din databas.

1. Klicka på rutan frågor och svar. Notera att Frågor och svar visar förslag för att hjälpa dig formulera din fråga, redan innan du ens börjar skriva.

   ![Förslag för rutan Frågor och svar](media/sample-human-resources/pbi_hr_sample_qabox.png)

2. Du kan välja något av dessa förslag eller skriva: *visa åldersgrupp, kön och dåliga anställningar samma period förra året där regionen är öst*.  

   ![Svar för rutan Frågor och svar](media/sample-human-resources/pbi_hr_sample_qa_answer.png)

   Lägg märke till att majoriteten av dåliga kvinnliga anställningar är under 30.

Den här miljön är säker att leka i eftersom du kan välja att inte spara dina ändringar. Men om du sparar dem kan du alltid välja **Hämta data** för att få en ny kopia av exemplet.

## <a name="next-steps-connect-to-your-data"></a>Nästa steg: Anslut till dina data
Vi hoppas att denna rundtur har visat hur Power BI-instrumentpaneler, frågor och svar, samt rapporter kan ge insikter om personalfrågor. Nu är det din tur – anslut till dina egna data. Med Power BI kan du ansluta till en mängd olika datakällor. Läs mer i [Kom igång med Power BI-tjänsten](service-get-started.md).
