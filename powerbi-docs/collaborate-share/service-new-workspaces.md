---
title: Organisera arbete på de nya arbetsytorna i Power BI
description: Lär dig mer om de nya arbetsytorna, som är samlingar av instrumentpaneler och rapporter som skapats för att förse din organisation med statistik.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/26/2020
ms.author: maggies
ms.custom: contperfq4
LocalizationGroup: Share your work
ms.openlocfilehash: 77de9608978379cee83236b0c362bd2d7d57d5c6
ms.sourcegitcommit: a7b142685738a2f26ae0a5fa08f894f9ff03557b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84120411"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organisera arbete på de nya arbetsytorna i Power BI

*Arbetsytor* är platser för samarbete med kollegor för att skapa samlingar med instrumentpaneler, rapporter och sidnumrerade rapporter. Den nya arbetsyteupplevelsen hjälper dig att bättre hantera åtkomst till innehåll. Den här artikeln beskriver de nya arbetsytorna och hur de skiljer sig åt från de klassiska arbetsytorna.  De används, precis som de klassiska arbetsytorna, för att skapa och distribuera appar. Är du redo att skapa en ny arbetsyta? Läs [Skapa en ny arbetsyta-upplevelsen](service-create-the-new-workspaces.md).

:::image type="content" source="media/service-new-workspaces/power-bi-workspace-opportunity.png" alt-text="Ny arbetsyteupplevelse i Power BI":::

Nya och uppgraderade arbetsytor kan samexistera sida vid sida med befintliga klassiska arbetsytor. Den nya arbetsyteupplevelsen är stardardarbetsytan. Du kan fortfarande skapa och använda [klassiska arbetsytor](service-create-workspaces.md) baserat på Microsoft 365-grupper om du vill. Är du redo för att migrera den klassiska arbetsytan? Mer information finns i [Uppgradera klassiska arbetsytor till de nya arbetsytorna i Power BI](service-upgrade-workspaces.md).

## <a name="new-and-classic-workspace-differences"></a>Skillnader mellan nya och klassiska arbetsytor

Vi har gjort om vissa funktioner för de nya arbetsytorna. Här är de viktigaste skillnaderna.

- **När du skapar de nya arbetsytorna skapas inte Microsoft 365-grupper** som för klassiska arbetsytor. All administration för nya arbetsytor sker i Power BI, inte i Office 365. Du kan hantera användaråtkomst till innehåll via Microsoft 365-grupper, om du vill. Lägg bara till en Microsoft 365-grupp i åtkomstlistan för arbetsytor.
- **Använda mer detaljerade arbetsyteroller** för mer flexibel hantering av behörigheter i de nya arbetsytorna.  I klassiska arbetsytor kan du bara lägga till enskilda personer till medlems- och administratörslistor. 
- **Tilldela roller för användargrupper till arbetsytan**: På de nya arbetsytorna kan du lägga till flera Active Directory-säkerhetsgrupper, distributionslistor eller Microsoft 365-grupper till de här rollerna för enklare användarhantering. 
- **Kontaktlista**: I de nya arbetsytorna kan du ange vilka som tar emot meddelanden om arbetsytans aktivitet.
- **Skapa mallappar**: Du kan bara skapa *mallappar* i de nya arbetsytorna. Mallappar är appar som du kan distribuera till kunder utanför organisationen. Dessa kunder kan sedan ansluta till sina egna data med din mallapp. Läs mer om [mallappar](../connect-data/service-template-apps-overview.md).
- **Dela datauppsättningar**: Om du vill dela en datauppsättning utanför en speciell arbetsyta måste du spara rapporten som innehåller datauppsättningen till en av de nya arbetsytorna. Du kan inte dela datauppsättningar från klassiska arbetsytor. Läs mer om [delade datauppsättningar](../connect-data/service-datasets-across-workspaces.md).
- **Organisationsinnehållspaket**: Du skapar och använder organisationsinnehållspaket i klassiska arbetsytor. Du kan inte skapa eller använda dem i de nya arbetsytorna. Appar och mallar ersätter organisationsinnehållspaket i de nya arbetsytorna.

I den här artikeln beskrivs dessa funktioner mer ingående.

> [!NOTE]
> Power BI fortsätter att visa en lista över alla Microsoft 365-grupper som du är medlem i. På så sätt undviker du att ändra befintliga arbetsflöden.

### <a name="features-that-work-differently"></a>Funktioner som fungerar annorlunda

