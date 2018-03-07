---
title: "Felsök panelfel"
description: "Vanliga fel som kan uppstå när en panel försöker uppdatera"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 26f92ee511b3a03f8e08aae0a33bb6f60c12908b
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="troubleshooting-tile-errors"></a>Felsök panelfel
Nedan visas vanliga fel som kan uppstå med paneler tillsammans med en förklaring.

> [!NOTE]
> Om det uppstår ett fel som inte finns i listan nedan och det orsakar problem, kan du be att få hjälp på [community-webbplatsen](http://community.powerbi.com/) eller så kan du skapa ett [supportärende](https://powerbi.microsoft.com/support/).
> 
> 

## <a name="errors"></a>Fel
**Power BI påträffade ett oväntat fel vid inläsning av modellen. Försök igen senare.**
eller **det gick inte att hämta datamodellen. Kontakta instrumentpanelens ägare och säkerställ att datakällorna och modellen finns och är tillgängliga.**

Det gick inte att komma åt dina data eftersom datakällan inte kan nås. Detta kan inträffa om datakällan har tagits bort, fått ett nytt namn, flyttats, offline eller behörigheten har ändrats. Kontrollera att källan fortfarande finns på den plats vi pekar på och att du fortfarande har behörighet att komma åt den. Om det inte är problemet, kan källan vara långsam. Försök igen senare under en tid när belastningen på källan är mindre. Om det är en lokal källa, kan dataägaren kanske ge dig mer information.

**Du har inte behörighet att visa den här panelen eller öppna arbetsboken.**

Kontakta instrumentpanelens ägare och säkerställ att datakällorna och modellen finns och är tillgängliga för ditt konto.

**Datastrukturer måste innehålla minst en grupp eller beräkning som producerar data. Kontakta instrumentpanelens ägare.**

Vi har inte några data att visa eftersom frågan är tom. Försök att lägga till fält från fältlistan till ditt visuella objekt och fästa det på nytt.

**Det går inte att visa data eftersom Power BI inte kan fastställa relationen mellan två eller flera fält.**

Du försöker använda två eller flera fält från tabeller som inte är relaterade. Du måste ta bort dessa fält från det visuella objektet och därefter skapa en relation mellan tabellerna. När du har gjort det, kan du lägga tillbaka fälten till det visuella objektet. Detta kan göras i Power BI Desktop eller Power Pivot för Excel. [Läs mer](desktop-create-and-manage-relationships.md)

**Grupperna i primäraxeln och sekundäraxeln överlappar varandra. Grupperna i primäraxeln kan inte ha samma nycklar som grupper på sekundäraxeln.**

Detta är vanligtvis ett övergående problem. Detta sker vanligtvis när du flyttar grupper från rader till kolumner. I det här fallet bör felet försvinna när du har flyttat alla grupper. Om du fortfarande ser meddelandet, försök växla fält mellan rader och kolumner eller axelförklaringen eller ta bort fält från det visuella objektet.  

**Det här visuella objektet har överskridit de tillgängliga resurserna. Försök filtrera för att minska mängden data som visas.**

Ditt visuella objekt har försökt att fråga för mycket data för att vi ska kunna slutföra resultatet med de tillgängliga resurserna. Försök att filtrera det visuella objektet för att minska mängden data i resultatet.

**Det går inte att identifiera följande fält: {0}. Uppdatera det visuella objektet med fält som finns i datauppsättningen.**

Fältet har förmodligen tagits bort eller bytt namn. Du kan ta bort det brutna fältet från det visuella objektet, lägg till ett annat fält och fästa det igen.

**Det gick inte att hämta data för det här visuella objektet. Försök igen senare.**

Detta är vanligtvis ett övergående problem. Kontakta supporten om du försöker igen senare och fortfarande ser det här meddelandet.

## <a name="contact-support"></a>Kontakta supporten
Om du fortfarande har problem, kan du [kontakta supporten](https://support.powerbi.com) för att undersöka vidare.

## <a name="next-steps"></a>Nästa steg
[Felsökning av den lokala datagatewayen](service-gateway-onprem-tshoot.md)  
[Felsök den personliga Power BI-gatewayen](service-admin-troubleshooting-power-bi-personal-gateway.md)  
Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

