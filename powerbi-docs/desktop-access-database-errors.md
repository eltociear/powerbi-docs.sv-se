---
title: "Lös Access- och .xls-importproblem i Power BI Desktop"
description: "Lösa problem när du importerar Access-databaser och .XLS-kalkylblad i Power BI Desktop och Power Query"
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
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 47abc345d773fe9274a1dc814b7799a956e909fc
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="resolve-issues-importing-access-and-xls-files-in-power-bi-desktop"></a>Lösa problem när du importerar Access- och. XLS-filer i Power BI Desktop
I **Power BI Desktop** använder både **Access-databaser** och tidigare versioner av **Excel-arbetsböcker** (.XLS filer av typen Excel 2007-2003) *Access Database Engine*. Det finns tre vanliga situationer som kan förhindra att Access Database Engine fungerar korrekt:

### <a name="situation-1-no-access-database-engine-installed"></a>Situation 1: Ingen Access Database Engine har installerats
När felmeddelandet i Power BI Desktop indikerar att Access Database Engine inte har installerats, måste du installera Access Database Engine-versionen, 32-bitars eller 64-bitars, som matchar din Power BI Desktop-version. Du kan installera Access Database Engine från [den här platsen](http://www.microsoft.com/en-us/download/details.aspx?id=13255).

>[!NOTE]
>Om den installerade Access Database Engine-bitarsversionen skiljer sig från din Microsoft Office-installation kan Office-program inte använda Access Database Engine.

### <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>Fall 2: Access Database Engine-bitarsversionen (32-bitars eller 64-bitars) skiljer sig från din Power BI Desktop-bitarsversion
Den här situationen ofta uppstår när den installerade versionen av Microsoft Office är 32-bitars och versionen av Power BI Desktop installerat 64-bitars. Motsatsen leder till samma problem (om du använder en Office 365-prenumeration, se **Situation 3** för ett annat problem och åtgärder). Något av följande lösningar kan åtgärda versionsmatchningsfelet:

1. Ändra versionen av Power BI Desktop så att den matchar versionen av Microsoft Office-installationen. Om du vill ändra versionen av Power BI Desktop, avinstallera Power BI Desktop och installera sedan versionen av Power BI Desktop som matchar din Office-installation. Om du vill ladda ned den senaste versionen av Power BI Desktop går du till nedladdningssidan för skrivbord och väljer **Avancerade alternativ för nedladdning**.
   
   ![](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
   På sidan download väljer du språk och väljer sedan knappen **Hämta**. På skärmen som visas markerar du kryssrutan bredvid PBIDesktop.msi för 32-bitarsversionen eller PBIDesktop_x64.msi för 64-bitarsversionen. I följande skärmbild väljs 64-bitarsversionen.
   
   ![](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >När du använder 32-bitarsversionen av Power BI Desktop när du skapade modeller för mycket stora mängder data kan det uppstå minnesproblem.
2. Ändra versionen av Microsoft Office så att den matchar versionen av Power BI Desktop-installationen. Om du vill ändra versionen av Microsoft Office, avinstallera Microsoft Office och installera sedan versionen av Office som matchar din Power BI Desktop-installation.
3. Om felet inträffade när du försökte att öppna en .XLS-fil (en Excel 2007-2003-arbetsbok) kan du undvika att använda Access Database Engine genom att öppna .XLS-filen i Excel och spara den som en XLSX-fil.
4. Om föregående tre lösningar är inte möjliga, är det möjligt att installera båda versioner av Access Database Engine, men detta är *inte* en rekommenderad lösning. Om du installerar båda versioner löser du problemet för Power Query för Excel och Power BI Desktop, men skapar fel och problem för program som automatiskt (som standard) använder samma bitarsversion av Access Database Engine som först installerades. För att installera båda bitarsversioner av Access Database Engine, [hämta](http://www.microsoft.com/en-us/download/details.aspx?id=13255) båda versionerna och kör var och en av dem med hjälp av växeln */passive*. Till exempel:
   
       c:\users\joe\downloads\AccessDatabaseEngine.exe /passive
   
       c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive

### <a name="situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription"></a>Situationen 3: Problem med åtkomst eller .XLS-filer med Office 365-prenumerationen
Om du använder Office 365-prenumerationen om **Office 2013** eller **Office 2016**, Access Database Engine-providern är registrerad på en virtuell registerplats som är *endast* Office-processer har åtkomst till. Därför kan Mashup-motorn, (som ansvarar för att köra processer som inte är Office 365 Excel och Power BI Desktop) som inte är en Office-process, inte använda Access Database Engine-providern.

För att åtgärda den här situationen kan du hämta och installera Access Database Engine redistributable som matchar bitversionen av din Power BI Desktop (se tidigare avsnitt för mer information om bitversioner).

Nedladdningslänk: [Hämta Access Database Engine](http://www.microsoft.com/en-us/download/details.aspx?id=13255).

### <a name="other-situations-that-cause-import-issues"></a>Andra situationer som kan orsaka importeringsfel
Vi strävar efter att täcka så många problem med åtkomst eller .XLS-filer som möjligt. Om det uppstår ett problem som inte beskrivs i den här artikeln kan du skicka en fråga om problemet till [Power BI-supporten](https://powerbi.microsoft.com/support/). Vi tittar regelbundet på problem som kan påverka många kunder och inkluderar dem i våra artiklar.

