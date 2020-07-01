---
title: Hitta Power BI-användare som har loggat in
description: Om du är klientorganisationsadministratör och vill se vem som har loggat in på Power BI kan du använda Azure Active Directory-rapporter för åtkomst och användning för att få insyn.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 4f9b69e863b71fda0cece06df7065740bd55463e
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85228893"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Hitta Power BI-användare som har loggat in

Om du är klientorganisationsadministratör och vill se vem som har loggat in på Power BI använder du [Azure Active Directory-rapporter för åtkomst och användning](/azure/active-directory/reports-monitoring/concept-sign-ins) för att få insyn.

> [!NOTE]
> **Inloggningsrapporten** ger användbar information men anger inte vilken typ av licens varje användare har. Använd administrationscentret för Microsoft 365 för att visa licenser.

## <a name="requirements"></a>Krav

Alla användare (inklusive icke-administratörer) kan visa en rapport med egna inloggningar men du måste uppfylla följande krav för att visa en rapport för alla användare.

* Din klientorganisation måste ha en associerad Azure Active Directory Premium-licens.

* Du måste vara i någon av följande roller: global administratör, säkerhetsadministratör eller säkerhetsläsare.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Använda Azure Portal för att visa inloggningar

Följ dessa steg om du vill visa en inloggningsaktivitet.

1. Välj **Azure Active Directory** i **Azure-portalen**.

1. Under **Övervakning** väljer du **Inloggningar**.
   
    ![Skärmbild av Azure-gränssnittet med Azure Active Directory och inloggningsalternativen markerade.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtrera programmet efter antingen **Microsoft Power BI** eller **Power BI Gateway** och välj **Tillämpa**.

    **Microsoft Power BI** filtrerar på inloggningsaktivitet som är relaterad till tjänsten medan **Power BI Gateway** filtrerar på aktivitet som är specifika för den lokala datagatewayen.
   
    ![Skärmbild av inloggningsfiltret med fältet Program markerat.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exportera data

Du kan [Ladda ned en inloggningsrapport](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) i som en CSV-fil eller en JSON-fil.

![Skärmbild av nedladdningsknappen.](media/service-admin-access-usage/download-sign-in-data-csv.png)

Längst upp på sidan **Inloggningar** väljer du **Ladda ned** och väljer sedan något av följande alternativ:

* **CSV** för att ladda ned en CSV-fil för aktuella filtrerade data.

* **JSON** för att ladda ned en JSON-fil för aktuella filtrerade data.

## <a name="data-retention"></a>Datakvarhållning

Inloggningsdata kan hållas kvar i upp till 30 dagar. Mer information finns i [Rapportkvarhållningsregler i Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Nästa steg

[Använda granskning i din organisation](service-admin-auditing.md)

Fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)