---
title: Power BI och utgående Azure-data
description: Förstå avgifter för utgående Azure-utgående och Power BI baserat på klientorganisationens plats och Power BI Premium
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from databases
ms.openlocfilehash: 720ef2f059c3c87be84c3d8db98e89400c161ad0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514412"
---
# <a name="power-bi-and-azure-egress"></a>Power BI och utgående Azure-data

När du använder Power BI med Azure-datakällor kan du undvika avgifter för utgående Azure-data genom att se till att din Power BI-klientorganisation är i samma region som dina Azure-datakällor.

När din Power BI-klientorganisation distribueras i samma Azure-region där du distribuerar dina datakällor debiteras du inte några avgifter för utgående data för schemalagd uppdatering och DirectQuery-interaktioner. 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>Fastställa var Power BI-klientorganisationen finns

Om du vill ta reda på var din Power BI-klientorganisation finns kan du läsa artikeln [Var finns min Power BI-klientorganisation?](service-admin-where-is-my-tenant-located.md).

För Power BI Premium Multi-Geo-kunder gäller att om Power BI-klientorganisationen inte är på den optimala platsen för vissa av dina Azure-baserade datakällor kan du distribuera Power BI Premium Multi-Geo i önskad Azure-region och dra fördel av att ha din Power BI-klientorganisation och Azure-datakällor i samma Azure-region.

## <a name="next-steps"></a>Nästa steg

Mer information om Power BI Premium och Multi-Geo finns i följande resurser:

* [Vad är Microsoft Power BI Premium?](service-premium-what-is.md)
* [Så här köper du Power BI Premium](service-admin-premium-purchase.md)
* [Multi-Geo-stöd för Power BI Premium (förhandsversion)](service-admin-premium-multi-geo.md)
* [Var finns min Power BI-klient?](service-admin-where-is-my-tenant-located.md)
* [Vanliga frågor och svar om Power BI Premium](service-premium-faq.md)


