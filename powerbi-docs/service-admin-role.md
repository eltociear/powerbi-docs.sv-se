---
title: Förstå Power BI-administratörsrollen
description: Så här konfigurerar du säkerhet på radnivå för importerade datauppsättningar och DirectQuery i Power BI-tjänsten.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 09/05/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: a20b6312f031452508c986565e27090fabbae019
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34293822"
---
# <a name="understanding-the-power-bi-admin-role"></a>Förstå Power BI-administratörsrollen
Lär dig hur du kan använda Power BI-administratörsrollen i din organisation.

<iframe width="640" height="360" src="https://www.youtube.com/embed/PQRbdJgEm3k?showinfo=0" frameborder="0" allowfullscreen></iframe>

Power BI-administratörsrollen kan tilldelas användare som ska ha åtkomst till Power BI-administratörsportalen utan att även ge dem annan administrativ Office 365-åtkomst. Ett exempel är rollen som global administratör. Den är avsedd för dem som har i uppgift att administrera Power BI för sin organisation.

Administratörer för Office 365-användare kan tilldela användare rollen som Power BI-administratör i administrationscentret för Office 365 eller via PowerShell-skript. När en användare har utsetts får denne åtkomst till [Power BI-administratörsportalen](service-admin-portal.md). Där får de åtkomst till användningsstatistik för hela klienten och kan styra den klientomfattande användningen av Power BI-funktionerna.

![](media/service-admin-role/powerbi-admin-portal.png)

## <a name="using-the-office-365-admin-center-to-assign-a-role"></a>Använda administrationscentret för Office 365 för att tilldela en roll
Du kan göra följande för att tilldela användare rollen som Power BI-administratör i administrationscentret för Office 365.

1. Bläddra till administrationscentret för Office 365 och välj **Användare** > **Aktiva användare**.
   
    ![](media/service-admin-role/powerbi-admin-users.png)
2. Välj den användare som du vill tilldela rollen.
3. Välj **Redigera** för roller.
   
    ![](media/service-admin-role/powerbi-admin-edit-roles.png)
4. Välj **Customized administrator (Anpassad administratör)** > **Power BI-tjänstadministratör**
   
    ![](media/service-admin-role/powerbi-admin-role.png)
5. Välj **Spara**.

Du bör se **Power BI-tjänstadministratör** som användarens roll i listan. Nu har han eller hon åtkomst till [Power BI-administratörsportalen](service-admin-portal.md).

![](media/service-admin-role/powerbi-admin-role-set.png)

## <a name="using-powershell-to-assign-a-role"></a>Använda PowerShell för att tilldela en roll
Du måste ha Azure Active Directory PowerShell-modulen installerad för att kunna köra PowerShell-kommandot.

### <a name="download-azure-ad-powershell-module"></a>Hämta Azure AD PowerShell-modulen
[Hämta Azure Active Directory PowerShell, version 2](https://github.com/Azure/azure-docs-powershell-azuread/blob/master/Azure%20AD%20Cmdlets/AzureAD/index.md)

[Hämta Azure Active Directory PowerShell, version 1.1.166.0 GA](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185)

### <a name="command-to-add-role-to-member"></a>Kommando för att lägga till roll till medlem
**Azure AD PowerShell v2-kommando**

Du måste hämta **ObjectId** för rollen **Power BI-tjänstadministratör**. Du kan köra [Get-AzureADDirectoryRole](https://docs.microsoft.com/powershell/azuread/v2/get-azureaddirectoryrole) för att hämta **ObjectId**

```
PS C:\Windows\system32> Get-AzureADDirectoryRole

ObjectId                             DisplayName                        Description
--------                             -----------                        -----------
00f79122-c45d-436d-8d4a-2c0c6ca246bf Power BI Service Administrator     Full access in the Power BI Service.
250d1222-4bc0-4b4b-8466-5d5765d14af9 Helpdesk Administrator             Helpdesk Administrator has access to perform..
3ddec257-efdc-423d-9d24-b7cf29e0c86b Directory Synchronization Accounts Directory Synchronization Accounts
50daa576-896c-4bf3-a84e-1d9d1875c7a7 Company Administrator              Company Administrator role has full access t..
6a452384-6eb9-4793-8782-f4e7313b4dfd Device Administrators              Device Administrators
9900b7db-35d9-4e56-a8e3-c5026cac3a11 AdHoc License Administrator        Allows access manage AdHoc license.
a3631cce-16ce-47a3-bbe1-79b9774a0570 Directory Readers                  Allows access to various read only tasks in ..
f727e2f3-0829-41a7-8c5c-5af83c37f57b Email Verified User Creator        Allows creation of new email verified users.
```

I det här fallet är ObjectId för rollen 00f79122-c45d-436d-8d4a-2c0c6ca246b.

Du behöver också känna till användarnas **ObjectID**. Du kan hitta det genom att köra [Get-AzureADUser](https://docs.microsoft.com/powershell/azuread/v2/get-azureaduser).

```
PS C:\Windows\system32> Get-AzureADUser -SearchString 'tim@contoso.com'

ObjectId                             DisplayName UserPrincipalName      UserType
--------                             ----------- -----------------      --------
6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c Tim         tim@contoso.com        Member
```

Om du vill lägga till medlemmen för rollen kör du [Add-AzureADDirectoryRoleMember](https://docs.microsoft.com/powershell/azuread/v2/add-azureaddirectoryrolemember).

| Parameter | Beskrivning |
| --- | --- |
| ObjectId |Rollens ObjectId. |
| RefObjectId |Medlemmarnas ObjectId. |

```
Add-AzureADDirectoryRoleMember -ObjectId 00f79122-c45d-436d-8d4a-2c0c6ca246bf -RefObjectId 6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c
```

**Azure AD PowerShell v1-kommando**

Om du vill lägga till en medlem till en roll med hjälp av Azure AD v1-cmdletar ska du köra kommandot [Add-MsolRoleMember](https://docs.microsoft.com/powershell/msonline/v1/add-msolrolemember).

```
Add-MsolRoleMember -RoleMemberEmailAddress "tim@contoso.com" -RoleName "Power BI Service Administrator"
```

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
Rollen Power BI-tjänstadministratör ger inte åtkomst till följande.

* Möjlighet att ändra användare och licenser i administrationscentret för Office 365
* Åtkomst till granskningsloggarna. Mer information finns i [Använda granskning i din organisation](service-admin-auditing.md).

## <a name="next-steps"></a>Nästa steg
[Power BI-administratörsportalen](service-admin-portal.md)  
[Add-AzureADDirectoryRoleMember](https://docs.microsoft.com/powershell/azuread/v2/add-azureaddirectoryrolemember)  
[Add-MsolRoleMember](https://docs.microsoft.com/powershell/msonline/v1/add-msolrolemember)  
[Granska Power BI i din organisation](service-admin-auditing.md)  
[Administrera Power BI i din organisation](service-admin-administering-power-bi-in-your-organization.md)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

