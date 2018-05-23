---
title: Hitta Power BI-användare som har loggat in
description: Om du är en klientadministratör och vill se vem som har signerat till Power BI, kan du använda Azure Active Directory-rapporter för åtkomst och användning för att få insyn.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 1f482cf9e3f0cf344a2808ca778839a50d851ac7
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Hitta Power BI-användare som har loggat in
Om du är en klientadministratör och vill se vem som har signerat till Power BI, kan du använda Azure Active Directory-rapporter för åtkomst och användning för att få insyn.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

Du kan komma åt aktivitetsrapporten inom de [nya](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-activity-sign-ins) och [klassiska](https://docs.microsoft.com/azure/active-directory/active-directory-view-access-usage-reports) portalerna för Azure Active Directory (Azure AD). Medan den ovanstående videon använder den klassiska portalen som exempel kommer den här artikeln att fokusera på den nya.

> [!NOTE]
> Den här aktivitetsrapporten omfattar både Power BI- (Free) och Pro-användare men gör ingen åtskillnad på dem baserat på deras licens.
> 
> 

## <a name="requirements"></a>Krav
Följande är krav för att visa inloggningsaktivitetsrapporten.

* Användare i rollerna Global administratör, Säkerhetsadministratör eller Säkerhetsläsare har åtkomst till data.
* Alla användare (icke-administratörer) kan komma åt sina egna inloggningar.
* Din klient måste ha en associerad Azure AD Premium-licens för att se hela inloggningsrapporten.

## <a name="using-the-azure-portal-to-view-sign-ins"></a>Använda Azure Portal för att visa inloggningar
Du kan använda Azure AD-portalen för att visa inloggningsaktivitet.

1. Bläddra till **Azure Portal** och välj **Azure Active Directory**.
2. Under **Aktivitet** väljer du **Inloggningar**.
   
    ![](media/service-admin-access-usage/azure-portal-sign-ins.png)
3. Filtrera programmet efter antingen **Microsoft Power BI** eller **Power BI Gateway** och välj **Tillämpa**.
   
    **Microsoft Power BI** avser inloggningsaktivitet som är relaterad till tjänsten medan **Power BI Gateway** är särskilda inloggningar för den lokala datagatewayen.
   
    ![](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exportera data
Du har två alternativ för att exportera data för inloggning. Du antingen ladda ner en csv-fil eller använda PowerShell.

### <a name="download-csv"></a>Hämta csv-fil
Välj **Hämta** i verktygsfältet på skärmen Aktivitet. Nu hämtas csv-filen för data med det aktuella filtret.

![](media/service-admin-access-usage/download-sign-in-data-csv.png)

### <a name="powershell"></a>PowerShell
Du kan använda PowerShell för att exportera inloggningsdata. En [exempel](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-api-sign-in-activity-samples#powershell-script) är tillgängligt i Azure AD-dokumentationen.

> [!NOTE]
> För att PowerShell-exemplet ska fungera måste du följa [kraven för att få åtkomst till rapporterings-API för Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-reporting-api-prerequisites).
> 
> 

## <a name="data-retention"></a>Datakvarhållning
Inloggningsdata kan hållas kvar i upp till 30 dagar. Mer information finns i [Rapportkvarhållningsregler i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-retention).

## <a name="next-steps"></a>Nästa steg
[Inloggningsaktivitetrapporter i Azure Active Directory-portalen (nya portalen)](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-activity-sign-ins)  
[Visa åtkomst och användning (klassisk portal)](https://docs.microsoft.com/azure/active-directory/active-directory-view-access-usage-reports#view-or-download-a-report)  
[Inloggningsexempel med PowerShell-skript](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-api-sign-in-activity-samples#powershell-script)  
[Rapportkvarhållningsregler i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-retention)  
[Använda granskning i din organisation](service-admin-auditing.md)  
[Aktivering av utökad Pro-utvärderingsversion](service-extended-pro-trial.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

