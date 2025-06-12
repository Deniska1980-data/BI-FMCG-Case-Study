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
---
## Porovnání top 5 kategorií podle zisku a marže – Prosinec 2024

Tento graf ukazuje, které kategorie generovaly nejvyšší **zisk** a jakou měly **marži** v prosinci 2024:

- Nejvyšší zisk: **Mobily a hodinky**
- Nejvyšší marže: **Kávovary (28 %)**

![Top 5 zisk a marže](top5_zisk_marze_prosinec2024.jpg)

---
## Predikce jaro 2025

Na základě sezónnosti a předchozích let očekáváme:
- Růst poptávky po **kosmetice, sportovních potřebách a domácích spotřebičích**
- Pokles poptávky u **elektroniky** (kvůli vánoční saturaci trhu)
- Doporučení: podpořit kategorie jako **outdoor, péče o tělo, zdraví** formou **krátkých promo (max 14 dní)**
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
