---
title: URL-parametrar i sidnumrerade rapporter – Power BI Report Builder
description: I det här ämnet beskrivs vanliga användningsområden för rapportparametrar i Power BI Report Builder, de egenskaper som du kan ange och mycket mer.
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.date: 08/29/2019
ms.openlocfilehash: 4dae849a18bbfc6e85eedc7ae9e338ad205cb436
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70189356"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>URL-parametrar i sidnumrerade rapporter i Power BI

Du kan skicka kommandon till sidnumrerade rapporter i Power BI genom att lägga till en parameter i en URL. Till exempel kanske du har visat rapporten med en specifik uppsättning rapportparametervärden. Du kapslar in informationen i URL:en med hjälp av fördefinierade parametrar för URL-åtkomst. Du kan anpassa hur Power BI bearbetar rapporten ytterligare genom att bädda in parametrar för renderingsformat, eller för verktygsfältets utseende i rapporten. Sedan klistrar du in URL: en direkt i ett e-postmeddelande eller på en webbsida, så att andra kan ta del av rapporten på samma sätt i webbläsaren. 

Här är några åtgärder som du kan utföra via URL-åtkomstparametrar: 

- Skicka rapportparametrar till en rapport. 
- Initiera exporten av rapportinnehållet i ett filformat som stöds. 
- Dölj eller visa parameterfönstret. 
- Ange inställningen DeviceInfo. 

En fullständig lista över kommandon och inställningar som är tillgängliga via URL-åtkomst finns i  [parameterreferens för URL-åtkomst](#url-access-parameter-reference) senare i den här artikeln. 

## <a name="url-access-concepts"></a>Begrepp för URL-åtkomst 

URL-begäranden till Power BI innehåller parametrar som bearbetas av tjänsten. Hur tjänsten hanterar URL-begäranden beror på parametrar, parameterprefix och vilka typer av objekt som ingår i URL: en. URL-funktionen för sidnumrerade rapporter är kompatibel med de flesta webbläsare och program som stöder standardiserad URL-adressering. 

## <a name="url-access-syntax"></a>Syntax för URL-åtkomst 

URL-begäranden kan innehålla flera parametrar, i vilken ordning som helst. Parametrar avgränsas med ett et-tecken (&). Namn- och värdepar avgränsas med ett likhetstecken (=). Till exempel:

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>syntax-beskrivning 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

Webbtjänstens URL för din Power BI-klient. Till exempel: 

**&** Används för att avgränsa namn- och värdepar för URL-åtkomstparametrar.

**prefix** Ett prefix för URL-parametern (till exempel rp: eller rdl:) som specificerar en åtgärd i Power BI-tjänsten. 

> [!NOTE]
> Rapportparametrar kräver ett parameterprefix och är skiftlägeskänsliga. 

**parameter** Parameternamnet. 

### <a name="value"></a>värde 

URL-text som motsvarar värdet för den parameter som används. 

Exempel på hur du kan skicka rapportparametrar i URL:en finns i [Skicka en rapportparameter i en URL](report-builder-url-pass-parameters.md).

## <a name="url-access-parameter-reference"></a>Parameterreferens för URL-åtkomst

Du kan använda följande parametrar som en del av en URL för att konfigurera utseendet i dina sidnumrerade rapporter i Power BI. De vanligaste parametrarna visas i det här avsnittet. Parametrar är skiftlägeskänsliga och börjar med parameterprefixet `rdl:` om det är relaterat till utdataformatet.  

### <a name="report-commands-rdl"></a>Rapportkommandon (`rdl:`) 

**Exportformat** Anger det format som ska användas för att rendera och exportera en rapport. Exempel på värden: 
- PPTX 
- MHTML 
- BILD 
- EXCEL 
- WORD 
- CSV 
- PDF 
- XML 

## <a name="next-steps"></a>Nästa steg

- [Skicka en rapportparameter i en URL för en sidnumrerad rapport i Power BI](report-builder-url-pass-parameters.md)
- [Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)