Vissa funktioner fungerar annorlunda i de nya arbetsytorna. Dessa skillnader är avsiktliga, baserat på feedback vi har fått från kunder. De möjliggör en mer flexibel metod för samarbete i arbetsytor.

- **Licensieringskontroll**: Vid publicering av rapporter till en ny arbetsyteupplevelse tillämpas befintliga licensieringsregler. Användare som samarbetar i nya arbetsytor eller delar innehåll till andra i Power BI-tjänsten behöver en Power BI Pro-licens. För användare utan Pro-licens visas ett felmeddelande om att ”endast användare med Power BI Pro-licenser kan publicera till här arbetsytan”.
- **Inställningen ”Medlemmar kan dela igen”** : Deltagarrollen i de nya arbetsytorna ersätter inställningen ”medlemmar kan dela igen” i de klassiska arbetsytorna.
- **Skrivskyddade arbetsytor**: Rollen Läsare i de nya arbetsytorna ersätter beviljande för användare till skrivskyddat läge av en klassisk arbetsyta. Rollen Läsare tillåter en liknande skrivskyddad åtkomst till innehållet i en ny arbetsyta.
- **Användare utan Pro-licens** kan få åtkomst till en ny arbetsyta om arbetsytan är i en Power BI Premium-kapacitet, men bara om de har rollen Läsare.
- **Tillåt användare att exportera data**: Även användare med rollen Läsare i den nya arbetsytan kan exportera data om de har behörighet att skapa i datauppsättningarna i arbetsytan. Läs mer om [behörighet att skapa för datamängder](../connect-data/service-datasets-build-permissions.md).
- Ingen knapp för **Lämna arbetsytan** i de nya arbetsytorna.

### <a name="workspace-contact-list"></a>Arbetsytans kontaktlista

I den nya **kontaktlistan** kan du ange vilka användare som ska informeras om problem som kan uppstå i de nya arbetsytorna. Som standard informeras alla användare eller grupper som angetts som arbetsyteadministratörer i den nya arbetsytan. Du kan lägga till i listan. Användare eller grupper i kontaktlistan visas också i användargränssnittet (UI) i de nya arbetsytorna, så att slutanvändare av arbetsytor vet vem som ska kontaktas. 

