# Výukové karty ke kazuistikám

Opakovací kartičky (flashcards) k jednotlivým případům. Vše vychází z jedné předlohy
`karty-data.json` — HTML i CSV se z ní odvozují, takže jsou vždy v souladu.

## Co je ve složce

| Soubor | K čemu |
|--------|--------|
| `karty-data.json` | **Předloha** — zdroj pravdy. Pole: `front, back, pripad, obor, tema, zdroj`. |
| `kazuistiky-karty.html` | Interaktivní balíček karet, **offline** (stačí otevřít v prohlížeči). |
| `kazuistiky-anki.csv` | Export pro **Anki / Quizlet** (`Front,Back,Tags`, zdroj přilepen na konec Back). |

> Stav: zatím **případ 1** (středně těžká MR), 9 karet — vzorek ke schválení formátu.
> Po schválení se doplní případy 2–23.

## HTML balíček — jak používat

Otevři `kazuistiky-karty.html` dvojklikem (funguje bez internetu, nic se neinstaluje).

| Akce | Ovládání |
|------|----------|
| Překlopit kartu (otázka ⇄ odpověď) | **klik** na kartu nebo **mezerník** |
| Další / předchozí | tlačítka **‹ ›** nebo **šipky** ← → |
| Filtr podle případu | rozbalovací menu **Případ** |
| Filtr podle oboru | rozbalovací menu **Obor** (psychopedie, organizace, …) |
| Zamíchat pořadí | tlačítko **Zamíchat** |
| Vrátit původní pořadí | tlačítko **Reset** |
| Kde jsem | počítadlo **X / N** |

## Import CSV do Anki

1. Anki → **File → Import…** → vyber `kazuistiky-anki.csv`.
2. **Type:** Basic (Front/Back). **Field separator:** Comma.
3. Zaškrtni **Allow HTML in fields** (kvůli diakritice a symbolům to není nutné, ale neuškodí).
4. Namapuj sloupce: **1 → Front**, **2 → Back**, **3 → Tags**.
5. Import. Tagy `pripad1 psychopedie definice` umožní filtrovat balíček podle případu i oboru.

## Import do Quizletu

Quizlet pracuje se 2 poli (termín + definice), sloupec Tags ignoruj:

1. Quizlet → **Create → Import**.
2. Mezi termínem a definicí zvol **Comma**, mezi kartami **New line**.
3. Vlož obsah CSV (Quizlet vezme první dva sloupce jako termín/definici).
   Pokud Quizlet zlobí s uvozovkami, jednodušší je zkopírovat dvojice Front⇥Back ručně
   (oddělené tabulátorem) — řekni a vygeneruju TSV variantu.

## Poznámka ke zdrojům

Každá karta má v poli `zdroj` (a v CSV na konci odpovědi) uvedeno, odkud informace pochází —
primárně **Vágnerová** s číslem strany, doplňkové zdroje jmenovitě. Nejisté údaje jsou
značené `⚠️ ověřit`.
