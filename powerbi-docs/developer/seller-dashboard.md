---
title: Skicka ett visuellt objekt för Power BI till AppSource med hjälp av Seller Dashboard
description: Skicka ett visuellt objekt för Power BI till AppSource med hjälp av Seller Dashboard
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/03/2019
ms.openlocfilehash: 73a6a3d16ae2515af41a3232a37579e18876f38b
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2020
ms.locfileid: "75223674"
---
# <a name="submit-a-power-bi-visual-to-appsource-using-seller-dashboard"></a>Skicka ett visuellt objekt för Power BI till AppSource med hjälp av Seller Dashboard

Innan du skickar till AppSource, måste du skicka ett e-postmeddelande med **pbiviz**-filen och **pbix**-filen till Power BI-teamet. På så vis kan Power BI-teamet överföra filerna till en offentlig resursserver. Annars kommer butiken inte att hämta filerna. Du måste skicka filerna med varje ny inlämning av visuella objekt för Power BI, uppdatering av visuella objekt för Power BI och korrigeringar av avvisade inlämningar.

>[!NOTE]
>[Seller Dashboard](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) kommer att fasas ut. Den ersätts av [Partner Center](https://docs.microsoft.com/partner-center/). Använd endast Seller Dashboard om du är mitt i en överföring av ett visuellt objekt för Power BI. Om du skickar ett nytt visuellt objekt för Power BI till AppSource ska du använda [Partner Center-metoden](office-store.md#submitting-to-appsource).

### <a name="seller-dashboard-submission-process"></a>Sändningsprocess för Seller Dashboard

Du måste ha ett giltigt Office-utvecklarkonto för att logga in på [Office Developer Center](https://dev.office.com/). Ett Office-utvecklarkonto måste vara ett Microsoft Account Live ID, t.ex. hotmail.com eller outlook.com.

1. Gå till [Developer Center](https://sellerdashboard.microsoft.com/Application/Summary).

2. Välj **lägg till en app**.

    ![Lägga till en app](media/office-store/powerbi-custom-visual-add-an-app.png)

3. Välj anpassat visuellt objekt i **Power BI** och sedan **Nästa**.

4. Välj **+** under **Appaket** och välj appaketets XML-fil som du har fått från Power BI-teamet från dialogrutan Öppna fil.

    ![Appaket](media/office-store/powerbi-custom-visual-apppackage.png)

5. Du bör få ett godkännande om att detta är ett giltigt programpaket för Power BI.

    ![Manifestet har godkänts](media/office-store/powerbi-custom-visual-manifest-approved.png)

6. Fyll i **Allmän information**.

   * *Överföringsrubrik:* Namnet din överföring får i Developer Center.
   * *Version:* Versionsnumret är automatiskt ifyllt från ditt tilläggsprogrampaket.
   * *Utgivningsdatum (UTC):* Välj ett datum då din app ska lanseras i butiken. Om du väljer ett datum i framtiden blir appen inte tillgängligt i store förrän detta datum har nåtts.
   * *Kategori:* Den första kategorin fylls i automatiskt som ”Datavisualisering + BI”. Så här markeras alla visuella Power BI-objekt. Du kan ange upp till två ytterligare kategorier som hjälper användare att söka efter ditt visuella objekt.
   * *Testanteckningar:* valfritt om du vill ge anvisningar till testarna på Microsoft
   * *Min app anropar, stöder, innehåller eller använder kryptografi eller kryptering:* lämna alternativet omarkerat
   * *Gör det här tillägget tillgängligt i Office-tillägg-katalogen på iPad:* lämna alternativet omarkerat
7. Ladda upp en logotyp för ditt visuella objekt genom att välja **+** under **App-logotyp**. Välj sedan ikonfilen i dialogrutan Öppna fil. Filen måste vara .png, .jpg, .jpeg eller .gif. Det måste vara exakt 300 px (bredd) x 300 px (höjd) och inte större än 512 kB.

    ![Applogotyp](media/office-store/powerbi-custom-visual-app-logo.png)

8. Fyll i **Stöddokumentationen**.

   * Länk till stöddokumentet
   * Länk till sekretessdokumentet
   * Videolänk
   * Licensavtalet (EULA)

       Du måste överföra ett licensavtal. Detta kan vara ditt eget licensavtal eller standardlicensavtalet från Office Store för visuella objekt i Power BI. Om du vill använda standardlicensavtalet klistrar du in följande URL i dialogrutan för filöverföring av ”Licensavtal” i försäljningsinstrumentpanelen: [https://visuals.azureedge.net/app-store/Power BI - Default Custom Visual EULA.pdf](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf).

9. Välj **nästa** för att komma till sidan **Information**.

10. Välj **språk** och välj ett språk i listan.

    ![Språk](media/office-store/powerbi-custom-visual-language.png)

11. Fyll i ”Beskrivning”.

    * *Programnamn (för det här språket):* Ange rubriken för appen som det visas i storefront.
    * *Kort beskrivning:* Ange den korta beskrivningen för din app, upp till 100 tecken, som det visas i storefront. Den här beskrivningen visas på sidorna på den högsta nivån tillsammans med logotypen. Du kan använda beskrivningen från pbiviz-paketet.
    * *Lång beskrivning:* Ge en mer detaljerad beskrivning av din app som kommer att visas på din appinformationssida. Ange en länk till den offentliga databasen, till exempel GitHub, här om du vill låta communityn förbättra din visuella genom att öppna källkoden.

12. Överför minst en skärmbild. Formatet kan vara .png, .jpg, .jpeg eller .gif. Det måste vara exakt 1366 px (bredd) x 768 px (höjd). Filstorleken får inte vara större än 1024 kB. *Lägg till textbubblor för att tydligt betona mervärdet av viktiga funktioner som visas i varje skärmbild.*

12. Om du vill lägga till fler språk väljer du **Lägg till ett språk** och upprepa steg 10 och 11. Genom att lägga till fler språk kan användarna visa information om det anpassade visuella objektet på sina egna språk. Språk som inte visas kommer att övergå till det första valda språket som standard.

13. När du är klar med att lägga till språk väljer du **Nästa** för att komma till sidan **Blockera åtkomst**.

14. Om du vill förhindra kunder i vissa länder eller regioner från att använda eller köpa din app, markerar du kryssrutan och väljer dessa i listan.

15. Välj **Nästa** för att komma till sidan **Prissättning**.

16. För närvarande stöds endast *kostnadsfria* visuella objekt och ytterligare inköp i visuella objekt (köp i appen) är inte tillåtna. Välj **Den här appen är kostnadsfri**.

    > [!NOTE]
    > Om du väljer något annat alternativ än kostnadsfri eller har inköp i appinnehåll i det skickade visuella objektet, kommer överföringen att avvisas.

17. Nu kan du välja **Spara som utkast** och skicka senare, eller välja **Överför för godkännande** för att skicka det anpassade visuella objektet till Office Store.

## <a name="seller-dashboard-certification-submission-process"></a>Sändningsprocess för Seller Dashboard

Följ anvisningarna i det här avsnittet om du vill skicka ett visuellt Power BI-objekt för certifiering i Seller Dashboard. Använd den här metoden om du tidigare skickade ett visuellt Power BI-objekt till AppSource med hjälp av Seller Dashboard.

1. Skicka ett e-postmeddelande till supportteamet för visuella Power BI-objekt i Power BI (pbicvsupport@microsoft.com). Inkludera följande information i e-postmeddelandet:
    * Rubrik: Begäran om certifiering av visuellt objekt
    * Länk till GitHub-lagringsplatsen där källkoden som är läsbar för människor finns
    * [Uppfylla kraven](power-bi-custom-visuals-certified.md#certification-requirements)
    * Skicka kodgranskningen

2. Teamet för visuella Power BI-objekt på Microsoft informerar dig när ditt visuella Power BI-objekt har certifierats och lagts till i [listan över certifierade visuella Power BI-objekt](power-bi-custom-visuals-certified.md#certified-power-bi-visuals) eller avvisats med en rapport som innehåller fel som ska åtgärdas. Det är utvecklarens ansvar för att kommunicera med Microsoft och för att uppdatera sina certifierade visuella objekt vid behov.

## <a name="tracking-submission-status-and-usage"></a>Spåra sändningsstatus och användning

Du kan granska [verifieringsprinciperna](https://dev.office.com/officestore/docs/validation-policies#13-power-bi-custom-visuals).

Därefter kommer du att kunna visa status för ansökan i [appinstrumentpanelen](https://sellerdashboard.microsoft.com/Application/Summary/).

## <a name="certify-your-visual"></a>Godkänn ditt visuella objekt

När du har skapat ditt visuella objekt kan du välja att få det [certifierat](../developer/power-bi-custom-visuals-certified.md).

## <a name="next-steps"></a>Nästa steg

[Utveckla ett anpassat visuellt objekt i Power BI](visuals/custom-visual-develop-tutorial.md)  
[Visualiseringar i Power BI](../visuals/power-bi-report-visualizations.md)  
[Anpassade visualiseringar i Power BI](../developer/power-bi-custom-visuals.md)  
[Certifiera ett visuellt Power BI-objekt](../developer/power-bi-custom-visuals-certified.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
