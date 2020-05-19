---
title: Organisera arbete på de nya arbetsytorna i Power BI
description: Lär dig mer om de nya arbetsytorna, som är samlingar av instrumentpaneler och rapporter som skapats för att förse din organisation med statistik.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c534a72594692c5cf404b095492e7d6425f23329
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83273671"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organisera arbete på de nya arbetsytorna i Power BI

*Arbetsytor* är platser för samarbete med kollegor för att skapa samlingar med instrumentpaneler, rapporter och sidnumrerade rapporter. Den nya arbetsyteupplevelsen hjälper dig att bättre hantera åtkomst till innehåll. Den här artikeln beskriver de nya arbetsytorna och hur de skiljer sig åt från de klassiska arbetsytorna.  De används, precis som de klassiska arbetsytorna, för att skapa och distribuera appar. Är du redo att skapa en ny arbetsyta? Läs [Skapa en ny arbetsyta-upplevelsen](service-create-the-new-workspaces.md).

Nya och uppgraderade arbetsytor kan samexistera sida vid sida med befintliga klassiska arbetsytor. Den nya arbetsyteupplevelsen är stardardarbetsytan. Du kan fortfarande skapa och använda [klassiska arbetsytor](service-create-workspaces.md) baserat på Office 365-grupper om du vill. Är du redo för att migrera den klassiska arbetsytan? Mer information finns i [Uppgradera klassiska arbetsytor till de nya arbetsytorna i Power BI](service-upgrade-workspaces.md).

Med de nya arbetsytorna kan du:

- Tilldela arbetsyteroller till användargrupper: säkerhetsgrupper, distributionslistor, Office 365-grupper och enskilda användare.
- När du skapar en arbetsyta i Power BI utan att skapa en underliggande, associerad Office 365-grupp. All administration för arbetsytor sker i Power BI, inte i Office 365.
- Fortsätt att hantera användaråtkomst till innehåll via Office 365-grupper, om du vill. Du lägger bara till en Office 365-grupp i arbetsytans åtkomstlista.
- Använda mer detaljerade arbetsyteroller för mer flexibel hantering av behörigheter på en arbetsyta.

Power BI fortsätter att lista alla Office 365-grupper som du är medlem i. På så sätt undviker du att ändra befintliga arbetsflöden.

## <a name="new-and-classic-workspace-differences"></a>Skillnader mellan nya och klassiska arbetsytor

Vi har gjort om vissa funktioner för de nya arbetsytorna. Här är de viktigaste skillnaderna.

* När du skapar de här arbetsytorna skapas inte Office 365-grupper som för klassiska arbetsytor. Du kan dock nu använda en Office 365-grupp för att ge användare åtkomst till din arbetsyta genom att tilldela den till en roll. 
* I klassiska arbetsytor kan du bara lägga till enskilda personer till medlems- och administratörslistor. I de nya arbetsytorna kan du lägga till flera Active Directory-säkerhetsgrupper, distributionslistor eller Office 365-grupper till de här listorna för enklare användarhantering. 
- Du kan skapa ett innehållspaket för organisationen från en klassisk arbetsyta. Du kan inte skapa sådana från de nya arbetsytorna.
- Du kan använda ett innehållspaket för organisationen från en klassisk arbetsyta. Du kan inte använda dessa från de nya arbetsytorna.

### <a name="workspace-features-that-work-differently"></a>Arbetsytefunktioner som fungerar annorlunda

Vissa funktioner fungerar annorlunda i de nya arbetsytorna jämfört med de aktuella arbetsytorna. Dessa skillnader är avsiktliga, baserat på feedback vi har fått från kunder. De möjliggör en mer flexibel metod för samarbete med arbetsytor.

