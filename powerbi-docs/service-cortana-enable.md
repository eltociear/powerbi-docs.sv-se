---
title: Aktivera Cortana för Power BI
description: Hämta svar från dina data med hjälp av Cortana med Power BI. Aktivera Cortana för varje Power BI-datauppsättning och aktivera sedan Cortana så att hon får åtkomst till dina datauppsättningar från Windows-enheter.
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: a631bc37c193521b2acc367a0c6d8540419e3b79
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872912"
---
# <a name="enable-cortana-to-access-power-bi-reports-and-their-underlying-datasets"></a>Aktivera Cortana för åtkomst till Power BI-rapporter (och deras underliggande datauppsättningar)
Förmodligen har du läst artikeln [Introduktion till Cortana och Power BI](service-cortana-intro.md) redan. Om du inte har gjort det, så läs den först, och kom sedan tillbaka hit. Och nu kan du prova själv.  Innan du kan ställa frågor på naturligt språk i Cortana och få svar från data som lagras i Power BI-***rapporter***, så måste vissa krav uppfyllas. Du måste i synnerhet göra följande.

> [!IMPORTANT]
> Cortana-integrering blir inaktuell i Power BI. Från och med 11 juni kommer Cortana inte längre att fungera för instrumentpaneler och rapporter.

I Power BI-tjänsten

* Aktivera en eller flera datauppsättningar för Cortana (rapporterna är byggda på datauppsättningar, så Cortana behöver åtkomst till dessa datauppsättningar)

I Microsoft Windows

* Kontrollera att du kör Windows 10 version 1511 eller senare
* Kontrollera att Power BI och Windows kan ”prata” med varandra. Det innebär att du ansluter ditt konto till Windows.

## <a name="use-power-bi-service-to-enable-cortana-to-access-report-pages-in-power-bi"></a>Använd Power BI-tjänsten för att aktivera Cortana för rapportsidor i Power BI
Att aktivera rapporter i Power BI så att de kan nås av Cortana är en enkel process.  Allt du behöver göra är att aktivera rapportens underliggande datauppsättning genom att välja ”Aktivera Cortana för åtkomst till den här datauppsättningen”. Efter det kan varje användare som har åtkomst till datauppsättningen i Power BI, via vanlig Power BI-delning, appar eller innehållspaketsfunktioner, få svar från rapporten i Cortana i Windows 10.

Du måste logga in på Power BI-tjänsten (inte Power BI Desktop) och upprepa dessa steg för varje datauppsättning som du vill att Cortana ska ha åtkomst till.

1. Bestämma vilka datauppsättningar som ska aktiveras. Välj den rapport du vill att Cortana ska ha åtkomst till från rapportinnehållslistan och välj ikonen **Visa relaterade** ![](media/service-cortana-enable/power-bi-cortana-view-related-icon.png) .
   
    ![Visa relaterat innehåll](media/service-cortana-enable/power-bi-view-related.png)
2. Den datauppsättning som är associerad med den här rapporten är **Contoso Sales**.
   
    ![Datauppsättningen Contoso Sales](media/service-cortana-enable/power-bi-identify-dataset.png)
3. Till höger om datauppsättningsnamnet väljer du **Fler alternativ** (...) > Inställningar**.  
   
    ![Välj Inställningar](media/service-cortana-enable/power-bi-settings-cortana.png)
4. Välj **Frågor och svar och Cortana** > **Ge Cortana åtkomst till den här datauppsättningen** > **Tillämpa**.
   
   ![Cortana har åtkomst till datauppsättning](media/service-cortana-enable/power-bi-cortana-enable-new.png)
   
   I det här exemplet aktiverar vi Cortana för datauppsättningen Contoso Sales.
   
   > [!NOTE]
   > När en ny datauppsättning eller ett Cortana-svarskort läggs till i Power BI och aktiveras i Cortana för rapporter, kan det ta upp till 30 minuter innan resultaten visas. Om du logga in och ut ur Windows 10 eller på annat sätt startar om Cortana-processen i Windows 10, kan det nya innehållet visas direkt.
   > 
   > Om du aktiverar en datauppsättning för Cortana och den datauppsättningen är en del av ett innehållspaketet eller en app som du äger, så måste du publicera om för dina kollegor så att även de kan använda det med Cortana.
   > 
   > 

## <a name="add-your-power-bi-credentials-to-windows"></a>Lägg till dina Power BI-autentiseringsuppgifter i Windows
Du måste köra Windows 10 version 1511 eller senare.

1. Bestämma vilken Windows 10-version du kör. Öppna **Inställningar**.
    ![Öppna Windows-inställningar](media/service-cortana-enable/power-bi-cortana-windows.png)

    Välj sedan **System > Om**. Längst ned på skärmen ser du **Windows-specifikationer > Version**

   * Om du har Windows 10 version 1511 (Windows-uppdateringen från den 10 november 2015) fram till 1607, lägger du till ditt arbets- eller skolkonto och Microsoft-konto (slutför steg 2 och 3 nedan).
   * Om du har Windows 10 version 1607 (Windows-uppdateringen från den 10 juli 2016) eller senare, lägger du till ditt arbets- eller skolkonto (slutför endast steg 2 nedan).
1. Lägg till arbets-eller skolkonto för Cortana.
   
   * Öppna **Inställningar** > **Konton**.
     
       ![Inställningar – Konton](media/service-cortana-enable/power-bi-windows-accounts.png)
   * Bläddra längst ned till botten och välj **Lägg till ett arbets- eller skolkonto**. Eller så väljer du **Åtkomst till arbete eller skola > Anslut** från sidan **Konton**.
     
     ![Lägg till arbetskonto](media/service-cortana-enable/power-bi-add-work-account2.png)

Cortana använder det här arbets- eller skolkontot för att söka efter potentiella svar på dina frågor i Power BI.

## <a name="next-steps"></a>Nästa steg
[Skapa Cortana *-svarskort* i Power BI](service-cortana-answer-cards.md)

[Felsökning av problem med Cortana och Power BI-integrering](service-cortana-troubleshoot.md)

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

