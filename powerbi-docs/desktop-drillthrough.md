---
title: Använd drillthrough i Power BI Desktop
description: Lär dig att öka detaljnivån för data på en ny rapportsida i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 8bbfafcecb6876ea063bb6751ca31c25697dc185
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/12/2018
ms.locfileid: "44725867"
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Använd drillthrough i Power BI Desktop
Med **drillthrough** i **Power BI Desktop** kan du skapa en sida i rapporten som fokuserar på en specifik enhet – till exempel en leverantör, kund eller tillverkare. Med den fokuserade rapportsidan kan användare högerklicka på en datapunkt i andra rapportsidor och använda drillthrough till sidan i fokus för att hämta information som har filtrerats för det sammanhanget.

![använda drillthrough](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Använda drillthrough
1. För att använda **drillthrough** skapar du en rapportsida med visuella objekt som du vill se för typen av enhet på vilken du ökar detaljnivån. 

    Om du vill använda drillthrough för en tillverkare kan du skapa en drillthrough-sida med visuella objekt som visar totalförsäljning, totalt antal levererade enheter, försäljning enligt kategori, försäljning enligt region och så vidare. Därmed är visualiseringen alltid specifik för tillverkaren du valde.

2. Sedan, på drillthrough-sidan i avsnittet **Fält** i rutan **Visuella objekt** kan du dra fältet som du vill använda drillthrough på i brunnen för **Drillthrough-filter**.

    ![drillthrough korrekt](media/desktop-drillthrough/drillthrough_02.png)

    När du lägger till ett fält i brunnen **Drillthrough-filter** skapar **Power BI Desktop** automatiskt en *bakåtknapp*. Knappen visas i publicerade rapporter och låter användare av rapporten **Power BI-tjänsten** enkelt komma tillbaka till sidan som de kommer ifrån (sidan där de har valt drillthrough).

    ![drillthrough-bild](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>Använda en egen bild för en bakåtknapp    
 Eftersom bakåtknappen är en bild kan du ersätta den med vilken bild du vill och den kommer fortfarande att fungera som en bakåtknapp för att låta användaren gå tillbaka till ursprungssidan.

1. På fliken **Hem** klickar du på **Bild**, letar upp bilden och placerar den på drillthrough-sidan.
2. Markera den nya bilden på drillthrough-sidan och under avsnittet Formatera bild genom att ange slutreglaget **Länk** till på och ange den **typen** som **Bakåt**. Bilden fungerar nu som en bakåtknapp.

    ![använda en avbildning för bakåt](media/desktop-drillthrough/drillthrough_05.png)

    När din **drillthrough**-sida är klar och användare högerklickar på en datapunkt i rapporten som använder fältet du la till i **drillthrough-filtret**, visas en snabbmeny som stöder drillthrough för sidan.

    ![drillthrough-meny](media/desktop-drillthrough/drillthrough_04.png)

    När rapportkonsumenterna valde drillthrough filtrerades sidan för att visa information om datapunkten som de högerklickade på. Om de högerklickade på en datapunkt om Contoso (en tillverkare) och har valt drillthough filtreras drillthrough-sidan till Contoso.

## <a name="pass-all-filters-in-drillthrough"></a>Skicka alla filter i drillthrough

Från och med versionen från maj 2018 av **Power BI Desktop**, kan du överföra alla filter till drillthrough-fönstret. Till exempel kanske du bara har valt en viss kategori av produkter och visualiseringarna filtrerats till denna kategori, då väljer du drillthrough. Du kan vara intresserad hur denna drillthrough skulle se ut med alla de filter som används.

För att behålla alla filter i avsnittet **Drillthrough** i fönstret **Visualiseringar** ställer du bara in **Skicka alla-filtren** till **på**. 

![behåll alla filter](media/desktop-drillthrough/drillthrough_06.png)

I versioner av **Power BI Desktop** före maj 2018, är beteendet likvärdigt med att ha den här inställningen satt till **av**.

När du sedan genomför drillthrough på någon visualisering ser du vilka filter som har tillämpats på grund av att källvisualiseringen har tillfälliga filter. I fönstret drillthrough visas dessa tillfälligt filter i kursiv stil. 

![tillfälliga filter i kursiv stil](media/desktop-drillthrough/drillthrough_07.png)

Observera att du kan göra detta med sidorna för knappbeskrivningar, men det skulle vara en konstig upplevelse (knappbeskrivningen skulle inte verka som att den fungerar korrekt), så det rekommenderas inte att göra det med knappbeskrivningar.

## <a name="add-a-measure-to-drillthrough"></a>Lägg till ett mått i drillthrough

Förutom att överföra alla filter till drillthrough-fönstret kan du även lägga till ett mått (eller en sammanfattande numerisk kolumn) i drillthrough-området. Du behöver bara dra drillthrough-fältet till Drillthrough-kortet för att tillämpningen ska börja gälla. 

![lägg till ett mått i drillthrough](media/desktop-drillthrough/drillthrough_08.png)

När du lägger till ett mått (eller en sammanfattade numerisk kolumn) kan du gå till sidan när fältet används i området *Värde* i en visualisering.

Svårare än så är det inte att använda **drillthrough** i dina rapporter. Det är ett bra sätt att få en utökad vy över den enhetsinformation som du har valt för ditt drillthrough-filter.

## <a name="next-steps"></a>Nästa steg

Följande artiklar kan också vara av intresse för dig:

* [Använda utsnitt i Power BI Desktop](visuals/desktop-slicers.md)

