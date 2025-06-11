## Business Intelligence Case Study: FMCG & Electronics – Seasonal Sales Analysis

## Cílem této mini BI analýzy bylo:
- Zmapovat tržby a ziskovost sortimentu v měsících listopad a prosinec 2024 – včetně dopadu slev, promo akcí a sezónních výkyvů.
- Zhodnotit efektivitu Black Friday a vánočních kampaní z pohledu zisku a marže.
- Vytvořit predikci pro jarní sezónu 2025 a navrhnout vhodný sortiment, promo strategii a plán zásob.
---
## Projekt pokrývá široké spektrum zboží napříč kategoriemi:
- Elektronika: mobily, TV, počítače, příslušenství
- FMCG: drogerie, kosmetika, potraviny, nápoje
- Domácnost: spotřebiče, kuchyňské potřeby
- Sezónní a dárkové zboží
---
## Klíčové výstupy:
- Porovnání tržeb, zisků a marží v jednotlivých kategoriích
- Identifikace tahounů výnosů (např. černá elektronika)
- Dopad promo akcí typu **2+1** na marži a logistiku
- Predikce růstu poptávky na jaře u kategorií jako **outdoor, sport, zdraví**
- BI doporučení pro strategické rozhodování

- Porovnávali jsme, Top 5 kategorií podle: zisku v Kč (sloupce) a marže v % (zelená čára)

Co jsme počítali:
Zisk = tržba × marže (pro každou kategorii)
Marže – byla různá pro každou kategorii podle reálných odhadů:
Mobily a hodinky: 20 %
TV a foto: 22 %
Velké spotřebiče: 24 %
Kávovary: 28 %
Gaming a hry: 25 %

Kategorie byly seřazeny podle výše zisku v prosinci 2024:
Nejvyšší zisk: Mobily a hodinky
Nejvyšší marže: Kávovary

Co tím graf ukazuje: I když mají mobily nejvyšší zisk, jejich marže je nejnižší
Kávovary mají nižší brat, ale nejvyšší maržovost (28 %)
Tento pohled je skvělý pro obchodní rozhodování: kde je objem vs. kde je zisk

Klíčové výstupy

- Prosinec 2024 byl z hlediska tržeb i zisků vrchol sezóny.
- Nejvyšší absolutní zisk přinesly **mobily a TV**, přestože měly nižší marže.
- **Kávovary a gaming** mají naopak vyšší marži, ale nižší obrat.
- 
### Porovnání top 5 kategorií podle zisku a marže – Prosinec 2024
Tento graf zobrazuje 5 nejvýkonnějších kategorií z hlediska zisku a jejich průměrnou marži v prosinci 2024.
- Nejvyšší zisk: **Mobily a hodinky**  
- Nejvyšší marže: **Kávovary** (28 %)

![Top 5 zisk a marže](images/GRAF_porovnání%20top%205%20kategorií%20dle%20marže%20a%20zisku.jpg)
---
## Složky projektu:
- `/data/` – vstupní dataset
- `/images/` – klíčové grafy a vizualizace
- `/notebooks/` – hlavní BI analýza v Pythonu
- `README.md` – tento souhrn
---
## Použité technologie:
- Excel	- Tvorba a údržba datasetu, výpočty, příprava vstupních dat
- Simulovaná datová základna (ručně tvořená)
- Analytická logika + vizualizace (grafy, trendy, porovnání)
- BI myšlení	Hodnocení efektivity promo, sezónnost, plánování zásob
- Python - Výpočty, predikce, marže, tržby, srovnání období
- SQL	- Dotazy pro agregace, filtrování, analýzu tržeb, počty kusů
