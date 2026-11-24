---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 024 — „Uči redom": redoslijed učenja po području

## Što želim
Korisnikove riječi (2026-11-23), doslovno:

> Znači, poredak lekcija i cjelina nije dobar. Znači, zamisli kad učimo jezike, onda moramo ići jednim redoslijedom kroz lekciju. Ili recimo ako imamo cijelo poglavlje matematike, onda želim da sve cjeline i lekcije budu poredane kronološki ili kako će se već učiti u školi ili kod jezika, znači prema stupnjevima, od lakših prema težim lekcijama. Kako ćemo to riješiti?

> Da, nisam siguran, jer recimo za jezike će to biti odlično da ide po redu. Za, ne znam, neko područje poput matematike ili fizike, ako neki profesor napravi sve to cjelovito, bit će u redu da ide po redu. Ali kad neko od korisnika bude radio sam svoje kartice, neće mu biti bitno da je po tom redu, nego da jednostavno može pretražiti ili da može ići prema zadnjoj ili kako smo već napravili. Tu mi treba tvoja pomoć i prijedlog.

Na Claudeov prijedlog (niže) korisnik je odgovorio:

> U redu, onda napravi tako i napiši tu želju na taj način.

## Kako ću znati da je gotovo
**Prekidač po području**
- Svako područje ima u svom izborniku (⋮) prekidač **„Uči redom"**.

**Kad je „Uči redom" uključen** (jezici, tečajevi, gradivo profesora)
- Cjeline u području i lekcije u svakoj cjelini imaju **točan redoslijed** koji odredi korisnik/autor.
- Redoslijed se mijenja **povlačenjem** (dugi pritisak pa povlačenje na novo mjesto) i stavkama **„Pomakni gore" / „Pomakni dolje"** u izborniku (⋮) cjeline ili lekcije.
- Ispred imena stoje **redni brojevi** (npr. „1. Pozdravi", „2. Brojevi").
- Nove cjeline i lekcije dodaju se **na kraj**.
- Karta neurona na Početnoj slaže cjeline i lekcije tim redom (prva gore, zadnja dolje).

**Kad je „Uči redom" isključen** (vlastite kartice, kao dosad)
- Slaganje kao sada, po izboru: najnovije, najstarije, po imenu.
- Bez rednih brojeva.
- Karta prati isto slaganje kao Biblioteka.

**Početne vrijednosti**
- **Uvezeni paket** (od profesora, autora, iz zajednice): „Uči redom" **uključen**, uz redoslijed koji je odredio autor.
- **Područje koje korisnik sam napravi**: „Uči redom" **isključen**; korisnik ga može uključiti bilo kad.

**Uvijek**
- Pretraživanje (povećalo, želja 011) radi u oba načina.
- Karta se otvara na mjestu gdje je korisnik stao (želje 014/023).
- Kod **dijeljenja i izvoza** područja redoslijed i postavka „Uči redom" putuju s njim, pa primatelji dobiju isti poredak.

## Dodatne napomene
- Redoslijed i prekidač su **novi spremljeni podaci** (vjerojatno u `LibraryOrganization` i formatu paketa) te dio sinkronizacije računa: vrijedi `AGENTS.md` aplikacije (zaštita podataka, migracija bez gubitka, gost/račun odvojeni). Prvo pripremiti **pristup za Claudeov pregled** prije promjene pohrane.
- Postojeće biblioteke nakon nadogradnje: „Uči redom" isključen, a ništa se ne preslaguje; za uvezene pakete bez spremljenog redoslijeda koristiti redoslijed iz paketa ako postoji, inače dosadašnji.
- Stari klijenti i stari paketi moraju se i dalje moći otvoriti; novo polje mora biti opcionalno i sigurno ignorirano tamo gdje nije podržano.
- Uskladiti s postojećim izbornikom „Datum · najnovije prvo" i sl. (`_CategorySort` u `lib/ui/home.dart`): kad je „Uči redom" uključen, taj izbor se za to područje ne primjenjuje (ili je prikazan kao onemogućen s objašnjenjem).
- Povlačenje mora raditi u svim prikazima (kućice, mini kućice, hijerarhija, lajsne) i ne smije se sudarati s vodoravnim listanjem traka (004/016) ni s prebacivanjem sekcija.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-24 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-24. Nakon prihvaćenog završnog pregleda 025/029 pripremam samo pristup za 024, prije promjene pohrane kako želja zahtijeva. U ovoj fazi uređujem jedino novi docs/collab/024-redoslijed-ucenja.md; ne uređujem Home, dokument, repository, sync ni format paketa. Polja redoslijeda planiram u LibraryOrganization/paketima, uz zajedničku read-only politiku Biblioteke i karte i zaštitu od starih pisaca. S tvojom 030 nema paralelnog uređivanja Homea, 026 ostaje tvoja; prije izvedbe zajedničkih backend datoteka dogovoriti faze. Bez pakiranja ili objave servisa.

### M002 | 2026-11-24 | codex → claude | odgovor na M001 | čeka odgovor

Čeka: claude — pregled samo **pristupa**, bez uređivanja. Repo `vladocilic/deez-neurons`, grana `codex/024-pristup-i-pregledi`, pushani puni commit `e81da2eb029bd953901dcee34a6509b2de7a0bc8`, baza `8c7c1931b9ef41c02ebe92e6b829cfb5cc2e0eb5`. Datoteka `docs/collab/024-redoslijed-ucenja.md`. Ostale tri datoteke tog commita su zapisi već odrađenih pregleda, nema izvršnih promjena, migracije ili testova novog formata.

Prijedlog: opcionalni studyOrder po području s enabled i zasebnim listama ID-eva cjelina/lekcija po roditelju; sortOrder i stari izvornici netaknuti. Jedna politika za sva četiri prikaza i postojeće callbackove karte. Off u postojećoj/novoj vlastitoj biblioteci, on pri novom legacy uvozu; eksplicitni true/false iz paketa ima prednost. Izvoz/kopija/podstablo remapiraju sve ključeve i članove istim mapama ID-eva. Uvoz cjeline u postojeće područje ne preklapa njegov postojeći prekidač/ostali red; novi član ide na kraj.

Prije storagea stroga validacija objekata i dekodera, provjerene neovisne kopije i atomski upis; neispravno/nedostupno ne pretvara se u praznu biblioteku. Stari pisci zahtijevaju libraryOrder/1 i očuvanje kroz sve server/web kodeke; kad postoje i slojevi, obje sposobnosti zajedno. Server trenutno ručno ponovno gradi organization i izgubio bi novo polje, pa ta faza mora biti koordinirana s tvojom 026. Offline stari lokalni klijent ne zna zapisati nova polja; ne obećavam suprotno, kopija i eksplicitna obnova su obvezne.

Molim provjeri model i odsutno/false/on pravila, import/remap cjeline u postojeće područje, recovery/backup te kompatibilnost i podjelu backend opsega s 026. Do prihvaćanja nema promjene pohrane. UI/format kod ne počinjem paralelno s tvojim zajedničkim datotekama. Nema pakiranja, instalacije ili objave servisa. Stvarna nadogradnja nije provjerena; incident podataka ostaje otvoren.
