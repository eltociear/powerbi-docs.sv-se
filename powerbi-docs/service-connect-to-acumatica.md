---
title: Anslut till Acumatica med Power BI
description: Acumatica för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: ea5ce2e1e635149c91fbcf38d84e3093af7915c9
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2018
ms.locfileid: "34243855"
---
# <a name="connect-to-acumatica-with-power-bi"></a>Anslut till Acumatica med Power BI
Med innehållspaketet Power BI Acumatica kan du snabbt få insikter om dina affärsmöjlighetsdata. Power BI hämtar dina data, inklusive affärsmöjligheter, konton och kunder och skapar sedan en standardinstrumentpanel och relaterade rapporter baserat på dessa data.

Anslut till [Acumatica-innehållspaketet](https://app.powerbi.com/getdata/services/acumatica) eller läs mer om [Acumatica-integrering](https://powerbi.microsoft.com/integrations/acumatica) med Power BI.

>[!NOTE]
>Det här Innehållspaketet kräver Acumatica v5.2 eller högre.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-acumatica/getdata3.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-acumatica/getdata2.png)
3. Välj **Acumatica** \> **hämta**.
   
   ![](media/service-connect-to-acumatica/acumatica.png)
4. Ange din Acumatica OData-slutpunkt. En OData-slutpunkt tillåter ett externt system att begära data från Acumatica. Acumatica OData-slutpunkten är formaterat på följande sätt och bör använda HTTPS:
   
     https://[sitedomain]/odata/[companyname]
   
   Företagets namn är bara obligatoriskt om du har en distribution till flera företag. Mer information om hur du hittar den här parametern i ditt Acumatica-konto finns nedan.
   
   ![](media/service-connect-to-acumatica/parameters.png)
5. Som autentiseringsmetod väljer du **Basic**. Ange ditt användarnamn och lösenord från ditt Acumatica-konto och klicka sedan på **logga In**.
   
    ![](media/service-connect-to-acumatica/creds2.png)
6. När Power BI har importerat dessa data, visas en ny instrumentpanel, rapport och datauppsättning i det vänstra navigeringsfönstret. Nya objekt markeras med en gul asterisk \* som försvinner när de valts, om du väljer intrumentpanelen så visas en layout som liknar den nedan:
   
    ![](media/service-connect-to-acumatica/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning är schemalagd för att uppdateras dagligen, kan du ändra uppdateringsschemat eller försöka uppdatera den på begäran med **Uppdatera nu**.

## <a name="system-requirements"></a>Systemkrav
Det här Innehållspaketet kräver Acumatica v5.2 eller högre, bekräfta versionen med din Acumatica-administratör.

## <a name="finding-parameters"></a>Hitta parametrar
**Acumatica OData-slutpunkt**

Acumatica OData-slutpunkten är formaterad på följande sätt och bör använda HTTPS:

    https://[sitedomain]/odata/[companyname]

Programmets webbplatsdomän finns i webbläsarens adressfält när du har loggat in på Acumatica. I exemplet nedan är webbplatsdomänen ”https://pbi.acumatica.com, så OData-slutpunkten att ange skulle vara ”https://pbi.acumatica.com/odata”.

 ![](media/service-connect-to-acumatica/url.png)

Företagets namn är bara obligatoriskt om du har en distribution till flera företag. Du hittar den här informationen från din Acumatica-inloggningssida.

![](media/service-connect-to-acumatica/signin2.png)

## <a name="troubleshooting"></a>Felsökning
Om du inte kan logga in, verifierar du att Acumatica OData-slutpunkten som du angav är korrekt formaterad.

    https://<application site domain>/odata/<company name>

Om du har problem med att ansluta, bekräftar du din version av Acumatica med din administratör. Det här innehållspaketet kräver version 5.2 eller senare.

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

