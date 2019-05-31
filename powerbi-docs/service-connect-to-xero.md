---
title: Ansluta till Xero med Power BI
description: Xero för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: d09936f2cce1d7835efdb82929d9e8eed2291163
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61156373"
---
# <a name="connect-to-xero-with-power-bi"></a>Ansluta till Xero med Power BI
Xero är en lättanvänd redovisningsprogramvara online som har specialutformats för små företag. Du kan skapa övertygande visualiseringar utifrån dina Xero-siffror med det här Power BI-innehållspaketet. Standardinstrumentpanelen innehåller många mått för småföretag som kontantposition, inkomster och utgifter, vinst-/förlusttrend, gäldenärsdagar och räntabilitet.

Anslut till [Xero-innehållspaketet](https://app.powerbi.com/getdata/services/xero) för Power BI eller lär dig mer om [Xero- och Power BI-](https://help.xero.com/Power-BI)integrering.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-xero/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-xero/services.png)
3. Välj **Xero** \> **Hämta**.
   
   ![](media/service-connect-to-xero/connect.png)
4. Ange ett smeknamn för organisation som ska associeras med Xero-kontot. Du kan fylla i vad som helst, namnet är mest avsett att hjälpa användare med flera Xero-organisationer att hålla redo på de olika kontona. Se information om detta [nedan](#FindingParams).
   
   ![](media/service-connect-to-xero/params.png)
5. Välj **OAuth** som **Autentiseringsmetod** när du ombes att logga in till ditt Xero-konto och välj organisation att ansluta till. När inloggningen är klar väljer du **Logga in** för att starta inläsningen.
   
    ![](media/service-connect-to-xero/creds.png)
   
    ![](media/service-connect-to-xero/creds2.png)
6. Efter att du har godkänt startar importen automatiskt. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.
   
     ![](media/service-connect-to-xero/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Det här ingår
Innehållspaketets instrumentpanel innehåller paneler och mått från en mängd olika områden med motsvarande rapporter där du kan lära dig mer om:  

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
Följande roller krävs för att få åtkomst till Xero-innehållspaketet: ”Standard + Rapporter” eller ”Advisor”.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Ange ett namn för din organisation som kan spåras i Power BI. På så sätt kan du ansluta till flera olika organisationer. Observera att du inte kan ansluta till samma organisation flera gånger, eftersom det påverkar den schemalagda uppdateringen.   

## <a name="troubleshooting"></a>Felsökning
* Xero-användare måste ha följande roller för att få åtkomst till Xero-innehållspaketet för Power BI: ”Standard + Rapporter” eller ”Advisor”. Innehållspaketet är beroende av användarbaserade behörigheter för åtkomst till rapportering av data via Power BI.  
* Om ett fel uppstår när inläsning pågått under en viss tid, kan du kontrollera hur lång tid det tog att visa felmeddelandet. Observera att den åtkomsttoken som tillhandahålls av Xero bara gäller i 30 minuter, så konton med mer data än vad som kan läsas in på den tiden misslyckas. Vi arbetar aktivt för att förbättra detta.
* Under inläsningen befinner sig panelerna på instrumentpanelen i ett allmänt inläsningstillstånd . Detta förväntas inte att förändras förrän hela inläsningen är avslutad. Om du får ett meddelande om att inläsningen har slutförts men panelerna fortfarande läses in, kan du prova att uppdatera instrumentpanelens paneler med hjälp av ... i övre högra hörnet på instrumentpanelen.
* Om det inte går att uppdatera innehållspaketet, kan du kontrollera om du har anslutit till samma organisation mer än en gång i Power BI. Xero tillåter endast en aktiv anslutning till en organisation och du kan se ett felmeddelande om att dina autentiseringsuppgifter är ogiltiga om du ansluter till samma mer än en gång.  
* Vid problem med att ansluta Xero-innehållspaketet för Power BI, som felmeddelanden eller mycket långsamma inläsningstider, kan du börja med att rensa cacheminnet/cookies, starta om webbläsaren och sedan återansluta till Power BI.  

För övriga problem kan du öppna ett supportärende på http://support.powerbi.com om problemet kvarstår.

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

