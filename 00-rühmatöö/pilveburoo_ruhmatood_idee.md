# Pilvebüroo digitaalse äri arendamine AI-agentide abil

## Rühmatöö idee

Rühmatöö objektiks võiks võtta **Pilvebüroo digitaalse äri – e-poe ja Profiklubi** – ning vaadata, kuidas seda saaks tehnoloogia ja AI-agentide abil paremini skaleerida.

Põhiküsimus võiks olla:

> **Kuidas saaks Pilvebüroo müüa olemasolevat teadmist suuremas mahus ilma, et inimese tehtava töö hulk samas tempos kasvaks?**

Pilvebüroo puhul on hea see, et tegemist on reaalse ja suhteliselt lihtsa ärimudeliga. Ettevõte müüb e-poes digitaalseid tooteid, näiteks webinare ja e-raamatuid, ning lisaks on Profiklubi, kus kliendid saavad regulaarselt erialast sisu. Samas on päris suur osa sisu loomisest, turundusest, müügijärgsest tegevusest ja kliendisuhtlusest endiselt käsitöö.

---

## Faas 1

### Ettevõtte visioon

Olla Eesti ettevõtjate ja finantsspetsialistide jaoks väga praktiline digitaalne teadmisteplatvorm, kus klient saab talle vajaliku teadmise kiiresti ja võimalikult personaalselt.

### Missioon

Muuta keerulised ettevõtlus-, finants- ja regulatsiooniteemad praktilisteks teadmisteks ning kasutada tehnoloogiat selleks, et õige sisu jõuaks õigel ajal õige inimeseni.

### SWOT

#### Tugevused
- tugev erialane kompetents;
- olemasolev sisubaas;
- olemasolevad kliendid;
- digitaalsed ja skaleeruvad tooted;
- Profiklubi korduvtulu mudel.

#### Nõrkused
- sõltuvus võtmeisikutest;
- suur käsitöö maht;
- sisu taaskasutamine ei ole süsteemne;
- kliendiinfo võib olla hajutatud;
- vähene personaliseerimine.

#### Võimalused
- AI-agentide kasutamine;
- turunduse personaliseerimine;
- olemasoleva sisu parem taaskasutamine;
- uued digitaalsed teenused;
- suurem müük sama meeskonnaga.

#### Ohud
- tasuta AI-sisu kiire kasv;
- tehnoloogiline sõltuvus;
- AI vigade risk;
- andmekaitse ja infoturbe riskid.

### Peamised goalid järgmiseks aastaks

1. **Kasvatada digitaalse äri müügitulu ilma tööjõukulu samas tempos kasvatamata.**
2. **Vähendada korduvatele turundus-, sisu- ja klienditeenindustegevustele kuluvat inimtööd.**
3. **Muuta kliendikogemus personaalsemaks ja suurendada olemasolevate klientide väärtust.**

---

## Faas 2

Edasi võiks valida kaks peamist goali: **müügi kasvatamine** ja **käsitöö vähendamine**.

### Võimalikud objective'id

- olemasoleva sisu parem kasutamine erinevates müügikanalites;
- personaalsemad pakkumised;
- kordusostude ja Profiklubi liikmelisuse kasvatamine;
- sisu ümbertöötamise automatiseerimine;
- turundustegevuste automatiseerimine;
- lihtsama kliendisuhtluse ja järeltegevuste automatiseerimine.

### Kolm value stream'i

#### 1. Teadmisest müüdavaks tooteks

**AS-IS:**  
Teema → uuring → materjali koostamine → webinar / e-raamat → e-poodi lisamine → turundussisu → müük

Siin saab analüüsida, millistes etappides saaks AI-agent vähendada käsitööd, näiteks eeluuringus, sisu ümbertöötamises või turundusmaterjalide ettevalmistamises.

#### 2. Potentsiaalsest kliendist ostjaks

**AS-IS:**  
Klient näeb sisu → liitub meililistiga → saab turundust → külastab e-poodi → ostab

Tulevikus võiks süsteem paremini aru saada, millised teemad klienti huvitavad, ning pakkuda talle sellest lähtuvalt sobivamat sisu ja toodet.

Näiteks kui inimene loeb korduvalt palgateemalist sisu, võiks talle pakkuda palgawebinari või Profiklubi vastavat sisu.

#### 3. Kliendist püsikliendiks

**AS-IS:**  
Klient liitub Profiklubiga → tarbib sisu → saab regulaarset kommunikatsiooni → pikendab liikmelisust või lõpetab

Tulevikus võiks süsteem jälgida kliendi huvisid ja aktiivsust, soovitada talle asjakohast sisu ning märgata, kui klient muutub passiivseks.

---

## AS-IS Capability Map

### Product & Content Management
- teemade valik;
- ekspertsisu loomine;
- webinaride loomine;
- digitoodete haldus.

### Marketing & Sales
- sihtrühmade haldus;
- e-mailiturundus;
- kampaaniad;
- e-poe müük;
- cross-sell ja upsell.

### Customer Management
- klienditeenindus;
- liikmete haldus;
- tagasiside;
- kliendisuhete hoidmine.

### Technology & Data
- e-pood;
- meiliturunduse süsteem;
- kliendiandmed;
- analüütika;
- automatiseerimine.

### Business Management
- strateegia;
- finantsjuhtimine;
- tootearendus;
- tulemuste mõõtmine.

---

## Faas 3

TO-BE mudelis saaks näidata, milliseid uusi võimekusi on ettevõttel vaja selleks, et protsessid oleksid rohkem automatiseeritud ja personaalsed.

### AI & Automation Management
- AI-agentide haldus;
- workflow'de automatiseerimine;
- kvaliteedikontroll;
- inimese kinnitust vajavate sammude haldus.

### Customer Intelligence
- kliendi huvide tuvastamine;
- segmentatsioon;
- personaalsed soovitused;
- passiivseks muutuvate klientide tuvastamine.

### Content Intelligence
- eeluuring;
- olemasoleva sisu ümbertöötamine;
- sisu klassifitseerimine;
- kliendile sobiva sisu soovitamine.

---

## Agentide lühiskeem

Üks võimalik lihtne lahendus:

```text
                  ┌────────────────────┐
                  │  Inimene / ekspert │
                  │ kontroll ja otsused│
                  └─────────┬──────────┘
                            │
                            ▼
                  ┌────────────────────┐
                  │ Koordineeriv agent │
                  └──────┬─────┬───────┘
                         │     │
              ┌──────────┘     └──────────┐
              ▼                           ▼
    ┌──────────────────┐        ┌──────────────────┐
    │   Sisuagent      │        │  Müügiagent      │
    │ - eeluuring      │        │ - segmentatsioon │
    │ - kokkuvõtted    │        │ - pakkumised     │
    │ - uued formaadid │        │ - järeltegevused │
    └────────┬─────────┘        └────────┬─────────┘
             │                           │
             └────────────┬──────────────┘
                          ▼
                ┌──────────────────┐
                │ Kliendiagent     │
                │ - soovitused     │
                │ - KKK vastused   │
                │ - aktiivsuse     │
                │   jälgimine      │
                └──────────────────┘
```

Loogika on lihtne: **AI-agent teeb ettevalmistava ja korduva töö, inimene kinnitab olulised otsused ja vastutab lõpptulemuse eest.**

---

## Võimalik TO-BE heatmap

| Capability | AS-IS | TO-BE vajadus |
|---|---|---|
| Ekspertsisu loomine | tugev | tugev |
| E-mailiturundus | tugev | tugev |
| Kliendisegmentatsioon | keskmine | tugev |
| Personaliseerimine | nõrk | tugev |
| AI-agentide haldus | puudub | tugev |
| Sisu automaatne ümbertöötamine | puudub | tugev |
| Personaalsed sisusoovitused | puudub | tugev |

---

## Töö keskne loogika

Rühmatöö keskne küsimus võiks olla:

> **Kuidas saaks Pilvebüroo müüa olemasolevat teadmist suuremas mahus ilma, et inimese tehtava töö hulk samas tempos kasvaks?**

Sellest liigume edasi küsimuseni:

> **Milliseid ärivõimekusi on selleks vaja?**

Ja seejärel:

> **Milliseid neist võimekustest saab tehnoloogia ja AI-agentide abil toetada või automatiseerida?**

Nii on võimalik siduda üheks tervikuks ärieesmärgid, capability map, value stream'id ja tehnoloogilised lahendused.
