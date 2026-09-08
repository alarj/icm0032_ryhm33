# Git kasutamine selles repos

Lühike juhend, kuidas me seda repot rühmatöö käigus kasutame.

## Dokumendi päritolu
See juhend on loodud valdavalt Claude.ai poolt.

## Põhimõte

`main` haru sisaldab alati **kinnitatud, valminud tulemust**. Töö-käigu ja arutelu jaoks kasutame eraldi harusid (branch).

## Harude (branch) struktuur

Branch luuakse teema/faasi kaupa, mitte inimese kaupa:

```
main
faas1/swot
faas1/tows
faas2/capability-map
faas2/value-streams
faas3/capability-map-tobe
faas3/value-streams-tobe
```

- **Sisulised otsused** (SWOT sisu, capability map, value stream valikud) → alati oma branch + Pull Request
- **Väikesed asjad** (kirjaviga, formaat) → võib teha otse `main`'i

## Töövoog

1. Ava uus branch teema kohta (nt `faas1/swot`)
2. Tee sinna tööd: lisa AI väljundid, arutelu, otsuste põhjendused
3. Kui rühm on tulemuses kokku leppinud → tee **Pull Request** `main` vastu
4. Kirjuta PR kirjeldusse lühike kokkuvõte: mis otsustati ja miks
5. Rühmaliikmed vaatavad üle ja kinnitavad (approve)
6. Merge `main`'i

PR kommentaaridesse võib kirjutada ka kriitika/vastuväited (devil's advocate arutelu) — need jäävad GitHub'i ajalukku alles.

## Branch'e ei kustutata

Pärast merge'i jäta branch alles. Nii saab igal hetkel minna tagasi ja vaadata, kuidas mingi tulemuseni jõuti.

## Tag'id faaside lõpuks

Kui faas on valmis ja kinnitatud, pane `main`'ile tag, nt:
```
faas1-valmis
faas2-valmis
faas3-valmis
```
See annab kiire checkpoint'i, kuhu saab alati naasta.

## Failide/kaustade struktuur

```
/README.md
/00-rühmatöö/
    Rühmatöö ülesanne.md
    Tehisaru rühmatöös.md
/faas1/
    ai-sisendid/       <- AI mudelite toorväljundid (igaüks eraldi failina)
    otsused/           <- otsuste logi (vt allpool)
    faas1-lopptulemus.md
/faas2/
    ...
/faas3/
    ...
```

## Otsuste logi

Iga koha peal, kus AI midagi pakkus ja rühm midagi otsustas, tehakse väike fail kausta `otsused/`:

```md
## Kontekst
Millist küsimust lahendasime

## AI sisend
Link ai-sisendid/ failile + 1 lause kokkuvõte

## Rühma otsus
Nõustuti / lükati tagasi / muudeti kuidas

## Põhjendus
Miks (2-3 lauset)

## Autor(id), kuupäev
```

See tagab, et hiljem on näha ja arusaadav, kuidas ja miks rühm konkreetse tulemuseni jõudis, ja kas AI andis reaalset väärtust.

## Praktilised käsud (kui kasutad käsurida)

```bash
# uus branch
git checkout -b faas1/swot

# muudatuste lisamine
git add .
git commit -m "Lisan GPT SWOT esialgse versiooni"
git push origin faas1/swot

# faili liigutamine
git mv vana-koht/fail.md uus-koht/fail.md
```

GitHub veebiliideses saab kõike sama teha ka "Add file" / faili redigeerimisakna kaudu — käsurida pole kohustuslik.
