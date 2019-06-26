---
title: Vad är Power BI-mallappar? (förhandsgranskning)
description: Den här artikeln ger en översikt över Power BI-mallappar. Lär dig hur du skapar Power BI-appar med lite eller ingen kodning och distribuerar dem till Power BI-kunder.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
ms.openlocfilehash: 600e2ed603773cada415f603202cc72f22e0d25b
ms.sourcegitcommit: 81ba3572531cbe95ea0b887b94e91f94050f3129
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66751101"
---
# <a name="what-are-power-bi-template-apps-preview"></a>Vad är Power BI-mallappar? (förhandsgranskning)

Med de nya Power BI-*mallapparna* kan Power BI-partner skapa Power BI-appar med lite eller ingen kodning och sedan distribuera dem till Power BI-kunder.  Den här artikeln ger en översikt över Power BI-mallappar.

Mallappar ersätter nuvarande innehållspaket för tjänsten. Som Power BI-partner kan du skapa en uppsättning färdigt innehåll för kunderna och publicera det själv.  

Du skapar mallappar som kunderna sedan kan ansluta och instantiera med sina egna konton. Som domänexperter kan de låsa upp data på ett användarvänligt sätt för företagsanvändarna.  

Du skickar dina mallappar till Cloud Partner Portal. Apparna blir sedan allmänt tillgängliga i Power BI-appgalleriet (app.powerbi.com/getdata/services) och på Microsoft AppSource (appsource.microsoft.com). Här ges en översikt över hur allmänt tillgängliga mallappar skapas.  

## <a name="process"></a>Process
Den generella processen för att utveckla och skicka in en mallapp består av flera steg. Vissa steg kan omfatta flera samtidiga aktiviteter.


| Steg | Power BI Desktop |  |Power BI-tjänst  |  |Cloud Partner Portal  |
|---|--------|--|---------|---------|---------|
| **Ett** | Skapa en datamodell och rapport i en PBIX-fil |  | Skapa en arbetsyta. Importera en PBIX-fil. Skapa en kompletterande instrumentpanel  |  | Registrera dig som en partner |
| **Två** |  |  | Skapa ett testpaket och kör en intern validering        |  | |
| **Tre** | |  | Höj upp testpaket till förproduktion för validering utanför din Power BI-klientorganisation och skicka den till AppSource  |  | Med förproduktionspaketet skapar du ett Power BI-mallapperbjudande och påbörjar valideringsprocessen |
| **Fyra** | |  | Höj upp förproduktionspaketet till produktion |  | Publicera |

## <a name="requirements"></a>Krav

Du behöver behörighet för att kunna skapa en mallapp. Se mallappinställningarna i Power BI-administratörsportalen för mer information. 

För att kunna publicera en mallapp i Power BI-tjänsten och AppSource måste du uppfylla kraven för att [bli en Cloud Marketplace-utgivare](https://docs.microsoft.com/azure/marketplace/become-publisher).
 
## <a name="high-level-steps"></a>Övergripande steg

Här är de övergripande stegen. 

1. [Granska kraven](#requirements) och se till att du uppfyller dem. 

1. Skapa en rapport i Power BI Desktop. Använd parametrarna så att du kan spara den som en fil som andra kan använda. 

1. Skapa en arbetsyta för din mallapp i din klientorganisation på Power BI-tjänsten (app.powerbi.com). 

1. Importera PBIX-filen och lägg till innehåll, till exempel en instrumentpanel, i din app. 

1. Skapa ett testpaket för att testa mallappen själv inom din organisation. 

1. Höj upp testappen till förproduktion för att skicka appen för validering i AppSource och testa den utanför din klientorganisation. 

1. Skicka innehållet till Cloud Partner Platform för publicering. 

1. Se till att ditt erbjudande är ”Live” (publicerad) i AppSource och flytta appen till produktion i Power BI.
2. Nu kan du börja utveckla nästa version i samma arbetsyta i förproduktion. 

## <a name="requirements"></a>Krav

Du behöver behörighet för att kunna skapa en mallapp. Se [mallappinställningarna i Power BI-administratörsportalen](service-admin-portal.md#template-apps-settings-preview) för mer information. 

För att kunna publicera en mallapp i Power BI-tjänsten och AppSource måste du uppfylla kraven för att [bli en Cloud Marketplace-utgivare](https://docs.microsoft.com/azure/marketplace/become-publisher).

## <a name="tips"></a>Tips 

- Se till att din app innehåller exempeldata så att alla kan komma igång direkt. 
- Granska appen noggrant genom att installera den i din klientorganisation och i en annan klientorganisation. Kontrollera att kunderna bara kan se det som du vill att de ska se. 
- Använd AppSource som onlinebutik för din app. På så sätt kan alla som använder Power BI hitta din app. 
- Överväg att erbjuda en mallapp för separata unika scenarier. 
- Aktivera dataanpassning, till exempel stöd för anpassade anslutningar och konfiguration av parametrar genom installationsprogrammet.

Se [Tips för att skapa mallappar i Power BI (förhandsversion)](service-template-apps-tips.md) för fler förslag.

## <a name="support"></a>Support
Använd [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support) för support under utveckling. Vi övervakar och hanterar den här webbplatsen aktivt. Kundincidenter når snabbt ett lämpligt team.

## <a name="next-steps"></a>Nästa steg

[Skapa en mallapp](service-template-apps-create.md)