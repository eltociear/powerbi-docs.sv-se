---
title: 'Självstudier: Utforska Power BI-rapportservern på en virtuell dator'
description: I de här självstudierna skapar du en virtuell dator med Power BI-rapportservern redan installerad och utforskar webbportalen.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: tutorial
ms.date: 05/18/2018
ms.author: maggies
ms.openlocfilehash: 38985014407a4d64998e25f6944f57aedcc67309
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2018
ms.locfileid: "34445013"
---
# <a name="tutorial-explore-the-power-bi-report-server-web-portal-in-a-vm"></a>Självstudier: Utforska Power BI-rapportservern på en virtuell dator
I de här självstudierna skapar du en virtuell Azure-dator med Power BI-rapportservern redan installerad, så att du kan visa, redigera och hantera exempel på Power BI- och sidnumrerade rapporter samt KPI:er.

![Report Server-webbportalen](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm-no-numbers.png)

De här uppgifterna kommer du att utföra i de här självstudierna:

> [!div class="checklist"]
> * Skapa och ansluta till en virtuell dator
> * Börja utforska Power BI-rapportserverns webbportal
> * Tagga ett favoritobjekt
> * Visa och redigera en Power BI-rapport
> * Visa, hantera och redigera en sidnumrerad rapport
> * Visa en Excel-arbetsbok i Excel Online

För de här självstudierna behöver du en Azure-prenumeration. Om du inte har någon, kan du [skapa ett kostnadsfritt konto](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) innan du börjar.

## <a name="create-a-power-bi-report-server-vm"></a>Skapa en virtuell dator med Power BI-rapportserver

Som tur är har Power BI-teamet skapat en virtuell dator som levereras med Power BI-rapportservern redan installerad.

