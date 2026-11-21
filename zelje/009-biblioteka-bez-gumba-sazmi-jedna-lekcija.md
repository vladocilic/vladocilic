---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 009 — Biblioteka: ukloniti gornji gumb Sažmi/Proširi; samo jedna otvorena lekcija

## Što želim
Korisnikove riječi (2026-11-21), doslovno:

> U biblioteci, bilo na području, cjelini ili lekciji, gumb sažmi proširi nam više nije potreban pa ga treba ukloniti. Ono što treba popraviti kod cjeline je da kada jednu lekciju proširimo, da se druga zatvori ako je slučajno bila otvorena i to je to.

Pojašnjenje korisnika na Claudeovo pitanje, doslovno:

> Da, mislim na gornji gumb sažmi proširi u traci sa alatima, a njega treba ukloniti.

## Kako ću znati da je gotovo
- Gornjeg gumba „Sažmi"/„Proširi" u traci s alatima (uz boje i brisanje) više nema, ni u korijenu Biblioteke ni unutar područja i cjeline.
- Strelice za proširivanje na pojedinom području, cjelini i lekciji ostaju i rade.
- Kad unutar cjeline proširim jednu lekciju, prethodno otvorena lekcija se zatvori; uvijek je otvorena najviše jedna lekcija.

## Dodatne napomene
Gornji gumb je `library-toggle-all` u `_libraryAppearanceControls` (`lib/ui/home.dart`), uveden/izmijenjen u željama 004 i 005. Mali gumb za izradu iz želje 005 u istoj traci ostaje.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-21 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-21. 008 je predana, sada radim samo 009. Uklanjam gornji Sažmi/Proširi, ostavljam pojedinačne strelice i mali kontekstni gumb 005. Otvaranje lekcije zatvara prethodnu, bez zapisivanja u biblioteku ili napredak. Bez pakiranja.
