---
title: Ansluta till Zuora med Power BI
description: Zuora för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: b183738c062af1d834a742639369ca90f2cb1bad
ms.sourcegitcommit: 42475ac398358d2725f98228247b78aedb8cbc4f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003235"
---
# <a name="connect-to-zuora-with-power-bi"></a>Ansluta till Zuora med Power BI
Med Zuora för Power BI kan du visualisera viktiga intäkter, fakturering och prenumerationsdata. Använd standardinstrumentpanelen och rapporter för att analysera användningstrender, spåra fakturering och betalningar och övervaka återkomma intäkter eller anpassa dem för att uppfylla dina unika behov av instrumentpaneler och rapporter.

Ansluta till [Zuora](https://app.powerbi.com/getdata/services/Zuora) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.

   ![](media/service-connect-to-zuora/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.

   ![](media/service-connect-to-zuora/services.png)
3. Välj **Zuora** \> **Hämta**.

   ![](media/service-connect-to-zuora/zuora.png)
4. Ange ditt Zuora-URL. URL:en är normalt ”<https://www.zuora.com>”. Information om hur du [söker efter dessa parametrar](#FindingParams) finns nedan.

   ![](media/service-connect-to-zuora/params.png)
5. Som **Autentiseringsmetod** väljer du **Grundläggande** och anger sedan ditt användarnamn och lösenord (skiftlägeskänsliga). Välj sedan **Logga in**.

    ![](media/service-connect-to-zuora/creds.png)
6. Efter att du har godkänt startar importen automatiskt. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.

     ![](media/service-connect-to-zuora/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Det här ingår
Innehållspaketet använder Zuora AQUA API för att hämta följande tabeller:

| Tables |  |  |
| --- | --- | --- |
| Konto |InvoiceItemAdjustment |Refund |
| AccountingCode |Payment |RevenueSchedule |
| AccountingPeriod |PaymentMethod |RevenueScheduleItem |
| BillTo |Produkt |Subscription |
| DateDim |ProductRatePlan |TaxationItem |
| Invoice |ProductRatePlanCharge |Usage |
| InvoiceAdjustment |RatePlan | |
| InvoiceItem |RatePlanCharge | |

Den inkluderar också dessa beräknade mått:

| Mått | Beskrivning | Halvberäkning |
| --- | --- | --- |
| Konto: betalningar |Totalt betalningsbelopp under en tidsperiod, baserat på betalningens förfallodatum. |SUM (Payment.Amount) <br>WHERE<br>Payment.EffectiveDate =< TimePeriod.EndDate<br>AND    Payment.EffectiveDate >= TimePeriod.StartDate |
| Konto: återbetalningar |Total återbetalning under en tidsperiod, baserat på återbetalningsdatumet. Mängden har rapporterats som ett negativt tal. |-1*SUM(Refund.Amount)<br>WHERE<br>Refund.RefundDate =< TimePeriod.EndDate<br>AND    Refund.RefundDate >= TimePeriod.StartDate |
| Konto: nettobetalningar |Kontobetalningar plus återbetalningar under en tidsperiod. |Account.Payments + Account.Refunds |
| Konto: Aktiva konton |Antal konton som var aktiva under en tidsperiod. Prenumerationer måste har startat innan (eller under) tidsperiodens startdatum. |COUNT (Account.AccountNumber)<br>WHERE<br>    Subscription.Status != "Expired"<br>AND    Subscription.Status != "Draft"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    (Subscription.SubscriptionEndDate > TimePeriod.StartDate<br>OR<br>Subscription.SubscriptionEndDate = null) –evergreen subscription |
| Konto: Genomsnittliga återkommande intäkter |Bruttomarginal MRR per aktivt konto under en tidsperiod. |Gross MRR / Account.ActiveAccounts |
| Konto: Annullerade prenumerationer |Antal konton som avbrutit en prenumeration under en tidsperiod. |COUNT (Account.AccountNumber)<br>WHERE<br>Subscription.Status = "Cancelled"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    Subscription.CancelledDate >= TimePeriod.StartDate |
| Konto: Betalningsfel |Summan av betalningsfel. |SUM (Payment.Amount)<br>WHERE<br>Payment.Status = "Error" |
| Objekt i intäktsschema: Identifierade intäkter |Totalt antal identifierade intäkter under en redovisningsperiod. |SUM (RevenueScheduleItem.Amount)<br>WHERE<br>AccountingPeriod.StartDate = TimePeriod.StartDate |
| Prenumerationen: Nya prenumerationer |Antal nya prenumerationer under en tidsperiod. |COUNT (Subscription.ID)<br>WHERE<br>Subscription.Version = "1"<br>AND    Subscription.CreatedDate <= TimePeriod.EndDate<br>AND    Subscription.CreatedDate >= TimePeriod.StartDate |
| Faktura: Fakturaposter |Totalt antal fakturaposter som har debiterats under en tidsperiod. |SUM (InvoiceItem.ChargeAmount)<br>WHERE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Faktura: Skatteobjekt |Totalt antal skattebelopp under en tidsperiod. |SUM (TaxationItem.TaxAmount)<br>WHERE<br>Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Fakturera: Justeringar hos fakturaobjekt |Totalt antal fakturaposter som har justerats under en tidsperiod. |SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceItemAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceItemAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| Faktura: Justeringar hos fakturor |Totalt antal fakturajusteringar under en tidsperiod. |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| Faktura: Nettobelopp |Summan av poster, skatteobjekt, fakturaobjektjusteringar och fakturajusteringar under en tidsperiod. |Invoice.InvoiceItems + Invoice.TaxationItems + Invoice.InvoiceItemAdjustments + Invoice.InvoiceAdjustments |
| Fakturera: Fakturans saldo |Summan av bokförda fakturasaldon. |SUM (Invoice.Balance) <br>WHERE<br>    Invoice.Status = "Posted" |
| Faktura: Bruttofakturering |Summan av fakturaobjekt för bokförda fakturor under en tidsperiod. |SUM (InvoiceItem.ChargeAmount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| Faktura: Totala justeringar |Summan av bearbetade fakturajusteringar och fakturaobjektjusteringar som är associerade med bokförda fakturor. |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.Status = "Processed"<br>+<br>SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    invoiceItemAdjustment.Status = "Processed" |
| Prenumerationsavgift: Brutto MMR |Summan av månatliga återkommande intäkter från prenumerationer under en tidsperiod. |SUM (RatePlanCharge.MRR) <br>WHERE<br>    Subscription.Status != "Expired"<br>AND    Subscription.Status != "Draft"<br>AND    RatePlanCharge.EffectiveStartDate <= TimePeriod.StartDate<br>AND        RatePlanCharge.EffectiveEndDate > TimePeriod.StartDate<br>    OR RatePlanCharge.EffectiveEndDate = null --evergreen subscription |

## <a name="system-requirements"></a>Systemkrav
Åtkomst till Zuora-API måste anges.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Ange en URL som du vanligtvis anger för att få åtkomst till dina Zuora-data. Giltiga alternativ är:  

* https://www.zuora.com  
* Den URL som motsvarar din instans av tjänsten  

## <a name="troubleshooting"></a>Felsökning
Innehållspaketet Zuora hämtar många olika aspekter av ditt Zuora-konto. Om du inte använder vissa funktioner kan motsvarande paneler/rapporter vara tomma. Kontakta supporten för Power BI om du har problem med att läsa in.

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)
