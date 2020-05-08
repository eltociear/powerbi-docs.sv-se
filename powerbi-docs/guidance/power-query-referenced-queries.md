---
title: Referera till Power Query-frågor
description: Vägledning för att referera till Power Query-frågor.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 49601798ae920d956441c5580079625bf7408e07
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "78290591"
---
# <a name="referencing-power-query-queries"></a>Referera till Power Query-frågor

Den här artikeln är avsedd för dig som är datamodellerare som arbetar med Power BI Desktop. Den ger vägledning när du definierar Power Query-frågor som refererar till andra frågor.

Låt oss ta en titt på vad det innebär: _När en fråga refererar till en andra fråga är det som om stegen i den andra frågan kombineras med och körs före stegen i den första frågan._

Överväg flera frågor: **Fråga1** hämtar data från en webbtjänst och dess belastning är inaktiverad. **Fråga2**, **Fråga3** och **Fråga4** refererar till **Fråga1** och deras utdata läses in i datamodellen.

![Frågeberoendevyn som visar de frågor som beskrivs i föregående stycke.](media/power-query-referenced-queries/query-dependencies-web-service.png)

När datamodellen uppdateras förutsätts det ofta att Power Query hämtar resultatet från **Fråga1** och att den återanvänds av refererade frågor. Detta är felaktigt. I själva verket kör Power Query **Fråga2**, **Fråga3** och **Fråga4** separat.

Du kan tänka att **Fråga2** har stegen för **Fråga1** inbäddade i den. Det är fallet för **Fråga3** och **Fråga4**. Följande diagram visar en tydligare bild av hur frågorna körs.

![En modifierad version av vyn Fråga beroenden som visar Fråga2, Fråga3 och Fråga4. Var och en av de tre frågorna har Fråga1 inbäddad.](media/power-query-referenced-queries/query-dependencies-web-service-concept.png)

**Fråga1** körs tre gånger. Flera körningar kan leda till långsam datauppdatering och påverka datakällan negativt.

Användningen av funktionen [Table.Buffer ](/powerquery-m/table-buffer) i **Fråga1** eliminerar inte ytterligare datahämtning. Den här funktionen buffrar en tabell till minnet. Och den buffrade tabellen kan bara användas inom samma frågekörning. I exemplet, om **Fråga1** buffras när **Fråga2** körs kan inte buffrade data användas när **Fråga3** och **Fråga4** körs. De kommer själva att buffra data två gånger till. (Det här resultatet kan i själva verket förvärra negativa prestanda eftersom tabellen kommer att buffras av varje refererande fråga.)

> [!NOTE]
> Power Query-cachelagringsarkitekturen är komplex och det är inte fokus för den här artikeln. Power Query kan cachelagra data som hämtats från en datakälla. Men när en fråga körs kan den hämta data från datakällan mer än en gång.

## <a name="recommendations"></a>Rekommendationer

I allmänhet rekommenderar vi att du refererar frågor för att undvika duplicering av logik över dina frågor. Som beskrivs i den här artikeln kan den här designmetoden dock bidra till långsammare datauppdateringar och överbelastade datakällor.

Vi rekommenderar att du skapar ett [dataflöde](../service-dataflows-overview.md) istället. Ett dataflöde kan förbättra datauppdateringstiden och minska påverkan på dina datakällor.

Du kan utforma dataflödet för att kapsla in källdata och transformeringar. Eftersom dataflödet är ett beständigt datalager i Power BI-tjänsten är datahämtningen snabb. Även om frågor med referenser leder det till flera begäranden för dataflödet kan datauppdateringstiderna alltså förbättras.

I exemplet, om **Fråga1** har gjorts om som en dataflödesentitet kan **Query2**, **Query3** och **Query4** använda den som en datakälla. Med den här designen kommer entiteten som skrivs av **Fråga1** endast att utvärderas en gång.

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Dataförberedelser med självbetjäning i Power BI](../service-dataflows-overview.md)
- [Skapa och använda dataflöden i Power BI](../service-dataflows-create-use.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
