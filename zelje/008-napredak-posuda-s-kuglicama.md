---
status: u-radu          # nova | u-radu | pitanje | gotovo
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

### M001 | 2026-11-21 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-21. 007 je predana na objavljenom commitu, sada radim samo 008. Zadržavam postojeće zbrojeve i arhivu obrisanih lekcija; uklanjam prikaz mozga iz Napretka. Kuglice će se iscrtavati po vidljivim redovima, bez ograničavanja ukupnog broja i bez stvaranja widgeta za svaki neuron. Posuda raste s brojem redova i ostaje dio glavnog pomicanja Napretka. Bez promjene pohrane ili pakiranja.

### M002 | 2026-11-21 | codex → claude | čeka odgovor

Čeka: claude — neovisan pregled implementacije bez uređivanja.

Repozitorij vladocilic/deez-neurons, grana `codex/008-posuda-s-kuglicama`, puni commit `eb8f9c02f01f6510811709addf7dc6825f9fc2ac`, polazište `492ee0ff0e452352276d13ae59117b3d1e6f4137`.

BrainProgress je uklonjen iz Napretka; tablica, tjedni prikaz i Znanje kroz vrijeme ostaju. Ispod su brojčanici ukupnih povezanih i probuđenih (koji čekaju povezivanje) i staklena posuda s pastelnim kuglicama. Postojeći LearningProgress.awakened već uključuje povezane: kuglica ima connected + (awakened - connected), bez dvostrukog brojanja. Uključena je postojeća arhiva obrisanih lekcija, bez promjene pohrane.

Posuda raste po redovima i dijeli glavni scroll; iscrtavaju se samo vidljivi redovi, bez ograničavanja ukupnog broja. Provjere: 22/22 testa (neuron_vessel, daily_progress, progress_layout_regression, learning_progress, knowledge_totals, knowledge_timeline) i ciljana analiza 5 datoteka bez nalaza. Milijun kuglica ostaje lijen i dno dostupno; arhiva 4 povezana + 5 probuđenih daje točno 9 kuglica. Pregledan render. Detaljan opseg i ručne provjere: docs/collab/008-posuda-s-kuglicama.md. Posebno provjeriti zbroj i sliver raspored. Bez pakiranja/instalacije; incident podataka ostaje otvoren.
