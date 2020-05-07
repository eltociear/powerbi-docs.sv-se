---
title: Kapacitet och SKU:er i inbäddad Power BI-analys
description: Förstå kapacitet och SKU:er i inbäddad Power BI-analys.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: 27d6ddd9b24e09805bd22150a22347e5cd93c8e0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79492846"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Kapacitet och SKU:er i inbäddad Power BI-analys

När du flyttar till produktion behövs en dedikerad kapacitet för publicering av inbäddat Power BI-innehåll och inbäddad Power BI-analys (SKU *A*, *EM* eller *P*).

Kapacitet är en dedikerad uppsättning resurser reserverade för exklusiv användning. Den gör att du kan publicera instrumentpaneler, rapporter och datamängder för användare utan att behöva köpa några licenser per användare. Den gör även att du får pålitlig och konsekvent prestanda för ditt innehåll.

>[!NOTE]
>Du behöver ett Power BI Pro-konto för att kunna publicera.

## <a name="what-is-embedded-analytics"></a>Vad är inbäddad analys?

Det finns två lösningar för inbäddad Power BI-analys:
* *Power BI Embedded* – ett Azure-erbjudande
* Inbäddning av Power BI som en del av *Power BI Premium* – ett Office-erbjudande

### <a name="power-bi-embedded"></a>Power BI Embedded

Power BI Embedded är avsett för ISV:er och utvecklare som vill bädda in visuella objekt i sina appar.

I appar med Power BI Embedded kan användarna interagera med innehåll i en Power BI Embedded-kapacitet.

### <a name="power-bi-premium"></a>Power BI Premium

[Power BI Premium](../../service-premium-what-is.md) är avsett för företag som behöver en komplett BI-lösning med en enhetlig översikt över organisationen, partners, kunder och leverantörer.

Power BI Premium är en SaaS-produkt där användarna interagerar med innehåll via mobilappar, internt utvecklade appar eller via Power BI-portalen (Power BI-tjänsten). Power BI Premium är därmed en lösning som passar både interna appar och kundorienterade externa appar.

## <a name="capacity-and-skus"></a>Kapacitet och SKU:er

Varje kapacitet har ett urval av SKU:er och varje SKU tillhandahåller olika resursnivåer gällande minne och beräkningskraft. Vilken typ av SKU du behöver beror på vilken typ av lösning du vill distribuera.

Information om vilka arbetsbelastningar som stöds för varje nivå finns i artikeln [Konfigurera arbetsbelastningar i en Premium-kapacitet](../../service-admin-premium-workloads.md)

Använd följande länkar när du planerar och testar din kapacitet:
* [Kapacitetsplanering](embedded-capacity-planning.md)
* [Testningsmetoder](../../service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>SKU:er för Power BI Embedded

Power BI Embedded levereras med en [*a*-SKU](../../service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios).

### <a name="power-bi-premium-skus"></a>SKU:er för Power BI Premium

Det finns två SKU:er för Power BI Premium, *P* och *EM*.
* [Förstå skillnaderna mellan SKU:erna *P* och *EM* ](../../service-premium-what-is.md#subscriptions-and-licensing)
* [Köp en Premium-SKU](../../service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>Vilken SKU ska jag använda?

I den här tabellen ges en sammanfattning av funktioner, vilken kapacitet som behövs för dem och den specifika SKU:n för var och en. 

</br>
<table>
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<tbody>
<tr>
<td style="text-align: center"; colspan="2"><p><b>Funktion</b></p></td>
<td style="text-align: center">
<p><b>Power BI Embedded</b></p>
</td>
<td style="text-align: center"; colspan="2">
<p><b>Power BI Premium</b></p>
</td>
</tr>
<tr>
<td><p><em>Vad förbrukas?</em><p></td>
<td><p><em>Vad är det som förbrukar?</em><p></td>
<td style="text-align: center"><p><em>A-SKU:er</br>(Azure)</em></p></td>
<td style="text-align: center"><p><em>EM-SKU:er</br>(Office)</em></p></td>
<td style="text-align: center"><p><em>P-SKU:er</br>(Office)</em></p></td>
</tr>
<tr>
<td>Bädda in artefakter från en Power BI-arbetsyta</td>
<td>
</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="2">Power BI-rapporter</td>
<td>En inbäddad app i organisationen</br>(användaren äger data)</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>En inbäddad app för dina kunder</br>(appen äger data)</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="3">Power BI-innehåll<br>(med en kostnadsfri Power BI-licens)</td>
<td>Power BI-tjänst</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Power BI mobilt</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>MS Office-appar</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
</tbody>
</table>

### <a name="capacity-considerations"></a>Överväganden för kapaciteter

I tabellen nedan ser du information om betalning och användning per kapacitet.

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>Power BI Embedded</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI Premium</strong></p></td>
</tr>
<tr>
<td><p><strong>Erbjudande</strong></p></td>
<td style="text-align: center;"><p>Azure</p></td>
<td style="text-align: center;" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center;"><p>A</p></td>
<td style="text-align: center;"><p>EM</p></td>
<td style="text-align: center;"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Billing</strong></td>
<td style="text-align: center;">Varje timma</td>
<td style="text-align: center;">Varje månad</td>
<td style="text-align: center;">Varje månad</td>
</tr>
<tr>
<td><p><strong>Bindningstid</strong></td>
<td style="text-align: center;">None</td>
<td style="text-align: center;">Varje år</td>
<td style="text-align: center;">Per månad eller år</td>
</tr>
<tr>
<td valign="top"><p><strong>Användning</strong></td>
<td style="text-align: center;">Azure-resurser kan:</br>- <a href="azure-pbie-scale-capacity.md">Skalas upp eller ned</a></br>- <a href="azure-pbie-pause-start.md">Pausas och återupptas</a>
</td>
<td style="text-align: center;">Bädda in i appar och i</br> Microsoft-program</td>
<td style="text-align: center;">Bädda in i appar och i</br> Power BI-tjänsten</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>Minne och beräkningskraft för SKU:er

I tabellen nedan beskrivs resurser och begränsningar för respektive SKU.

| Kapacitetsnoder | Totalt antal virtuella kärnor | Virtuella kärnor för serverdel | RAM (GB) | Virtuella kärnor för klientdel | DirectQuery/Live Connection (per sek) | Modellens uppdateringsparallellitet |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

## <a name="next-steps"></a>Nästa steg

> [!div class="nextstepaction"]
>[Bädda in för dina kunder](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Bädda in för din organisation](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Bädda in från appar](embed-from-apps.md)