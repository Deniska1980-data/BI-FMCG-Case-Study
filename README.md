# Mega Slevy – BI Analýza FMCG & Elektronika

## Cíl projektu

Cílem této BI analýzy bylo:
- Zhodnotit tržby a ziskovost v předvánoční sezóně (listopad a prosinec 2024),
- Vyhodnotit dopad promo akcí (např. 2+1 zdarma),
- Porovnat vývoj poptávky u konkrétních značek mezi měsíci,
- Vytvořit predikci pro jarní kampaň 2025.
---
## Použité technologie

- **Excel** – tvorba a údržba datasetu (FMCG, elektronika)
- **SQL** – agregace tržeb, průměrů, porovnání měsíců
- **Python** – výpočty, predikce, vizualizace
- **AI – ChatGPT** – nápověda při návrhu KPI, struktury, prezentace
---
## SQL porovnání značek (listopad vs. prosinec)

Porovnávali jsme výkonnost klíčových značek **mobilních telefonů** v měsících:

| Značka     | Tržba listopad | Tržba prosinec |
|------------|----------------|----------------|
| iPhone     | 856 000 Kč     | 1 206 000 Kč   |
| Samsung    | 740 000 Kč     | 1 003 000 Kč   |
| Huawei     | 402 000 Kč     | 586 000 Kč     |
| Xiaomi     | 611 000 Kč     | 694 000 Kč     |

**Závěr:** Ve všech značkách došlo k nárůstu tržeb v prosinci, nejvíce u **iPhonu**.

## Porovnání zisku podle kategorií – Listopad vs. Prosinec 2024

Následující graf ukazuje, jak se změnil zisk napříč jednotlivými kategoriemi mezi listopadem a prosincem 2024.

- Největší nárůst zaznamenaly **mobily a hodinky**, **potraviny**, **TV a foto**.
- Naopak kosmetika, drogerie a kuchyňské potřeby zůstaly spíše stabilní.

![Porovnání zisku – Listopad vs. Prosinec 2024](porovnani_zisku_katergorie_listopad_prosinec2024.jpg)

---
## Porovnání top 5 kategorií podle zisku a marže – Prosinec 2024

Tento graf ukazuje, které kategorie generovaly nejvyšší **zisk** a jakou měly **marži** v prosinci 2024:

- Nejvyšší zisk: **Mobily a hodinky**
- Nejvyšší marže: **Kávovary (28 %)**

![Top 5 zisk a marže](top5_zisk_marze_prosinec2024.jpg)

---
## Predikce jaro 2025

Na základě předchozích sezón a zákaznického chování jsme vytvořili predikci nejvýkonnějších kategorií pro jarní období:

- Nejvyšší odhad tržeb: **Sport a outdoor**
- Stabilní výkon: **Kosmetika, domácí spotřebiče, kávovary**
- Doporučení: zaměřit promo a zásobování na tyto segmenty

![Predikce jaro 2025](predikce_trzby_jarokampan2025.jpg)
---
## Klíčové BI závěry

- **Prosinec** přináší vyšší tržby, ale také **vyšší logistické a personální náklady**
- Ne každé promo přináší vyšší zisk – sledování **marže** je klíčové
- Výkonné promo potřebuje i **plánování zásob a personálu (HR + Office)**
- **Spring campaign** by se měla zaměřit na kategorie s vyšší maržovostí
---
## Struktura projektu

Mega-Slevy-BI-Case/
├── data/ # dataset (Excel / CSV)
├── images/ # grafy (JPG, PNG)
├── notebooks/ # analýza v Pythonu (Jupyter)
├── README.md # dokumentace

---
## Licence
Tento projekt slouží jako ukázka analytické práce v rámci portfolia BI Data Analyst.
