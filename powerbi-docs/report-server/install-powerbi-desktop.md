---
title: "Installera Power BI Desktop som har optimerats för Power BI-rapportservern"
description: "Lär dig att installera Power BI Desktop som har optimerats för Power BI-rapportservern"
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 06/20/2017
ms.author: asaxton
ms.openlocfilehash: 5fd5f41523ffcba03eb4749a9560922bcff42a7c
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="install-power-bi-desktop-optimized-for-power-bi-report-server"></a>Installera Power BI Desktop som har optimerats för Power BI-rapportservern
Lär dig att installera Power BI Desktop som har optimerats för Power BI-rapportservern.

Du måste hämta och installera Power BI Desktop som har optimerats för Power BI-rapportservern. Det här är en annan version av Power BI Desktop än den som används med Power BI-tjänsten. Detta behövs för att kontrollera att rapportservern kan interagera med en känd version av rapporter och modell. 

> [!NOTE]
> Power BI Desktop och Power BI Desktop som är optimerade för Power BI Report Server kan installeras sida vid sida.
> 
> 

## <a name="download-and-install"></a>Hämta och installera
Du kan hämta Power BI Desktop som är optimerat för Power BI-rapportservern från [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=837581) eller från webbportalen för rapportservern.

När du har hämtat installationsprogrammet kan du installera Power BI Desktop.

## <a name="verify-you-are-using-the-correct-version"></a>Kontrollera att du använder rätt version
Du kan kontrollera att du använder rätt version av Power BI Desktop genom att titta på startskärmen eller namnlisten i Power BI Desktop. Namnlisten kommer visas versionens lanseringsmånad och -år.

![](media/install-powerbi-desktop/powerbi-desktop-rs-title-bar.png "Namnlisten för Power BI Desktop")

Power BI Desktop-versionen för Power BI-tjänsten har inte månaden och året i namnlisten.

## <a name="file-extension-association"></a>Association för filtillägg
Om du har installerat både Power BI Desktop- och Power BI Desktop som är optimerade för Power BI-rapportservern på samma dator har den senaste installationen av Power BI Desktop en filassociation med .pbix. Det innebär att när du dubbelklickar på en pbix-fil så startas den Power BI Desktop-version som installerades senast.

Om du hade Power BI Desktop och sedan installerade Power BI Desktop som har optimerats för Power BI-rapportservern öppnas alla pbix-filer i Power BI Desktop som har optimerats för Power BI-rapportservern som standard. Om du hellre vill att Power BI Desktop ska vara standard för att öppna en pbix-fil ska du installera om Power BI Desktop från Power BI-tjänsten.

Du kan alltid öppna den version av Power BI Desktop som du vill använda först. Och sedan öppna filen i Power BI Desktop.

När du redigerar en Power BI-rapport från Power BI-rapportservern eller skapar en ny Power BI-rapport från webbportalen öppnas alltid rätt version av Power BI Desktop.

## <a name="next-steps"></a>Nästa steg
Nu när du har installerat Power BI Desktop kan du börja skapa Power BI-rapporter.

[Snabbstart: Skapa en Power BI-rapport för Power BI-rapportservern](quickstart-create-powerbi-report.md)  
[Kom igång med Power BI Desktop](../desktop-getting-started.md)  
Interaktiv inlärning: [Kom igång med Power BI Desktop](../guided-learning/gettingdata.yml#step-2)  
[Översikt i handbok, Power BI-rapportserver](user-handbook-overview.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

