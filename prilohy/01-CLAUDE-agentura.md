# CLAUDE.md - agentura [NÁZEV AGENTURY]

> Šablona pro práci s Mergado MCP v Claude (projekt / složka agentury). Hranaté závorky nahraď, sekce, které nepotřebuješ, smaž. Soubor drž krátký (1-2 strany), detaily o klientech patří do jejich vlastních kontextů.

## Kdo jsme a jak pracujeme
- Agentura: [název], [počet lidí], zaměření: [PPC - Google Ads, Sklik, Meta, srovnávače].
- Já: [jméno], [role]. Spravuju klienty uvedené ve složce `klienti/`.
- Komunikace s klienty: [tykáme / vykáme], jazyk výstupů: čeština, pokud klient nechce jinak.

## Zlatá pravidla pro práci v Mergadu
1. **Nejdřív číst, pak navrhnout, až potom měnit.** Než cokoli vytvoříš nebo upravíš, projdi existující pravidla, výběry a elementy projektu.
2. **Bez mého výslovného souhlasu nic neměň.** Ke každé změně napiš: co vytvoříš, na jaké produkty to dopadne (výběr a počet) a jak to vrátit zpátky.
3. **Nejjednodušší řešení vyhrává.** Jedno pravidlo s dobře zvoleným výběrem je lepší než pět pravidel. Když navrhuješ víc pravidel, zdůvodni proč.
4. **Pojmenování:** pravidla a výběry pojmenuj `[prefix agentury] - účel - datum`, např. `JS - cenové hladiny - 2026-11`.
5. **Názvy elementů nehádej.** Zjisti je z projektu, rozlišují velká a malá písmena.
6. **Před změnou otestuj dopad** na pár konkrétních produktech a ukaž mi rozdíl před a po.
7. **Přegenerování feedu spouštím já**, ne ty.
8. Když si nejsi jistý, zeptej se. Radši jedna otázka navíc než změna v klientském feedu.

## Klienti a jejich kontexty
Ke každému klientovi existuje soubor `klienti/[klient].md` (šablona B). Před prací na klientovi si ho vždy přečti. Když kontext chybí, upozorni mě a nepokračuj s odhady.

| Klient | E-shop v Mergadu | Projekty (ID a kanál) | Smí AI měnit data? |
|---|---|---|---|
| [Klient 1] | [e-shop] | [123456 Google, 123457 Heureka] | [ano / jen návrhy / ne] |
| [Klient 2] | [e-shop] | [...] | [...] |

## Opakované úlohy (hotové postupy)
- **Štítky podle cenových hladin** do `custom_label_[x]`: hladiny podle kontextu klienta, jedno pravidlo s výběry.
- **Datum dostupnosti / akční cena:** řiď se pravidly v kontextu klienta.
- **Popisky produktů:** jen podle description briefu klienta (šablona C), nejdřív vzorek 3-5 produktů ke schválení.
- **Obohacení popisků z kontextu (kontext → tvrzení → doplněk):**
  1. Z recenzí a článků klienta vytáhni tvrzení do `tvrzeni.csv` (schéma v `03-tvrzeni-schema.md`, prompty v `prompty.md`). Čísla nevymýšlej, každé tvrzení musí mít zdroj.
  2. Tvrzení mi dej ke schválení. Bez schválení z nich nic nepiš.
  3. Ze schválených tvrzení napiš doplněk popisku na produkt do `doplnek-popisu.csv` (sloupce `g:id` a `DOPLNEK_POPISU`, jen odrážky, bez nadpisu).
  4. Do Mergada doplněk dostaň přes Import dat do skrytého pomocného elementu a jedno pravidlo Přepisování, které ho připojí k popisku. Stávající popisek nikdy nepřepisuj celý.
  5. Začni vzorkem desítek produktů v méně důležité kategorii, ověř na sledovaných produktech a teprve pak rozšiřuj.
- **Audit projektu:** shrň pravidla, výběry, skryté produkty a chyby importu, navrhni max. 5 nejdůležitějších úprav.

## Formát výstupů
- Stručně, česky, v bodech. Na konci vždy: co se změnilo (nebo co navrhuješ) a co mám udělat já.
- Tabulky jen tam, kde srovnáváš produkty nebo varianty.

## Zdroje
- Nápověda Mergada: https://help.mergado.com (čti při nejasnostech s pravidly a formáty).
- Mergado skilly: https://github.com/mergado/mergado-skills (před prací zkontroluj nejnovější verzi).
