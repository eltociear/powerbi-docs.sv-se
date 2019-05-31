---
title: Betrodda tredjeparts-kopplingar i Powerbi
description: Hur ska lita på en signerad tredjepartsanslutningsprogrammet i Power BI
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 30b7457c6149320c43f24b967a842382821b01b1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65607790"
---
# <a name="trusting-third-party-connectors"></a>Betrodda tredjeparts-kopplingar

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Varför behöver du betrodda tredjeparts-anslutningsprogram?

I Power BI allmänhet rekommenderar vi att hålla din 'tillägget datasäkerhet ”nivå på högre nivå, vilket förhindrar inläsning av kod som inte är certifierade av Microsoft. Det kan dock finnas många fall där du vill läsa in specifika anslutningsappar, som du har skrivit eller paket som du fått av en konsult eller leverantör utanför Microsoft certifieringssökvägen.

Utvecklaren av en viss anslutningsapp kan signera den med ett certifikat och ge dig den information du behöver läsa in den på ett säkert sätt utan att sänka säkerhetsinställningarna.

Om du vill veta mer om säkerhetsinställningar kan du läsa om dem [här](https://docs.microsoft.com/power-bi/desktop-connector-extensibility).

## <a name="using-the-registry-to-trust-third-party-connectors"></a>Med hjälp av registret ska lita på tredje parts-kopplingar

Betrodda tredjeparts-kopplingar i Power BI görs genom att ange tumavtrycket för certifikatet som du vill lita på en angiven registervärdet. Om det här tumavtrycket matchar tumavtrycket för certifikatet på kopplingen du vill läsa in, kommer du att kunna läsa in den i ”rekommenderade” säkerhetsnivån för Power BI. 

Registersökvägen är HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Kontrollera att sökvägen finns eller skapa den. Vi har valt den här platsen på grund av det främst som kontrolleras av IT-principen, samt kräver lokal dator administration behörighet att redigera. 

![Ställ in Power BI Desktop registret med några betrodda tredjeparts-nycklar](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Lägg till ett nytt värde under sökvägen som anges ovan. Typen ska vara ”Multisträngvärde” (REG_MULTI_SZ), och det bör vara kallas ”TrustedCertificateThumbprints” 

![Power BI Desktop registret med en post för den betrodda tredjeparts-anslutningsappar men inga nycklar](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Lägg till tumavtrycken för de certifikat som du vill lita på. Du kan lägga till flera certifikat med hjälp av ”\0” som avgränsare, eller i Registereditorn rätt -> Klicka på Ändra och placera varje tumavtrycket i en ny rad. Exempel på ett tumavtryck hämtas från ett självsignerat certifikat. 

 ![Power BI Desktop registret med en betrodd tredje parts nyckeluppsättning](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Om du har följt anvisningarna korrekt och har tilldelats rätt tumavtrycket av utvecklaren, bör du nu kunna på ett säkert sätt förtroende kopplingar som signerats med det associerade certifikatet.

## <a name="how-to-sign-connectors"></a>Så här registrerar du kopplingar

Om du har en anslutningsapp du eller en utvecklare behöva logga in kan du läsa om den i Power Query-dokumenten [här](https://docs.microsoft.com/power-query/handlingconnectorsigning).
