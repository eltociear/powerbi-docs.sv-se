---
title: Begränsningar för tjänstens huvudnamn
description: Begränsningar för tjänstens huvudnamn
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 06/06/2020
ms.custom: include file
ms.openlocfilehash: 569d7dfe251183962a14de1c42d85ee2e58950af
ms.sourcegitcommit: d8acf2fb0318708a3e8e1e259cb3747b0312b312
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86401676"
---
## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

* Tjänstens huvudnamn fungerar bara med [nya arbetsytor](../collaborate-share/service-create-the-new-workspaces.md).
* **Min arbetsyta** stöds inte när du använder tjänstens huvudnamn.
* Dedikerad kapacitet krävs vid flytt till produktion.
* Du kan inte logga in på Power BI-portal med tjänstens huvudnamn.
* Power BI-administratörsbehörighet krävs för att aktivera tjänstens huvudnamn i inställningarna för utvecklare i Power BI-administratörsportalen.
* Det går inte att använda tjänstens huvudnamn för [inbäddning för organisationens](../developer/embedded/embed-sample-for-your-organization.md) program.
* Hantering av [dataflöden](../transform-model/service-dataflows-overview.md) stöds inte.
* Tjänstens huvudnamn har för närvarande inte stöd för några administratörs-API:er.
* Vid användning av tjänsthuvudnamn med en [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview)-datakälla måste själva tjänsthuvudnamnet ha en Azure Analysis Services-instansbehörighet. Det fungerar inte att använda en säkerhetsgrupp som innehåller tjänsthuvudnamnet för detta ändamål.
* Tjänstens huvudnamn har för närvarande inte åtkomst till datakällorna i gatewayen. Det innebär att du inte kan lägga till tjänstens huvudnamn som daatakällsanvändare i gatewayen.
