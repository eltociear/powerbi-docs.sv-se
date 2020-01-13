---
title: Betrodda tredjepartsanslutningar i Power BI
description: Hur du litar på en signerad tredjepartsanslutning i Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 05db20b2f83f10409339fad949874fc1076a6b98
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75759846"
---
# <a name="trusted-third-party-connectors"></a>Betrodda anslutningsappar från tredje part

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Varför behöver du betrodda anslutningar från tredje part?

I Power BI rekommenderar vi vanligtvis att du behåller ”Säkerhet för datatillägg” på den högre nivån, vilket förhindrar inläsning av kod som inte har certifierats av Microsoft. Det kan dock finnas många fall där du vill läsa in vissa anslutningar, som du har skrivit eller som du har fått av en konsult eller leverantör utanför Microsoft-certifieringen.

Utvecklaren av en specifik anslutning kan signera den med ett certifikat och förse dig med den information du behöver för att läsa in den på ett säkert sätt utan att sänka säkerhetsinställningarna.

Om du vill veta mer om säkerhetsinställningarna kan du läsa om dem [här](https://docs.microsoft.com/power-bi/desktop-connector-extensibility).

## <a name="using-the-registry-to-trust-third-party-connectors"></a>Använda registret för att lita på anslutningar från tredje part

Att lita på anslutningar från tredje part i Power BI görs genom att lista tumavtrycket för det certifikat som du vill lita på i ett angivet registervärde. Om detta tumavtryck matchar tumavtrycket för certifikatet på den anslutning som du vill läsa in, kan du läsa in den i den rekommenderade säkerhetsnivån för Power BI. 

Registersökvägen är HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Kontrollera att sökvägen finns eller skapa den. Vi har valt den här platsen eftersom den främst styrs av IT-principen, samt kräver åtkomst till lokal datoradministration vid redigering. 

![Power BI Desktop-register utan att några betrodda nycklar från tredje part har angetts](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Lägg till ett nytt värde under den sökväg som anges ovan. Typen ska vara ett ”Multisträngvärde” (REG_MULTI_SZ) och heta ”TrustedCertificateThumbprints” 

![Power BI Desktop-registret med en post för betrodda anslutningar från tredje part, men inga nycklar](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Lägg till tumavtrycken för de certifikat som du vill lita på. Du kan lägga till flera certifikat med hjälp ”\0” som avgränsare, eller genom att högerklicka på -> ändra och lägga till varje tumavtryck på en ny rad i registereditorn. Tumavtrycksexemplet är hämtat från ett självsignerat certifikat. 

 ![Power BI Desktop-register med en betrodd nyckel från tredje part](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Om du har följt instruktionerna och fått rätt tumavtryck av din utvecklare, bör du nu kunna lita på säkra betrodda anslutningar som är signerade med det associerade certifikatet.

## <a name="how-to-sign-connectors"></a>Så här signerar du anslutningar

Om du har en anslutning som du eller en utvecklare behöver signera, kan du läsa mer om detta i Power Query-dokumentationen [här](https://docs.microsoft.com/power-query/handlingconnectorsigning).
