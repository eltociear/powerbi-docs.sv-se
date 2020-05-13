---
title: Ansluta till Snowflake i Power BI
description: Snowflake med enkel inloggning för Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: gepopell
LocalizationGroup: Connect to services
ms.openlocfilehash: 5e5519e30be30d6367791d1b6822196b407a21b1
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83300331"
---
#  <a name="connecting-to-snowflake-in-power-bi-service"></a>Ansluta till Snowflake i Power BI-tjänsten

## <a name="introduction"></a>Introduktion

Att ansluta till Snowflake i Power BI-tjänsten skiljer sig bara från andra anslutningar på ett enda sätt, vilket är att en ytterligare funktion erbjuds för AAD (med ett alternativ för enkel inloggning). Olika delar av integreringen kräver olika administrativa roller för Snowflake, Power BI och Azure. Du kan också välja att aktivera AAD-autentisering utan att använda enkel inloggning. Grundläggande autentisering fungerar på samma sätt som för andra anslutningsprogram i tjänsten.

Gör så här om du är intresserad av att konfigurera AAD-integrering och även aktivera enkel inloggning:
* Om du är Snowflake-administratör läser du artikeln [Power BI enkel inloggning till Snowflake – Komma igång](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html) i Snowflake-dokumentationen.
* (Enkel inloggning) Om du är Power BI-administratör kan du läsa avsnittet Konfigurera Power BI-tjänsten – Administratörsportal
* (Enkel inloggning) Om du skapar Power BI-datamängder kan du läsa avsnittet Konfigurera Power BI-tjänsten – Aktivera en datamängd

## <a name="power-bi-service-configuration"></a>Konfigurera Power BI-tjänsten

### <a name="admin-portal"></a>Administratörsportal

Om du vill aktivera enkel inloggning måste klientorganisationens administratör gå till administratörsportalen och godkänna att Power BI AAD-autentiseringsuppgifter skickas till Snowflake.

![Administratörsinställning för enkel inloggning till Snowflake](media/service-connect-snowflake/snowflakessotenant.png)

Gå till administratörsportalen, välj ”Klientinställningar” i sidofältet och rulla ned till ”Integrationsinställningar” så ser du alternativet ”Snowflake enkel inloggning”.

Som vi sade måste du alltså aktivera detta manuellt för att kunna skicka din AAD-token till Snowflake-servrarna. Aktivera det genom att klicka på ”Inaktiverat”, trycka på Verkställ och vänta tills inställningarna börjar gälla. Det kan ta upp till en timme för tjänsten att sprida konfigurationen.

När det är färdigt kan du använda rapporter med enkel inloggning.

### <a name="configuring-a-dataset-with-aad"></a>Konfigurera en datamängd med AAD

När en rapport som baseras på Snowflake-anslutningsprogrammet har publicerats på webben måste den som skapat datamängden gå till lämplig arbetsyta i Power BI-webbtjänsten, välja Datamängder och sedan Inställningar (under menyn ... för ytterligare åtgärder bredvid den aktuella datamängden).

På grund av hur Power BI är utformat så fungerar enkel inloggning bara när inga datakällor körs via den lokala datagatewayen.

* Om du bara använder en Snowflake-källa i din datamodell kan du använda enkel inloggning om du väljer att inte använda den lokala datagatewayen
* Om du använder en Snowflake-källa tillsammans med en annan källa kan du använda enkel inloggning om ingen av källorna använder den lokala datagatewayen
* Om du använder en Snowflake-källa via den lokala datagatewayen, så stöds inte AAD-autentiseringsuppgifter för närvarande. Det här kan vara relevant om du försöker komma åt ett virtuellt nätverk från en enskild IP-adress där gatewayen är installerad, snarare än från hela IP-intervallet för Power BI.
* Om du använder en Snowflake-källa tillsammans med en annan källa som behöver en gateway måste du även använda Snowflake via den lokala datagatewayen, och då kan du inte använda enkel inloggning.

Du kan läsa mer om att använda den lokala datagatewayen i artikeln [Vad är en lokal datagateway?](https://docs.microsoft.com/power-bi/service-gateway-onprem)

Om du inte använder gatewayen är du färdig. Om du har autentiseringsuppgifter för Snowflake konfigurerade i din lokala datagateway, men bara använder den datakällan i din modell, kan du klicka på växlingsknappen på sidan Inställningar för datamängd och stänga av gatewayen för datamodellen.

![Inställning för att stänga av gatewayen](media/service-connect-snowflake/snowflake_gateway_toggle_off.png)

Den som skapat datamängden måste välja Autentiseringsuppgifter för datakälla och logga in. Du kan logga in datamängden i Snowflake med grundläggande autentiseringsuppgifter eller OAuth2-autentiseringsuppgifter (AAD). Om du väljer att använda AAD kan datamängden aktiveras för enkel inloggning. När den första användaren loggar in i Snowflake för datamängden måste användaren välja alternativet att alla andra använder sina OAuth2-autentiseringsuppgifter till att hämta data. Det här aktiverar enkel AAD-inloggning. Oavsett om den första användaren loggar in med grundläggande autentisering eller OAuth2 (AAD) så är det AAD-autentiseringsuppgifterna som skickas för enkel inloggning. 

![Datamängdsinställning för enkel inloggning till Snowflake](media/service-connect-snowflake/snowflakessocredui.png)

När det här är klart ska eventuella ytterligare användare automatiskt använda sin AAD-autentisering för anslutning till data från Snowflake-datamängden.

Om du väljer att inte aktivera enkel inloggning så kommer de användare som uppdaterar rapporten att använda autentiseringsuppgifterna för den användare som loggade in, precis som i de flesta andra Power BI-rapporter.

### <a name="troubleshooting"></a>Felsökning

Om du får problem med integreringen kan du läsa i [felsökningsguiden](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html#troubleshooting) för Snowflake.