1. Öppna [Power BI-rapportservern](https://azuremarketplace.microsoft.com/marketplace/apps/reportingservices.technical-preview?tab=Overview) på Microsoft Azure Marketplace.  

2. Välj **Hämta nu**.
3. Om du accepterar leverantörens användningsvillkor och sekretesspolicy väljer du **Fortsätt**.

    ![Skapa en virtuell dator med Power BI-rapportserver](media/tutorial-explore-report-server-web-portal/power-bi-report-server-virtual-machine-create.png)

4. **Steg 1: Grundläggande** för **namn på virtuell dator**, kalla den **reportservervm**.

5. Skapa ett användarnamn och ett lösenord.

6. För **Resursgrupp** behåller du **Skapa ny** och kallar den **reportserverresourcegroup**.

    Om du går igenom kursen mer än en gång måste du ge resursgruppen ett annat namn efter första gången. Du kan inte använda samma namn på resursgruppen två gånger i samma prenumeration. 

7. Behåll de övriga standardvärdena > **OK**.

    ![Namnge den virtuella datorn och resursgruppen](media/tutorial-explore-report-server-web-portal/power-bi-report-server-create-resource-group.png)

8. **Steg 2: Inställningar**, behåll standardvärdena > **OK**.

9. **Steg 3: Sammanfattning** > **OK**.

10. **Steg 4**: Läs igenom användarvillkoren och sekretesspolicyn > **Skapa**.

    Processen för att **skicka distribution för Power BI-rapportservern** tar ett par minuter.

## <a name="connect-to-your-virtual-machine"></a>Anslut till den virtuella datorn

1. Välj **Virtuella datorer** i det vänstra navigeringsfönstret i Azure. 

2. I rutan **Filtrera efter namn** skriver du ”rapport”. 

3. Välj den virtuella datorn med namnet **REPORTSERVERVM**.

    ![Visa den virtuella datorn](media/tutorial-explore-report-server-web-portal/power-bi-report-server-view-virtual-machine.png)

4. Välj **Anslut** under den virtuella datorn REPORTSERVERVM.

    ![Anslut till den virtuella datorn](media/tutorial-explore-report-server-web-portal/power-bi-report-server-connect-to-virtual-machine.png)

5. Välj **Anslut** i dialogrutan för anslutning till fjärrskrivbord.

6. Ange det namn och lösenord som du skapade för den virtuella datorn > **OK**.

7. Nästa dialogruta säger att fjärrdatorns identitet inte kan identifieras. Välj **Ja**.

   Ta-da! Din nya virtuella dator öppnas.

## <a name="power-bi-report-server-on-the-vm"></a>Power BI-rapportservern på den virtuella datorn

När den virtuella datorn öppnas visas nedanstående objekt på skrivbordet.

![Den virtuella datorn med Power BI-rapportservern startar](media/tutorial-explore-report-server-web-portal/power-bi-report-server-start-vm-numbered.png)

|Tal  |Vad det är  |
|---------|---------|
|![Nummer 1](media/tutorial-explore-report-server-web-portal/number-1.png) | Startar SQL Server Data Tools för att skapa sidnumrerade rapporter (av typen .RDL) |
|![Nummer 2](media/tutorial-explore-report-server-web-portal/number-2.png) | Exempel på Power BI-rapporter (av typen .PBIX)  |
|![Nummer 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Länkar till Power BI-rapportserverns dokumentation   |
|![Nummer 4](media/tutorial-explore-report-server-web-portal/number-4.png) | Startar Power BI Desktop som har optimerats för Power BI-rapportservern (mars 2018)  |
|![Nummer 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Öppnar Power BI-rapportserverns webbportal i webbläsaren   |

Dubbelklicka på ikonen för **rapportserverns webbportal**. Webbläsaren öppnar http://localhost/reports/browse. I webbportalen kan du se olika filer grupperade efter typ. 

![Webbportalen för Power BI-rapportserver](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm.png)

|Tal  |Vad det är  |
|---------|---------|
|![Nummer 1](media/tutorial-explore-report-server-web-portal/number-1.png) | KPI:er som skapats i webbportalen |
|![Nummer 2](media/tutorial-explore-report-server-web-portal/number-2.png) |  Power BI-rapporter (av typen .PBIX)  |
|![Nummer 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Mobila rapporter som skapats i SQL Server Mobile Report Publisher  |
|![Nummer 4](media/tutorial-explore-report-server-web-portal/number-4.png) |  Sidnumrerade rapporter som skapats i Report Builder eller i SQL Server Data Tools  |
|![Nummer 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Excel-arbetsböcker   | 
|![Nummer 6](media/tutorial-explore-report-server-web-portal/number-6.png) | Datakällor för sidnumrerade rapporter | 


## <a name="tag-your-favorites"></a>Tagga dina favoriter
Du kan tagga de rapporter och KPI:er som du vill ska vara favoriter. De är lättare att hitta eftersom de är samlade i en enda favoritmapp, både i webbportalen och i Power BI-mobilappar. 

1. Välj ellipsen (**...**) i det övre högra hörnet i av **Vinstmarginal** KPI > **Lägg till i favoriter**.
   
    ![Lägg till i favoriter](media/tutorial-explore-report-server-web-portal/power-bi-report-server-add-to-favorites.png)
2. Välj **favoriter** från webbportalens menyflik för att se dem tillsammans med dina andra favoriter på favoriter-sidan i webbportalen.
   
    ![Visa favoriter](media/tutorial-explore-report-server-web-portal/power-bi-report-server-favorites.png)

3. Välj **Bläddra** för att gå tillbaka till webbportalen.
   
## <a name="view-items-in-list-view"></a>Visa objekt i listvyn
Som standard visar webbportalen innehållet i panelvyn.

Du kan växla till listvy, där det är enkelt att flytta eller ta bort flera objekt i taget. 

1. Select **panel** > **-listan**.
   
    ![Växla vyer](media/tutorial-explore-report-server-web-portal/report-server-web-portal-list-view.png)

2. Gå tillbaka till panel och välj **Lista** > **Paneler**.

## <a name="power-bi-reports"></a>Power BI-rapporter

Du kan visa och interagera med Power BI-rapporter i webbportalen och starta Power BI Desktop direkt från webbportalen.

### <a name="view-power-bi-reports"></a>Visa Power BI-rapporter

1. I webbportalen, under **Power BI-rapporter**, väljer du **exemplet på kundöversiktsrapporten**. Rapporten öppnas i webbläsaren.

1. Välj USA-blocket i trädkartan för att se hur det markerar relaterade värden i de övriga visuella objekten.

    ![Power BI-rapporten markerad](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi.png)

### <a name="edit-in-power-bi-desktop"></a>Redigera i Power BI Desktop

1. Välj **Redigera i Power BI Desktop**.

1. Välj **Tillåt** för att tillåta att den här webbplatsen får öppna ett program på datorn. 

     Rapporten öppnas i Power BI Desktop. Notera namnet på den översta raden, ”Power BI Desktop (mars 2018)”. Det är den version som optimerats för Power BI-rapportservern.

    ![Power BI Desktop](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-desktop.png)

     Använd versionen av Power BI Desktop som är installerad på den virtuella datorn. Du kan inte ladda upp en rapport på en annan domän.

3. I fönstret Fält expanderar du tabellen Kunder och drar fältet Sysselsättning till Rapportnivåfilter.

    ![Dra ett fält till fönstret Filter](media/tutorial-explore-report-server-web-portal/power-bi-report-server-desktop-filter.png)

1. Spara rapporten.

1. Gå tillbaka till rapporten i webbläsaren och välj ikonen **Uppdatera** i webbläsaren.

    ![Ikonen för att uppdatera webbläsaren](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-refresh.png)

8. Expandera fönstret **Filter** till höger om du vill se filtret **Sysselsättning** som du lade till. Välj **Professionell**.

    ![Filtrerad Power BI-rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-filtered.png)

3. Välj **Bläddra** för att gå tillbaka till webbportalen.

## <a name="paginated-rdl-reports"></a>Sidnumrerade rapporter (av typen .RDL)

Du kan visa och hantera sidnumrerade rapporter och starta Report Builder från webbportalen.

### <a name="manage-a-paginated-report"></a>Hantera en sidnumrerad rapport

1. I webbportalen, under **Sidnumrerade rapporter**, väljer du ellipsen (...) bredvid **Försäljningsorder** > **Hantera**.

1. Välj **Parametrar**, ändra standardvärdet för **SalesOrderNumber** till **SO50689** > **Verkställ**.

   ![Ange rapportparametrar](media/tutorial-explore-report-server-web-portal/power-bi-report-server-set-parameters.png)

3. Välj **Bläddra** för att gå tillbaka till webbportalen.

### <a name="view-a-paginated-report"></a>Visa en sidnumrerad rapport

1. Välj **Försäljningsorder** i webbportalen.
 
3.  Du ser att den öppnas efter den parameter för **Order** som du angav, **SO50689**. 

    ![Parameter för sidnumrerad rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated.png)

    Du kan ändra den här parametern här, tillsammans med de övriga parametrarna, utan att ändra standardvärdena.

1. Välj **Order** **SO48339** > **Visa rapport**.

4. Du ser att detta är sidan 1 av 2. Välj högerpilen för att se den andra sidan. Tabellen fortsätter på den sidan.

    ![Sidnumrerad rapport, sida 2 av 2](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-2-of-2.png)

5. Välj **Bläddra** för att gå tillbaka till webbportalen.

### <a name="edit-a-paginated-report"></a>Redigera en sidnumrerad rapport

Du kan redigera sidnumrerade rapporter i Report Builder och du kan starta Report Builder direkt från webbläsaren.

1. Välj ellipsen (...) bredvid **Försäljningsorder** > **Redigera i Report Builder** i webbportalen.

1. Välj **Tillåt** för att tillåta att den här webbplatsen får öppna ett program på datorn.

1. Försäljningsorderrapporten öppnas i designvyn i Report Builder.

    ![Vyn Design, sidnumrerad rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-design-view.png)

1. Välj **Kör** för att förhandsgranska rapporten.

    ![Förhandsgranska en sidnumrerad rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-preview.png)

5. Stäng Report Builder och gå tillbaka till webbläsaren.

## <a name="view-excel-workbooks"></a>Visa Excel-arbetsböcker

Du kan visa och interagera med Excel-arbetsböcker i Excel Online i Power BI-rapportservern. 

1. Välj Excel-arbetsboken **Office Liquidation Sale.xlsx**. Du kan bli ombedd att ange autentiseringsuppgifter. Välj **Avbryt**. 
    Den öppnas i webbportalen.
1. Välj **Installation** i utsnittet.

    ![Excel Online i webbportalen](media/tutorial-explore-report-server-web-portal/power-bi-report-server-excel-online.png)

1. Välj **Bläddra** för att gå tillbaka till webbportalen.

## <a name="clean-up-resources"></a>Rensa resurser

Nu när du är klar med de här självstudierna kan du ta bort resursgruppen, den virtuella datorn och alla relaterade resurser. 

- För att göra det väljer du resursgruppen för den virtuella datorn och sedan **Ta bort**.

## <a name="next-steps"></a>Nästa steg

I de här självstudierna har du skapat en virtuell dator med Power BI-rapportservern. Du har provat några av funktionerna i webbportalen och du har öppnat en Power BI-rapport och en sidnumrerad rapport i sina respektive redigerare. Den här virtuella datorn har installerade SQL Server Analysis Services-datakällor, så du kan prova att skapa egna Power BI- och sidnumrerade rapporter med de här datakällorna. 

Om du vill veta mer om hur du skapar rapporter för Power BI-rapportservern kan du fortsätta läsa.

> [!div class="nextstepaction"]
> [Skapa en Power BI-rapport för Power BI-rapportservern](./quickstart-create-powerbi-report.md)



