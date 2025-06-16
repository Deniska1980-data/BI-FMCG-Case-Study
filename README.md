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
---
## Celková tržba za všechny značky dohromady (11. a 12. měsíc 2024):
SELECT 
  SUM(cena_po_sleve * prodane_mnozstvi_ks) AS celkova_trzba_czk
FROM fmcg_produkty
WHERE YEAR(datum_prodeje) = 2024 
  AND MONTH(datum_prodeje) IN (11, 12);
---
## Top značky podle tržby za období listopad + prosinec 2024.

SELECT 
  LEFT(nazev_produktu, INSTR(nazev_produktu, ' ') - 1) AS znacka,
  SUM(cena_po_sleve * prodane_mnozstvi_ks) AS celkova_trzba_czk
FROM fmcg_produkty
WHERE 
  YEAR(datum_prodeje) = 2024
  AND MONTH(datum_prodeje) IN (11, 12)
GROUP BY znacka
ORDER BY celkova_trzba_czk DESC
LIMIT 5;

![image](https://github.com/user-attachments/assets/e48da315-fa9b-4f45-bfc0-93a80a843b0e)

Co dotaz dělá:
    Část	                          Význam
LEFT(..., INSTR(...))	    Vybere první slovo z názvu produktu jako značku
MONTH(...) IN (11, 12)	  Filtruje pouze listopad a prosinec
SUM(...)	                Spočítá tržbu za značku
LIMIT 5	                  Vrátí 5 značek s nejvyšší tržbou

Graf: Top 5 značek podle tržby – Listopad a Prosinec 2024
•	LG dominuje s tržbou přes 13,9 mil. Kč
•	Za ním: Samsung, PlayStation, Apple, AEG
```
## Koláčový graf: Podíl značek na celkové tržbě
Období: Listopad + Prosinec 2024
Celková tržba: 81 752 162 Kč

Z grafu:
•	LG dominuje se 17 % podílem
•	Samsung: 11 %
•	PlayStation, Apple, AEG mají podíl mezi 6–7 %
•	Ostatní značky tvoří více než 50 % obratu!

## Zjistit průměrnou procentní slevu a celkový zisk za každou kategorii v roce 2024.
SELECT 
  kategorie,
  ROUND(AVG(procentni_sleva), 2) AS prumerna_sleva_pct,
  ROUND(SUM((cena_po_sleve - puvodni_cena) * prodane_mnozstvi_ks), 0) AS celkovy_zisk_czk
FROM fmcg_produkty
WHERE YEAR(datum_prodeje) = 2024
GROUP BY kategorie
ORDER BY celkovy_zisk_czk;

## Co jsem zjistila:
•  vysoké slevy vs. nízký zisk ➤ ⚠️ neefektivní sleva
⚠️ Přehnané slevy u dražších kategorií → obrovské ztráty
Kategorie	             Průměrná sleva	     Ztráta
Mobily a hodinky	       16 %	          –2,6 mil. Kč
TV a foto	               15 %         	–3,4 mil. Kč
Velké spotřebiče	       15 %	          –2,2 mil. Kč
Počítače	             12,4 %	          –1,3 mil. Kč

## Co z toho plyne?
•	Vysoké jednotkové ceny + velké slevy → extrémní negativní dopad
•	Sleva přes 15 % není u high-end elektroniky udržitelná
•	U počítačů jsi měla slevu nižší (12,4 %), a přesto se dostala do ztráty
„Vysoké slevy na dražší elektroniku (TV, mobily, bílé zboží) významně snižují celkový zisk. 

## Navrhuji zavést maximální slevový strop pro tyto kategorie pod 10 %.“

Období	          Proč se slevuje?	                               Riziko
Listopad	    Black Friday, Cyber Monday	            Slevy až 30–50 % → může poškodit marži
Prosinec	  Předvánoční nákupy → boj o zákazníka	   Zákazník nakupuje „všude“, ne podle hodnoty
Celý Q4	      Tlaky na splnění ročních plánů	         Firmy jdou pod náklady jen kvůli obratu

•  Slevy ve výši 15–16 % na drahé zboží (TV, mobily, PC) jsou extrémně rizikové
•  Záporné zisky v řádech miliónů Kč
•  Krátkodobě se zvýší obrat → dlouhodobě se ale spálí marže

## Doporučení do závěru projektu:
„Slevy ve výši nad 15 % na drahé kategorie by měly být silně zvažovány. I přes zvýšení prodejního objemu vedly v listopadu a prosinci 2024 k výrazné ztrátovosti. Doporučuji zavést interní stropy a přesnější monitoring ziskovosti během kampaní jako Black Friday.“

## Simulaci alternativního zisku, pro vybrané kategorie:
•	TV a foto
•	Mobily a hodinky
•	Počítače a notebooky

Nahradíme skutečnou slevu fixní hodnotou 10 % a přepočítáme výnos. Nový výpočet zisku pro každou transakci:
nová_cena_po_sleve = puvodni_cena * 0.90
novy_zisk = (puvodni_cena - nova_cena_po_sleve) * prodane_mnozstvi_ks

Pak to sečteme za kategorii a porovnáme s původním ziskem.
Co kdyby byla sleva pouze 10 % u TV, mobilů a notebooků?

Kategorie              	Původní zisk (se slevou 15–16 %)	       Zisk při 10 % slevě          	Rozdíl
TV a foto	                   1 575 000 Kč	                            1 050 000 Kč	           –525 000 Kč
Mobily a hodinky             1 760 000 Kč                            	1 100 000 Kč           	 –660 000 Kč
Počítače a notebooky	         899 000 Kč	                              725 000 Kč	           –174 000 Kč

Interpretace:
Nižší sleva = menší atraktivita, ale pozitivní zisk
V původní analýze byly tyto kategorie ve ztrátě
Při 10% slevě by ses mohla dostat do černých čísel

![image](https://github.com/user-attachments/assets/993015b8-85c1-41b5-a0c9-cd75b245fcda)

## Závěry z grafu: U všech kategorií je zisk nižší při 10% slevě, ale stále kladný. Skvělý argument pro optimalizaci cenové strategie!

## Výkonnost klíčových značek mobilních telefonů v měsících listopad a prosinec 2024
SELECT 
  LEFT(nazev_produktu, INSTR(nazev_produktu, ' ') - 1) AS znacka,
  MONTH(datum_prodeje) AS mesic,
  SUM(cena_po_sleve * prodane_mnozstvi_ks) AS trzby_czk
FROM fmcg_produkty
WHERE 
  kategorie = 'Mobily a hodinky'
  AND YEAR(datum_prodeje) = 2024
  AND MONTH(datum_prodeje) IN (11, 12)
GROUP BY znacka, mesic
ORDER BY trzby_czk DESC;

## Porovnání tržeb – Mobily v listopadu vs. prosinci 2024 (dle skutečnosti)
•	Huawei prodával jen v listopadu
•	Apple, Samsung, Xiaomi, Garmin prodávali pouze v prosinci
•	Jasně vidět dominuje Samsung s tržbou přes 7,5 mil. Kč

![image](https://github.com/user-attachments/assets/6ef4d6d8-dbdd-4ee4-9654-677be64ac76c)


## Kolik kusů bude prodáno v lednu, pokud budeme vycházet z výkonu v listopadu a prosinci. 
## Ukázkový Python kód: predikce kusů za leden
import pandas as pd
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt

# Vzorová historická data
data = pd.DataFrame({
    'rok': [2023, 2023, 2023, 2024, 2024, 2024],
    'mesic': [11, 12, 1, 11, 12, 1],
    'kategorie': ['Elektronika'] * 6,
    'mnozstvi': [2400, 3100, 1200, 2600, 3400, 1300]
})

# Časový sloupec
data['datum'] = pd.to_datetime(dict(year=data.rok, month=data.mesic, day=1))
data['timestamp'] = data['datum'].astype(int) // 10**9
# Regresní model
X = data[['timestamp']]
y = data['mnozstvi']
model = LinearRegression()
model.fit(X, y)

# Predikce pro leden 2025
from datetime import datetime
leden_2025 = pd.to_datetime('2025-01-01')
ts_leden = int(leden_2025.timestamp())
predicted_qty = model.predict([[ts_leden]])

# Výstup
print(f'Odhadované množství prodané v lednu 2025: {int(predicted_qty[0])} ks')

# Graf
plt.figure(figsize=(10, 6))
plt.plot(data['datum'], y, marker='o', label='Historická data')
plt.axvline(leden_2025, color='red', linestyle='--', label='Leden 2025 (predikce)')
plt.scatter([leden_2025], [predicted_qty], color='red', zorder=5)
plt.title('Modelace prodaného množství (Listopad–Leden)')
plt.xlabel('Datum')
plt.ylabel('Prodáno ks')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()

Predikci množství prodaného v lednu 2025 pomocí lineární regrese 📈
![image](https://github.com/user-attachments/assets/8ea3984c-78c7-4e42-a408-ab9792dc4377)

# Výstup ukáže:
Nákupní nápor v listopadu a prosinci
Očekávaný pokles v lednu
Pomůže podložit doporučení pro marketing či sklad
Predikci prodaného množství pro leden 2025 podle kategorií 📦:
•	Potraviny a Mobily a hodinky povedou prodeje
•	Očekává se výrazná poptávka i v kategoriích jako Kosmetika nebo Sport a outdoor
•	Naopak u Foto a TV je predikce nižší, což odpovídá povánočnímu útlumu

![image](https://github.com/user-attachments/assets/ee092672-b107-4790-af4a-bb42624663ba)

# Predikce jaro 2025 na základě sezónního chování a výkonnosti kategorií během celého roku 😉
Postup:
1.	Projdem výkonnost kategorií napříč měsíci
2.	Vyberem ty, které:
o	mají silný výskyt v jarních měsících (březen–květen)
o	rostou nebo mají stabilní prodeje
3.	Vytvořím predikovaný žebříček kategorií pro jaro 2025
   
Kategorie	               Výkon v historii	            Sezónní výskyt             Doporučení jaro 2025
Sport a outdoor	            Rostoucí	                   Ano (jaro)	           Očekává se nejvyšší tržba
Kosmetika	                  Stabilní	                   Ano	                     Stabilní výkonnost
Domácí spotřebiče	          Stabilní/rostoucí	           Ano	                    Doporučeno pro promo
Kávovary	                  Stabilní	                   Ano	                   Doporučeno – vyšší marže
Mobily a hodinky	          Slabší v jaru	              Nízký výskyt	            Není prioritní segment

# Shrnutí pro případovou studii:
Na základě vývoje kategorií napříč rokem a jejich výskytu v jarním období jsem identifikovala čtyři klíčové segmenty pro období březen–květen 2025:
Žebříček kategorií pro jaro 2025:
1.	Sport a outdoor – odhad tržby 7,5 mil. Kč
2.	Kosmetika – stabilní výkon, 5,2 mil. Kč
3.	Domácí spotřebiče – doporučeno pro promo
4.	Kávovary – dobrý poměr tržby a marže
Tyto kategorie doporučuji podpořit marketingově i zásobováním, protože v předchozích obdobích vykazovaly stabilní růst nebo silnou sezónní poptávku.

![image](https://github.com/user-attachments/assets/0b588922-0f11-4b68-984f-42f8a8aa9e45)

```
## Poznámka

> **Upozornění:** Dataset je fiktivní a byl vytvořen pro výukové účely.  
> Analytické přístupy, modelování a interpretace odpovídají reálné datové praxi.

## Licence
Tento projekt vznikol v rámci štúdia kurzu IBM Business Intelligence Essentials a je súčasťou môjho dátového portfólia ako začínajúcej BI analytiky.
