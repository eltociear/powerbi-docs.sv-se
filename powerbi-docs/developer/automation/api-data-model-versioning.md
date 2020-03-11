---
title: Power BI versionshantering av datamodell
description: Datamodell som exponeras av en OData-tjänst
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 76947b1e311bbd1a21e09ce39461a70bed61d926
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79079610"
---
# <a name="data-model-versioning"></a>Versionshantering av datamodell

Den datamodell som exponeras av en OData-tjänst, till exempel Power BI-datamodellen, definierar ett avtal mellan OData-tjänsten och dess klienter. Tjänster får bara utöka sin modell till den grad att det inte bryter befintliga klienter. Större ändringar, till exempel borttagning av egenskaper eller ändring av typ för befintliga egenskaper, kräver att en ny tjänstversion anges på en annan tjänsts rot-URL för den nya modellen.  
  
Följande datamodelltillägg betraktas som säkra och kräver inte att tjänster lägger till en version vid sin startpunkt.  
  
* Lägga till en egenskap som kan ha värdet null eller har ett standardvärde: Om den har samma namn som en befintlig dynamisk egenskap så måste den ha samma typ (eller bastyp) som den befintliga dynamiska egenskapen  
* Lägga till en navigeringsegenskap som kan ha värdet null eller har ett samlingsvärde: om den har samma namn som en befintlig dynamisk navigeringsegenskap så måste den ha samma typ (eller bastyp) som den befintliga dynamiska navigeringsegenskapen  
* Lägga till en ny entitetstyp till modellen  
* Lägga till en ny komplex typ till modellen  
* Lägga till en ny entitetsuppsättning  
* Lägga till en ny singleton-instans  
* Lägga till en åtgärd, en funktion, en åtgärdsimport eller funktionsimport
* Lägga till en åtgärdsparameter som kan ha värdet null  
* Lägga till en typdefinition eller uppräkning  
* Lägga till en kommentar till ett modellelement som inte behöver tolkas av klienten för att interagera med tjänsten korrekt  
  
Klienter ***ska*** vara förberedda för tjänster för att göra sådana inkrementella ändringar i sin modell. I synnerhet ska klienter vara beredda att ta emot egenskaper och härledda typer som inte tidigare definierats av tjänsten.  
  
Tjänster ***ska inte*** ändra sin datamodell beroende på den autentiserade användaren. Om datamodellen är användar- eller användargruppberoende så måste alla ändringar vara säkra ändringar som det definieras i det här avsnittet när du jämför den fullständiga modellen till den modell som är synlig för användare med begränsade behörigheter.  
  
Mer information om standarder för OData-datamodellen finns i [OData Version 4.0 del 1: Protokollet Plus rättelser 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html).  
  
## <a name="see-also"></a>Se även
[Översikt över Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)