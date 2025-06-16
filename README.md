# FMCG – Analýza prodeje spotřebního zboží / FMCG Sales & Margin Case Study (SQL + Python)

Tento projekt představuje praktickou analýzu prodejních dat z oblasti rychloobrátkového zboží (FMCG) s využitím SQL a Pythonu.  
**Analýza je postavená na fiktivním datasetu**, který simuluje reálné prodeje, slevy, marže a zákaznické chování v prostředí českého maloobchodu.

Cílem bylo procvičit si reálné analytické přístupy, vytvářet byznysové závěry a predikce, a připravit výstupy vhodné pro datovou praxi.

---
## Cíle projektu

- Porovnat výkon značek a kategorií napříč měsíci
- Analyzovat dopad slev na zisk a marži
- Zjistit, které značky dominují v klíčových obdobích (např. před Vánoci)
- Modelovat dopad snížení slev na ziskovost
- Vytvořit predikci nejvýkonnějších kategorií pro jaro 2025
---
## Použité nástroje

- **MySQL** – výpočty tržeb, zisků, marží
- **Python (Pandas, Matplotlib, scikit-learn)** – vizualizace a predikce
- **Jupyter Notebook** – analýza, simulace a prezentace výstupů
- **Excel/CSV** – strukturovaný vstupní dataset
---
## Struktura složek

```
/images         → Grafy, ERD diagram, vizualizace
/data           → Očištěné datové soubory (.csv)
/sql            → SQL dotazy použití v analýze
/python         → Jupyter notebooky, predikce, simulace
README.md       → Tento soubor s popisem projektu
---

## Ukázkový SQL dotaz

SELECT znacka, SUM(prodane_mnozstvi_ks * jednotkova_cena) AS trzba
FROM prodeje
WHERE datum_prodeje BETWEEN '2024-11-01' AND '2024-12-31'
GROUP BY znacka
ORDER BY trzba DESC;
```

## Poznámka

> **Upozornění:** Dataset je fiktivní a byl vytvořen pro výukové účely.  
> Analytické přístupy, modelování a interpretace odpovídají reálné datové praxi.

## Licence
Tento projekt vznikol v rámci štúdia kurzu IBM Business Intelligence Essentials a je súčasťou môjho dátového portfólia ako začínajúcej BI analytiky.
