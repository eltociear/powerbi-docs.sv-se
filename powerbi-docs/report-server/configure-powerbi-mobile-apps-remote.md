---
title: Fjärrkonfiguration av iOS-mobilappar för åtkomst till en rapportserver
description: Lär dig hur du fjärrkonfigurerar mobila iOS-appar för din rapportserver.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/15/2018
ms.author: maggies
ms.openlocfilehash: 27b3aad6f1a96c069f56ed68823b71b38115a98a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770651"
---
# <a name="configure-power-bi-ios-mobile-app-access-to-a-report-server-remotely"></a>Fjärrkonfiguration av Power BI iOS-mobilappar för åtkomst till en rapportserver

I den här artikeln kommer du lära dig att använda din organisations MDM-verktyg för att konfigurera åtkomsten från iOS-mobilappen för Power BI till en rapportserver. För att konfigurera detta skapar IT-administratören en appkonfigurationsprincip med nödvändig information som sedan skickas till appen. 

 När rapportservern har konfigurerats blir det lättare för Power BI iOS-mobilappanvändarna att ansluta till organisationens rapportserver. 

## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Skapa appkonfigurationsprincipen i MDM-verktyget 

Som administratör följer du de här anvisningarna i Microsoft Intune för att skapa appkonfigurationsprincipen. Hur man skapar appkonfigurationsprinciper kan skilja sig åt mellan olika MDM-verktyg. 

1. Anslut ditt MDM-verktyg. 
2. Skapa och namnge en ny appkonfigurationsprincip. 
3. Välj vilka användare som appkonfigurationsprincipen ska distribueras till. 
4. Skapa nyckel-värdepar. 

I följande tabell anges paren.

|Nyckel  |Typ  |Beskrivning  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | Sträng | URL till rapportserver <br> Bör börja med http eller https |
| com.microsoft.powerbi.mobile.ServerUsername | Sträng | [valfritt] <br> Användarnamnet som ska användas för att ansluta servern. <br> Om det inte finns, uppmanas användaren att ange användarnamn för anslutningen i appen.| 
| com.microsoft.powerbi.mobile.ServerDisplayName | Sträng | [valfritt] <br> Standardvärdet är ”Rapportserver” <br> Ett eget namn som används i appen för att representera servern | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolesk | Standardvärdet är True <br>När värdet är ”True” åsidosätts eventuella rapportserverdefinitioner som redan finns i den mobila enheten. Befintliga servrar som redan är konfigurerade tas bort. <br> Genom att sätta Åsidosätt till True förhindras också att användaren tar bort konfigurationen. <br> Sätt värdet till ”False” för att lägga till de push-överförda värdera, vilket bevarar de befintliga inställningarna. <br> Om samma server-URL redan har konfigurerats i mobilappen, lämnas den konfigurationen i befintligt skick. Användaren uppmanas inte att logga in på nytt för samma server. |

Här är ett exempel på hur man ställer in konfigurationsprincipen i Intune.

![Intune-konfigurationsinställningar](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-a-report-server"></a>Slutanvändare som ansluter till en rapportserver

 Anta att du publicerar appkonfigurationsprincipen för en distributionslista. När användare och enheter på distributionslistan startar iOS-mobilappen händer följande. 

1. De ser ett meddelande som anger att mobilappen har konfigurerats med en rapportserver och trycker på **Logga in**.

    ![Logga in på rapportservern](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  Informationen om rapportservern är redan ifylld på sidan **Anslut till server**. De trycker på **Anslut**.

    ![Informationen om rapportservern är ifylld](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. De skriver ett lösenord för att autentisera och tryck sedan på **Logga in**. 

    ![Informationen om rapportservern är ifylld](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

Nu kan de visa och interagera med KPI:er och Power BI-rapporter som lagras på rapportservern.

## <a name="next-steps"></a>Nästa steg
[Administratörsöversikt](admin-handbook-overview.md)  
[Installera Power BI-rapportserver](install-report-server.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

