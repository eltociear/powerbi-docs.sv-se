---
title: Registrera en app med Azure AD
description: "Genomgång – Skicka data i en dataset – Registrera en app med Azure AD"
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
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: asaxton
ms.openlocfilehash: e5c1629ea6b90ec52a3c567916a9f686eb4d1bee
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="step-1-register-an-app-with-azure-ad"></a>Steg 1: Registrera en app med Azure AD
Den här artikeln ingår i en stegvis genomgång för att [skicka data till en datauppsättning](walkthrough-push-data.md).

Det första steget för att skicka data till en datauppsättning i Power BI är att registrera din app i Azure AD. Du måste först ha ett **klient-ID** som identifierar din app i Azure AD. Utan ett **klient-ID** kan Azure AD inte autentisera appen.

> **Obs**: Innan du registrerar en app för Power BI måste du [registrera dig för Power BI](create-an-azure-active-directory-tenant.md).
> 
> 

Här följer stegen för att registrera en app i Azure AD.

## <a name="register-an-app-in-azure-ad"></a>Registrera en app i Azure AD
1. Gå till dev.powerbi.com/apps.
2. Klicka på **Logga in med ditt befintliga konto** och logga in på ditt Power BI-konto.
3. Ange ett **Appnamn**, till exempel ”testapp för att skicka data”.
4. Välj **inbyggd app** som **apptyp**.
5. Ange ett **omdirigerings-URL** som **https://login.live.com/oauth20_desktop.srf**. En omdirigerings-uri ger **Azure AD** mer information om den **inbyggda kundappen** som den ska autentisera. Standard-Uri för ett klientprogram är https://login.live.com/oauth20_desktop.srf.
6. För **Välj API:er för åtkomst**, välj **Läsa och skriva alla datauppsättningar**. För alla behörigheter för Power BI-appen, se [Power BI behörigheter](power-bi-permissions.md).
7. Klicka på **Registrera app** och spara det **klient-ID** som genererades. En **klient-ID** identifierar appen i Azure AD.

Så här bör sidan **Registrera ett program för Power BI** se ut:

![](media/walkthrough-push-data-register-app-with-azure-ad/powerbi-developer-sample-register-app.png)

Nästa steg visar hur du [hämtar en autentiseringsåtkomsttoken](walkthrough-push-data-get-token.md).

[Nästa steg >](walkthrough-push-data-get-token.md)

## <a name="next-steps"></a>Nästa steg
[Registrera dig för Power BI](create-an-azure-active-directory-tenant.md)  
[Hämta en åtkomsttoken för autentisering](walkthrough-push-data-get-token.md)  
[Genomgång – Skicka data till en datauppsättning](walkthrough-push-data.md)  
[Registrera ett program](register-app.md)  
[Översikt över Power BI REST API](overview-of-power-bi-rest-api.md)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

