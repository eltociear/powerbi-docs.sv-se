---
title: Administrera Power BI – Vanliga frågor och svar
description: Få reda på svaren på vanliga frågor om Power BI-registrering, hantering av klientorganisationer och andra administrativa uppgifter.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 0c9d346017dc3b18abd6a56d0d3a62e1305e6575
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74698749"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Administrera Power BI – Vanliga frågor och svar

Den här artikeln tar upp vanliga frågor och svar för Power BI-administration. En översikt över Power BI-administration finns i [vad är Power BI-administration?](service-admin-administering-power-bi-in-your-organization.md).

## <a name="whats-in-this-article"></a>Innehåll i artikeln

### <a name="sign-up-for-power-bi-section"></a>Avsnittet registrera dig för Power BI

* [Använda PowerShell](#using-powershell)
* [Hur registrerar sig användare för Power BI?](#how-do-users-sign-up-for-power-bi)
* [Hur registrerar sig enskilda användare i organisationen?](#how-do-individual-users-in-my-organization-sign-up)
* [Hur kan jag förhindra användare från att ansluta till min befintliga Office 365-klient?](#how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant)
* [Hur kan jag låta användare att ansluta till min befintliga Office 365-klient?](#how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant)
* [Hur kontrollerar jag om klienten är blockerad?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [Hur förhindrar jag att mina befintliga användare börjar använda Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Hur låter jag mina befintliga användare registrera dig för Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Avsnittet administration av Power BI

* [Hur kommer detta att ändra hur jag hanterar identiteter för användare i min organisation idag?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Hur hanterar vi Power BI?](#how-do-we-manage-power-bi)
* [Hur hanterar jag en klient som skapas av Microsoft för mina användare?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Om jag har flera domäner, kan jag styra vilken Microsoft 365-klient som användare läggs till i?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to)
* [Hur tar jag bort Power BI för användare som redan har registrerat sig?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Hur vet jag när nya användare har anslutit sig min klient?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Finns andra saker som kräver förberedelser?](#are-there-any-additional-things-i-should-prepare-for)
* [Var finns min Power BI-klient?](#where-is-my-power-bi-tenant-located)
* [Vad är Power BI SLA (serviceavtal)?](#what-is-the-power-bi-sla)
* [Hur hanterar Power BI hög tillgänglighet och redundans?](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Avsnittet säkerhet i Power BI

* [Uppfyller Power BI nationella, regionala och branschspecifika efterlevnadskrav?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Hur fungerar säkerheten i Power BI?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Registrera dig för Power BI

### <a name="using-powershell"></a>Använda PowerShell

Vissa av procedurerna i det här avsnittet kräver Windows PowerShell-skript. Om du inte är bekant med PowerShell, rekommenderar vi [guiden Kom igång med PowerShell](https://go.microsoft.com/fwlink/p/?LinkID=286814). För att köra skripten ska du först installera den senaste 64-bitarsversionen av [Azure Active Directory PowerShell för Graph](/powershell/azure/active-directory/).

### <a name="how-do-users-sign-up-for-power-bi"></a>Hur registrerar sig användare för Power BI?

Som administratör för Microsoft 365 kan du registrera dig för Power BI via [Power BI-webbplatsen](https://powerbi.microsoft.com) eller sidan [Köptjänster](https://admin.microsoft.com/AdminPortal/Home#/catalog) i administrationscentret för Microsoft 365. När administratörer för Microsoft 365 registrerar sig för Power BI kan de tilldela användarlicenser till användare som ska ha åtkomst.

Dessutom kan enskilda användare i din organisation kanske registrera sig för Power BI via [Power BI-webbplatsen](https://powerbi.microsoft.com). När en användare i din organisation registrerar sig för Power BI, tilldelas användaren automatiskt en Power BI-licens. Mer information finns i [Registrera dig för Power BI som individ](service-self-service-signup-for-power-bi.md) och [Power BI-licensiering i din organisation](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Hur registrerar sig enskilda användare i organisationen?

Det finns tre scenarier som kan gälla för användare i organisationen:

* **Scenario 1**: Din organisation har redan en befintlig Microsoft 365-miljö och användaren som registrerar sig för Power BI har redan ett Microsoft 365-konto.
    Om användaren redan har ett arbets- eller skolkonto i klientorganisationen i den här situationen (till exempel contoso.com) men inte har Power BI ännu så aktiverar Microsoft helt enkelt den kostnadsfria Power BI-planen för kontot. Användaren får automatiskt ett meddelande om hur de kan använda Power BI-tjänsten.

* **Scenario 2**: Din organisation har redan en befintlig Microsoft 365-miljö, men användaren som registrerar sig för Power BI har inte något Microsoft 365-konto.
    I den här situationen har användaren en e-postadress i organisationens domän (till exempel contoso.com), men har ännu inte något Microsoft 365-konto. I detta fall kan användaren registrera sig för Power BI och får ett konto automatiskt. Den här åtgärden ger användaren åtkomst till Power BI-tjänsten. Om medarbetaren Nancy till exempel använder sin jobbadress (exempelvis nancy@contoso.com) i registreringen lägger Microsoft automatiskt till Nancy som en användare i Contosos miljö i Microsoft 365 och aktiverar Power BI för kontot.

* **Scenario 3**: Din organisation har inte någon Microsoft 365-miljö kopplad till er e-postdomän.
    Det finns inga administrativa åtgärder som din organisation behöver vidta för att dra nytta av Power BI. Tjänsten lägger till användare till en ny, endast molnbaserad, användarkatalog. Du kan också välja att ta över som global administratör för klientorganisationen i Microsoft 365 och hantera användarna.

> [!IMPORTANT]
> Om din organisation har flera e-postdomäner och du vill att alla e-postadresstillägg ska vara i samma klient kan du lägga till alla e-postdomäner i en Azure Active Directory-klient innan användarna registrerar sig. Det finns ingen automatisk mekanism för att flytta användare mellan klienter när de väl har skapats. Mer information om den här processen finns i [Om jag har flera domäner, kan jag styra vilken Microsoft 365-klient som användare läggs till i?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to) senare i den här artikeln och [Lägga till en domän i Microsoft 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant"></a>Hur kan jag förhindra att användare ansluter till min befintliga Microsoft 365-klientorganisation?

Det finns steg som du kan vidta som global administratör för Microsoft 365 så att inte användare ansluter till din Microsoft 365-klientorganisation. Om du blockerar åtkomst kommer användarnas försök att registrera sig att misslyckas och ett meddelande visas som hänvisar dem till att kontakta administratören för deras organisation. Du behöver inte upprepa den här proceduren om du redan har inaktiverat licensen för automatisk distribution (till exempel via Office 365 för utbildning för studenter, lärare och övrig personal).

Använd följande PowerShell-skript för att förhindra att nya användare ansluter till en hanterad klient. ([Läs mer om PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> Den här blockeringen förhindrar att nya användare i din organisation registrerar sig för Power BI. Användare som registrerar sig för Power BI innan du inaktiverar nya registreringar för din organisation, behåller sina licenser. Om du vill ta bort en användare, se [Hur tar jag bort Power BI för användare som redan har registrerat sig?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) senare i den här artikeln.

### <a name="how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant"></a>Hur kan jag låta användare ansluta till min befintliga Microsoft 365-klientorganisation?

Använd följande PowerShell-skript för att låta nya användare ansluta till en hanterad klient. ([Läs mer om PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>Hur kontrollerar jag om klienten är blockerad?

Kör följande PowerShell-skript för att kontrollera inställningarna. *AllowEmailVerifiedUsers* bör vara false. ([Läs mer om PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Hur förhindrar jag att mina befintliga användare börjar använda Power BI?

Azure AD-inställningen som styr detta är **AllowAdHocSubscriptions**. De flesta klienter har den inställd på *sant*, vilket innebär att den är aktiverad. Om du har köpt Power BI via en partner kan den vara inställd på *falskt*, vilket innebär att den är inaktiverad.

Använd följande PowerShell-skript för att inaktivera ad hoc-prenumerationer ([Läs mer om PowerShell][1].)

1. Logga in i Azure Active Directory med dina autentiseringsuppgifter för Microsoft 365. Den första raden i följande PowerShell-skript uppmanar dig att ange dina autentiseringsuppgifter. Den andra raden ansluter till Azure Active Directory.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Skärmbild av Azure Active Directory-inloggning via PowerShell](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. När du har loggat in kan du köra följande kommando för att se hur din klient är konfigurerad.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. Kör det här kommandot för att aktivera (`$true`) eller inaktivera (`$false`) **AllowAdHocSubscriptions**.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Använd flaggan **AllowAdHocSubscriptions** om du vill styra flera användarfunktioner i organisationen, inklusive möjligheten för användare att registrera sig för Azure Rights Management-tjänsten. Om du ändrar flaggan påverkas alla dessa funktioner. Med inställningen *false* kan användarna fortfarande registrera sig för enskilda utvärderingsversioner av Power BI Pro.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Hur låter jag mina befintliga användare registrera dig för Power BI?

Kör kommandot i den tidigare frågan för att låta befintliga användare registrera sig för Power BI men skicka värdet `$true` i stället för `$false` i det sista steget.

## <a name="administration-of-power-bi"></a>Administration av Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Hur kommer detta för att ändra hur jag hanterar identiteter för användare i min organisation idag?

Det finns tre scenarier som kan gälla för användare i organisationen:

* **Scenario 1**: Om din organisation redan har en befintlig Microsoft 365-miljö och alla användare i organisationen har ett Microsoft 365-konto ändras inte identitetshanteringen.

* **Scenario 2**: Om din organisation redan har en befintlig Microsoft 365-miljö, men alla användare i organisationen inte har Microsoft 365-konton, skapar vi en användare i klientorganisationen och tilldelar licenser utifrån användarens e-post för skola eller arbete.

    Det innebär att antalet användare som du hanterar kan växa allteftersom användare i din organisation registrerar sig för tjänsten.

* **Scenario 3**: Om din organisation inte har någon Microsoft 365-miljö kopplad till e-postdomänen ändras inte hur du hanterar identiteter.

    Tjänsten lägger till användare i en ny, molnbaserad användarkatalog som du kan välja att ta över som global administratör i Microsoft 365.

### <a name="how-do-we-manage-power-bi"></a>Hur hanterar vi Power BI?

I Power BI finns det en administratörsportal för användare som är globala administratörer i Microsoft 365 eller administratörer för Power BI-tjänsten. För att kunna använda Power BI-administratörsportalen måste du markera ditt konto som **Global administratör** i Microsoft 365 eller Azure Active Directory, eller så måste någon tilldela administratörsrollen för Power BI-tjänsten till ditt användarkonto. Mer information finns i [Förstå administratörsrollen för Power BI](service-admin-role.md) och [Power BI-administratörsportalen](service-admin-portal.md). I portalen kan du ange inställningar för hela klientorganisationen, visa användningsstatistik för Power BI och hantera användare och grupper via en länk till administrationscentret för Microsoft 365.

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Hur hanterar jag en klient som skapas av Microsoft för mina användare?

När en självbetjäningsanvändare registrerar sig för en molntjänst som använder Azure AD läggs de till i en ohanterad Azure AD-katalog baserat på e-postdomänen. Du kan göra anspråk på och hantera en klientorganisation som någon annan skapat, via en process som kallas för *adminövertagande*. Mer information finns i [Ta över en ohanterad katalog som administratör i Azure Active Directory](/azure/active-directory/users-groups-roles/domains-admin-takeover). Typen av övertagande beror på om det finns en befintlig hanterad klient som är associerad med domänen:

* Power BI stöder internt administratörsövertagande. När du utför ett _internt_ administratörsövertagande av en ohanterad Azure-katalog läggs du till som global administratör för den ohanterade katalogen. Inga användare, domäner eller tjänstplaner migreras till någon annan katalog som du administrerar.

* Power BI stöder inte längre externt administratörsövertagande. När du utför ett _externt_ administratörsövertagande av en ohanterad Azure-katalog lägger du till DNS-domännamnet för den ohanterade katalogen i din hanterade Azure-katalog. Vid ett externt övertagande förloras åtkomsten till allt Power BI-innehåll i den ursprungliga klientorganisationen som inte hanteras. Power BI-rapporterna måste publiceras på nytt till den nya klientorganisationen, och du måste skapa instrumentpaneler och appar för Power BI på nytt i den nya klientorganisationen.

### <a name="if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to"></a>Om jag har flera domäner, kan jag styra vilken Microsoft 365-klientorganisation som användare läggs till i?

Om du inte gör något skapas en klient för varje användares e-postdomäner och underdomäner. Om du vill att alla användare ska vara i samma klient oavsett deras e-postadressdomän: Skapa en målklient i förväg eller använd en befintlig klient. Lägg sedan till alla befintliga domäner och underdomäner som du vill samla inom klienten. Alla användare med e-postadresser som slutar på dessa domäner och underdomäner ansluts automatiskt till målklienten när de registreras.

> [!IMPORTANT]
> Det finns ingen automatisk mekanism för att flytta användare mellan klienter när de väl har skapats. Mer information om att lägga till domäner i en enda Microsoft 365-klientorganisation finns i [Lägga till användare och domän i Office 365](/office365/admin/setup/add-domain/).

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Hur tar jag bort Power BI för användare som redan har registrerat sig?

Om en användare har registrerat dig för Power BI, men du inte längre vill att hen ska ha åtkomst till Power BI, kan du ta bort Power BI-licensen för den användaren.

1. Gå till [Administrationscenter för Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Välj **Användare** > **Aktiva användare** i navigeringsfönstret.

1. Hitta den användare vars licens du vill ta bort och markera användarens namn.

    Du kan också hantera användarlicenser i grupp. Markera flera användare och välj **Redigera produktlicenser**.

1. Välj **Redigera** i fönstret för användarinformation intill **Produktlicenser**.

1. Ställ in **Power BI (kostnadsfri)** eller **Power BI Pro** på **Av** beroende på vilken licens som du har tilldelat till deras konto.

1. Välj **Spara**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Hur vet jag när nya användare har anslutit sig min klient?

Användare som har anslutit sig till din klientorganisation via självregistrering tilldelas en unik licens som du kan filtrera efter i fönstret med aktiva användare på instrumentpanelen för administratörer. Följ dessa steg om du vill skapa den nya vyn.

1. Gå till [Administrationscenter för Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Välj **Användare** > **Aktiva användare** i navigeringsfönstret.

1. Välj **Lägg till anpassad vy** i menyn **Vyer**.

1. Namnge den nya vyn och välj **Power BI (kostnadsfri)** eller **Power BI Pro** under **Tilldelad produktlicens**.

    Du kan endast markera en licens per vy. Om du har licenser för både **Power BI (kostnadsfri)** och **Power BI Pro** i din organisation kan du skapa två vyer.

1. Ange eventuella andra villkor som du vill ha och välj **Lägg till**.

1. När du har skapat den nya vyn är den tillgänglig från menyn **Vyer**.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>Finns andra saker som kräver förberedelser?

Du kan uppleva en ökning av begäranden om lösenordsåterställning. Information om den här processen finns i [Återställa en användares lösenord](/office365/admin/add-users/reset-passwords).

Du kan ta bort en användare från din klient via standardprocessen i administrationscentret för Microsoft 365. Om användaren fortfarande har en aktiv e-postadress från din organisation kommer de att kunna återansluta om du inte blockerar alla användare från att ansluta.

### <a name="where-is-my-power-bi-tenant-located"></a>Var finns min Power BI-klient?

För information om vilket dataområde din Power BI-klient är i, se [Var finns min Power BI-klient?](service-admin-where-is-my-tenant-located.md).

### <a name="what-is-the-power-bi-sla"></a>Vad är Power BI SLA?

Mer information om Power BI SLA (serviceavtal) finns i artikeln [Licensvillkor och dokumentation](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) i avsnittet **Licensiering** på Microsoft Licensing-webbplatsen.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Hur hanterar Power BI hög tillgänglighet och redundans?

Mer information om hög tillgänglighet och redundans finns i [Vanliga frågor och svar om hög tillgänglighet, redundans och haveriberedskap i Power BI](service-admin-failover.md).

## <a name="security-in-power-bi"></a>Säkerhet i Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Uppfyller Power BI nationella, regionala och branschspecifika efterlevnadskrav?

Lär dig mer om Power BI-efterlevnad på [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Hur fungerar säkerheten i Power BI?

Microsoft Power BI bygger på Microsoft 365, som i sin tur bygger på Azure-tjänster som Azure Active Directory. En översikt av Power BI-arkitekturen finns i [Power BI-säkerhet](service-admin-power-bi-security.md).

## <a name="next-steps"></a>Nästa steg

[Power BI-administratörsportalen](service-admin-portal.md)  
[Förstå Power BI-administratörsrollen](service-admin-role.md)  
[Självregistrering för Power BI](service-self-service-signup-for-power-bi.md)  
[Köp Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Vad är Power BI Premium?](service-premium-what-is.md)  
[Så här köper du Power BI Premium](service-admin-premium-purchase.md)  
[Power BI Premium – white paper](https://aka.ms/pbipremiumwhitepaper)  
[Hantera din grupp i Power BI och Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Användarkontohantering i Office 365](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Grupphantering i Office 365](/office365/admin/email/create-edit-or-delete-a-security-group/)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview
