---
title: "Hantera din datakälla – SQL"
description: "Hantera den lokala datagatewayen och datakällorna som tillhör denna gateway."
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 8f8a090714a7dabcc189304428f03161f3d47abc
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="manage-your-data-source---sql-server"></a>Hantera din datakälla – SQL Server
När du har installerat den lokala datagatewayen kan du lägga till datakällor som kan användas med gatewayen. I den här artikeln tittar vi på hur du kan använda gatewayer och datakällor. Du kan antingen använda SQL Server-datakällan för schemalagd uppdatering eller för DirectQuery.

## <a name="download-and-install-the-gateway"></a>Ladda ned och installera gatewayen
Du kan ladda ned gatewayen från Power BI-tjänsten. Välj **Nedladdningar** > **Datagateway** eller gå till [nedladdningssidan för gatewayer](https://go.microsoft.com/fwlink/?LinkId=698861).

![](media/service-gateway-enterprise-manage-sql/powerbi-download-data-gateway.png)

## <a name="add-a-gateway"></a>Lägga till en gateway
Du lägger till en gateway genom att helt enkelt [ladda ned](https://go.microsoft.com/fwlink/?LinkId=698861) och installera gatewayen på en server i din miljö. När du har installerat gatewayen visas den i listan med gatewayer under **Hantera gatewayer**.

> [!NOTE]
> **Hantera gatewayer** visas inte förrän du är administratör för minst en gateway. Detta inträffar när du har lagts till som en administratör för en gateway, eller om du installerar och konfigurerar en gateway själv.
> 
> 

## <a name="remove-a-gateway"></a>Ta bort en gateway
Om en gateway tas bort raderas även alla datakällor under gatewayen.  Detta bryter också anslutningen till alla instrumentpaneler och rapporter som är beroende av dessa datakällor.

1. Välj kugghjulsikonen ![](media/service-gateway-enterprise-manage-sql/pbi_gearicon.png) i det övre högra hörnet > **Hantera gatewayer**.
2. Gateway > **Ta bort**
   
   ![](media/service-gateway-enterprise-manage-sql/datasourcesettings7.png)

## <a name="add-a-data-source"></a>Lägga till en datakälla
Du kan lägga till en datakälla genom att antingen välja en gateway och klicka på **Lägg till datakälla** eller gå till Gateway > **Lägg till datakälla**.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings1.png)

Du kan sedan välja **Typ av datakälla** i listan.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> Om du använder DirectQuery har gatewayen endast stöd för **SQL Server 2012 SP1** och senare versioner.
> 
> 

Du kan fylla i informationen för datakällan med **Server** och **Databas**.  

Du måste också välja en **Autentiseringsmetod**.  Det kan antingen vara **Windows** eller **Grundläggande**.  Välj **Grundläggande** om du tänker använda SQL-autentisering i stället för Windows-autentisering. Ange sedan de autentiseringsuppgifter som ska användas för datakällan.

> [!NOTE]
> Alla frågor till datakällan kommer att köras med autentiseringsuppgifterna, såvida inte enkel inloggning (SSO) med Kerberos har konfigurerats och aktiverats för datakällan. När SSO används kommer de importerade datauppsättningarna använda lagrade autentiseringsuppgifter, medan DirectQuery-datauppsättningar använder den aktuella Power BI-användaren för att köra frågor. Mer information finns i huvudartikeln om lokala datagatewayer där du lär dig mer om hur [autentiseringsuppgifter](service-gateway-onprem.md#credentials) lagras, eller i artikeln som beskriver hur du [använder Kerberos för SSO (enkel inloggning) från Power BI till lokala datakällor](service-gateway-kerberos-for-sso-pbi-to-on-premises-data.md).
> 
> 

![](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

Klicka på **Lägg till** när allt har fyllts i.  Nu kan du använda den här datakällan för schemalagd uppdatering, eller DirectQuery mot en lokal SQL Server. *Anslutningen lyckades* visas.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>Avancerade inställningar
Du kan konfigurera sekretessnivån för datakällan. Detta styr hur data kan kombineras. Det används endast vid schemalagd uppdatering. Det gäller inte för DirectQuery. [Läs mer](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)

![](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="remove-a-data-source"></a>Ta bort en datakälla
Om en datakälla tas bort bryts alla anslutningar till instrumentpaneler och rapporter som är beroende av den.  

Ta bort en datakälla genom att gå till Datakälla > **Ta bort**.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings6.png)

## <a name="manage-administrators"></a>Hantera administratörer
På fliken Administratörer för gatewayen kan du lägga till och ta bort användare (eller säkerhetsgrupper) som kan administrera gatewayen.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings8.png)

## <a name="manage-users"></a>Hantera användare
På datakällans flik Användare kan du lägga till och ta bort användare eller säkerhetsgrupper som kan använda datakällan.

> [!NOTE]
> Användarlistan styr enbart vem som har behörighet att publicera rapporter. Rapportägare kan skapa instrumentpaneler eller innehållspaket och dela dem med andra användare.
> 
> 

![](media/service-gateway-enterprise-manage-sql/datasourcesettings5.png)

## <a name="using-the-data-source"></a>Använda datakällan
När du har skapat datakällan blir den tillgänglig för användning med antingen DirectQuery-anslutningar eller genom schemalagd uppdatering.

> [!NOTE]
> Server- och databasnamnen måste vara samma mellan Power BI Desktop och datakällan i den lokala datagatewayen!
> 
> 

Länken mellan din datauppsättning och datakällan i gatewayen är baserad på servernamnet och databasnamnet. Dessa måste överensstämma. Om du exempelvis anger en IP-adress för servernamnet i **Power BI Desktop**, måste du använda IP-adressen för datakällan i gatewaykonfigurationen. Om du använder *SERVER\INSTANCE* i Power BI Desktop måste du använda samma i datakällan som konfigurerats för gatewayen.

Detta gäller både DirectQuery och schemalagd uppdatering.

### <a name="using-the-data-source-with-directquery-connections"></a>Använda datakällan med DirectQuery-anslutningar
Du måste kontrollera att server- och databasnamnet är likadana i **Power BI Desktop** och den konfigurerade datakällan för gatewayen. Du måste också kontrollera att användaren finns med på fliken **Användare** för datakällan för att DirectQuery-datauppsättningar ska kunna publiceras. Valet för DirectQuery inträffar i Power BI Desktop när du importerar data första gången. [Läs mer](desktop-use-directquery.md)

När du har publicerat, antingen från Power BI Desktop eller **Hämta Data**, borde dina rapporter fungera. Det kan ta ett par minuter efter att du har skapat datakällan i gatewayen innan anslutningen kan användas.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Använda datakällan med schemalagd uppdatering
Om du finns med på fliken **Användare** i den datakälla som konfigurerats i gatewayen, samt om server- och databasnamnen matchar, visas gatewayen som ett alternativ för schemalagd uppdatering.

![](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Nästa steg
* [Lokal datagateway](service-gateway-onprem.md)  
* [Lokal datagateway – på djupet](service-gateway-onprem-indepth.md)  
* [Felsökning av den lokala datagatewayen](service-gateway-onprem-tshoot.md)
* [Använda Kerberos för SSO (enkel inloggning) från Power BI till lokala datakällor](service-gateway-kerberos-for-sso-pbi-to-on-premises-data.md). 
* Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

