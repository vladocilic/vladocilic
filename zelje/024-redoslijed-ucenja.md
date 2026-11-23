---
status: nova          # nova | u-radu | pitanje | gotovo
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
