---
title: Aktivera eller inaktivera registrering och inköp via självbetjäning
description: Instruktioner för hur administratörer stänger av möjligheten för användare att registrera sig för Power BI-tjänsten och köpa eller uppgradera en licens.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 751db634ceb9e7d6349b35f7348b09e0c0d648ed
ms.sourcegitcommit: 3f864ec22f99ca9e25cda3a5abda8a5f69ccfa8e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2020
ms.locfileid: "84160075"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Aktivera eller inaktivera registrering och inköp via självbetjäning

I de flesta organisationer är självbetjäningsregistrering aktiverad som standard. Enskilda användare i din organisation kan registrera sig för Power BI med sitt arbets- eller skolkonto. Användarna kan även ges möjlighet att direkt köpa en Power BI Pro-licens om de försöker använda en funktion som kräver Pro. Som administratör bestämmer du om du vill aktivera eller inaktivera självbetjäningsregistrering. Du kan dessutom styra om användare i din organisation kan göra självbetjäningsinköp för att få sin egen licens.

> [!NOTE]
>Om du har köpt Power BI via en Leverantör av Microsoft-molnlösningar (CSP) kan inställningen vara inaktiverad för att blockera användare från att registrera sig individuellt. Din CSP kan också agera som global administratör för din organisation, vilket kräver att du kontaktar dem för att hjälpa dig att ändra den här inställningen.
>
>

Du använder PowerShell-kommandon för att ändra de inställningar som styr registrering och inköp via självbetjäning. Det finns två inställningar som kontrollerar huruvida användare i din organisation kan utföra självbetjäningsregistrering eller självbetjäningsinköp.

- Om du vill inaktivera alla självbetjäningsregistreringar ändrar du en inställning i Azure Active Directory som heter **AllowAdHocSubscriptions** med hjälp av Azure AD PowerShell-kommandon. Följ stegen i den här artikeln för att [aktivera eller inaktivera självbetjäningsregistrering](#enable-or-disable-self-service-signup). Det här alternativet stänger av självbetjäningsregistrering för *alla* Microsofts molnbaserade appar och tjänster.

- Om du vill hindra användare från att köpa sin egen Pro-licens ändrar du inställningen **AllowSelfServicePurchase** med hjälp av MSCommerce PowerShell-kommandon. Med den här inställningen kan du stänga av självbetjäningsinköp för specifika produkter. Följ stegen i den här artikeln för att [aktivera eller inaktivera självbetjäningsinköp av Power BI Pro-licenser](#enable-or-disable-self-service-purchase).

## <a name="enable-or-disable-self-service-signup"></a>Aktivera eller inaktivera självbetjäningsregistrering

Om självbetjäningsregistrering är aktiverad är värdet för **AllowAdHocSubscriptions** *true*. Vi tittar på vad som händer när du ändrar den här inställningen till *false*:

- Om du ändrar inställningen från true till false blockeras nya användare i din organisation från att kunna registrera sig individuellt. Användare som har registrerat sig för Power BI innan du ändrar inställningen behåller sina licenser.

- Om du ändrar inställningen till false kan användare som redan har en Power BI-licens (kostnadsfri) fortfarande registrera sig för en individuell utvärdering av Power BI Pro.

- En administratör behöver tilldela alla Power BI-licenser till nya användare som behöver en.

### <a name="before-you-begin"></a>Innan du börjar

De här stegen använder Azure Active Directory PowerShell-kommandon för att ändra värdet för inställningen **AllowAdHocSubscriptions**. Du måste ha Azure AD PowerShell-modulen installerad för att de här kommandona ska vara tillgängliga. Mer information om hur du använder PowerShell finns i [Komma igång med Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Installera Azure AD-modulen genom att starta Windows PowerShell som administratör. Kontrollera att din lokala körningsprincip tillåter att du kör skript. Om du stöter på problem kan du läsa mer i [PowerShell-körningsprinciper](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) för att lära dig hur du ändrar den lokala principen.

Kör följande kommando för att installera Azure AD-modulen:

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>Ändra principen för självbetjäningsregistrering

I PowerShell kör du följande kommando för att ansluta till Azure AD:

```powershell
Connect-MsolService
```

Ange autentiseringsuppgifterna för administratör i inloggningsdialogrutan och slutför eventuell tvåfaktorautentisering som kan behövas. Efter verifieringen kommer du tillbaka till PowerShell-fönstret.

Visa den aktuella inställningen genom att köra följande kommando. Utdata skickas till en formaterad lista med hjälp av växeln ”fl”.

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

Du ändrar den aktuella inställningen genom att köra det här kommandot:

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

När du har kört det här kommandot inaktiveras självbetjäningsregistrering för alla användare. Om du vill återaktivera det kör du det här kommandot igen och anger värdet till $true.

## <a name="enable-or-disable-self-service-purchase"></a>Aktivera eller inaktivera självbetjäningsinköp

Om självbetjäningsinköp är aktiverat är värdet för **AllowSelfServicePurchase** *true*. Vi tittar på vad som händer när du ändrar den här inställningen till *false*:

- Om du ändrar inställningen från true till false blockeras användare i din organisation från att kunna köpa sin egen Power BI Pro-licens. Användare som har köpt en licens innan du ändrar inställningen behåller sina licenser.

- Om du ändrar inställningen till false kan användare som har en Power BI-licens (kostnadsfri) inte skaffa en individuell Power BI Pro-licens. 

- En administratör behöver tilldela en Pro-licens till alla användare som behöver en.

### <a name="before-you-begin"></a>Innan du börjar

I de här stegen används MSCommerce PowerShell-kommandon för att ändra värdet för inställningen **AllowSelfServicePurchase**. Du måste ha MSCommerce PowerShell-modulen installerad för att de här kommandona ska vara tillgängliga. Mer information om hur du använder PowerShell finns i [Komma igång med Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Installera MSCommerce-modulen genom att starta Windows PowerShell som administratör. Kontrollera att din lokala körningsprincip tillåter att du kör skript. Om du stöter på problem kan du läsa mer i [PowerShell-körningsprinciper](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) för att lära dig hur du ändrar den lokala principen.

Kör följande kommando för att installera MSCommerce-modulen:

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>Ändra principen för självbetjäningsinköp

I PowerShell kör du följande kommando för att ansluta:

```powershell
Connect-MSCommerce
```

Ange autentiseringsuppgifterna för administratör i inloggningsdialogrutan och slutför eventuell tvåfaktorautentisering som kan behövas. Efter verifieringen visar PowerShell-fönstret en lyckad anslutning.

Visa den aktuella inställningen genom att köra följande kommando. I syfte att förhindra trunkering av text skickas utdata till en formaterad lista med hjälp av växeln ”fl”.

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

Du kan inaktivera den inställning som tillåter självbetjäningsinköp för en enskild produkt genom att ange dess **ProductId**. Kör det här kommandot om du vill ändra den aktuella inställningen för Power BI-tjänsten:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

När du har kört det här kommandot inaktiveras självbetjäningsinköp för Power BI för alla användare. Om du vill återaktivera det kör du det här kommandot igen och anger värdet till $true.

## <a name="next-steps"></a>Nästa steg

Mer information om självbetjäningsinköp i Power BI och resten av Power Platform finns i följande artiklar:

- [Vanliga frågor och svar om självbetjäning](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide#admin-capabilities)
- [Använda AllowSelfServicePurchase för MSCommerce PowerShell-modulen](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide)
