---
status: nova          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 011 — Biblioteka: ime i slika korisnika uz naslov; pretraživanje iza povećala

## Što želim
Korisnik je želju izrekao u dvije poruke (2026-11-22) i zatražio slanje nakon druge. Doslovno:

> **1.** Znači u biblioteci želim da pored naziva biblioteka samo desno od naziva stoji napisano ime korisnika, a ne da izgleda kao gumb na kojem piše račun pa ime korisnika. Sljedeća stvar, isto tako u biblioteci. Bilo da je riječ o području ili cjelini, želim da traka za pretraživanje se ne vidi, nego da bude gore u alatnoj traci samo malo povećalo, koje kad kliknemo, tek tada se spusti ili pojavi traka za pretraživanje i tek tada u nju možemo upisivati traženi pojam.

> **2.** neka uz ime korisnika koje će se nalaziti desno od riječi biblioteka stoji i mala ikona za sliku korisnika koju će on staviti po potrebi, a kao default koristi ikonu koju koristiš na moj diz neuron račun. Sada možeš spremiti ovu želju na GitHub.

Odgovori korisnika na otvorena pitanja (2026-11-22), doslovno:

> Kada korisnik nije prijavljen, neka stoji samo ikona sa defaultnom slikom, a pod 2 vrijedi, dakle, gdje god imamo alatnu traku i za pretraživanje, traku za pretraživanje, napravi da je traka za pretraživanje skrivena, a na alatnoj traci da stoji povećalo.

## Kako ću znati da je gotovo
**A. Ime i slika korisnika**
- Desno od naslova „Biblioteka" piše ime korisnika kao običan tekst, a ne kao oznaka/gumb „Račun: …".
- Uz ime je mala ikona sa slikom korisnika.
- Korisnik po želji može postaviti svoju sliku.
- Dok korisnik nije postavio sliku, prikazuje se ikona koju aplikacija koristi za „Moj Deez Neurons račun".
- Kad korisnik nije prijavljen, desno od naslova stoji samo ikona sa zadanom slikom, bez teksta.

**B. Pretraživanje**
- Gdje god postoje alatna traka i traka za pretraživanje (glavni ekran Biblioteke, područje, cjelina), traka za pretraživanje je skrivena.
- U alatnoj traci gore je malo povećalo.
- Klikom na povećalo traka za pretraživanje se spusti/pojavi i tek tada se u nju može pisati.

## Dodatne napomene
Claudeove napomene (provjeri):
- Oznaka „Na uređaju" / „Račun: …" je `_libraryHeading` u `lib/ui/home.dart` (želja 004). Korisnik je u 004 odlučio „Zadrži"; ova želja to mijenja u običan tekst s imenom i slikom.
- Ikona za „Moj Deez Neurons račun": `assets/menu/account.png` (izbornik Više, `home.dart`).
- Slika korisnika je novi spremljeni podatak (i možda dio računa/sinkronizacije): promjena pohrane — vrijedi `AGENTS.md` aplikacije i neovisni pregled.
- Pretraživanje: polje iz želje 004 mora i dalje zadržati tipkovnicu otvorenom dok se tipka.

Odgovori korisnika (2026-11-22):
1. Nije prijavljen → samo ikona sa zadanom slikom, bez teksta. Napomena: `AGENTS.md` traži jasno razlikovanje lokalne i računske biblioteke; razlika ostaje vidljiva (ime ↔ samo ikona), a dulji opis može ostati u tooltipu/opisu ikone.
2. Povećalo vrijedi svugdje gdje postoje alatna traka i traka za pretraživanje, uključujući glavni ekran Biblioteke.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta
