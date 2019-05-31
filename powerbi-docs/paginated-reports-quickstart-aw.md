---
title: 'Självstudie: Skapa en sidnumrerad rapport och ladda upp den till Power BI-tjänsten (förhandsversion)'
description: I den här självstudien ansluter du till en Azure SQL-exempeldatabas. Sedan använder du en guide i Report Builder för att skapa en sidnumrerad rapport. Sedan överför du den sidnumrerade rapporten till en arbetsyta i en Premium-kapacitet i Power BI-tjänsten.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: tutorial
ms.date: 11/06/2018
ms.openlocfilehash: e7baff9a6427578266e08e7bde91be664e46edb9
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "60990114"
---
# <a name="tutorial-create-a-paginated-report-and-upload-it-to-the-power-bi-service-preview"></a>Självstudie: Skapa en sidnumrerad rapport och ladda upp den till Power BI-tjänsten (förhandsversion)

I den här självstudien ansluter du till en Azure SQL-exempeldatabas. Sedan använder du en guide i Power BI Report Builder för att skapa en sidnumrerad rapport med en tabell som radbryts till flera sidor. Sedan överför du den sidnumrerade rapporten till en arbetsyta i en Premium-kapacitet i Power BI-tjänsten. Sidnumrerade rapporter i Power BI-tjänsten är för närvarande i förhandsversion.

![Sidnumrerad rapport i Power BI-tjänsten](media/paginated-reports-quickstart-aw/power-bi-paginated-report-service.png)

Här är de steg som du har slutfört i den här självstudien:

> [!div class="checklist"]
> * Skapa en Azure-exempeldatabas.
> * Skapa en matris i Power BI Report Builder med hjälp av en guide.
> * Formatera rapporten med rubrik, sidnummer och kolumnrubriker på varje sida.
> * Formatera valutan.
> * Ladda upp rapporten till Power BI-tjänsten.

Om du inte har någon Azure-prenumeration kan du [skapa ett kostnadsfritt konto](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) innan du börjar.
 
## <a name="prerequisites"></a>Förutsättningar  

Här följer förutsättningarna för att skapa den sidnumrerade rapporten:

- Installera [Power BI Report Builder från Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=2086513). 

- Följ snabbstarten [Skapa ett Azure SQL-exempeldatabas i Azure Portal](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal). Kopiera och spara värdet i rutan **Servernamn** på fliken **Översikt**. Kom ihåg det användarnamn och det lösenord som du skapade i Azure.

Här är förutsättningarna för att ladda upp din sidnumrerade rapport till Power BI-tjänsten:

- Du måste ha en [Power BI Pro-licens](service-admin-power-bi-pro-in-your-organization.md).
- Du måste ha en apparbetsyta i tjänsten i en [Power BI Premium-kapacitet](service-premium-what-is.md). Den visas med en diamantikon ![Premium-diamantikon](media/paginated-reports-quickstart-aw/premium-diamond.png) bredvid arbetsytans namn.

## <a name="create-the-matrix-with-a-wizard"></a>Skapa matrisen med en guide
  
1.  Starta Power BI Report Builder från datorn.  
  
     Dialogrutan **Komma igång** öppnas.  
  
     ![Komma igång med Report Builder](media/paginated-reports-create-embedded-dataset/power-bi-paginated-get-started.png)
  
1.  Kontrollera att **Ny rapport** har markerats i den vänstra rutan och välj **Tabell- eller matrisguide** i den högra rutan.  
  
4.  Välj **Skapa en datauppsättning** > **Nästa** på sidan **Välj en datauppsättning**.  

    ![Skapa en datauppsättning](media/paginated-reports-quickstart-aw/power-bi-paginated-create-dataset.png)
  
5.  Välj **Ny** på sidan **Välj en anslutning till en datakälla**. 

    ![Ny datakälla](media/paginated-reports-quickstart-aw/power-bi-paginated-new-data-source-connection.png)
  
     Dialogrutan **Egenskaper för datakälla** öppnas.  
  
6.  Du kan ge en datakälla vilket namn du vill med hjälp av tecken och understreck. Skriv **MyAzureDataSource** i rutan **Namn** i den här självstudiekursen.  
  
7.  Välj **Microsoft Azure SQL Database** i rutan **Välj anslutningstyp**.  
  
8.  Välj **Skapa** intill rutan **Anslutningssträng**. 

    ![Egenskaper för datakälla – Skapa](media/paginated-reports-quickstart-aw/power-bi-paginated-data-source-properties-build.png)

9. **I Azure:** Gå tillbaka till Azure Portal och välj **SQL-databaser**.

1. Välj den Azure SQL-databas som du skapade i snabbstarten ”Skapa en Azure SQL-exempeldatabas i Azure Portal” i avsnittet **Förutsättningar** i den här artikeln.

1. Kopiera värdet i rutan **Servernamn** på fliken **Översikt**.

2. **I Report Builder**: Klistra in det servernamn som du kopierade under **Servernamn** i dialogrutan **Anslutningsegenskaper**. 

1. Kontrollera att **Använd SQL Server-autentisering** har valts för **Logga in på servern** och skriv sedan det användarnamn och det lösenord som du skapade i Azure för exempeldatabasen.

1. Klicka på listrutepilen under **Anslut till en databas** och välj namnet på databasen som du skapade i Azure.
 
    ![Egenskaper för anslutningssträng till datakälla](media/paginated-reports-quickstart-aw/power-bi-paginated-connection-properties.png)

1. Välj **Testanslutning**. **Testresultat**-meddelandet **Testanslutningen lyckades** visas.

1. Välj **OK** > **OK**. 

   Report Builder visar den anslutningssträng som du nyss skapade i rutan **Anslutningssträng**. 

    ![Anslutningssträng för datakälla](media/paginated-reports-quickstart-aw/power-bi-paginated-data-source-properties-connection-string.png)

1. Välj **OK**.
  
9. På sidan **Välj en anslutning till en datakälla** visas ”(i den här rapporten)” under den anslutning till datakälla som du just har skapat. Välj den datakällan > **Nästa**.  

    ![Min Azure-datakälla](media/paginated-reports-quickstart-aw/power-bi-paginated-my-azure-data-source.png)

10. Skriv samma användarnamn och lösenord i rutan. 
  
10. Expandera SalesLT på sidan **Utforma en fråga**, expandera Tabeller och välj följande tabeller:

    - Adress
    - Kund
    - Produkt
    - ProductCategory
    - SalesOrderDetail
    - SalesOrderHeader

     Eftersom du har valt **Relationer** > **Automatisk identifiering** identifierar Report Builder relationer mellan dessa tabeller. 
    
    ![Utforma en fråga](media/paginated-reports-quickstart-aw/power-bi-paginated-design-query.png)
 
1.  Välj **Kör fråga**. Report Builder visar **Frågeresultat**. 
 
     ![Frågeresultat](media/paginated-reports-quickstart-aw/power-bi-paginated-query-results.png)

18. Välj **Nästa**. 

19. Välj den datauppsättning du just har skapat i **Välj en datauppsättning** > **Nästa**.

    ![Välj en datauppsättning](media/paginated-reports-quickstart-aw/power-bi-paginated-choose-dataset.png)

1. Dra dessa fält från rutan **Tillgängliga fält** på sidan **Ordna fält** till rutan **Radgrupper**:

    - CompanyName
    - SalesOrderNumber
    - Product_Name

1. Dra dessa fält från rutan **Tillgängliga fält** till rutan **Värden**:

    - OrderQty
    - UnitPrice
    - LineTotal

    Report Builder görs automatiskt fälten i rutan **Värden** till summor.

    ![Ordna fält](media/paginated-reports-quickstart-aw/power-bi-paginated-drag-fields.png)

24. Behåll alla standardinställningar på sidan **Välj layout**, men avmarkera **Visa/dölj grupper**. Funktionen Visa/dölj grupper är bra, men den här gången vill du att tabellen att sträcka sig över flera sidor.

1. Välj **Nästa** > **Slutför**. Tabellen visas på designytan.
 
## <a name="what-youve-created"></a>Det du har skapat

Låt oss pausa för att titta på guidens resultat.

![Matrisguidens resultat](media/paginated-reports-quickstart-aw/power-bi-paginated-wizard-results.png)

1. Den inbäddade Azure-datakällan och den inbäddade datauppsättningen som baseras på den, vilka du har skapat, visas i fönstret Rapportdata. 

2. Designytan är ungefär 6 tum bred. Matrisen visas på designytan med kolumnrubriker och platshållarvärdena. Matrisen innehåller sex kolumner och verkar bara vara fem rader lång. 

3. Beställningsantal, Enhetspris och Radtotal är alla summor och varje radgrupp har en delsumma. 

    De faktiska datavärdena visas ännu inte. Du måste köra rapporten för att de ska visas.

4. Den valda matrisen kallas Tablix1 i fönstret Egenskaper. En *tablix* i Report Builder är ett dataområde som visar data på rader och i kolumner. Det kan vara en tabell eller en matris.

5. De tre gupper som du skapade i guiden visas i fönstret Gruppering: 

    - CompanyName
    - Försäljningsorder
    - Produktnamn

    Den här matrisen har inte några kolumngrupper.

### <a name="run-the-report"></a>Kör rapporten

Du måste köra rapporten för att kunna se de faktiska värdena.

1. Välj **Kör** i verktygsfältet **Start**.

   Nu visas värdena. Matrisen har många fler rader än de som visas i vyn Design! Observera att i Report Builder anges sidan som **1** av **2?** . Report Builder läser in rapporten så snabbt som möjligt, vilket innebär att den endast hämtar tillräckligt med data för några sidor i taget. Frågetecknet anger att Report Builder inte har lästs in alla data ännu.

   ![Kör rapporten](media/paginated-reports-quickstart-aw/power-bi-paginated-run-report.png)

2. Välj **Utskriftslayout**. Rapporten är i det här formatet när du skriver ut den. Report Builder har nu registrerat att rapporten innehåller 33 sidor och har automatiskt lagt till en datum- och tidsstämpel i sidfoten.

## <a name="format-the-report"></a>Formatera rapporten

Nu har du en rapport med en matris som sträcker sig över 33 sidor. Låt oss lägga till några fler funktioner och förbättra utseendet. Du kan köra rapporten efter varje steg om du vill se hur den artar sig.

- Välj **Design** på filken **Kör** i menyfliksområdet, så att du kan fortsätta att ändra den.  

### <a name="set-page-width"></a>Ange sidbredd

En sidnumrerad rapport förmateras normalt för utskrift och en normal sida är 8 1/2 x 11 tum. 

1. Dra linjalen så att designytan blir 7 tum bred. Standardmarginalerna är 1 tum på varje sida, så båda sidmarginalerna måste vara smalare.

1. Visa **Rapport**-egenskaperna genom att klicka i det grå området runt designytan.

    Om fönstret Egenskaper inte visas klickar du på fliken **Visa** > **Egenskaper**.

2. Expandera **Marginaler** och ändra **Vänster** och **Höger** från 1 tum till 0,75 tum. 

    ![Ställa in sidmarginalerna](media/paginated-reports-quickstart-aw/power-bi-paginated-set-margins.png)
  
### <a name="add-a-report-title"></a>Lägga till en rapportrubrik  

1. Markera orden **Klicka om du vill lägga till rubrik** högst upp på sidan, och skriv sedan **Försäljning efter företag**.  

2. Markera rubriktexten, och ändra **Färg** till **Blå** under **Teckensnitt** i fönstret Egenskaper.
  
### <a name="add-a-page-number"></a>Lägg till ett sidnummer

Du kan se att rapporten innehåller en datum- och tidsstämpel i sidfoten. Du kan även lägga till ett sidnummer i sidfoten.

1. Längst ned på designytan visas [&ExecutionTime] till höger i sidfoten. 

2. Expandera mappen Inbyggda fält i fönstret Rapportdata. Dra **Sidnummer** till vänster sida av sidfoten på samma höjd som [&ExecutionTime].

3. Dra till höger sida av rutan [&PageNumber] rutan så att den blir kvadratisk.

4. Välj **Textruta** på fliken **Infoga**.

5. Klicka till höger om [&PageNumber], skriv ”av” och gör sedan textrutan kvadratisk.

6. Dra **Totalt antal sidor** i sidfoten till höger om ”av”, och dra sedan dess högra sida så att den också blir kvadratisk.

    ![Dra sidnummer](media/paginated-reports-quickstart-aw/power-bi-paginated-add-page-numbers.png)

### <a name="make-the-table-wider"></a>Gör tabellen bredare  

Nu kan du göra matrisen tillräckligt bred för att fylla sidans bredd och göra textkolumnerna bredare så att namnen inte rullar så mycket. 
 
1. Välj matrisen och välj sedan kolumnen Företagsnamn.

3. Hovra över det grå fältet högst upp i matrisen till höger i kolumnen Företagsnamn. Dra till höger tills kolumnen slutar vid 1 3/8 tum. 

    ![Dra den högra kanten av kolumnen](media/paginated-reports-quickstart-aw/power-bi-paginated-drag-column.png)

4. Dra den högra kanten av Produktnamn tills kolumnen slutar vid 3 3/4 tum.   

Matrisen är nästan lika stor som utskriftsområdet.

### <a name="format-the-currency"></a>Formatera valutan

Som du kanske märkte när du körde rapporten så har dollarbeloppen ännu inte formaterats som valuta.

1. Välj övre vänstra cellen [Sum(OrderQty)], håll ned Skift-tangenten och markera cellen [Sum(LineTotal)] nere till höger.

    ![Markera celler med valutavärden](media/paginated-reports-quickstart-aw/power-bi-paginated-select-money-cells.png)

2. Välj valutasymbolen för dollar ( **$** ) på fliken **Start** och sedan pilen bredvid **Platshållarformat** > **Exempelvärden**.
 
    ![Visa exempelvärden](media/paginated-reports-quickstart-aw/power-bi-paginated-format-currency.png)

    Nu kan du se att värdena har formaterats som valuta.

    ![Valutaexempelvärden](media/paginated-reports-quickstart-aw/power-bi-paginated-display-sample-values.png)