Läs mer om [hur du skapar arbetsytans kontaktlista](service-create-the-new-workspaces.md#create-a-contact-list).

### <a name="workspace-onedrive"></a>Arbetsytans OneDrive

Såsom angetts skapar Power BI inte någon Microsoft 365-grupp i bakgrunden när du skapar en av de nya arbetsytorna. Det kan fortfarande vara bra att ha en OneDrive kopplad till den nya arbetsytan. Med arbetsytans OneDrive-funktion i de nya arbetsytorna kan du konfigurera en Microsoft 365-grupp vars fillagring för SharePoint-dokumentbiblioteket är tillgänglig för arbetsyteanvändarna. Du skapar gruppen utanför Power BI.
 
Power BI synkroniseras inte mellan Microsoft 365-gruppmedlemskap och behörigheter för användare eller grupper med åtkomst till den nya arbetsytan. Du kan synkronisera dem: Hantera arbetsyteåtkomst via den Microsoft 365-grupp vars fillagring du konfigurerar i den här inställningen. 

Läs mer om hur du kan [konfigurera arbetsytans OneDrive](service-create-the-new-workspaces.md#set-a-workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Roller i de nya arbetsytorna

Med roller kan du hantera vem som kan göra vad i de nya arbetsytorna, så att teamen kan samarbeta. De nya arbetsytorna gör att du kan tilldela roller till enskilda användare och användargrupper: säkerhetsgrupper, Microsoft 365-grupper och distributionslistor. 

Om du vill bevilja åtkomst till en ny arbetsyta, tilldelar du dessa användargrupper eller enskilda personer till en av arbetsyterollerna: Administratör, Medlem, Deltagare eller Läsare. Alla i en användargrupp får den roll som du har tilldelat. Om någon finns i flera användargrupper, får personen den högsta av de behörighetsnivåer som följer av de roller som denne har tilldelats. Om du kapslar användargrupper får alla berörda användare behörighet. För alla dessa funktioner (utom visning och interaktion) krävs en Power BI Pro-licens. Läs mer om [licensiering](#licenses) i den här artikeln.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> - Du kan tilldela användare till roller, antingen ensamma eller i en grupp, även om de inte kan använda rollen. Med andra ord kan du tilldela användare som inte har Power BI Pro-licenser till en roll som kräver en licens. Mer information finns i [Licenser](#licenses) i den här artikeln.
> - Om du vill införa säkerhet på [radnivå (RLS)](../admin/service-admin-rls.md) för användare som bläddrar i innehållet i en arbetsyta, kan du använda dig av läsarrollen. Du kan också använda RLS utan att ge åtkomst till den nya arbetsytan. [Publicera en app](service-create-distribute-apps.md) och tilldela den till dessa användarna eller använda [delning för att distribuera innehåll](service-share-dashboards.md) till dem.

## <a name="licensing-and-administering"></a>Licensiering och administrering

### <a name="licenses"></a>Licenser
Om en av de nya arbetsytorna är i en delad kapacitet, behöver alla du lägger till en Power BI Pro-licens. Dessa användare kan samarbeta på instrumentpaneler och rapporter i den nya arbetsytan. Om du vill distribuera innehåll till andra i organisationen kan du antingen tilldela Power BI Pro-licenser till dessa användarna eller placera arbetsytan i en Power BI Premium-kapacitet.

När arbetsytan är i en Power BI Premium-kapacitet, kan användare med läsarroll få åtkomst till den nya arbetsytan även om de inte har en Power BI Pro-licens. Om du tilldelar dessa användare en högre roll som Administratör, Medlem eller Deltagare så ombes de dock att starta en Pro-utvärdering när de försöker komma åt arbetsytan. Om du vill att användare utan Pro-licenser ska använda rollen Läsare, se till att de inte har andra arbetsyteroller också, antingen som individer eller som en del av en användargrupp.

> [!NOTE]
> Vid publicering av rapporter till den nya arbetsyteupplevelsen tillämpas befintliga licensieringsregler strängare. Om du försöker publicera från Power BI Desktop eller andra klientverktyg utan en Pro-licens får du upp felet ”Endast användare med Power BI Pro-licens kan publicera till den här arbetsytan”.

### <a name="guest-users"></a>Gästanvändare

Som standard har [Azure AD B2B-gästanvändare](../admin/service-admin-azure-ad-b2b.md) inte någon åtkomst till arbetsytor. Power BI-administratörer kan [tillåta att externa gästanvändare kan redigera och hantera innehåll i organisationen](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). De aktiverade gästanvändarna kan komma åt de arbetsytor som de har behörighet till.

### <a name="administering-new-workspace-experience-workspaces"></a>Administrera arbetsytor för den nya arbetsyteupplevelsen

Administration för arbetsytor i den nya arbetsyteupplevelsen finns i administratörsportalen för Power BI. Power BI-administratörer bestämmer vem i en organisation som kan skapa arbetsytor och distribuera appar. Administratörer kan se status för alla arbetsytor i organisationen. De kan också hantera och återställa arbetsytor. Läs mer om att [administrera nya arbetsytor](../admin/service-admin-portal.md#create-the-new-workspaces) i artikeln Administratörsportalen.

### <a name="auditing"></a>Granskning

Power BI granskar följande aktiviteter för arbetsytor för den nya arbetsytupplevelsen.

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

**Påverkas länkar till befintligt innehåll av den nya arbetsyteupplevelsen?**

Nej. Länkar till befintliga objekt i klassiska arbetsytor påverkas inte av den nya arbetsyteupplevelsen. Den allmänna tillgänglighet för den nya arbetsyteupplevelsen ändrar den standardarbetsyta som du skapar, men inte befintliga arbetsytor. 

**Uppgraderas befintliga arbetsytor till den nya arbetsyteupplevelsen med allmän tillgänglighet?**

Nej. Den nya arbetsyteupplevelsen med allmän tillgänglighet ändrar bara standardarbetsytans typ till den nya arbetsyteupplevelsen. Befintliga klassiska arbetsytor som är baserade på Microsoft 365-grupper förblir oförändrade.

**Skapas arbetsytor fortfarande automatiskt för Microsoft 365-grupper?**

Ja. Eftersom vi stöder bägge typer av arbetsytor, sida vid sida, fortsätter vi att lista alla Microsoft 365-grupper som användaren har åtkomst till i listan över arbetsytor.

## <a name="next-steps"></a>Nästa steg

* [Skapa de nya arbetsytorna i Power BI](service-create-the-new-workspaces.md)
* [Skapa klassiska arbetsytor](service-create-workspaces.md)
* [Installera och använda appar i Power BI](service-create-distribute-apps.md)
* Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)

