---
status: nova          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 008 — Napredak: posuda s kuglicama umjesto mozga

## Što želim
Korisnikove riječi (2026-11-21), doslovno:

> U sekciji napredak uklonit ćemo mozak kroz vrijeme i prikaz mozga sa točkicama i umjesto toga ćemo napraviti da se vidi koliko novih i probuđenih neurona smo do sada napravili. Znači, prikaz će biti takav da kao da se u dnu ekrana skupljaju kuglice koje kao da je neko istresao u neku staklenu posudu. Znači, ekran sam je ta posuda, a taj dio s kuglicama će se sve više povećavati kako budemo završavali lekcije, tako da će broj tih kuglica s vremenom sve više rasti, a ta sekcija će biti sve veća i veća zbog toga što te kuglice ćemo stavljati na dno ekrana. Dakle, ostaje iznad kuglica da treba pisati koliko smo sve do sada stvorili novih neurona i koliko smo ih probudili. A u posudi će biti sve ukupno novih i probuđenih neurona, prikazanih u obliku malih šarenih kuglica.

## Kako ću znati da je gotovo
- U sekciji Napredak više nema prikaza „Mozak kroz vrijeme" ni mozga s točkicama.
- Ekran Napretka izgleda kao staklena posuda: na dnu ekrana skupljene su male šarene kuglice, kao da su istresene.
- Broj kuglica jednak je ukupnom broju novih i probuđenih neurona.
- Kako završavam lekcije, kuglica je sve više i sloj kuglica na dnu raste prema gore.
- Iznad kuglica piše koliko sam do sada stvorio novih neurona i koliko sam ih probudio.

## Dodatne napomene
Claudeove napomene za snalaženje (provjeri):
- „Mozak kroz vrijeme" i opis točkica nalaze se u `lib/ui/brain_progress.dart`; Napredak se gradi u `lib/ui/progress_dashboard.dart` (`_progressView()` u `home.dart`).
- Aplikacija koristi naziv **„povezani neuroni"**, a korisnik kaže **„novi neuroni"**. Pretpostavka je da je to isto; potvrdi s korisnikom ako nije.
- Korisnik nije rekao što s ostalim dijelovima Napretka (npr. „Znanje kroz vrijeme", tablica i grafovi). Uklanjaju se samo dva navedena prikaza mozga; ostalo ostaje dok korisnik ne kaže drugačije.
- Nije rečeno smiju li se nove i probuđene kuglice razlikovati bojom; korisnik je rekao samo „male šarene kuglice".
- Ako kuglica bude jako mnogo, posuda se može napuniti; to riješiti razumno i pitati korisnika ako je potrebna odluka.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta
