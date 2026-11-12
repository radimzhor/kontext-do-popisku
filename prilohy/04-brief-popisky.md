# Description brief: [NÁZEV E-SHOPU] - [KATEGORIE / VÝBĚR]

> Zadání pro generování popisků produktů přes Mergado MCP. Patří ke kontextu klienta (šablona B). Na jeden brief jedna skupina produktů s podobným typem popisku.

## 1. Rozsah
- Projekt v Mergadu: [ID] ([kanál, např. Google Nákupy])
- Produkty: [výběr v Mergadu nebo podmínka, např. kategorie "Trekové boty" a cena nad 1 500 Kč]
- Cílový element: [description / g:description / vlastní element]
- Zdroj dat pro popisek: [název, parametry, kategorie, značka, stávající popis, web e-shopu]

## 2. Proč popisky měníme
- Cíl: [lepší relevance v Google Nákupech / popisky pro ChatGPT / chybějící popisy / sjednocení stylu]
- Jak poznáme úspěch: [např. žádný produkt bez popisku, CTR ve skupině, schválení klientem]

## 3. Struktura popisku
1. První věta: co to je a pro koho (hlavní klíčové slovo na začátku).
2. 2-3 hlavní přínosy pro zákazníka, opřené o parametry z feedu.
3. Klíčové parametry: [rozměr, materiál, kompatibilita, ...].
4. Na co upozornit: [údržba, kompatibilita, omezení].
- Délka: [např. 300-800 znaků], bez HTML [nebo: povolené odstavce].

## 4. Tón a jazyk
- [vykáme / neosobně], [odborně / srozumitelně pro laika]
- Používat: [slova a obraty klienta]
- Nepoužívat: superlativy bez opory ("nejlepší na trhu"), nepodložená tvrzení, ceny a akce (mění se), výzvy typu "kupte hned", emoji, VELKÁ PÍSMENA.

## 5. Pravidla pravdivosti
- Piš jen to, co je v datech produktu nebo v kontextu klienta. Nic si nedomýšlej.
- Když chybí údaj, který struktura vyžaduje, vynech ho a produkt označ do seznamu "chybí data".
- Názvy značek a modelů přepisuj přesně.

## 6. Ukázka (vzor, jak má výsledek vypadat)
- Produkt: [název]
- Dobrý popisek: [vlož vzorový text, který klient schválil]

## 7. Postup práce s Mergado MCP
1. Přečti kontext klienta a tento brief.
2. Najdi produkty v rozsahu a ukaž mi jejich počet a 5 příkladů stávajících popisků.
3. Napiš návrh pro 3-5 produktů jako tabulku: produkt | stávající popisek | nový popisek | z jakých dat vychází.
4. Počkej na mé schválení nebo připomínky.
5. Po schválení navrhni, jak popisky do Mergada dostat, a znovu počkej na souhlas. U doplňku pod stávající popisek: tabulka `g:id` a `DOPLNEK_POPISU` → Import dat do skrytého pomocného elementu → jedno pravidlo Přepisování na výstupní element popisku (u Googlu `g:description`) s hodnotou `%g:description%`, prázdný řádek, nadpis bloku a `%DOPLNEK_POPISU%`, omezené výběrem „DOPLNEK_POPISU není prázdný“. Zapisuj do výstupního elementu, ne do vstupního `description`, převod formátu ho přepisuje dřív.
6. Po zápisu ověř výsledek na několika produktech a vypiš seznam produktů, u kterých chyběla data.
