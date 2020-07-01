---
title: Ansluta till Xero med Power BI
description: Xero för Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 03/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 8ac9081e1cf7d6ec4ca53863c8111e56ae3ad68e
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85231724"
---
# <a name="connect-to-xero-with-power-bi"></a>Ansluta till Xero med Power BI
Xero är ett lättanvänt redovisningsprogram online som har specialutformats för små företag. Du kan skapa övertygande visuella objekt utifrån dina Xero-siffror med den här Power BI-mallappen. Standardinstrumentpanelen innehåller många mått för småföretag som kontantposition, inkomster och utgifter, vinst-/förlusttrend, gäldenärsdagar och räntabilitet.

Anslut till [Xero-mallappen](https://app.powerbi.com/getdata/services/xero) för Power BI eller lär dig mer om [Xero- och Power BI](https://help.xero.com/Power-BI)-integrering.

## <a name="how-to-connect"></a>Så här ansluter du

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Välj **Xero** \> **Hämta det nu**.
4. Välj **Installera** i **Vill du installera den här Power BI-appen?** .

    ![Installera Xero](media/service-connect-to-xero/power-bi-install-xero.png)

4. Välj **Xero**-panelen i fönstret **Appar**.

   ![Välj Xero-panelen](media/service-connect-to-xero/power-bi-start-xero.png)

6. I **Kom igång med din nya app** väljer du **Anslut**.

    ![Kom igång med din nya app](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Ange ett smeknamn för organisationen som ska associeras med Xero-kontot. Du kan fylla i vad som helst, namnet är mest avsett att hjälpa användare med flera Xero-organisationer att hålla redo på de olika kontona. Läs information om hur man [hittar parametrar](#FindingParams) längre fram i den här artikeln.

    ![Smeknamn för organisationen](media/service-connect-to-xero/params.png)

5. Välj **OAuth** som **Autentiseringsmetod**. Logga in till ditt Xero-konto, när du uppmanas till detta, och välj vilken organisation du ska ansluta till. När inloggningen är klar startar du inläsningsprocessen genom att välja **Logga in**.
   
    ![Autentiseringsmetod](media/service-connect-to-xero/creds.png)
   
    ![Välkommen till Xero](media/service-connect-to-xero/creds2.png)
6. Efter att du har godkänt startar importen automatiskt. När den är klar visas en ny instrumentpanel, en ny rapport och en ny modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.
   
     ![Xero-instrumentpanel](media/service-connect-to-xero/power-bi-xero-dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](../consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](../create-reports/service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](../consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Det här ingår
Mallappens instrumentpanel innehåller paneler och mått från en mängd olika områden med motsvarande rapporter där du kan lära dig mer om:  

| Område | Paneler på instrumentpanelen | Rapport |
| --- | --- | --- |
| Kontanter |Dagliga kassaflöde <br>Kontanter in <br>Kontanter ut <br>Utgående saldo per konto <br>Utgående saldo idag |Bankkonton |
| Kund |Fakturerad försäljning <br>Fakturerad försäljning per kund <br>Tillväxttrend för fakturerad försäljning <br>Förfallna fakturor <br>Utestående fodringar <br>Förfallna fodringar |Kund <br>Lager |
| Leverantör |Fakturerade inköp <br>Fakturerade inköp per leverantör <br>Tillväxttrend för fakturerade inköp <br> Förfallna räkningar <br>Utestående skulder <br>Förfallna skulder |Leverantörs- <br>Lager |
| Lager |Månatligt försäljningsbelopp per produkt |Lager |
| Vinst och förlust |Vinst och förlust per månad <br>Nettovinst detta räkenskapsår <br>Nettovinst denna månad <br>Största utgiftskontona |Vinst och förlust |
| Balansräkning |Tillgångar totalt <br>Skulder totalt <br>Kapital |Balansräkning |
| Hälsa |Likviditetskvot <br>Bruttomarginal procent <br> Avkastning på totala tillgångar <br>Förhållande mellan totala skulder och kapital |Hälsa <br>Ordlista och teknisk information |

Datauppsättningen innehåller också följande tabeller för att anpassa dina rapporter och instrumentpaneler:  

* Adresser  
* Aviseringar  
* Kontoutdrag dagsbalans  
* Kontoutdrag  
* Kontakter  
* Utgiftsanspråk  
* Fakturaradsposter  
* Fakturor  
* Poster  
* Månadsslut  
* Organisation  
* Råbalans  
* Xero-konton

## <a name="system-requirements"></a>Systemkrav
Följande roller krävs för att få åtkomst till Xero-mallappen: ”Standard + Rapporter” eller ”Advisor”.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Ange ett namn för din organisation som kan spåras i Power BI. Med ett specifikt namn kan du ansluta till flera olika organisationer. Du kan inte ansluta till samma organisation flera gånger, eftersom det påverkar den schemalagda uppdateringen.   

## <a name="troubleshooting"></a>Felsökning
* Xero-användare måste ha följande roller för att få åtkomst till Xero-mallappen för Power BI: ”Standard + Rapporter” eller ”Advisor”. Mallappen är beroende av användarbaserade behörigheter för åtkomst till rapportering av data via Power BI.
* Under inläsningen befinner sig panelerna på instrumentpanelen i ett allmänt inläsningstillstånd. De förblir på tills inläsningen har slutförts. Om du får ett meddelande om att inläsningen har slutförts men panelerna fortfarande läses in, kan du prova att uppdatera instrumentpanelens paneler med hjälp av ... i övre högra hörnet på instrumentpanelen.
* Om det inte går att uppdatera mallappen, så kontrollera om du har anslutit till samma organisation mer än en gång i Power BI. Xero tillåter endast en aktiv anslutning till en organisation och du kan se ett felmeddelande om att dina autentiseringsuppgifter är ogiltiga om du ansluter till samma mer än en gång.  
* Vid problem med att ansluta Xero-mallappen för Power BI, som felmeddelanden eller långsamma inläsningstider, kan du börja med att rensa cacheminnet/cookies, starta om webbläsaren och sedan återansluta till Power BI.  

När det gäller andra problem kan du öppna ett supportärende på https://support.powerbi.com om problemet kvarstår.

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](../fundamentals/service-get-started.md)

[Hämta data i Power BI](service-get-data.md)
