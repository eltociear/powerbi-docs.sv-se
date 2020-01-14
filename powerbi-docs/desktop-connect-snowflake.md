---
title: Ansluta till ett Snowflake Computing-lager i Power BI Desktop
description: Anslut enkelt till ett Snowflake Computing-lager i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a62d1cf6d21df822265c3c41d4e74e74181b7051
ms.sourcegitcommit: 801d2baa944469a5b79cf591eb8afd18ca4e00b1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885189"
---
# <a name="connect-to-a-snowflake-computing-warehouse-in-power-bi-desktop"></a>Ansluta till ett Snowflake Computing-lager i Power BI Desktop
I Power BI Desktop kan du ansluta till en **Snowflake**-databas och använda underliggande data precis som andra datakällor i Power BI Desktop. 

> [!NOTE]
> Du *måste* också installera **Snowflake ODBC-drivrutinen** på datorer som använder anslutningsappen för **Snowflake**, med hjälp av arkitekturen som matchar installationen av  **Power BI Desktop**, 32-bitars eller 64-bitars. Följ länken nedan och [hämta lämplig Snowflake ODBC-drivrutin](https://go.microsoft.com/fwlink/?LinkID=823762).
> 
> 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Ansluta till ett Snowflake Computing-lager
Om du vill ansluta till ett **Snowflake**-lager väljer du **Hämta data** från **Start**-menyfliksområdet i Power BI Desktop. Välj **Databas** från kategorierna till vänster så ser du **Snowflake**.

![](media/desktop-connect-snowflake/connect_snowflake_2b.png)

I fönstret **Snowflake** som visas skriver eller klistrar du in namnet på ditt Snowflake-datalager i rutan och väljer **OK**. Observera att du kan välja att **importera** data direkt i Power BI, eller så kan du använda **DirectQuery**. Du kan läsa mer om att [använda DirectQuery](desktop-use-directquery.md).

![](media/desktop-connect-snowflake/connect_snowflake_3.png)

När du uppmanas, ange ditt användarnamn och lösenord.

![](media/desktop-connect-snowflake/connect-snowflake-4.png)

> [!NOTE]
> När du anger ditt användarnamn och lösenord för en viss **Snowflake**-server, använder Power BI Desktop samma autentiseringsuppgifter i efterföljande anslutningsförsök. Du kan ändra autentiseringsuppgifterna genom att gå till **Arkiv > Alternativ och inställningar > Inställningar för datakälla**.
> 
> 

Om du vill använda alternativet för Microsoft-konto kan du be din Snowflake-administratör att kontakta Snowflake om att gå med i den privata förhandsversionen för den här funktionen.

![Autentiseringstyp för Microsoft-konto i Snowflake.](media/desktop-connect-snowflake/connect-snowflake-6.png)


När du har anslutit, visas ett **navigator**-fönster som visar data som är tillgängliga på servern, där du kan välja ett eller flera element att importera och använda i **Power BI Desktop**.

![ODBC-fel 28000 orsakar ett fel vid anslutning.](media/desktop-connect-snowflake/connect_snowflake_5.png)

Du kan **Hämta** den markerade tabellen, vilket öppnar hela tabellen i **Power BI Desktop**, eller så kan du **Redigera** frågan, vilket öppnar **frågeredigeraren** så att du kan filtrera och begränsa uppsättningen av data som du vill använda och läsa in en förfinad datauppsättning till **Power BI Desktop**.

## <a name="next-steps"></a>Nästa steg
Det finns alla möjliga sorters data du kan ansluta till med Power BI Desktop. Kolla in följande resurser för mer information om datakällor:

* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till Excel-arbetsböcker i Power BI Desktop](desktop-connect-excel.md)   
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

