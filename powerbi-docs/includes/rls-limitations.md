## <a name="limitations"></a>Begränsningar

Nedan följer en lista med aktuella begränsningar för säkerhet på radnivå i molnmodeller.

* Om du tidigare har definierat roller och regler i Power BI-tjänsten måste du återskapa dem i Power BI Desktop.

* Du kan endast definiera RLS på datauppsättningar som skapats med Power BI Desktop. Om du vill aktivera RLS för datauppsättningar som skapats med Excel måste du först konvertera filerna till PBIX-filer (Power BI Desktop-filer). [Läs mer](../desktop-import-excel-workbooks.md)

* Endast ETL- och DirectQuery-anslutningar stöds. Live-anslutningar till Analysis Services hanteras i modellen lokalt.

* Frågor och svar och Cortana kan inte användas med RLS för närvarande. Om alla modeller har konfigurerats med RLS, visas inte inmatningsrutan Frågor och svar för instrumentpaneler. Det finns med i planeringen, men vi har ingen tidsangivelse för när det kommer att införas.

## <a name="known-issues"></a>Kända problem

Det finns ett känt problem där du får ett felmeddelande om du försöker publicera en tidigare publicerad rapport från Power BI Desktop. Scenariot är följande.

1. Anna har en datauppsättning som har publicerats till Power BI-tjänsten och är konfigurerad med RLS.

1. Hon uppdaterar rapporten i Power BI Desktop och publicerar den igen.

1. Anna får ett fel.

**Lösning:** Publicera Power BI Desktop-filen från Power BI-tjänsten tills problemet är löst. Du kan göra det genom att välja **Hämta data** > **Filer**.
