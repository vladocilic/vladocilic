---
status: nova          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 008 — Napredak: posuda s kuglicama umjesto mozga

## Što želim
Korisnikove riječi (2026-11-21), doslovno:

> U sekciji napredak uklonit ćemo mozak kroz vrijeme i prikaz mozga sa točkicama i umjesto toga ćemo napraviti da se vidi koliko novih i probuđenih neurona smo do sada napravili. Znači, prikaz će biti takav da kao da se u dnu ekrana skupljaju kuglice koje kao da je neko istresao u neku staklenu posudu. Znači, ekran sam je ta posuda, a taj dio s kuglicama će se sve više povećavati kako budemo završavali lekcije, tako da će broj tih kuglica s vremenom sve više rasti, a ta sekcija će biti sve veća i veća zbog toga što te kuglice ćemo stavljati na dno ekrana. Dakle, ostaje iznad kuglica da treba pisati koliko smo sve do sada stvorili novih neurona i koliko smo ih probudili. A u posudi će biti sve ukupno novih i probuđenih neurona, prikazanih u obliku malih šarenih kuglica.

Odgovori korisnika na Claudeova pitanja (2026-11-21), doslovno:

> U aplikaciji se novi neuroni zovu povezani neuroni, dobro si pretpostavio. Pod dva, ostali dijelovi napretka poput grafa znanje kroz vrijeme i tablice ostaju, i to si dobro rekao. Pod tri, smiju li nove probuđene kuglice imati različite boje? Da, smiju i trebaju biti različitih boja, da budu šarene, ali pastelne boje.

## Kako ću znati da je gotovo
- U sekciji Napredak više nema prikaza „Mozak kroz vrijeme" ni mozga s točkicama.
- Ekran Napretka izgleda kao staklena posuda: na dnu ekrana skupljene su male šarene kuglice, kao da su istresene.
- Broj kuglica jednak je ukupnom broju novih i probuđenih neurona.
- Kako završavam lekcije, kuglica je sve više i sloj kuglica na dnu raste prema gore.
- Iznad kuglica piše koliko sam do sada stvorio novih neurona i koliko sam ih probudio.
- Kuglice su različitih pastelnih boja.
- Ostali dijelovi Napretka (graf „Znanje kroz vrijeme", tablica) ostaju.

## Dodatne napomene
Claudeove napomene za snalaženje (provjeri):
- „Mozak kroz vrijeme" i opis točkica nalaze se u `lib/ui/brain_progress.dart`; Napredak se gradi u `lib/ui/progress_dashboard.dart` (`_progressView()` u `home.dart`).
- „Novi neuroni" = **„povezani neuroni"** u aplikaciji (korisnik potvrdio).
- Uklanjaju se samo dva navedena prikaza mozga; ostalo u Napretku ostaje (korisnik potvrdio).
- Kuglice trebaju biti različitih pastelnih boja (korisnik potvrdio).
- Ako kuglica bude jako mnogo, posuda se može napuniti; to riješiti razumno i pitati korisnika ako je potrebna odluka.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta
