# Juhend ja reeglid ArchiMate XML-failide töötlemiseks

## Dokumendi päritolu

See dokument on loodud inimese, Gemini ja OpenAI koostöös ning seda on täiendatud projekti käigus tekkinud vajaduste põhjal.

## Sisukord

1. [Eesmärk](#eesmärk)
2. [Kohustuslik tutvumine Archie juhendiga](#kohustuslik-tutvumine-archie-juhendiga)
3. [Töövoog](#töövoog)
4. [Faili päis ja XML-nimeruumid](#faili-päis-ja-xml-nimeruumid)
5. [Kataloogide struktuur](#kataloogide-struktuur)
6. [ID-d](#id-d)
7. [Mudeli elemendid](#mudeli-elemendid)
8. [Seosed](#seosed)
9. [Vaated ja diagrammid](#vaated-ja-diagrammid)
10. [Diagramm on mudeli põhiline kasutajaliides](#diagramm-on-mudeli-põhiline-kasutajaliides)
11. [Sisulise kvaliteedi kohustus](#sisulise-kvaliteedi-kohustus)
12. [Diagrammiühendused](#diagrammiühendused)
13. [Grupid](#grupid)
14. [Muudatuste tegemise protseduur](#muudatuste-tegemise-protseduur)
15. [Minimaalne struktuurinäide](#minimaalne-struktuurinäide)
16. [Olemasoleva mudeli järgimine ja ebakindluse käsitlemine](#olemasoleva-mudeli-järgimine-ja-ebakindluse-käsitlemine)

## Eesmärk

Seda juhendit kasutatakse koos failiga `vaartusvoog.archimate`, et AI saaks lugeda, kontrollida ja täiendada Archi töölauarakenduse loodud ArchiMate mudelit.

AI peab suutma:

- säilitada olemasoleva Archi XML-struktuuri;
- lisada, muuta ja vajadusel eemaldada mudeli elemente, seoseid ning vaateid;
- lisada uued objektid olemasolevate vaadete sisse;
- hoida kõik ID-viited terviklikuna;
- luua faili, mida saab Archis avada, redigeerida ja salvestada;
- luua diagramme, millel olev info on sisuliselt loogiline, inimesele loetav ja ülesande eesmärgi jaoks kasulik.

Näidisfail on selle juhendi tehniline alus. Kui juhendi üldine kirjeldus ja näidisfail erinevad, tuleb järgida näidisfaili tegelikku struktuuri.

## Kohustuslik tutvumine Archie juhendiga

Projekti ainus kohustuslik väline sisuline juhend on kasutaja antud juhend:

[Enterprise Design Cookbook](https://hosiaisluoma.fi/Enterprise-Design-Cookbook.pdf)

AI peab kasutama ainult seda juhendit arhitektuurimudelite, väärtusvoogude, võimekuste, seoste ja diagrammide sisulise koostamise alusena. Teisi väliseid metoodilisi või modelleerimisjuhendeid ei tohi vaikimisi kasutada ega sellele projektile alusena lisada.

Käesolev dokument kirjeldab selle projekti XML-i eripärasid ja täiendab Enterprise Design Cookbooki ainult tehnilise failitöötluse reeglitega.

Enne töö alustamist tuleb üle vaadata vähemalt ülesandega seotud väärtusvoo, võimekuste kaardi, seoste ja diagrammide modelleerimise juhised. Kui XML-struktuuri lahendus ja Archie tegelik käitumine lähevad lahku, tuleb eelistada lahendust, mille tulemust saab Archis avada ja mille tähendus on diagrammil inimesele arusaadav.

## Töövoog

Töö toimub inimese ja AI koostöös Git-repositooriumi kaudu:

0. Inimene loob esmase versiooni archimate failist. Uue sisulise ja **inimesele loetava** väärtusvoo diagrammi loomisel ei ole AI  piisavalt usaldusväärne. Keeruline on korraga tagada Archi XML-i korrektne struktuur, Archi tegelik visuaalne renderdus ja **sisuliselt mõtestatud diagramm**. Seega on mõistlik, et **inimene loob esimese visuaalse mudeli Archis ning AI aitab seda seejärel analüüsida, täiendada ja kontrollida**.
1. AI loeb olemasoleva `.archimate` faili ja analüüsib selle struktuuri.
2. AI teeb ülesandes nõutud muudatused.
3. AI kontrollib ID-de, seoste ja diagrammiviidete terviklikkust.
4. AI salvestab muudatuse Git-repositooriumisse.
5. Inimene tõmbab muudatused arvutisse, avab faili Archis ja kontrollib diagrammide visuaalset tulemust.
6. Inimene võib Archis objekte liigutada, ümber nimetada või lisada.
7. Pärast inimese muudatusi loeb AI faili uuesti sisse ega eelda, et varasemad ID-d või koordinaadid on muutumatud.

AI ei tohi üle kirjutada inimese tehtud muudatusi, kui ülesanne ei nõua seda otseselt.

## Faili päis ja XML-nimeruumid

Näidisfail kasutab järgmist juurelementi:

```xml
<archimate:model
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:archimate="http://www.archimatetool.com/archimate"
  name="HTM Moodle"
  id="id-d59a2f0e2732485897bb3f92c1c3fcfc"
  version="5.0.0">
```

Reeglid:

- Ära muuda `xmlns:xsi` ega `xmlns:archimate` väärtusi.
- Ära lisa juurelemendile teistsugust vaikimisi nimeruumi.
- Kasuta näidisfailiga kooskõlas versiooni `5.0.0`, välja arvatud juhul, kui olemasolev fail kasutab juba mõnda muud versiooni.
- Säilita juurelemendi `name` ja `id`, kui ülesanne ei nõua mudeli ümbernimetamist.
- Ära lisa skeemi või atribuute, mida olemasolev Archi fail ei kasuta.

Näidisfailis ei kasutata `xsi:schemaLocation` atribuuti. Seda ei tohi automaatselt lisada.

## Kataloogide struktuur

Mudel kasutab katalooge kujul:

```xml
<folder name="Strategy" id="..." type="strategy">
  ...
</folder>
```

Näidisfaili peamised kataloogid on:

- `Strategy`, `type="strategy"`;
- `Business`, `type="business"`;
- `Application`, `type="application"`;
- `Technology & Physical`, `type="technology"`;
- `Motivation`, `type="motivation"`;
- `Implementation & Migration`, `type="implementation_migration"`;
- `Other`, `type="other"`;
- `Relations`, `type="relations"`;
- `Views`, `type="diagrams"`.

Kõik elemendid, seosed ja vaated paigutatakse olemasolevasse sobiva `type` väärtusega kataloogi. Uut kataloogi ei looda, kui olemasolev kataloog sobib.

Elementide paigutus peab järgima olemasoleva mudeli loogikat. Näiteks ei tohi ressursse automaatselt Business-kataloogi tõsta ainult sellepärast, et need on ärimudeli osa. Näidisfailis asuvad mitmed ressursid Strategy-kataloogis ja seda struktuuri tuleb säilitada.

## ID-d

Näidisfail kasutab ID-kuju:

```text
id- + 32 väikest kuueteistkümnendmärki
```

Näiteks:

```xml
id="id-c60e5dddb9334a3dba93d440f7502f28"
```

Reeglid:

- Iga uus objekt peab saama uue kogu faili ulatuses unikaalse ID.
- ID-d tuleb genereerida sama kujuga nagu näidisfailis.
- Olemasolevaid ID-sid ei tohi uue objekti jaoks taaskasutada.
- ID-d ei tohi muuta ainult nime või asukoha muutmise tõttu.
- ID muutmisel tuleb uuendada kõik sellele ID-le viitavad `source`, `target`, `archimateElement`, `archimateRelationship`, `targetConnections` ja muud viited.
- Enne faili lõpetamist tuleb kontrollida, et kõik `id` väärtused on unikaalsed.

Näidisfaili ID-d on Archi identifikaatorid; neid ei tohi asendada tavalise UUID v4 formaadiga, kui selleks ei ole eraldi põhjust.

## Mudeli elemendid

Tavalised mudelielemendid asuvad vastava kihi kataloogis ja on kujul:

```xml
<element xsi:type="archimate:ValueStream"
         name="Õppimine ajast ja kohast sõltumatult"
         id="id-..."/>
```

Elemendi tüübi määrab alati `xsi:type`. AI peab kasutama ArchiMate’i tüüpi, mis sobib elemendi tähendusega, näiteks:

- `archimate:ValueStream` väärtusvoo jaoks;
- `archimate:Capability` võimekuse jaoks;
- `archimate:Resource` ressursi jaoks;
- `archimate:CourseOfAction` tegevussuuna jaoks;
- `archimate:Requirement`, `archimate:Outcome` ja `archimate:Value` motivatsioonielementide jaoks.

Kõik `xsi:type` väärtused peavad kasutama `archimate:` prefiksit. Näiteks on õige `xsi:type="archimate:AssignmentRelationship"`; paljas `xsi:type="AssignmentRelationship"` ei ole selle faili vormingus lubatud ja Archi võib faili avamisel märkida mudeli ühildumatuks.

Olemasoleva elemendi nime muutmisel muuda ainult `name` atribuuti, välja arvatud juhul, kui ülesanne nõuab ka tüübi või kataloogi muutmist.

## Seosed

Näidisfailis asuvad kõik seosed `Relations`-kataloogis ja on samuti `<element>` elemendid:

```xml
<folder name="Relations" id="..." type="relations">
  <element
    xsi:type="archimate:CompositionRelationship"
    id="id-..."
    source="id-..."
    target="id-..."/>
</folder>
```

Ära kasuta selle mudeli puhul eraldi `<relationship>` XML-elementi.

Seose loomisel:

- loo uus `<element>` seose tüübiga `archimate:...Relationship`;
- paiguta see `Relations`-kataloogi;
- anna talle uus ID;
- määra `source` ja `target` olemasolevate ID-de abil;
- kontrolli, et mõlemad viidatud ID-d eksisteerivad failis;
- kasuta ArchiMate’i semantikaga sobivat seosetüüpi.

Näidisfailis kasutatakse muu hulgas järgmisi tüüpe:

- `CompositionRelationship`;
- `FlowRelationship`;
- `AssociationRelationship`;
- `RealizationRelationship`;
- `AssignmentRelationship`;
- `ServingRelationship`.

`source` ja `target` peavad viitama failis olemasolevale objektile. Näidisfailis on mõnes Association-seoses sihtmärgiks ka seose ID. Seda mustrit ei tohi automaatselt ümber parandada; säilita olemasolev struktuur ja kasuta sama lahendust ainult siis, kui see on mudeli tähenduse jaoks põhjendatud.

Seose kustutamisel tuleb eemaldada ka kõik sellele seosele viitavad diagrammiühendused.

## Vaated ja diagrammid

Vaated asuvad `Views`-kataloogis:

```xml
<folder name="Views" id="..." type="diagrams">
  <element
    xsi:type="archimate:ArchimateDiagramModel"
    name="Value stream"
    id="id-...">
    ...
  </element>
</folder>
```

Näidisfailis on kaks vaadet: `Value stream` ja `Capability Map`.

Vaate sees olev graafiline objekt on kujul:

```xml
<child
  xsi:type="archimate:DiagramObject"
  id="id-..."
  archimateElement="id-...">
  <bounds x="168" y="156" width="1105" height="157"/>
</child>
```

Reeglid:

- Kasuta `archimate:DiagramObject` tüüpi, kui näidisfaili struktuur seda nõuab.
- Kasuta atribuuti `archimateElement`, mitte atribuuti `element`.
- `archimateElement` peab viitama olemasoleva mudelielemendi ID-le.
- Diagrammiobjekti ID on eraldi ID ega tohi kattuda mudelielemendi ID-ga.
- Uue diagrammiobjekti lisamisel lisa ka tema `<bounds>` element.
- Olemasoleva objekti liigutamisel muuda ainult `bounds` koordinaate, kui muudatuse eesmärk on visuaalne paigutus.
- Ära loo sama mudelielemendi jaoks uut diagrammiobjekti, kui sobiv objekt on vaates juba olemas.

## Diagramm on mudeli põhiline kasutajaliides

Mudeli XML on tehniline salvestusvorm. Inimene kasutab mudelit eelkõige Archi diagrammide kaudu. Seetõttu ei piisa sellest, et elemendid ja seosed on XML-is olemas: oluline info peab olema ka sobivas vaates nähtav.

Reeglid:

- Iga sisuline seos, mida kasutaja peab mudelist mõistma, peab olema nähtav vähemalt ühes asjakohases vaates.
- Mudelis olevat olulist seost ei tohi jätta ainult `Relations`-kataloogi ilma diagrammiühenduseta.
- Iga diagrammil kuvatav ühendus peab omakorda viitama tegelikule mudeliseosele; jooni ei tohi luua ainult visuaalse kaunistusena.
- Põhivaates peab olema võimalik saada mudeli eesmärgist aru ilma XML-i lugemata.
- Diagrammil ei tohi olla sisulisi isoleeritud kaste, välja arvatud juhul, kui nende isoleeritus on teadlikult põhjendatud.
- Kui kõiki seoseid ei ole võimalik ühes vaates loetavalt näidata, tuleb luua eraldi vaated, näiteks väärtusvoo põhivaade ja seda toetav võimekuste kaart.
- Vaade peab olema paigutatud loogilises lugemissuunas: tavaliselt vasakult paremale või ülevalt alla.
- Väärtusvoo etapid tuleb järjestada ning järjestikuste etappide vahel peavad olema nähtavad `FlowRelationship`-ühendused.
- Võimekuste kaardil peavad olema nähtavad vähemalt võimekuste omavahelised struktuursed seosed ja nende seosed väärtusvoo või teenustega.
- Väldi liigseid ristuvaid jooni, ebaloogilisi tagasisuunas ühendusi ja olukorda, kus kõik elemendid on kõigega ühendatud.

Enne faili üleandmist peab AI kontrollima iga loodud vaadet kasutaja seisukohast: mida inimene näeb, mis järjekorras ta seda loeb ja kas mudeli peamine sõnum on diagrammilt arusaadav. Ainult XML-i ID-de kontroll ei ole piisav.

## Sisulise kvaliteedi kohustus

Tehniliselt korrektne XML-fail ei ole piisav tulemus. Loodud mudel ja diagrammid peavad kandma inimesele arusaadavat arhitektuurset infot.

Enne töö lõpetamist peab AI kontrollima vähemalt järgmist:

- diagrammil on arusaadav eesmärk ja pealkiri;
- diagramm vastab ülesandele ega ole lihtsalt elementide paigutus;
- väärtusvoo puhul on arusaadav, kellele väärtust luuakse, milline on sisend, millised on etapid ja milline on väljund või tulemus;
- väärtusvoo etapid moodustavad loogilise järjestuse;
- capability map’i puhul on võimekused rühmitatud või hierarhiliselt mõtestatud ning nende roll on arusaadav;
- võimekused, ressursid, rakendused ja tehnoloogia on seotud nendega, mida nad toetavad;
- olulised seosed on diagrammil nähtavad, mitte ainult XML-i `Relations`-kataloogis;
- elementide nimed, tüübid ja seoste suunad moodustavad sisuliselt koherentse terviku;
- diagrammil ei ole ühendamata või põhjendamatult lisatud elemente;
- inimene saab diagrammi põhisõnumist aru XML-faili lugemata.

AI peab eristama kahte kvaliteeditaset:

1. tehniline korrektsus: fail avaneb Archis, XML on korrektne ning viited ja ID-d toimivad;
2. sisuline korrektsus: mudel kirjeldab loogilist arhitektuuri ja diagramm edastab selle inimesele arusaadavalt.

Mõlemad tasemed on kohustuslikud. Tehniliselt avanev, kuid sisuliselt arusaamatu või kasutamatu diagramm ei ole lõpetatud töö.

## Diagrammiühendused

Seos mudelis ja joon selle kuvamiseks diagrammil on eri asjad.

Mudeli seos asub `Relations`-kataloogis. Diagrammil kuvatav joon on vaate sees olev `archimate:Connection`:

```xml
<sourceConnection
  xsi:type="archimate:Connection"
  id="id-..."
  source="id-diagrammiobjekt"
  target="id-diagrammiobjekt"
  archimateRelationship="id-mudeli-seos"/>
```

Reeglid:

- `source` ja `target` viitavad diagrammiobjektide ID-dele, mitte otse mudelielementide ID-dele.
- `archimateRelationship` viitab `Relations`-kataloogis olevale seose ID-le.
- Ka ühendusel peab olema kogu faili ulatuses unikaalne ID.
- Kui lisad seose vaatesse, peab seose mõlema otsa diagrammiobjekt olema selles vaates olemas.
- Kui eemaldad diagrammiobjekti, eemalda või uuenda ka temaga seotud ühendused.
- Diagrammiobjekti `targetConnections` atribuut peab vastama ühendustele, mis selle objektiga seotud on. Pärast ühenduste muutmist kontrolli seda atribuuti.

Kui mudeliseos peab olema diagrammil nähtav, on vajalik mõlema taseme olemasolu:

1. seos `Relations`-kataloogis, näiteks `CompositionRelationship` või `FlowRelationship`;
2. selle seose jaoks `sourceConnection` diagrammiobjekti sees koos `archimateRelationship` viitega.

Lisaks peavad ühenduse sihtobjektil ja vajadusel lähteobjektil olema näidisfailiga kooskõlas olevad `targetConnections` viited. Seose olemasolu ainult esimesel tasemel ei muuda seda Archi vaates nähtavaks.

## Grupid

Näidisfailis kasutatakse võimekuskaardil gruppe:

```xml
<child xsi:type="archimate:Group" name="Strateegia" id="id-...">
  <bounds x="408" y="192" width="661" height="140"/>
  ...
</child>
```

Grupp on diagrammiobjektide visuaalne konteiner. Grupi lisamine või muutmine ei muuda automaatselt mudelielementide kataloogi ega ArchiMate’i tüüpi.

Kui element kuulub gruppi, paikneb tema diagrammiobjekt grupi sees oleva `child` elemendina. Säilita see pesastus, kui muudad ainult diagrammi paigutust.

## Muudatuste tegemise protseduur

Enne muudatuse tegemist:

1. Loe kogu XML sisse.
2. Koosta ID-de register kõigi `id` atribuutidega objektide kohta.
3. Leia üles ülesandes nimetatud elemendid nime, tüübi ja ID järgi.
4. Kontrolli, millistes vaadetes need elemendid esinevad.
5. Kontrolli seotud seoseid ja diagrammiühendusi.

Pärast muudatust:

1. Kontrolli XML-i korrektset sulgemist ja pesastust.
2. Kontrolli kõigi ID-de unikaalsust.
3. Kontrolli, et kõik `xsi:type` väärtused algavad prefiksiga `archimate:`.
4. Kontrolli kõiki `source` ja `target` viiteid.
5. Kontrolli kõiki `archimateElement` viiteid.
6. Kontrolli kõiki `archimateRelationship` viiteid.
7. Kontrolli diagrammiühenduste `source` ja `target` viiteid.
8. Kontrolli, et uued objektid paiknevad õiges kataloogis või vaates.
9. Säilita inimese olemasolevad nimed, paigutused ja seosed, kui ülesanne ei nõua nende muutmist.
10. Kontrolli, et iga oluline mudeliseos on vähemalt ühes vaates diagrammiühendusena nähtav.
11. Kontrolli, et iga vaate sisuline objekt on seotud teiste objektidega või on selle isoleeritus põhjendatud.
12. Ava fail Archis või korralda võimalusel Archis avamise test; XML-i parsitavus üksi ei tõenda diagrammi kasutatavust.
13. Vaata loodud vaateid inimese pilguga üle ja paranda paigutust, ühenduste suunda, loetavust ning liigseid ristumisi.

## Minimaalne struktuurinäide

Järgnev näide kasutab näidisfailiga sama struktuuri:

```xml
<archimate:model
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:archimate="http://www.archimatetool.com/archimate"
  name="Abstraktne mudel"
  id="id-00000000000000000000000000000001"
  version="5.0.0">

  <folder name="Strategy" id="id-00000000000000000000000000000002" type="strategy">
    <element
      xsi:type="archimate:ValueStream"
      name="Näidis väärtusvoog"
      id="id-00000000000000000000000000000003"/>
    <element
      xsi:type="archimate:Capability"
      name="Näidis võimekus"
      id="id-00000000000000000000000000000004"/>
  </folder>

  <folder name="Relations" id="id-00000000000000000000000000000005" type="relations">
    <element
      xsi:type="archimate:CompositionRelationship"
      id="id-00000000000000000000000000000006"
      source="id-00000000000000000000000000000003"
      target="id-00000000000000000000000000000004"/>
  </folder>

  <folder name="Views" id="id-00000000000000000000000000000007" type="diagrams">
    <element
      xsi:type="archimate:ArchimateDiagramModel"
      name="Peavaade"
      id="id-00000000000000000000000000000008">
      <child
        xsi:type="archimate:DiagramObject"
        id="id-00000000000000000000000000000009"
        archimateElement="id-00000000000000000000000000000003"
        type="1">
        <bounds x="20" y="20" width="120" height="55"/>
        <sourceConnection
          xsi:type="archimate:Connection"
          id="id-0000000000000000000000000000000a"
          source="id-00000000000000000000000000000009"
          target="id-0000000000000000000000000000000b"
          archimateRelationship="id-00000000000000000000000000000006"/>
      </child>
      <child
        xsi:type="archimate:DiagramObject"
        id="id-0000000000000000000000000000000b"
        targetConnections="id-0000000000000000000000000000000a"
        archimateElement="id-00000000000000000000000000000004">
        <bounds x="220" y="20" width="120" height="55"/>
      </child>
    </element>
  </folder>
</archimate:model>
```

See on ainult struktuurinäide. Tegelikus failis tuleb kasutada olemasolevaid katalooge, ID-sid, elementide tüüpe ja Archi poolt salvestatud atribuute.

## Olemasoleva mudeli järgimine ja ebakindluse käsitlemine

Ära rekonstrueeri ArchiMate XML-i ega mudeli sisu üldise oletuse põhjal. Loe kõigepealt olemasoleva faili tegelik struktuur, elemendid, seosed ja vaated läbi ning järgi näidisfaili vormi.

Olemasolev inimese loodud fail on sisuline alus, mitte ainult XML-i süntaksi näide. Seetõttu:

- ära asenda olemasolevaid sisulisi elemente üldisemate või enda välja mõeldud elementidega, kui ülesanne seda otseselt ei nõua;
- ära kustuta originaalis olnud võimekusi, ressursse, väärtusi, tulemusi ega seoseid ainult sellepärast, et koostad lihtsustatud vaate;
- ära muuda elementide nimesid, tüüpe, ID-sid, katalooge ega diagrammipaigutust ilma ülesandest tuleneva põhjuseta;
- uue soovituse lisamisel säilita olemasolev mudel ja lisa ainult vajalikud elemendid või seosed;
- kui uus vaade peab olema lihtsam, lihtsusta vaadet, mitte ära vähenda põhjendamatult mudeli sisulist rikkust;
- eraldi väärtusvoo väljajätmine ei tähenda, et selle väärtusvooga seotud võimekused ja ressursid tuleb mudelist eemaldada;
- enne muudatuse tegemist kirjelda endale, milline olemasolev info säilib ja milline uus info lisandub.

Kui tekib vähimgi sisuline või tehniline kahtlus, tuleb töö peatada ja küsida inimeselt järele. Kahtlus tähendab muu hulgas olukorda, kus AI ei tea kindlalt:

- kas olemasolev element tuleb säilitada või asendada;
- kas uus element kuulub olemasolevasse väärtusvoogu või eraldi vaatesse;
- milline on seose õige suund või ArchiMate’i tüüp;
- kas diagrammil nähtav seos kirjeldab inimese jaoks arusaadavat tähendust;
- kas ülesanne lubab olemasolevat infot lihtsustada, ümber nimetada või eemaldada.

Sellises olukorras ei tohi AI täita lünka oletuse, üldise ArchiMate’i näite ega enda väljamõeldud mudeliga.
