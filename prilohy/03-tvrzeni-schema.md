# Tvrzení: schéma a pravidla

Tvrzení je věta o tom, co o produktu nebo skupině produktů platí. Je to mezivrstva mezi surovým kontextem (recenze, články, podpora) a textem ve feedu (popisky, Q&A, highlights). Tvrzení se nejdřív validuje a teprve potom se z něj píše.

## Sedm polí

| Pole | Co do něj patří | Příklad |
|---|---|---|
| entita | čeho se tvrzení týká: konkrétní produkt (ID), nebo typ produktu | Trekové boty s membránou |
| vlastnost | co platí | Membrána nepropustí vodu ani při celodenním dešti |
| důsledek | co z toho plyne pro zákazníka, obyčejnými slovy | Na vícedenní trek v horách zůstanou nohy suché |
| podmínka | kdy to platí | Jen když je svršek pravidelně impregnovaný |
| vymezení | kdy to neplatí, s čím si to lidé pletou | V horkém létě se v nich noha víc potí než v botě bez membrány |
| jazyk zákazníka | jak se zákazníci ptají, jejich slovy | „promokají?", „dají se nosit v létě?" |
| zdroj | odkud tvrzení je (recenze, článek, podpora) a kolik dokladů má | recenze, 4 nezávislé |

## Dva druhy tvrzení

- **Tvrzení na produkt** pochází hlavně z recenzí. Patří jednomu produktu a páruje se přes jeho ID.
- **Tvrzení na segment** pochází hlavně z článků a návodů. Platí pro skupinu produktů, takže potřebuje **selektor**: podle čeho ve feedu poznáte produkty, kterých se týká (název, kategorie, parametr). U selektoru vždy ověřte, kde by mohl zradit.

## Pravidla

1. Čísla se negenerují, jen přenášejí. Když číslo ve zdroji není, v tvrzení není.
2. Každé tvrzení má zdroj. Bez zdroje se nepoužije.
3. Tvrzení z jediné recenze, nebo z recenze sdílené víc produkty, se označí jako slabě doložené. Zveřejňuje se až po rozhodnutí člověka.
4. Do segmentu patří jen to, co platí bez výjimky pro celou skupinu (typicky podmínky použití a údržby). Vlastnosti, které se mezi produkty liší, patří k produktu.
5. Když si tvrzení odporuje s popiskem výrobce, nepoužije se ani jedno a rozhodne člověk.
6. Výhrady se nevynechávají. Píšou se věcně jako vlastnost produktu, bez citace a bez zmínky o recenzích.

## Tabulka tvrzení

Doporučené sloupce souboru `tvrzeni.csv` (oddělovač středník):

`druh;entita;selektor;vlastnost;dusledek;podminka;vymezeni;jazyk_zakaznika;zdroj;doklady;stav`

- `druh`: produkt / segment
- `selektor`: u segmentu podmínka pro výběr v Mergadu, u produktu prázdné
- `doklady`: počet nezávislých zdrojů
- `stav`: navrženo / schváleno / zamítnuto

Ukázka je v souboru `ukazka-tvrzeni.csv`.