- **Licensieringskontroll**: Vid publicering av rapporter till den nya arbetsyteupplevelsen tillämpas befintliga licensieringsregler. Användare som samarbetar i arbetsytor eller delar innehåll till andra i Power BI-tjänsten behöver en Power BI Pro-licens. För användare utan Pro-licens visas ett felmeddelande om att ”endast användare med Power BI Pro-licenser kan publicera till här arbetsytan”.
- **Medlemmar kan eller kan inte dela om**: Deltagarrollen ersätter den här inställningen.
- **Skrivskyddade arbetsytor**: I stället för att ge användare skrivskyddad åtkomst till en arbetsyta, tilldelar du dem rollen Läsare. Den tillåter liknande skrivskyddad åtkomst till innehållet i en arbetsyta.
- **Användare utan Pro-licens** kan få åtkomst till arbetsytan om arbetsytan är i en Power BI Premium-kapacitet, även om användarna endast har rollen Läsare.
- **Tillåt användare att exportera data**: Användare med rollen Läsare kan exportera data om de har behörighet att skapa för datauppsättningarna i arbetsytan. Läs mer om [behörighet att skapa för datamängder](../connect-data/service-datasets-build-permissions.md).
- Det finns ingen knapp för att **lämna arbetsytan**.

### <a name="workspace-contact-list"></a>Arbetsytans kontaktlista

I den nya **kontaktlistan** kan du ange vilka användare som ska informeras om problem som kan uppstå i arbetsytan. Som standard informeras alla användare och grupper som angetts som arbetsyteadministratör, men du kan justera listan. Användare eller grupper som finns med i kontaktlistan visas i användargränssnittet för att hjälpa användarna att få hjälp med arbetsytan. 

