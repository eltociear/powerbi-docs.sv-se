---
title: Hitta Power BI-användare som har loggat in
description: Om du är en klientadministratör och vill se vem som har signerat till Power BI, kan du använda Azure Active Directory-rapporter för åtkomst och användning för att få insyn.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/31/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 26cf9b10d2a7bfffca151fe36cd45626487b6eef
ms.sourcegitcommit: 20ae9e9ffab6328f575833be691073de2061a64d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58383656"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Hitta Power BI-användare som har loggat in

Om du är en klientadministratör och vill se vem som har signerat till Power BI, kan du använda [Azure Active Directory-rapporter för åtkomst](/azure/active-directory/reports-monitoring/concept-sign-ins) och användning för att få insyn.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Den här aktivitetsrapporten tillhandahåller användbar information men anger inte vilken typ av licens varje användare har. Använd administrationscentret för Microsoft 365 för att visa licenser.

## <a name="requirements"></a>Krav

Alla användare (inklusive icke-administratörer) kan visa en rapport med egna inloggningar men du måste uppfylla följande krav för att visa en rapport för alla användare.

* Din klient måste ha en associerad Azure AD Premium-licens.

* Du måste ha någon av följande roller: Global administratör, Säkerhetsadministratör eller Säkerhetsläsare.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Använda Azure Portal för att visa inloggningar

Följ dessa steg om du vill visa en inloggningsaktivitet.

1. Välj **Azure Active Directory** i **Azure-portalen**.

1. Under **Övervakning** väljer du **Inloggningar**.
   
    ![Azure AD-inloggningar](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtrera programmet efter antingen **Microsoft Power BI** eller **Power BI Gateway** och välj **Tillämpa**.

    **Microsoft Power BI** avser inloggningsaktivitet som är relaterad till tjänsten medan **Power BI Gateway** filtrerar särskilda inloggningar för den lokala datagatewayen.
   
    ![Filtrera inloggningar](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exportera data

Du har två alternativ för att exportera data för inloggning: hämta en csv-fil eller använd PowerShell. Längst ned på rapporten väljer du något av följande alternativ:

* **Hämta** för att hämta csv-filen för data med det aktuella filtret.

* **Skript** för att hämta ett PowerShell-skript för data med det aktuella filtret. Du kan uppdatera filtret i skriptet efter behov.

![Ladda ned en csv-fil eller ett skript](media/service-admin-access-usage/download-sign-in-data-csv.png)

## <a name="data-retention"></a>Datakvarhållning

Inloggningsdata kan hållas kvar i upp till 30 dagar. Mer information finns i [Rapportkvarhållningsregler i Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Nästa steg

[Använda granskning i din organisation](service-admin-auditing.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

