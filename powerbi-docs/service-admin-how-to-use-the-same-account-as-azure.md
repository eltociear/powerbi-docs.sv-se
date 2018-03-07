---
title: "Använda samma kontoinloggning för Power BI och Azure"
description: "Så här använder du samma kontoinloggning för Power BI och Azure"
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 06/28/2017
ms.author: maghan
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 46e9f8e3e19be53e46a51aa78cd63eb27c50555a
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="using-the-same-account-for-power-bi-and-azure"></a>Använda samma kontoinloggning för Power BI och Azure
Om du är en användare av både Power BI och Azure, vill du kanske använda samma inloggning för båda tjänsterna så att du inte behöver ange ditt lösenord två gånger.

Power BI loggar in dig med ditt organisationskonto som är kopplat till din arbets- eller skolmejl.  Azure loggar in dig med ett Microsoft-konto eller ditt organisationskonto.

Om du vill använda samma inloggning för både Azure och Power BI ska du logga in på Azure med ditt organisationskonto.

**Vad händer om jag redan har loggat in på Azure med mitt Microsoft-konto?**

Du kan lägga till ditt organisationskonto som medadministratör i Azure.  Gör så här:

1. Logga in på [Azure Management Portal](http://manage.windowsazure.com/). Om du är en användare i flera kataloger i Azure, klickar du på **Prenumerationer** och filtrerar sedan för att visa katalogen och de prenumerationer som du vill redigera.
2. I navigeringsfönstret klickar du på **Inställningar**. Klicka på **Administratörer** och sedan på **Lägg till**.
3. Ange den e-postadress som är associerat med ditt organisationskonto.
4. Välj den prenumeration som du vill komma åt med ditt organisationskonto och sedan klicka på kryssrutan.

Nästa gång du loggar in på Azure-hanteringsportalen ska du använda din organisations e-postadress.

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

