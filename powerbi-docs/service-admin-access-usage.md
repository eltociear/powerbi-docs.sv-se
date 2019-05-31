---
title: Hitta Power BI-användare som har loggat in
description: Om du är en Innehavaradministratör och vill se vem som har signerat till Power BI, kan du kan använda Azure Active Directory-rapporter för åtkomst och användning för att få insyn.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: e513607dd89aee15f10145cf62bd461621cc12c0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906685"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Hitta Power BI-användare som har loggat in

Om du är en klientadministratör och vill se vem som har signerat till Power BI, Använd den [rapporter för åtkomst och användning av Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) insyn.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Den **inloggningar** rapporten innehåller användbar information, men den inte kan hitta typ av licens som varje användare har. Använd administrationscentret för Microsoft 365 för att visa licenser.

## <a name="requirements"></a>Krav

Alla användare (inklusive icke-administratörer) kan visa en rapport med egna inloggningar men du måste uppfylla följande krav för att visa en rapport för alla användare.

* Din klient måste ha en associerad med den Azure Active Directory Premium-licens.

* Du måste ha någon av följande roller: Global administratör, Säkerhetsadministratör eller Säkerhetsläsare.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Använda Azure Portal för att visa inloggningar

Följ dessa steg om du vill visa en inloggningsaktivitet.

1. Välj **Azure Active Directory** i **Azure-portalen**.

1. Under **Övervakning** väljer du **Inloggningar**.
   
    ![Skärmbild av Gränssnittet i Azure med Azure Active Directory och inloggningar alternativ som markerats.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtrera programmet efter antingen **Microsoft Power BI** eller **Power BI Gateway** och välj **Tillämpa**.

    **Microsoft Power BI** filter för att inloggningsaktivitet som är relaterad till tjänsten, medan **Power BI Gateway** filter för att inloggningsaktivitet specifika till den lokala datagatewayen.
   
    ![Skärmbild av inloggningar filtret med program-fältet markerat.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exportera data

Du kan [ladda ned en rapport för inloggning](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) i något av två format: en CSV-fil eller en JSON-fil.

![Skärmbild av knappen ladda ned.](media/service-admin-access-usage/download-sign-in-data-csv.png)

Överst på den **inloggningar** rapporten, Välj **hämta** och välj sedan något av följande alternativ:

* **CSV** att hämta en CSV-fil för filtrerade data.

* **JSON** att hämta en JSON-fil för filtrerade data.

## <a name="data-retention"></a>Datakvarhållning

Inloggningsdata kan hållas kvar i upp till 30 dagar. Mer information finns i [rapportkvarhållningsregler i Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Nästa steg

[Använda granskning i din organisation](service-admin-auditing.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)