Läs mer om att [ställa in arbetsytans kontaktlista](service-create-the-new-workspaces.md#workspace-contact-list).

### <a name="workspace-onedrive"></a>Arbetsytans OneDrive

Med arbetsytans OneDrive-funktion kan du konfigurera en Office 365-grupp vars fillagring för SharePoint-dokumentbiblioteket är tillgänglig för arbetsyteanvändarna. Du skapar gruppen utanför Power BI.

Power BI synkroniserar inte behörigheter för användare eller grupper, som är konfigurerade med arbetsyteåtkomst, med Office 365-gruppmedlemskapet. Det bästa sättet är att hantera arbetsyteåtkomst via den Office 365-grupp vars fillagring du konfigurerar i den här inställningen. 

Läs mer om hur du kan [konfigurera och få åtkomst till arbetsytans OneDrive](service-create-the-new-workspaces.md#workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Roller i de nya arbetsytorna

Om du vill bevilja åtkomst till en ny arbetsyta, lägger du till användargrupper eller enskilda personer till en av arbetsyterollerna administratörer, medlemmar, deltagare eller läsare. Alla i en användargrupp får den roll som du har definierat. Om en person finns i flera användargrupper, får personen den högsta av de behörighetsnivåer som följer av de roller som denne har tilldelats.

Med roller kan du hantera vem som kan göra vad i en arbetsyta, så att teamen kan samarbeta. De nya arbetsytorna gör att du kan tilldela roller till enskilda användare och användargrupper: säkerhetsgrupper, Office 365-grupper och distributionslistor. 

När du tilldelar roller till en användargrupp får personer i gruppen åtkomst till innehåll. Om du kapslar användargrupper får alla berörda användare behörighet.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> Om du vill inför säkerhet på radnivå (RLS) för användare som bläddrar i innehållet i en arbetsyta, kan du använda dig av läsarrollen. Om du vill införa säkerhet på radnivå (RLS) utan att ge åtkomst till arbetsytan kan du publicera en Power BI-app för dessa användare eller distribuera innehåll via delning.

## <a name="licensing"></a>Licensiering
Alla som du lägger till i en arbetsyta i den delade kapaciteten behöver en Power BI Pro-licens. På arbetsytan kan användarna samarbeta kring instrumentpaneler och rapporter som du planerar att publicera till en bredare publik eller hela organisationen. 

Om du vill distribuera innehåll till andra i organisationen kan du tilldela Power BI Pro-licenser till de användarna eller placera arbetsytan i en Power BI Premium-kapacitet.

När arbetsytan är i en Power BI Premium-kapacitet, kan användare med läsarroll få åtkomst till arbetsytan även om de inte har en Power BI Pro-licens. Om du tilldelar dessa användare en högre roll som Administratör, Medlem eller Deltagare så ombes de dock att starta en Pro-utvärdering när de försöker komma åt arbetsytan. För att kunna använda Läsarrollen för användare utan Pro-licenser, se till att de inte har andra arbetsyteroller, antingen individuellt eller via en användargrupp.

> [!NOTE]
> Vid publicering av rapporter till den nya arbetsyteupplevelsen tillämpas befintliga licensieringsregler strängare. Om du försöker publicera från Power BI Desktop eller andra klientverktyg utan en Pro-licens får du upp felet ”Endast användare med Power BI Pro-licens kan publicera till den här arbetsytan”.

## <a name="administering-new-workspace-experience-workspaces"></a>Administrera arbetsytor för den nya arbetsyteupplevelsen

Administration för arbetsytor i den nya arbetsyteupplevelsen finns nu i administratörsportalen för Power BI. Power BI-administratörer bestämmer vem i en organisation som kan skapa arbetsytor och distribuera appar. Administratörer kan se status för alla arbetsytor i organisationen. De kan också hantera och återställa arbetsytor. Läs mer om att [Skapa nya arbetsytor](../admin/service-admin-portal.md#create-the-new-workspaces) i artikeln Admin Portal.

## <a name="guest-users"></a>Gästanvändare

Som standard har [Azure AD B2B-gästanvändare](../admin/service-admin-azure-ad-b2b.md) inte någon åtkomst till arbetsytor. Power BI-administratörer kan [tillåta att externa gästanvändare kan redigera och hantera innehåll i organisationen](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). De aktiverade gästanvändarna kan komma åt de arbetsytor som de har behörighet till.

## <a name="auditing"></a>Granskning

Följande aktiviteter granskas av Power BI för arbetsytor för den nya arbetsytupplevelsen.

| Eget namn | Åtgärdsnamn |
|---|---|
| Power BI-mapp skapades | CreateFolder |
| Power BI-mapp togs bort | DeleteFolder |
| Power BI-mapp uppdaterades | UpdateFolder |
| Power BI-mappåtkomst uppdaterades| UpdateFolderAccess |

Läs mer om [Power BI-granskning](../admin/service-admin-auditing.md).

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

Begränsningar att känna till:

- Arbetsytor kan innehålla högst 1 000 datauppsättningar eller 1 000 rapporter per datauppsättning. 
- En person med Power BI Pro-licens kan vara medlem av högst 1 000 arbetsytor.
- Power BI Publisher för Excel stöds inte.

## <a name="frequently-asked-questions"></a>Vanliga frågor och svar

**Påverkas länkar till befintligt innehåll av den nya arbetsyteupplevelsen**

Nej. Länkar till befintliga objekt i klassiska arbetsytor påverkas inte av den nya arbetsyteupplevelsen. Den allmänna tillgänglighet för den nya arbetsyteupplevelsen ändrar den standardarbetsyta som du skapar, men inte befintliga arbetsytor. 

**Uppgraderas befintliga arbetsytor till den nya arbetsyteupplevelsen med allmän tillgänglighet?**

Nej. Den nya arbetsyteupplevelsen med allmän tillgänglighet ändrar bara standardarbetsytans typ till den nya arbetsyteupplevelsen. Befintliga klassiska arbetsytor som är baserade på Office 365-grupper förblir oförändrade.

**Skapas arbetsytor fortfarande automatiskt för Office 365-grupper?**

Ja. Eftersom vi stöder bägge typer av arbetsytor, sida vid sida, fortsätter vi att lista alla Office 365-grupper som användaren har åtkomst till i listan över arbetsytor.

## <a name="next-steps"></a>Nästa steg

* [Skapa de nya arbetsytorna i Power BI](service-create-the-new-workspaces.md)
* [Skapa klassiska arbetsytor](service-create-workspaces.md)
* [Installera och använda appar i Power BI](service-create-distribute-apps.md)
* Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)

