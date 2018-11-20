---
title: Administrera Power BI – Vanliga frågor och svar
description: Få reda på svaren på vanliga frågor om Power BI-registrering, hantering av klientorganisationer och andra administrativa uppgifter.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 4379caf909360688e602601795066f51c9660633
ms.sourcegitcommit: 46f1ba3f972f6e64bce05ad0fd527b27c49aedd6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52157090"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Administrera Power BI – Vanliga frågor och svar

Den här artikeln tar upp vanliga frågor och svar för Power BI-administration. En översikt över Power BI-administration finns i [vad är Power BI-administration?](service-admin-administering-power-bi-in-your-organization.md).

## <a name="whats-in-this-article"></a>Innehåll i artikeln

### <a name="sign-up-for-power-bi-section"></a>Avsnittet registrera dig för Power BI

* [Använda PowerShell](#using-powershell)
* [Hur registrerar sig användare för Power BI?](#how-do-users-sign-up-for-power-bi)
* [Hur registrerar sig enskilda användare i organisationen?](#how-do-individual-users-in-my-organization-sign-up)
* [Hur kan jag förhindra användare från att ansluta till min befintliga Office 365-klient?](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [Hur kan jag låta användare att ansluta till min befintliga Office 365-klient?](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [Hur bekräftar jag om klienten är blockerad?](#how-do-i-verify-if-i-have-the-block-on-in-the-tenant)
* [Hur förhindrar jag att mina befintliga användare börjar använda Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Hur låter jag mina befintliga användare registrera dig för Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Avsnittet administration av Power BI

* [Hur kommer detta att ändra hur jag hanterar identiteter för användare i min organisation idag?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Hur hanterar vi Power BI?](#how-do-we-manage-power-bi)
* [Hur hanterar jag en klient som skapas av Microsoft för mina användare?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Om jag har flera domäner, kan jag styra vilken Office 365-klient som användare läggs till?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to)
* [Hur tar jag bort Power BI för användare som redan har registrerat sig?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Hur vet jag när nya användare har anslutit sig min klient?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Bör jag vara medveten om några andra förberedelser?](#are-there-any-additional-things-i-should-be-prepared-for)
* [Var finns min Power BI-klient?](#where-is-my-power-bi-tenant-located)
* [Vad är Power BI SLA (serviceavtal)?](#what-is-the-power-bi-sla)

### <a name="security-in-power-bi-section"></a>Avsnittet säkerhet i Power BI

* [Uppfyller Power BI nationella, regionala och branschspecifika efterlevnadskrav?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Hur fungerar säkerheten i Power BI?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Registrera dig för Power BI

### <a name="using-powershell"></a>Använda PowerShell

Vissa av procedurerna i det här avsnittet kräver Windows PowerShell-skript. Om du inte är bekant med PowerShell, rekommenderar vi [guiden Kom igång med PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=286814). För att köra skripten ska du först installera den senaste 64-bitarsversionen av [Azure Active Directory PowerShell för Graph](/powershell/azure/active-directory/).

### <a name="how-do-users-sign-up-for-power-bi"></a>Hur registrerar sig användare för Power BI?

Som administratör kan du registrera dig för Power BI via [Power BI-webbplatsen](https://powerbi.microsoft.com) eller [Köptjänster](https://admin.microsoft.com/AdminPortal/Home#/catalog) på administrationscentret för Office 365. När en administratör loggar på Power BI kan de tilldela användarlicenser till användare som ska ha åtkomst.

Dessutom kan enskilda användare i din organisation kanske registrera sig för Power BI via [Power BI-webbplatsen](https://powerbi.microsoft.com). När en användare i din organisation registrerar sig för Power BI, tilldelas som användaren en licens för Power BI automatiskt. Mer information finns i [Registrera dig för Power BI som individ](service-self-service-signup-for-power-bi.md) och [Power BI-licensiering i din organisation](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Hur registrerar sig enskilda användare i organisationen?

Det finns tre scenarier som kan gälla för användare i organisationen:

* **Scenario 1**: Din organisation redan har en befintlig Office 365-miljö och användaren som registrerar sig för Power BI har redan ett Office 365-konto.
    I det här scenariot, om en användare redan har ett arbets- eller skolkonto i klienten (t.ex, contoso.com) men inte Power BI kommer Microsoft att aktiveras prenumerationen för det kontot,och användaren får automatiskt ett meddelande om hur de kan använda Power BI-tjänsten.

* **Scenario 2**: Din organisation redan har en befintlig Office 365-miljö men användaren som registrerar sig för Power BI har inte ett Office 365-konto.
    Användaren har en e-postadress i organisationens domän (till exempel contoso.com) i men har ännu inte något Office 365-konto. I detta fall kan användaren registrera sig för Power BI och får ett konto automatiskt. På så sätt får användaren åtkomst till Power BI-tjänsten. Till exempel om medarbetaren Nancy använder sin arbets-e-postadress (till exempel nancy@contoso.com) för att registrera sig lägger Microsoft automatiskt till Nancy som en användare i Contosos miljö i Office 365 och aktiverar Power BI för det kontot.

* **Scenario 3**: Din organisation inte har en Office 365-miljö som är ansluten till din e-domän.
    Det finns inga administrativa åtgärder som din organisation behöver vidta för att dra nytta av Power BI. Användare läggs till i en ny, endast molnbaserad användarkatalog och du har möjlighet att ta över som administratör och hantera dem.

> [!IMPORTANT]
> Om din organisation har flera e-postdomäner och du vill att alla e-postadresstillägg ska vara i samma klient kan du lägga till alla e-postdomäner i en Azure Active Directory-klient innan användarna registrerar sig. Det finns ingen automatisk mekanism för att flytta användare över klienter när de väl har skapats. Mer information om den här processen finns i [Om jag har flera domäner, kan jag styra Office 365-klienten som användare läggs till? i](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to) senare i den här artikeln och [Lägga till en domän i Office 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>Hur kan jag förhindra användare från att ansluta till min befintliga Office 365-klient?

Det finns steg som du kan ta som administratör för att hindra användare från att ansluta till din befintliga Office 365-klient. Om du blockerar åtkomst kommer användarnas försök att registrera sig att misslyckas och de kommer att omdirigeras till att kontakta administratören för deras organisation. Du behöver inte upprepa den här proceduren om du redan har inaktiverat licensen för automatisk distribution (t.ex. via Office 365 för utbildning för studenter, lärare och övrig personal).

Använd följande PowerShell-skript för att förhindra att nya användare ansluter till en hanterad klient. [Lär dig mer om PowerShell](#basic-powershell-information)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> Den här blockeringen förhindrar att nya användare i din organisation registrerar sig för Power BI. Användare som registrerar sig för Power BI innan du inaktiverar nya registreringar för din organisation, behåller sina licenser. Om du vill ta bort en användare, se [Hur tar jag bort Power BI för användare som redan har registrerat sig?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) senare i den här artikeln.

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>Hur kan jag låta användare att ansluta till min befintliga Office 365-klient?

Använd följande PowerShell-skript för att låta nya användare ansluta till en hanterad klient. [Lär dig mer om PowerShell](#basic-powershell-information)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>Hur bekräftar jag om klienten är blockerad?

Kör följande PowerShell-skript för att verifiera inställningarna. *AllowEmailVerifiedUsers* bör vara false. [Lär dig mer om PowerShell](#basic-powershell-information)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Hur förhindrar jag att mina befintliga användare börjar använda Power BI?

Azure AD-inställningen som styr detta är **AllowAdHocSubscriptions**. De flesta klienter har inställningen inställd till sant, vilket innebär att den är aktiverad. Om du har köpt Power BI via en partner kan detta vara inställt på false, vilket innebär att det är inaktiverat.

Använd följande PowerShell-skript för att inaktivera ad hoc-prenumerationer. [Lär dig mer om PowerShell](#basic-powershell-information)

1. Logga in på Azure Active Directory med dina Office 365-autentiseringsuppgifter. Den första raden i följande PowerShell-skript uppmanar dig att ange dina autentiseringsuppgifter. Den andra raden ansluter till Azure Active Directory.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Inloggning i Azure Active Directory](media/service-admin-licensing-organization/aad-signin.png)

1. När du har loggat in kan du köra följande kommando för att se hur din klient är konfigurerad.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```
1. Kör det här kommandot för att aktivera ($true) eller inaktivera ($false) **AllowAdHocSubscriptions**.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Flaggan AllowAdHocSubscriptions används för att styra flera användarfunktioner i organisationen, inklusive möjligheten för användare att registrera sig för Azure Rights Management-tjänsten. Om du ändrar flaggan påverkas alla dessa funktioner.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Hur låter jag mina befintliga användare registrera dig för Power BI?

Kör kommandot i ovanstående fråga för att låta befintliga användare registrera sig för Power BI men skicka värdet true i stället för false i det sista steget.

## <a name="administration-of-power-bi"></a>Administration av Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Hur kommer detta för att ändra hur jag hanterar identiteter för användare i min organisation idag?

Det finns tre scenarier som kan gälla för användare i organisationen:

* **Scenario 1**: Om din organisation redan har en befintlig miljö i Office 365 och alla användare i organisationen har ett Office 365-konto ändras inte identitetshanteringen.

* **Scenario 2**: Om din organisation redan har en befintlig miljö i Office 365, men alla användare i organisationen inte har Office 365-konton skapar vi en användare på klienten och tilldelar licenser utifrån användarens e-post för skola eller arbete.

    Det innebär att antalet användare som du hanterar när som helst viss kan växa efter hand som användare i din organisation registrerar sig för tjänsten.

* **Scenario 3**: Om din organisation inte har en Office 365-miljö som är ansluten till din e-domän sker det ingen ändring i hur du hanterar identiteter.

    Användare läggs till i en ny, endast molnbaserad användarkatalog och du har möjlighet att ta över som administratör och hantera dem.

### <a name="how-do-we-manage-power-bi"></a>Hur hanterar vi Power BI?

Power BI har en administratörsportal där du kan visa användarstatistik med länkar till administrationscentret för Office 365 för att hantera användare och grupper samt möjlighet att styra inställningarna för hela klienten.

Ditt konto måste vara markerat som **Global administratör** i Office 365 eller Azure Active Directory, eller ha tilldelats administratörsrollen för Power BI-tjänsten, för att ha åtkomst till Power BI-administratörsportalen. Läs mer i [Förstå administratörsrollen för Power BI](service-admin-role.md) och [Power BI-administratörsportalen](service-admin-portal.md).

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Hur hanterar jag en klient som skapas av Microsoft för mina användare?

Om en klient har skapats av Microsoft kan du göra anspråk på och hantera som klienten med följande steg:

1. Anslut klienten genom att registrera dig för Power BI med en e-postadress som matchar klient-domänen som du vill hantera. Till exempel om Microsoft har skapat klienten contoso.com ska du ansluta till klienten med en e-postadress som slutar med @contoso.com.

1. Gör anspråk administratörsrättigheter genom att verifiera att du äger domänen: när du har loggat in på klienten kan du ge dig till rollen som *global administratör* genom att verifiera att du äger domänen. Följ stegen nedan i [Office 365-dokumentation](/office365/admin/misc/become-the-admin).

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to"></a>Om jag har flera domäner, kan jag styra vilken Office 365-klient som användare läggs till?

Om du inte gör något skapas en klient för varje användares e-postdomäner och underdomäner. Om du vill att alla användare ska vara i samma klient oavsett deras e-postadresstillägg: Skapa en målklient i förväg eller använd en befintlig klient och lägg till alla befintliga domäner och underdomäner som ska konsolideras i klienten. Alla användare med e-postadresser som slutar på dessa domäner och underdomäner ansluts automatiskt till målklienten när de registreras.

> [!IMPORTANT]
> Det finns ingen automatisk mekanism för att flytta användare över klienter när de väl har skapats. Mer information om att lägga till domäner i en enda Office 365-klient, finns i [Lägga till användare och domän i Office 365](/office365/admin/setup/add-domain/).

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Hur tar jag bort Power BI för användare som redan har registrerat sig?

Om en användare har registrerat dig för Power BI, men du inte längre vill att hen ska ha åtkomst till Power BI, kan du ta bort Power BI-licensen för den användaren.

1. Gå till [administrationscentret för Office 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. I det vänstra navigeringsfältet väljer du **Användare** > **Aktiva användare**.

1. Hitta den användare vars licens du vill ta bort och markera användarens namn.

    Du kan också hantera användarlicenser i grupp. Markera flera användare och välj **Redigera produktlicenser**.

1. Välj **Redigera** i fönstret för användarinformation intill **Produktlicenser**.

1. Ställ in **Power BI (kostnadsfri)** eller **Power BI Pro** på **Av** beroende på vilken licens som tillämpas på deras konto.

1. Välj **Spara**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Hur vet jag när nya användare har anslutit sig min klient?

Användare som har anslutit sig till din klient som en del av det här programmet tilldelas en unik licens som du kan filtrera efter i fönstret aktiva användare på admin-instrumentpanelen. Följ dessa steg om du vill skapa den nya vyn.

1. Gå till [administrationscentret för Office 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. I det vänstra navigeringsfältet väljer du **Användare** > **Aktiva användare**.

1. Välj **Lägg till anpassad vy** i menyn **Vyer**.

1. Namnge den nya vyn och välj **Power BI (kostnadsfri)** eller **Power BI Pro** under **Tilldelad produktlicens**.

    Du kan endast markera en licens per vy. Om du har licenser för både **Power BI (kostnadsfri)** och **Power BI Pro** i din organisation kan du skapa två vyer.

1. Ange eventuella andra villkor som du vill ha och välj **Lägg till**.

1. När den nya vyn har skapats är den tillgänglig från menyn **Vyer**.

### <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>Bör jag vara medveten om några andra förberedelser?

Du kan uppleva en ökning av begäranden om lösenordsåterställning. Information om den här processen finns i [Återställa en användares lösenord](/office365/admin/add-users/reset-passwords).

Du kan ta bort en användare från din klient via standardprocessen i administrationscentret för Office 365. Om användaren fortfarande har en aktiv e-postadress från din organisation kommer de att kunna återansluta om du inte blockerar alla användare från att ansluta.

### <a name="where-is-my-power-bi-tenant-located"></a>Var finns min Power BI-klient?

Information om vilka dataområdet din Power BI-klient finns i se [Var finns min Power BI-klient?](service-admin-where-is-my-tenant-located.md).

### <a name="what-is-the-power-bi-sla"></a>Vad är Power BI SLA?

Mer information om Power BI SLA (serviceavtal) finns i artikeln [Licensvillkor och dokumentation](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) i avsnittet **Licensiering** på Microsoft Licensing-webbplatsen.

## <a name="security-in-power-bi"></a>Säkerhet i Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Uppfyller Power BI nationella, regionala och branschspecifika efterlevnadskrav?

Lär dig mer om Power BI-efterlevnad på [Microsoft Trust Center](https://www.microsoft.com/en-us/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Hur fungerar säkerheten i Power BI?

Power BI bygger på Office 365, som i sin tur bygger på Azure-tjänster som Azure Active Directory. En översikt av Power BI-arkitekturen finns i [Power BI-säkerhet](service-admin-power-bi-security.md).

## <a name="next-steps"></a>Nästa steg

[Power BI-administratörsportalen](service-admin-portal.md)  
[Förstå Power BI-administratörsrollen](service-admin-role.md)  
[Självregistrering för Power BI](service-self-service-signup-for-power-bi.md)  
[Köp Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Vad är Power BI Premium?](service-premium.md)  
[Så här köper du Power BI Premium](service-admin-premium-purchase.md)  
[Power BI Premium – white paper](https://aka.ms/pbipremiumwhitepaper)  
[Hantera din grupp i Power BI och Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Användarkontohantering i Office 365](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Grupphantering i Office 365](/office365/admin/email/create-edit-or-delete-a-security-group/)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)
