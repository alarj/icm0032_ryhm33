# Projekti tööreeglid

## Dokumendi päritolu

See dokument on loodud Alari poolt, täiendatud OpenAI poolt 9.09.2026

## 1. Charset ja failivorming

- Kõik failid peavad olema UTF-8 kodeeringus.
- Uute failide loomisel ja olemasolevate failide muutmisel tuleb säilitada UTF-8.
- Kui failis esineb kodeeringuprobleem, tuleb see käsitleda veana ja parandada juurpõhjus, mitte peita sümptomit.
- Dokumendi formaat, kui ei ole öeldud teisiti, on Markdown (.md)
- Dokumendil peab olema sisukord kohe dokumendi päritolu peatüki järel, kui dokumendis on vähemalt viis sisulist Markdowni pealkirja tasemetel `##`–`######` või dokument on mahukas — tavavaates ligikaudu üle kahe A4 lehekülje — ja selles on vähemalt kaks sisulist alapeatükki.
	- „Dokumendi päritolu” pealkiri sisukorra vajaduse hindamisel arvesse ei lähe.
	- Sisukorda ei ole vaja dokumendile, milles on ainult üks sisuline alapeatükk, ka siis, kui see alapeatükk on pikk.
- Faili alguses peab olema dokumendi päritolu kohta eraldi nummerdamata peatükk, näiteks: `## Dokumendi päritolu` ja selle all „See dokument on loodud OpenAI poolt.”
- Faili sisu muutes tuleb kontrollida, et punktide võimalik numeratsioon ja viited paika jäävad ning vajadusel ka need parandada, sealhulgas sisukord.
- Tekstisisesed allikaviited peavad viitama sama dokumendi `Allikad` jaotise punktidele, näiteks `[1](#allikas-1)`, mitte otse veebilehtedele. Veebiaadressid peavad olema esitatud ainult `Allikad` jaotises ning iga viide peab viima vastava allikapunkti juurde.
- Dokumentide lisamine, commit'imine ja push'imine on lubatud ainult tööharudes; `main` harusse ei tohi otse muudatusi teha.
- Enne käske `git add`, `git commit` ja `git push` kontrolli alati aktiivset haru käsuga `git branch --show-current`.
	- `main` harusse tohib muudatusi otse commit'ida või push'ida ainult siis, kui seda on promptis sõnaselgelt nõutud.
- Tööharu muudatusi võib `main` harusse ühendada ainult Pull Requesti kaudu. Pull Request tuleb enne merge'imist meeskonnal üle vaadata ja kinnitada vastavalt dokumendis `Git kasutamine.md` kirjeldatud töövoole.
- Igal commit'il peab olema sisuline commit-sõnum. Commit-sõnum tuleb enne commit'i tegemist kasutajaga kooskõlastada.

## 2. Enne muudatusi loe läbi allikad

- Enne sisuliste muudatuste kavandamist loe läbi kõik dokumendid, mis puudutavad muudetavat ala.
- Kui dokumentide vahel on vastuolu, ära eelda vaikimisi, et üks dokument on õigem kui teine.
- Tuvasta ja kirjelda vastuolu konkreetselt: millised dokumendid või väited on omavahel vastuolus ja milles vastuolu seisneb.
- Küsi vastuolu kohta kinnitust ning tegutse edasi alles pärast selle saamist.
- Kui töö käigus tekib kahtlus, ära oleta vaid peatu ning küsi üle.

## 3. Tööpõhimõtted
- ...
