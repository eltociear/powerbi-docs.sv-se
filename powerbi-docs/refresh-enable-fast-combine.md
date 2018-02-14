---
title: "Inaktivera sekretessinställningar"
description: "Så här aktiverar du snabb kombinering inom den personliga gatewayen för att inaktivera sekretessinställning för uppdatering."
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
ms.date: 02/06/2018
ms.author: davidi
ms.openlocfilehash: 5d754dbdd5d52e7a5b123755015e656d9fb2cea2
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/09/2018
---
# <a name="disable-privacy-setting-in-power-bi-gateway---personal"></a>Inaktivera sekretessinställningarna i Power BI Gateway – Personal
> [!NOTE]
> Det finns en ny version av den personliga gatewayen för Power BI, det vill säga **lokal datagateway (personligt läge)**. Följande artikel beskriver den tidigare versionen av personlig gateway, **Power BI Gateway - Personal**, som dras tillbaka och slutar fungera från och med den 31 juli 2017. Information om den nya versionen av personlig gateway, inklusive hur du installerar den nya versionen finns i artikeln [**lokal datagateway (personligt läge)**](service-gateway-personal-mode.md). Snabb kombinering är också tillgängligt i den nya versionen av personlig gateway och beskrivs i den här artikeln.
> 
> 

Du får följande felmeddelande baserat på sekretessinställningarna för dina datakällor när de använda med den personliga gatewayen.

> *Ett fel inträffade vid bearbetningen av informationen i datauppsättningen.*
> 
> *[Det går inte att kombinera data] &lt;frågedel&gt;/&lt;... &gt; / &lt;... &gt; ansluter till datakällor som har sekretessnivåer som inte kan användas tillsammans. Återskapa den här datakombinationen.*
> 
> 

Du kan undvika det här felet kan du aktivera **Snabb kombinering**. **Snabb kombinering** kommer att ignorera sådana inställningar så att de olika datakällorna kan kombineras.

> [!NOTE]
> Sekretessnivåerna åsidosätts när du kombinerar data. Det kan göra att känsliga eller konfidentiella data exponeras mot en annan datakälla när du kombinerar data.
> 
> 

## <a name="what-is-fast-combine"></a>Vad är snabb kombinering?
Se mer information om sekretessnivåer och snabb kombinering i [Sekretessnivåer](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540). Som standard är sekretessnivån inställd på privat, vilket kan leda till ovanstående fel. Det beror på att den privata inställningen isolerar datakällan från andra källor. Ett exempel på var detta kan leda till problem är parameterbaserade frågor som hämtar indata från andra datakällor.

När du aktiverar snabb kombinering åsidosätts sekretessinställningen så att körningen kan utföras.

## <a name="turn-on-fast-combine"></a>Aktivera snabb kombinering
Du kan använda följande steg för att aktivera snabb kombinering som din personliga gateway. Den lokala datagatewayen har inte den här inställningen.

1. Öppna **ConnectorConfig.xml**.  Den kan finnas på en av två platser på din dator.  Om du är administratör på datorn är det följande plats.
   
    <pre><code>C:\Program Files\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
   
    Om du inte är administratör är det följande plats.
   
    <pre><code>C:\Users\[username]\AppData\Local\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
    
2. Lägg till elementet **&lt;EnableFastCombine&gt;** med värdet sant till konfigurationsfilen. När du lägger till det här elementet aktiveras **snabb kombinering**.
   
   <pre><code>&lt;EnableFastCombine&gt;true&lt;/EnableFastCombine&gt;</code></pre>
   
   ![](media/refresh-enable-fast-combine/configfile.png)
3. Avsluta och starta om konfigurationsskärmen för gatewayen.
4. Du ser en status som visar att snabb kombinering har aktiverats.
   
   ![](media/refresh-enable-fast-combine/fastcombineenabled.png)

## <a name="turn-off-fast-combine"></a>Inaktivera snabb kombinering
1. Öppna **ConnectorConfig.xml**.  Den kan finnas på en av två platser på din dator.  Om du är administratör på datorn är det följande plats.
   
    <pre><code>C:\Program Files\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
   
    Om du inte är administratör är det följande plats.
   
    <pre><code>C:\Users\[username]\AppData\Local\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>

2. Ta bort **&lt;EnableFastCombine&gt;**-elementet från konfigurationsfilen. När du lägger till det här elementet inaktiveras **snabb kombinering**.
3. Avsluta och starta om konfigurationsskärmen för gatewayen.
4. Du ser inte längre en status som visar att **snabb kombinering** har aktiverats.

## <a name="next-steps"></a>Nästa steg
[Lokal datagateway (personligt läge) – en ny version av den personliga gatewayen för Power BI](service-gateway-personal-mode.md)
[Säkerhetsnivåer](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)  
[Vanliga frågeuppgifter i Power BI Desktop](desktop-common-query-tasks.md)  
Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

