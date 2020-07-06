---
title: Använda utökade datamängder med metadata i Power BI Desktop (förhandsversion)
description: I den här artikeln beskrivs hur du använder utökade datamängdsmetadata i Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0a09311c5fdb1a8b2e008996d993015f33ee9b5f
ms.sourcegitcommit: a07fa723bb459494c60cf6d749b4554af723482a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2020
ms.locfileid: "84739263"
---
# <a name="using-enhanced-dataset-metadata-preview"></a>Använda utökade datamängdsmetadata (förhandsversion)

När Power BI Desktop skapar rapporter skapas även datamängdsmetadata i motsvarande PBIX- och PBIT-filer. Tidigare lagrades metadata i ett format som var specifikt för Power BI Desktop. Det använde Base-64-kodade M-uttryck och datakällor, och antaganden gjordes om hur metadata lagrades.

I och med att funktionen för **förbättrade datamängdsmetadata** släpps tas många av dessa begränsningar bort. Nu när funktionen för **förbättrade datamängdsmetadata** aktiveras, använder metadata som skapats av Power BI Desktop ett format som liknar det som används för Analysis Services-tabellmodeller, baserat på [tabellobjektsmodellen](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


Funktionen för **förbättrade datamängdsmetadata** är strategisk och grundläggande, eftersom framtida Power BI funktioner kommer att skapas utifrån sina metadata. Några ytterligare funktioner som drar nytta av förbättrade datamängdsmetadata är [XMLA läs/skriv](https://docs.microsoft.com/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) för hantering av Power BI-datauppsättningar och migrering av Analysis Services-arbetsbelastningar till Power BI för att dra nytta av nästa generations funktioner.



## <a name="enable-enhanced-dataset-metadata"></a>Aktivera utökade datamängdsmetadata

Funktionen **Förbättrade datamängdsmetadata** är för närvarande en förhandsversion. Om du vill aktivera utökade datamängdsmetadata går du till Power BI Desktop väljer **Arkiv > Alternativ och inställningar > Alternativ > Förhandsgranskningsfunktioner**, och markerar sedan kryssrutan **Lagra datamängder i förbättrat metadataformat** som i följande bild. 

![Aktivera förhandsfunktionen](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-01.png)

Du kan bli ombedd att starta om Power BI Desktop.

![Uppmaning att starta om](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-02.png)

När förhandsfunktionen har aktiverats försöker Power BI Desktop uppgradera PBIX- och PBIT-filer som använder det tidigare metadataformatet. 

> [!IMPORTANT]
> Om du aktiverar funktionen **Utökade datauppsättningens metadata** uppgraderas rapporterna. Detta kan inte ångras. Alla Power BI rapporter som läses in eller skapas med Power BI Desktop när **utökade metadata för datauppsättningen** har aktiverats konverteras oåterkalleligt till det utökade formatet för datauppsättningen.

## <a name="report-backup-files"></a>Säkerhetskopior av rapporter

Processen då man uppdaterar en rapport för att använda **utökade metadata för datauppsättningen** kan inte ångras. Under uppdateringen skapas dock en säkerhetskopia av rapporten för att spara en version av rapporten i originalformatet (före uppdateringen). Säkerhetskopian tas bort efter 30 dagar. 

För att hitta säkerhetskopian av rapportfilen gör du följande:

1. Gå till följande plats: ```C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\TempSaves\Backup```. Om du använder Microsoft Store-versionen av Power BI Desktop, använder du följande plats: ```C:\Users\<user>\Microsoft\Power BI Desktop Store App\TempSaves\Backups``` 

2. Leta upp kopian av rapporten som har samma namn och tidstämpel som originalfilen.

3. Kopiera filen till en plats som du föredrar, för att spara den.

4. Kontrollera att förhandsgranskningsfunktionen för **förbättrat metadataformat** är inaktiverad i Power BI Desktop om du väljer att öppna eller använda den ursprungliga filen. 

Säkerhetskopian skapas när rapporten uppgraderas, så ändringar som görs efter uppgraderingen ingår inte. Nya rapporter som skapas när funktionen för **förbättrat metadataformat** är aktiverad saknar säkerhetskopia.


## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

I förhandsversionen gäller följande begränsningar när förhandsfunktionen är aktiverad.

### <a name="unsupported-features-and-connectors"></a>Funktioner och anslutningar som inte stöds

Följande begränsningar gäller:

När du öppnar en befintlig PBIX- eller PBIT-fil som inte har uppgraderats misslyckas uppgraderingen om datamängden innehåller någon av följande funktioner eller anslutningar. Om den misslyckas bör det inte ha någon direkt påverkan på användarupplevelsen, och Power BI Desktop fortsätter använda det tidigare metadataformatet.

* Alla anpassade anslutningsprogram (versionsbegränsning maj 2020)
* Python-skript
* Azure DevOps Server
* BI-anslutningsapp
* Denodo
* Dremio
* Exasol
* Indexima
* IRIS
* Jethro ODBC
* Kyligence Enterprise
* Mark Logic ODBC
* Qubole Presto
* Team Desk
* M-uttryck som innehåller vissa teckenkombinationer som "\\n" i kolumnnamn
* När du använder datamängder med funktionen **Förbättrade datamängdsmetadata** aktiverad kan inte SSO-datakällor (datakällor för enkel inloggning) konfigureras i Power BI-tjänsten

Om du använder Power BI Desktop-versionen från **juni 2020** (eller senare) *har* alla anpassade anslutningsprogram och alla inbyggda anslutningsprogram stöd för Power BI Desktop och Power BI-tjänsten. När du använder versionen från juni 2020 eller senare under publiceringsprocessen, och om gatewayen påträffar problem, så publiceras visserligen datamängden, men användarna måste publicera om rapporten så att data uppdateras. Dialogrutan **Inställningar för datakälla** är den enda indikatorn på problem under publiceringsprocessen.

Rapporter som använder anslutningsprogram som inte stöds uppgraderas inte till det nya formatet. Rapporter som redan har uppgraderats, eller som skapades efter att den här nya funktionen aktiverades, har inte stöd för att lägga till de listade funktionerna eller anslutningsprogrammen som saknar stöd. 

Frågor med dynamiska datakällor stöds inte. Rapporter som har dynamiska datakällor kommer inte att uppgraderas till det nya formatet och rapporter som redan har uppgraderats eller som nyligen har skapats med funktionen aktiverad stöder inte tillägg av dynamiska datakällor. En fråga har en dynamisk datakälla om källan ändras beroende på en parameter, en instabil funktion eller funktionsindata. 

Frågor med fel i överordnade steg eller grenar stöds inte. 

PBIX- och PBIT-filer som redan har uppgraderats att använda **förbättrade datamängdsmetadata** *kan inte* heller använda ovanstående funktioner (eller eventuella anslutningsprogram som inte stöds).

### <a name="lineage-view"></a>Ursprungsvy
Datauppsättningar med det nya metadataformatet visar för närvarande inte länkar till dataflöden i ursprungsvyn i Power BI-tjänsten.

## <a name="next-steps"></a>Nästa steg

Du kan göra många olika saker med Power BI Desktop. Läs följande resurser för mer information om dess möjligheter:

* [Vad är Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Nyheter i Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Frågeöversikt med Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Datatyper i Power BI Desktop](desktop-data-types.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Vanliga frågeuppgifter i Power BI Desktop](../transform-model/desktop-common-query-tasks.md)
