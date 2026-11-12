# Prompty: kontext → tvrzení → doplněk popisku

Prompty jsou psané pro Claude Code se složkou klienta (CLAUDE.md agentury, kontext klienta, brief). Fungují i v běžném chatu, když data vložíte ručně. Hranaté závorky nahraďte.

---

## 1. Recenze → tvrzení na produkt

```
Pracuji pro e-shop [klient]. V souboru [data/recenze] jsou recenze jeho produktů.

Nejdřív ověř, že máš všechny zdroje recenzí (export platformy, tabulky po migraci,
srovnávače, recenze uložené v projektu v Mergadu). Když se počty u stejného produktu liší, upozorni mě.

Vytáhni z nich tvrzení o produktech podle schématu v 03-tvrzeni-schema.md.
Tvrzení je věta o tom, co o produktu platí. Není to citace toho, co kdo napsal.

Pravidla:
- Piš jen to, co v recenzích opravdu je. Nic nedoplňuj z toho, co víš odjinud.
- Nevymýšlej čísla, ani hodnocení, ani parametry.
- U každého tvrzení uveď ID recenze a počet nezávislých recenzí, které ho dokládají.
- Recenze bez obsahu ("funguje", "spokojenost") vynech a napiš, kolik jich bylo.
- Když stejná recenze visí u víc produktů, označ tvrzení jako sdílené.
- Výhrady nevynechávej.

Výstup: tabulka tvrzeni.csv (sloupce podle schématu, druh = produkt, stav = navrženo).
Na konci tři věci, které se v recenzích opakují nejčastěji napříč produkty.
```

## 2. Článek → tvrzení na segment

```
V souboru [data/clanky/nazev.md] je článek z blogu klienta.

Vytáhni z něj tvrzení, která zákazníkovi pomůžou vybrat mezi produkty, podle schématu
v 03-tvrzeni-schema.md. Vynech všechno ostatní.

Pravidla:
- Jen to, co je v článku. Nevymýšlej čísla.
- Když si článek protiřečí, napiš mi to a nech obě verze.
- U každého tvrzení navrhni selektor: podle čeho v katalogu poznám produkty, kterých
  se týká (název, kategorie, parametr). Ověř ho přes Mergado MCP na projektu [ID]:
  kolik produktů vybere a 5 příkladů. Vypiš i produkty, které do selektoru spadly,
  ale tvrzení na ně neplatí (doplňky, poukazy, příbuzné produkty), a vyluč je.
- Do segmentu dej jen to, co platí bez výjimky pro celou skupinu.

Výstup: řádky do tvrzeni.csv (druh = segment, stav = navrženo).
```

## 3. Schválená tvrzení → doplněk popisku

```
Vezmi z tvrzeni.csv jen řádky se stavem schváleno. Pro každý produkt, kterého se týká
aspoň jedno tvrzení (přímo, nebo přes selektor segmentu), napiš doplněk popisku.

Stávající popisek načti z projektu [ID] přes Mergado MCP a nepřepisuj ho.
Doplněk je blok, který se připojí pod něj.

Co do doplňku patří:
- přednostně to, co stávající popisek neříká: co zákazník k produktu potřebuje,
  kdy se nehodí, na co si dát pozor
- výhrady napsané věcně jako vlastnost produktu, bez zmínky o recenzích

Pravidla:
- Nic, co už v popisku je, neopakuj. Posuzuj to po smyslu, ne podle shody slov.
- Když tvrzení s popiskem nesouhlasí i jen nepřímo (popisek "pohodlná na celodenní túry",
  tvrzení "po pár hodinách tlačí"), nepiš ho a dej produkt do seznamu k rozhodnutí.
- Bezpečnostní tvrzení nepřenášej na produkty se zvláštním určením (např. zdravotní pomůcky).
- Čísla jen z tvrzení.
- Když si tvrzení s popiskem odporuje, nepiš ani jedno a dej produkt do seznamu k rozhodnutí.
- Nejvýš 4 odrážky, každá nejvýš 2 věty, celý doplněk do 600 znaků.
- Původní popisek a doplněk dohromady se musí vejít do limitu kanálu
  (u Googlu 5 000 znaků). Když se nevejde, doplněk zkrať nebo vynech a upozorni mě.
- Vykej. Žádné superlativy, výzvy ke koupi ani ceny.
- Nadpis bloku nepiš, přidá ho pravidlo v Mergadu.

Výstup:
1. doplnek-popisu.csv se sloupci g:id a DOPLNEK_POPISU. Když se doplněk liší jen mezi
   modely, ne mezi velikostmi, použij místo g:id item_group_id (jeden řádek na model).
   (odrážky začínají "- ",
   každá na novém řádku v jedné buňce, oddělovač středník).
2. Kontrolní tabulka: g:id | odrážka | z jakého tvrzení | zdroj.
3. Seznam produktů k rozhodnutí (rozpory, slabě doložená tvrzení, přetečení délky).

Začni vzorkem [20] produktů z kategorie [kategorie] a počkej na schválení.
```

## 4. Zápis do Mergada (po schválení vzorku)

```
Doplněk z doplnek-popisu.csv dostaň do projektu [ID]. Nejdřív mi popiš plán a počkej na souhlas:
1. skrytý element DOPLNEK_POPISU
2. pravidlo Import dat (CSV, párování přes g:id, importovat jen DOPLNEK_POPISU)
3. výběr "DOPLNEK_POPISU není prázdný"
4. pravidlo Přepisování na g:description nad tím výběrem s hodnotou:
   %g:description%
   (prázdný řádek)
   Co je dobré vědět před nákupem
   %DOPLNEK_POPISU%
Import musí běžet před přepisováním. Po založení ověř výsledek na sledovaných produktech:
produkt s doplňkem, produkt se dvěma zdroji a produkt bez doplňku (ten se nesmí změnit).
Přegenerování feedu spouštím já.
```

## 5. Volitelně: tvrzení → otázky a odpovědi

```
Ze schválených tvrzení udělej otázky a odpovědi k produktům.
- Otázka je to, co zákazník napíše, když vybírá. Ptá se na situaci, ne na recenze.
- Odpověď začíná Ano nebo Ne, když to jde, má nejvýš tři věty a uvádí podmínky.
- Řádky s výhradou označ, ať se rozhodnu, jestli je zveřejnit.

Výstup jako tabulka se sloupci:
g:id
g:question_and_answer { @@POSITION = 1 } | g:question
g:question_and_answer { @@POSITION = 1 } | g:answer
g:question_and_answer { @@POSITION = 2 } | g:question
g:question_and_answer { @@POSITION = 2 } | g:answer
poznamka
```
