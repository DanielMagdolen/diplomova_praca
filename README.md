# Metódy objavovania znalostí z časových radov

Tento repozitár obsahuje praktickú časť diplomovej práce zameranej na analýzu a predikciu časových radov v oblasti realitného trhu. Projekt implementuje kompletný analytický pipeline podľa metodiky CRISP-DM a porovnáva výkonnosť štatistických a neurónových modelov na reálnych dátach.

## Autor

**Bc. Daniel Magdolen**
Diplomová práca – *Metódy objavovania znalostí z časových radov*
Univerzita Konštantína Filozofa v Nitre, Fakulta prírodných vied a informatiky


## Prehľad projektu

Cieľom projektu je analyzovať vývoj cien nehnuteľností a vytvoriť modely na ich predikciu na základe historických dát.

Projekt zahŕňa:

- spracovanie datasetu predajov nehnuteľností,
- agregáciu dát do mesačného časového radu,
- identifikáciu trendu a sezónnosti,
- implementáciu predikčných modelov,
- porovnanie ich presnosti pomocou metrík.


## Dataset

Použitý dataset: **King County House Sales (Kaggle)**

Obsahuje viac ako **656 000 záznamov** o predajoch nehnuteľností, vrátane:

- dátumu predaja (`sale_date`),
- predajnej ceny (`sale_price`),
- atribútov nehnuteľností,
- lokalizačných údajov.

Dáta sú transformované na:

- **mesačný univariátny časový rad**
- následne aplikovaná **logaritmická transformácia (log1p)**


## Metodika

Projekt je realizovaný podľa metodiky **CRISP-DM**:

1. **Business Understanding** – definovanie cieľa predikcie cien
2. **Data Understanding** – analýza dát a ich kvality
3. **Data Preparation** – čistenie, agregácia, transformácie
4. **Modeling** – implementácia modelov
5. **Evaluation** – vyhodnotenie výkonnosti


## Použité modely

Implementované modely:

- **Naívny model (Last Value)**
- **Sezónny naívny model**
- **SARIMAX**
- **Prophet**
- **LSTM Ensemble**


## Vyhodnocovacie metriky

Modely sú hodnotené pomocou:

- **MAE** – Mean Absolute Error
- **RMSE** – Root Mean Squared Error
- **MAPE** – Mean Absolute Percentage Error

Vyhodnotenie prebieha:

- v **logaritmickom priestore**
- v pôvodnej mierke **USD**


## Výsledky (súhrn)

Hlavné zistenia:

- Modely **SARIMAX** a **LSTM** dosahujú najlepšie a porovnateľné výsledky
- Model **Prophet** vykazuje vyššiu chybu
- Naívne modely majú výrazne horšiu výkonnosť

| Model          | MAE_USD | RMSE_USD | MAPE (%) |
| -------------- | ------: | -------: | -------: |
| SARIMAX        |  49 141 |   60 844 |     3.91 |
| LSTM Ensemble  |  49 254 |   61 184 |     3.88 |
| Prophet        |  80 791 |  101 086 |     6.57 |
| Sezónny naívny |  82 940 |  101 714 |     6.61 |
| Naívny         | 167 300 |  177 536 |    13.16 |


## Workflow

Postup spracovania:

1. Načítanie datasetu
2. Agregácia na mesačné dáta
3. Logaritmická transformácia
4. Trénovanie modelov
5. Predikcia (test = 24 mesiacov)
6. Vyhodnotenie metrík


## Použité technológie

Projekt využíva:

```bash
pandas
numpy
matplotlib
statsmodels
pmdarima
prophet
scikit-learn
tensorflow
scipy
kagglehub
```


## Inštalácia

```bash
git clone https://github.com/DanielMagdolen/diplomova_praca
cd diplomova_praca
python -m venv .venv
source .venv/bin/activate  # Linux / macOS
# alebo
.venv\Scripts\activate     # Windows
```


## Spustenie

```bash
jupyter notebook Dimplomová_práca_CRISP-DM.ipynb
```


## Hlavné výstupy projektu

Projekt demonštruje:

- analýzu vývoja cien nehnuteľností
- identifikáciu trendu a sezónnosti
- porovnanie štatistických a neurónových modelov
- interpretáciu výsledkov predikcie
- diskusiu limitov modelov


## Poznámka

Dataset je načítavaný priamo v notebooku prostredníctvom Kaggle API.

## Licencia

Projekt je určený na akademické a výskumné účely.
