---
title: Aktivera känslighetsetiketter i Power BI
description: Lär dig att aktivera känslighetsetiketter i Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 08/10/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: ebc4601f3575e84c248aef9204537a7d93c428ac
ms.sourcegitcommit: 9e39232cbc28d8b39dfec5496db7ece9837b5e53
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "88049194"
---
# <a name="enable-sensitivity-labels-in-power-bi"></a>Aktivera känslighetsetiketter i Power BI

[Känslighetsetiketter från Microsoft Information Protection](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) måste vara aktiverade i klientorganisationen för att kunna användas i Power BI. I den här artikeln kan Power BI-klientadministratörer se hur de gör detta. Om du vill få en översikt över känslighetsetiketterna i Power BI, kan du läsa [Känslighetsetiketter i Power BI](service-security-sensitivity-label-overview.md). Mer information om att tillämpa känslighetsetiketter i Power BI finns i [Tillämpa känslighetsetiketter](./service-security-apply-data-sensitivity-labels.md) 

När känslighetsetiketter är aktiverade:

* Angivna användare och säkerhetsgrupper i organisationen kan klassificera och [tillämpa känslighetsetiketter](./service-security-apply-data-sensitivity-labels.md) för sina rapporter, instrumentpaneler, datamängder och dataflöden i Power BI.
* Alla medlemmar i organisationen kan se de här etiketterna.

Om du ska aktivera känslighetsetiketter måste du ha en licens för Azure Information Protection. Mer information finns i [Licensiering och krav](#licensing-and-requirements).

## <a name="licensing-and-requirements"></a>Licensiering och krav

* Om du vill använda eller visa Microsoft Information Protection-känslighetsetiketter i Power BI måste du ha en Premium P1- eller Premium P2-licens för Azure Information Protection. Du kan köpa Azure Information Protection separat eller via något av Microsofts licenspaket. Läs mer i [Prissättning för Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/).

* Om en användare ska kunna använda etiketter på Power BI-innehåll måste hen dessutom ha en Power BI Pro-licens utöver någon av de Azure Information Protection-licenser som anges ovan.

* Office-appar har sina egna [licensieringskrav för visning och användning av känslighetsetiketter]( https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels ).

* Innan du aktiverar känslighetsetiketter på din klient, så kontrollera att känslighetsetiketter har definierats och publicerats för relevanta användare och grupper. Mer information finns i [Skapa och konfigurera känslighetsetiketter och deras principer](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels?view=o365-worldwide).

>[!NOTE]
> Om din organisation använder Azure Information Protection-känslighetsetiketter måste de migreras till Microsoft Information Protection Unified Labeling-plattformen om de ska kunna användas i Power BI. [Läs mer om att migrera känslighetsetiketter](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels).

## <a name="enable-sensitivity-labels"></a>Aktivera känslighetsetiketter

Gå till **administrationsportalen** för Power BI, öppna panelen **Klientinställningar** och letar reda på avsnittet **Informationsskydd**.

![Leta rätt på avsnittet Information Protection](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

Utför följande steg i avsnittet **Information Protection**:
1. Öppna **Låt användare tillämpa känslighetsetiketter för Power BI-innehåll**.
1. Aktivera växlingsknappen.
1. Definiera vem som kan tillämpa och ändra känslighetsetiketter för Power BI-tillgångar. Som standard kan alla i organisationen tillämpa känslighetsetiketter. Du kan dock välja att endast låta vissa användare eller säkerhetsgrupper ställa in känslighetsetiketter. Om du väljer antingen hela organisationen eller specifika säkerhets grupper kan du undanta vissa delmängder av användare eller säkerhetsgrupper.
   
   * När känslighetsetiketter är aktiverade för hela organisationen är undantagen normalt säkerhetsgrupper.
   * När känslighetsetiketter bara är aktiverade för vissa användare eller säkerhetsgrupper så är undantagen normalt specifika användare.  
    Det här gör att du kan förhindra att vissa användare tillämpar känslighetsetiketter i Power BI, även om de tillhör en grupp som har behörighet att göra det.

1. Tryck på **Tillämpa**.

![Aktivera känslighetsetiketter](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> Det är bara Power BI Pro-användare med behörigheterna *skapa* och *redigera* för tillgången, och som ingår i säkerhetsgruppen du angav i avsnittet, som kan ställa in och redigera känslighetsetiketter. Användare som inte ingår i den här gruppen kan inte ställa in eller redigera etiketter.  

## <a name="troubleshooting"></a>Felsökning

Power BI använder känslighetsetiketter från Microsoft Information Protection. Om du får ett felmeddelande när du försöker aktivera känslighetsetiketter kan det bero på något av följande:

* Du har ingen [licens](#licensing-and-requirements) för Azure Information Protection.
* Känslighetsetiketter har inte [migrerats](#enable-sensitivity-labels) till den version av Microsoft Information Protection som stöds i Power BI.
* Inga känslighetsetiketter från Microsoft Information Protection har [definierats i organisationen](#enable-sensitivity-labels).

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

I [Känslighetsetiketter i Power BI](service-security-sensitivity-label-overview.md#limitations) finns en lista med begränsningar för känslighetsetiketter i Power BI.

## <a name="next-steps"></a>Nästa steg

I den här artikeln beskrivs hur du aktiverar känslighetsetiketter i Power BI. De här artiklarna innehåller mer information om dataskydd i Power BI. 

* [Översikt över känslighetsetiketter i Power BI](service-security-sensitivity-label-overview.md)
* [Använda känslighetsetiketter i Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Använda Microsoft Cloud App Security-kontroller i Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Rapport om skyddsmått](service-security-data-protection-metrics-report.md)