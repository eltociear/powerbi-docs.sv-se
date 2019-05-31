---
title: Organisera arbete i nya arbetsyteförhandsversionen – Power BI
description: Läs mer om de nya arbetsytor som är samlingar av instrumentpaneler och rapporter som skapats för att leverera nyckelvärden för din organisation.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 9f5dfaa5a23ae46fef131a52355531b5fbde3051
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100698"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organisera arbete i nya arbetsytor i Power BI

 *Arbetsytor* är platser där du kan samarbeta med kollegor för att skapa samlingar av instrumentpaneler, rapporter och sidnumrerade rapporter. Den nya arbetsyta upplevelsen hjälper dig att bättre hantera åtkomst till innehåll. Den här artikeln beskriver nya arbetsytor och hur de skiljer sig från de klassiska arbetsytorna.  Som med klassiska arbetsytor använda du fortfarande dem för att skapa och distribuera appar. Läs om hur du [skapa en ny arbetsyta upplevelse](service-create-the-new-workspaces.md).

Den nya arbetsyta-upplevelsen har blivit allmänt tillgängliga (GA) och är nu standardarbetsytan. Du kan fortsätta att skapa och använda [klassiska arbetsytor](service-create-workspaces.md) baserat på Office 365-grupper. 

> [!NOTE]
> Om du vill framtvinga säkerhet på radnivå (RLS) för Power BI Pro-användare surfning innehållet i en arbetsyta måste fortsätta att använda [klassiska arbetsytor](service-create-workspaces.md). Välj den **medlemmar kan bara visa Power BI-innehåll** alternativet. Du kan också publicera en Power BI-app till de användarna eller Använd delning för att distribuera innehåll. Rollen kommande visningsprogrammet kan det här scenariot i framtiden i nya arbetsytor för arbetsyta-upplevelse.

Med de nya arbetsytorna kan du:

- Tilldela arbetsyteroller till användargrupper: säkerhetsgrupper, distributionslistor, Office 365-grupper och enskilda användare.
- Skapa en arbetsyta i Power BI utan att skapa en Office 365-grupp.
- Använda mer detaljerade arbetsyteroller för mer flexibel hantering av behörigheter på en arbetsyta.

När du skapar en av de nya arbetsytorna skapar du inte en underliggande, associerad Office 365-grupp. All administration för arbetsytor sker i Power BI, inte i Office 365. Du kan nu lägga till en Office 365-grupp i listan över arbetsytan om du vill fortsätta att hantera användarnas åtkomst till innehållet via Office 365-grupper i den nya upplevelsen i arbetsytan.

## <a name="administering-new-workspace-experience-workspaces"></a>Administrera nya arbetsytan upplevelse arbetsytor
Administration för nya arbetsytan upplevelse arbetsytor är nu i Power BI, Power BI-administratörer bestämma vem som i en organisation kan skapa arbetsytor. De kan också hantera och återställa arbetsytan. De måste använda Power BI admin portal eller PowerShell-CmdLets för att göra detta. För klassiska arbetsytor baserat på Office 365-grupper, fortsätter administration kan förekomma i administrationsportalen för Office 365 och Azure Active Directory.

I **arbetsyteinställningarna** i administrationsportalen kan administratörer använda skapa arbetsytor (avanmäla till arbetsytan) till att tillåta alla eller ingen i en organisation för att skapa ny arbetsyta upplevelse arbetsytor. De kan även begränsa skapandet till medlemmar eller vissa säkerhetsgrupper.

> [!NOTE]
> Skapa arbetsytor (avanmäla till arbetsytan) standardinställningar att endast tillåta användare som kan skapa Office 365-grupper för att skapa nya arbetsytor i Power BI. Glöm inte att ange ett värde i Power BI-administratörsportalen att se till att rätt användare kan skapa ny arbetsyta upplevelse arbetsytor.

