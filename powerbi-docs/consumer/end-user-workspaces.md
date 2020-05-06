---
title: Så här organiseras innehållet på arbetsytor
description: Lär dig mer om arbetsytor och arbetsytans roller
author: mihart
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 801b5cf5400bbe1cc0487eef596ea3d1cdc5fb1e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82120209"
---
# <a name="collaborate-in-workspaces"></a>Samarbeta på arbetsytor

 *Arbetsytor* är platser för samarbete kollegor emellan kring ett speciellt innehåll. Arbetsytor skapas av Power BI-*designer* i syfte att lagra samlingar med instrumentpaneler och rapporter. Designern kan sedan paketera samlingarna i *appar* och distribuera dem till hela organisationen eller till vissa personer eller grupper. 

 Alla som använder Power BI-tjänsten har också tillgång till **Min arbetsyta**.  Min arbetsyta är din personliga sandbox-miljö där du själv kan skapa innehåll.

 Du kan se dina arbetsytor från **startsidan** för Power BI eller genom att välja **Arbetsyta** eller **Min arbetsyta** i det vänstra navigeringsfönstret.

 ![navigeringsfönster som visar två typer av arbetsytor](media/end-user-workspaces/power-bi-home.png)

## <a name="types-of-workspaces"></a>Typer av arbetsytor
Under **Min arbetsyta** lagras allt innehåll som du äger och skapar. Du kan se det som det personliga utvecklingsutrymme eller ett område för ditt eget innehåll. För många Power BI-*användare* är **Min arbetsyta** tom eftersom de inte skapar nytt innehåll i sin yrkesroll. *Användare* använder per definition data som skapats av andra till att fatta affärsbeslut. Om det visar sig att du behöver skapa innehåll ska du läsa [Power BI-artiklarna för designers](../create-reports/index.yml) i stället.

På **apparbetsytan** finns allt innehåll för den aktuella appen. När en *designer* skapar en app sammanställer de allt innehåll som krävs för att appen ska kunna användas. Innehållet kan omfatta instrumentpaneler, rapporter och datamängder. Alla appar har inte samma sorts innehåll. En app kanske bara innehåller en instrumentpanel, en annan tre av varje innehållstyp och någon kan innehålla tjugo rapporter. Det beror helt på vad *designern* tar med i appen. Normalt innehåller dock inte apparbetsytor för *användare* några datamängder.

Apparbetsytan för försäljningssiffror nedan innehåller tre rapporter och en instrumentpanel. 

![navigeringsfönster som visar två typer av arbetsytor](media/end-user-workspaces/power-bi-app-workspace.png)

## <a name="roles-in-the-workspaces"></a>Roller på arbetsytorna

Rollerna avgör vad du kan göra på en arbetsyta, så att olika team kan samarbeta.  När du beviljar åtkomst till en ny arbetsyta lägger *designrarna* till individer eller grupper till någon av arbetsyterollerna: **Tittare**, **Medlem**, **Deltagare** eller **Administratör**. 


Som Power BI-*konsument* interagerar du vanligtvis på arbetsytorna med hjälp av rollen **Läsare**. Men en *designer* kan också tilldela dig rollen **Medlem** eller **Deltagare**. Med rollen Läsare kan du visa och interagera med innehåll (instrumentpaneler, rapporter, appar) som skapats av andra och delats med dig. Och eftersom läsarrollen inte kommer åt den underliggande datamängden är det ett säkert sätt att interagera med innehåll och du behöver inte oroa dig för att påverka underliggande data.


En detaljerad lista över vad du kan göra som *konsument* med läsarrollen finns i [Power BI-funktioner för konsumenter](end-user-features.md).


### <a name="workspace-roles"></a>Arbetsyteroller
Här är funktionerna för de fyra rollerna: administratörer, medlemmar, deltagare och läsare. För alla dessa funktioner (utom visning och interaktion) krävs en Power BI Pro-licens.

|Kapacitet   | Admin  | Medlem  | Deltagare  | Läsare |
|---|---|---|---|---|
| Uppdatera och ta bort arbetsytan.  | X  |   |   |   | 
| Lägga till/ta bort personer, inklusive andra administratörer.  | X  |   |   |   |
| Lägga till medlemmar eller andra med lägre behörighet.  |  X | X  |   |   |
| Publicera och uppdatera en app. |  X | X  |   |   |
| Dela ett objekt eller dela en app.<sup>1</sup> |  X | X  |   |   |
| Tillåta att andra delar objekt igen.<sup>1</sup> |  X | X  |   |   |
| Framhäva appar på kollegors startsida |  X | X  |   |   |
| Framhäva instrumentpaneler och rapporter på kollegors startsida |  X | X  | X |   |
| Skapa, redigera och ta bort innehåll på arbetsytan.  |  X | X  | X  |   |
| Publicera rapporter till arbetsytan och ta bort innehåll.  |  X | X  | X  |   |
| Skapa en rapport på en annan arbetsyta baserat på en datamängd i den här arbetsytan.<sup>1</sup> |  X | X  | X  |   |
| Kopiera en rapport. | X | X | X |  |
| Visa och interagera med ett objekt.<sup>2</sup> |  X | X  | X  | X  |
| Läs data som lagrats på arbetsytedataflöden | X | X | X | X |

1. Deltagare och medlemmar kan dela objekt i en arbetsyta om de har omdelningsbehörighet.

2. Även om du inte har en Power BI Pro-licens kan du visa och interagera med objekt i Power BI-tjänsten om objekten finns i en arbetsyta i en Premium-kapacitet.

## <a name="licensing-workspaces-and-capacity"></a>Licensiering, arbetsytor och kapacitet
Licensiering spelar också en stor roll när du ska fastställa vad man kan och inte kan göra på en arbetsyta. För många funktioner krävs det att användaren har en Power BI *Pro*-licens. De flesta *konsumenter* arbetar med en *kostnadsfri* licens. 

Om du har en kostnadsfri licens och arbetsytan lagras i *Premium-kapaciteten* kan du visa och interagera med innehållet på den arbetsytan. En rombformad ikon identifierar arbetsytor och appar som lagras i Premium-kapaciteten.

![Valda arbetsytor](media/end-user-workspaces/power-bi-diamond.png) Mer information finns i [Vilken licens har jag?](end-user-license.md).



## <a name="next-steps"></a>Nästa steg
* [Appar i Power BI](end-user-apps.md)    

* Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)

