---
title: Hitta Power BI-användare som har loggat in
description: Om du är klientorganisationsadministratör och vill se vem som har loggat in på Power BI kan du använda Azure Active Directory-rapporter för åtkomst och användning för att få insyn.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 8b1ebbfc323698ed8ab092b8396ef22e4199720e
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71075866"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Hitta Power BI-användare som har loggat in

Om du är klientorganisationsadministratör och vill se vem som har loggat in på Power BI använder du [Azure Active Directory-rapporter för åtkomst och användning](/azure/active-directory/reports-monitoring/concept-sign-ins) för att få insyn.

> [!NOTE]
> **Inloggningsrapporten** ger användbar information men anger inte vilken typ av licens varje användare har. Använd administrationscentret för Microsoft 365 för att visa licenser.

## <a name="requirements"></a>Krav

Alla användare (inklusive icke-administratörer) kan visa en rapport med egna inloggningar men du måste uppfylla följande krav för att visa en rapport för alla användare.

* Din klientorganisation måste ha en associerad Azure Active Directory Premium-licens.

* Du måste ha någon av följande roller: Global administratör, Säkerhetsadministratör eller Säkerhetsläsare.

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

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)