![Arbetsyteinställningar i administrationsportalen](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

Den [arbetsytor är tillgänglig](service-admin-portal.md#workspaces) i Power BI-administratörsportalen. 

![Lista över arbetsytor](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>Nya arbetsytor sida vid sida med klassiska arbetsytor

Nya och uppgraderade arbetsytor och befintliga klassiska arbetsytor fungera sida vid sida och du kan skapa. Den nya arbetsyta upplevelsen är typ av arbetsytan. Powerbi fortsätter att lista alla Office 365-grupper som användaren är medlem i Power BI för att undvika att ändra befintliga arbetsflöden. Läs hur du skapar en ny arbetsyta [skapa nya arbetsytor](service-create-the-new-workspaces.md). Läs hur du skapar en klassiska arbetsyta [skapa klassiska arbetsytor](service-create-workspaces.md).

## <a name="roles-in-the-new-workspaces"></a>Roller i de nya arbetsytorna

Om du vill bevilja åtkomst till en ny arbetsyta, lägger du till användargrupper eller enskilda personer som finns till någon av rollerna arbetsyta: medlemmar, deltagare eller administratörer. Alla i en användargrupp får den roll som du har definierat. Om en person är i flera användargrupper, får de den högsta behörighetsnivån som tillhandahålls av de roller som de har tilldelats.

Med roller kan du hantera vem som kan göra vad i en arbetsyta, så att teamen kan samarbeta. De nya arbetsytorna gör att du kan tilldela roller till enskilda användare och användargrupper: säkerhetsgrupper, Office 365-grupper och distributionslistor. 

När du tilldelar roller till en användargrupp får personer i gruppen åtkomst till innehåll. Om du kapslar användargrupper får alla berörda användare behörighet. En användare som finns i flera användargrupper med olika roller får den högsta behörighetsnivån som de har tilldelats. 

De nya arbetsytorna erbjuder tre roller: administratörer, medlemmar och deltagare.

|Kapacitet   | Admin  | Medlem  | Deltagare  | 
|---|---|---|---|
| Uppdatera och ta bort arbetsytan.  | X  |   |   |
| Lägga till/ta bort personer, inklusive andra administratörer.  | X  |   |   |
| Lägga till medlemmar eller andra med lägre behörighet.  |  X | X  |   |
| Publicera och uppdatera en app. |  X | X  |   |
| Dela ett objekt eller dela en app. |  X | X  |   |
| Tillåta att andra delar objekt igen. |  X | X  |   |
| Skapa, redigera och ta bort innehåll på arbetsytan.  |  X | X  | X  |
| Publicera rapporter till arbetsytan och ta bort innehåll. |  X | X  | X  |
 
 
## <a name="licensing"></a>Licensiering
Alla som du lägger till i en arbetsyta behöver en Power BI Pro-licens. På arbetsytan kan användarna samarbeta kring instrumentpaneler och rapporter som du planerar att publicera till en bredare publik eller hela organisationen. Om du vill distribuera innehåll till andra i organisationen kan du tilldela Power BI Pro-licenser till de användarna eller placera arbetsytan i en Power BI Premium-kapacitet.

> [!NOTE]
> Publicera rapporter till den nya arbetsytan miljön har strängare tvingande befintliga licensiering regler. Användare som försöker publicera från Power BI Desktop eller andra klienter verktyg utan en Pro-licens du ser felet ”endast användare med Power BI Pro-licenser kan publicera den här arbetsytan”.

## <a name="how-are-the-new-workspaces-different-from-current-workspaces"></a>Hur skiljer sig de nya arbetsytorna åt från aktuella arbetsytor?

Vi gör om vissa funktioner i och med de nya arbetsytorna. Här följer de ändringar som du kan förvänta dig ska vara permanent. 

* Skapa dessa arbetsytor kommer inte att skapa Office 365-grupper som gör klassiska arbetsytor. Du kan nu använda en Office 365-grupp för att ge användare åtkomst till din arbetsyta genom att tilldela den till en roll. 
* I klassiska arbetsytor, kan du lägga till endast personer till medlems- och administratörslistor. I de nya arbetsytorna kan du lägga till flera AD-säkerhetsgrupper, distributionslistor eller Office 365-grupper till de här listorna för enklare användarhantering. 
- Du kan skapa en organisations innehållspaket från en klassiska arbetsyta. Du kan inte skapa sådana från de nya arbetsytorna.
- Du kan använda en organisations innehållspaket från en klassiska arbetsyta. Du kan inte använda sådana från de nya arbetsytorna.

## <a name="workspace-contact-list"></a>Arbetsytan kontaktlista
Den nya **kontaktlista** funktionen kan du ange vilka användare informeras om problem uppstår i arbetsytan. Som standard angetts en användare eller grupp som som en arbetsyta administratören meddelas, men du kan anpassa listan. Användare eller grupper som visas i listan visas i användargränssnittet (UI) för att användare kan få hjälp relaterade till arbetsytan. 

Läs mer om den [inställningen arbetsytan kontaktlista](service-create-the-new-workspaces.md#workspace-contact-list).

## <a name="workspace-onedrive"></a>Workspace OneDrive
Arbetsytan OneDrive-funktionen kan du konfigurera en Office 365-grupp vars SharePoint-dokumentbibliotek file storage är tillgängligt för arbetsyteanvändare. Gruppen måste skapas utanför Power BI. 

Powerbi Synkronisera inte behörigheterna för användare eller grupper som är konfigurerade med arbetsyteåtkomst med Office 365-gruppmedlemskap. Det bästa sättet är att hantera arbetsyteåtkomst via samma Office 365-grupp vars fillagring som du konfigurerar i den här inställningen. 

Läs om hur du [konfigurera och komma åt arbetsytan OneDrive](service-create-the-new-workspaces.md#workspace-onedrive).  
   
## <a name="auditing"></a>Granskning
Följande aktiviteter som granskas av Power BI för nya arbetsytor för arbetsyta-upplevelse.

| Eget namn |   Åtgärdsnamn |
|---|---|
| Power BI-mapp skapades | CreateFolder |
| Power BI-mapp togs bort | DeleteFolder |
| Power BI-mapp uppdaterades | UpdateFolder |
| Power BI-mappåtkomst uppdaterades| UpdateFolderAccess |

Läs mer om [Power BI granskning](service-admin-auditing.md#activities-audited-by-power-bi).

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

Begränsningar att känna till:

- Arbetsytor kan innehålla högst 1 000 datauppsättningar eller 1 000 rapporter per datauppsättning. 
- En person med en Power BI Pro-licens kan vara medlem i en maximalt 1 000 arbetsytor.
- Power BI publisher för Excel stöds inte.

## <a name="workspace-features-that-work-differently"></a>Arbetsytefunktioner som fungerar annorlunda

Vissa funktioner fungerar annorlunda i de nya arbetsytorna jämfört med de aktuella arbetsytorna. Dessa skillnader är avsiktlig, baserat på feedback vi har fått från kunder och aktivera en mer flexibel metod för samarbete med arbetsytor:

- Tvingande licensiering: Publicera rapporter på arbetsytan avanmäla framtvingar befintliga licensieringsreglerna som kräver en Power BI Pro-licens för användare samarbeta i arbetsytor eller dela innehåll till andra i Power BI-tjänsten. Användare utan en Pro-licens du ser felet ”endast användare med Powre BI Pro-licenser kan publicera den här arbetsytan”.
- Medlemmar kan eller kan inte dela igen: ersätts med rollen Deltagare
- Skrivskyddade arbetsytor: I stället för att bevilja användare skrivskyddad åtkomst till en arbetsyta tilldelar du användare till en kommande läsarroll som ger liknande skrivskyddad åtkomst till innehållet i en arbetsyta.
- Det finns ingen knapp för att **lämna arbetsytan**.

## <a name="frequently-asked-questions"></a>Vanliga frågor och svar

**Är länkar till befintliga innehåll som påverkas av den nya arbetsytan uppleva GA**

Nej. Länkar till befintliga objekt i klassiska arbetsytor påverkas inte av den nya upplevelsen för arbetsytan. Allmän tillgänglighet (GA) av den nya upplevelsen för arbetsytan ändrar standardarbetsytan du skapar, men inte ändra befintliga arbetsytor. 

**Är de befintliga arbetsytor som uppgraderas till den nya arbetsyta upplevelsen med GA**

Nej. Ny arbetsyta upplevelse GA ändras bara typ av arbetsytan till den nya arbetsyta-miljön. Befintliga klassiska arbetsytor som är baserade på Office 365-grupper ändras inte.

**Arbetsytor fortfarande skapas automatiskt för Office 365-grupper**

Ja. Eftersom vi stöder båda typer av arbetsytor sida vid sida, fortsätter vi att lista alla Office 365-grupper som användaren har åtkomst till i listan över arbetsytor.

## <a name="next-steps"></a>Nästa steg
* [Skapa nya arbetsytor i Power BI](service-create-the-new-workspaces.md)
* [Skapa klassiska arbetsytor](service-create-workspaces.md)
* [Installera och använda appar i Power BI](service-create-distribute-apps.md)
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)