### <a name="add-column-headers-on-each-page"></a>Lägg till kolumnrubriker på varje sida

Ytterligare en formateringsförbättring innan du publicerar rapporten till Power BI-tjänsten: Gör så att kolumnrubrikerna visas på varje sida i rapporten.

1. Välj listrutepilen > **Avancerat läge** längst ut till höger i det översta fältet i fönstret Gruppering.

    ![Aktivera avancerat läge](media/paginated-reports-quickstart-aw/power-bi-paginated-advanced-mode.png)

2. Välj den översta **Statiska** stapeln i **Radgrupper**. Cellen Företagsnamn i matrisen har valts.

   ![Välj statisk grupp](media/paginated-reports-quickstart-aw/power-bi-paginated-static-group.png)

3. Kontrollera egenskaperna för **Tablixmedlem** i fönstret **Egenskaper**. Ställ in **KeepWithGroup** på **Efter** och **RepeatOnNewPage** på **Sant**.

    ![Konfigurera RepeatOnNewPage](media/paginated-reports-quickstart-aw/power-bi-paginated-repeat-on-new-page.png)

    Nu är det dags att köra rapporten och se hur den ser ut.

5. Välj **Kör** på fliken **Start**.

6. Välj alternativet **Utskriftslayout** om det inte redan har valts. Nu innehåller rapporten 29 sidor. Bläddra igenom några sidor. Du kan se att valutan är formaterad, att kolumnerna har rubriker på varje sida och att rapporten innehåller en sidfot med sidnummer och datum- och tidsstämpel på varje sida.
 
    ![Färdig sida](media/paginated-reports-quickstart-aw/power-bi-paginated-finished-page.png)

7. Spara rapporten på datorn.
 
##  <a name="upload-the-report-to-the-service"></a>Ladda upp rapporten till tjänsten

Nu när du har skapat den här sidnumrerade rapporten är det dags att överföra den till Power BI-tjänsten.

1. Välj **Arbetsytor** > **Skapa apparbetsyta** i Power BI-tjänsten (http://app.powerbi.com) i det vänstra navigeringsfönstret.

2. Ge arbetsytan namnet **Azure AW** eller något annat unikt namn. Du är den enda medlemmen för tillfället. 

3. Välj pilen bredvid **Avancerat** och aktivera **Dedikerad kapacitet**. 

    ![Skapa arbetsyta i Premium-kapacitet](media/paginated-reports-quickstart-aw/power-bi-paginated-create-workspace-premium-capacity.png)

    Om du inte kan aktivera arbetsytan måste du be Power BI-administratören att ge dig behörighet att lägga till den i den dedikerade Premium-kapaciteten.

4. Välj en **tillgänglig dedicerad kapacitet för den här arbetsytan**, om så behövs > **Spara**.
    
    ![Premium -diamantikon](media/paginated-reports-quickstart-aw/power-bi-paginated-diamond-icon.png)

    Om arbetsytan inte är i en Premium-kapacitet så visas meddeladet ”Det går inte att lada upp sidnumrerad rapport” när du försöker att ladda upp rapporten. Kontakta Power BI-administratören om du vill flytta arbetsytan.

1. Välj **Hämta data** på din nya arbetsyta.

2. Välj **Hämta** i rutan **Filer**.

3. Välj **Lokal fil**, navigera till platsen där du sparade filen > **öppna**.

   Power BI har importerar filen, och du kan se den under **Rapporter** på lista med applistor.

    ![Rapport i applista](media/paginated-reports-quickstart-aw/power-bi-paginated-app-list.png)

4. Visa rapporten genom att markera den.

5. Om dett uppstår ett fel kan du behöva ange dina autentiseringsuppgifter på nytt. Välj ikonen **Hantera**.

    ![Spara rapporten](media/paginated-reports-quickstart-aw/power-bi-paginated-manage-report.png)

6. Välj **Redigera autentiseringsuppgifter** och ange de autentiseringsuppgifter som du använde i Azure när du skapade Azure-databasen.

    ![Redigera rapportautentiseringsuppgifter](media/paginated-reports-quickstart-aw/power-bi-paginated-edit-credentials.png)

7. Nu kan du visa din sidnumrerade rapport i Power BI-tjänsten.

    ![Sidnumrerad rapport i Power BI-tjänsten](media/paginated-reports-quickstart-aw/power-bi-paginated-report-service.png)

## <a name="next-steps"></a>Nästa steg

[Vad är sidnumrerade rapporter i Power BI Premium? (Förhandsversion)](paginated-reports-report-builder-power-bi.md)

