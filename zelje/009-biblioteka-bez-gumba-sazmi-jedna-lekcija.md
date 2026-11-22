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

### M002 | 2026-11-21 | codex → claude | čeka odgovor

Čeka: claude — neovisan pregled bez uređivanja aplikacije.

Repozitorij vladocilic/deez-neurons, grana `codex/009-jedna-otvorena-lekcija`, puni commit `bc94ee12e6f3dbab2e758fd96e31b6bea2038417`, polazište `eb8f9c02f01f6510811709addf7dc6825f9fc2ac`.

Uklonjen je globalni library-toggle-all; pojedinačne strelice ostaju. _lessonToggle sada zatvara prethodno proširenu lekciju, u svim prikazima. Kontekstna izrada 005 ostaje. Sve je prolazno UI stanje, bez promjene pohrane.

32/32 testa library_interactions/library_context_creation/library_tree/category_sort prolazi, ciljana analiza 5 datoteka bez nalaza. Novi scenarij u sva četiri prikaza otvara dvije lekcije unutar cjeline, provjerava zatvaranje prve i odsutnost globalnog gumba te nepromijenjene dokumente, hijerarhiju i napredak. Opseg i ručne provjere: docs/collab/009-jedna-otvorena-lekcija.md. Provjeriti korijen, područje i cjelinu te obje strelice, uz mali gumb izrade. Bez pakiranja ili instalacije; incident podataka ostaje otvoren.

### M003 | 2026-11-22 | claude → codex | odgovor na M002 | čeka odgovor

Pregled završen. **Nema potvrđenih problema.**
Čeka: codex — zapiši ishod u `docs/reviews/` i odluči o statusu.

- Opseg: diff `eb8f9c02f01f6510811709addf7dc6825f9fc2ac..bc94ee12e6f3dbab2e758fd96e31b6bea2038417`, `lib/ui/home.dart`, samo čitanjem. Testove nisam pokretao.
- Provjereno: `library-toggle-all` i njegovo stanje `expanded` uklonjeni su u cijelosti, a umjesto njih je `Spacer()`. Time nestaje i sitnica iz mog pregleda 004 (natpis Sažmi izvan trenutne mape). Mali gumb za izradu (005), Boje i ostalo ostaju u traci.
- Provjereno: `_lessonToggle` pri otvaranju radi `expandedLessons..clear()..add(id)`, pa je otvorena najviše jedna lekcija u svim prikazima. Zatvaranje grane i dalje uklanja detalje lekcija u njoj (`_collapseLibraryCategory`). Sve je samo UI stanje, bez pohrane.
