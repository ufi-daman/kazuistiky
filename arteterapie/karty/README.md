# Výukové karty — Arteterapie

Opakovací kartičky (flashcards) ke kazuistikám **optikou arteterapie**. Vše vychází z jedné
předlohy `karty-data.json` — HTML i CSV se z ní odvozují, takže jsou vždy v souladu.

Jde o **samostatný balíček** vedle speciálně-pedagogických karet: tenhle export má vlastní
balíček **`Arteterapie`** (spec-ped má `Kazuistiky`), takže se v Anki nemíchají.

## Co je ve složce

| Soubor | K čemu |
|--------|--------|
| `karty-data.json` | **Předloha** — zdroj pravdy. Pole: `front, back, pripad, obor, tema, zdroj`. |
| `kazuistiky-karty.html` | Interaktivní balíček karet, **offline** (stačí otevřít v prohlížeči). |
| `kazuistiky-anki.csv` | Export pro **Anki / Quizlet** (TSV `Front⇥Back⇥Tags`, zdroj přilepen na konec Back). |

> Stav: zatím **případ 1** (středně těžká MR + vada řeči), 10 karet — vzorek ke schválení formátu.
> Po schválení se doplní případy 2–23 (přes `_fragments/NN.json` + rebuild).

## HTML balíček — jak používat

Otevři `kazuistiky-karty.html` dvojklikem (funguje bez internetu, nic se neinstaluje).

| Akce | Ovládání |
|------|----------|
| Překlopit kartu (otázka ⇄ odpověď) | **klik** na kartu nebo **mezerník** |
| Další / předchozí | tlačítka **◀ ▶** nebo **šipky** ← → |
| Filtr podle případu | rozbalovací menu **Případ** |
| Filtr podle oboru | rozbalovací menu **Obor** (arteterapie, artefiletika, arteterapie-technika, …) |
| Zamíchat pořadí | tlačítko **Zamíchat** |
| Vrátit původní pořadí | tlačítko **Pořadí** |
| Kde jsem | počítadlo **X / N** |

## Import CSV do Anki

Soubor `kazuistiky-anki.csv` má na začátku **direktivy**, které Anki přečte sám
(`#separator:Tab`, `#html:false`, `#deck:Arteterapie`, `#tags column:3`) — díky tomu se
oddělovač i cílový balíček nastaví automaticky.

1. Anki → **File → Import…** → vyber `kazuistiky-anki.csv`.
2. **Type:** Basic (Front/Back). **Field separator:** **Tab** (soubor ji určuje direktivou `#separator:Tab`).
3. **Allow HTML in fields:** nech **vypnuté** (`#html:false`) — text je čistý, bez HTML značek.
4. Namapuj sloupce: **1 → Front**, **2 → Back**, **3 → Tags**.
5. Import přistane v balíčku **Arteterapie** (kvůli `#deck:Arteterapie`).
   Tagy `pripad1 arteterapie definice` umožní filtrovat podle případu i arteterapeutického směru.

> Pozn.: dřív byl častý problém „karty bez zadní strany“ = špatně zvolený oddělovač.
> Tady je export **tabulátorový** (TSV) a direktiva to říká Anki rovnou — drž se kroku 2.

## Import do Quizletu

Quizlet pracuje se 2 poli (termín + definice), sloupec Tags ignoruj:

1. Quizlet → **Create → Import**.
2. Mezi termínem a definicí zvol **Tab**, mezi kartami **New line**.
3. Vlož obsah CSV (Quizlet vezme první dva sloupce jako termín/definici).
   Direktivní řádky `#…` na začátku případně smaž (Quizlet je nepotřebuje).

## Poznámka ke zdrojům

Každá karta má v poli `zdroj` (a v CSV na konci odpovědi) uvedeno, odkud informace pochází.
V arteterapeutické větvi jsou primární zdroje **Šicková-Fabrici / Slavík / Liebmann**;
protože knihy zatím nejsou po ruce, jsou tato tvrzení značená `⚠️ ověřit`. **Vágnerová** se
uvádí jen jako **klinické pozadí** klienta (s číslem strany). Plný seznam: `../zdroje/bibliografie.md`.
