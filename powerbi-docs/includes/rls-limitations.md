## <a name="limitations"></a>Begränsningar
Nedan följer en lista med aktuella begränsningar för säkerhet på radnivå i molnmodeller.

* Om du tidigare hade roller och regler som definierats i Power BI-tjänsten måste du återskapa dem i Power BI Desktop.
* Du kan endast definiera RLS på de datauppsättningar som skapats med Power BI Desktop-klienten. Om du vill aktivera RLS för datauppsättningar som skapats med Excel, måste du konvertera filerna till PBIX-filer först. [Läs mer](../desktop-import-excel-workbooks.md)
* Endast ETL- och DirectQuery-anslutningar stöds. Live-anslutningar till Analysis Services hanteras i modellen lokalt.
* Frågor och svar och Cortana stöds inte med RLS just nu. Du kommer inte se inmatningsrutan Frågor och svar för instrumentpaneler om alla modeller har konfigurerats med RLS. Det finns med i planeringen, men vi har ingen tidsangivelse för när det kommer att införas.
* Extern delning stöds inte för närvarande med datauppsättningar som använder RLS.
* För en viss modell är det maximala antalet Azure AD-huvudkonton (dvs. enskilda användare eller säkerhetsgrupper) som kan tilldelas säkerhetsroller 1 000. Om du vill tilldela roller till ett stort antal användare, tilldelar du säkerhetsgrupper i stället för enskilda användare.

## <a name="known-issues"></a>Kända problem
Det finns ett känt problem där du får ett felmeddelande när du försöker publicera från Power BI Desktop om det tidigare har publicerats. Scenariot är följande.

1. Anna har en datauppsättning som är publicerad till Power BI-tjänsten och är konfigurerad med RLS.
2. Hon uppdaterar rapporten i Power BI Desktop och publicerar den igen.
3. Anna får ett fel.

**Lösning:** Publicera Power BI Desktop-filen från Power BI-tjänsten tills problemet är löst. Du kan göra det genom att välja **Hämta data** > **Filer**. 

