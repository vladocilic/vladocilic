---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 013 — „Više": slika dva neurona umjesto aksolotla

## Što želim
Korisnikove riječi (2026-11-22), doslovno:

> Sljedeća želja je da zamijeniš sliku aksolotla koji se nalazi u sekciji više sa slikom dva neurona koji se dodiruju, koji se inače nalaze u headeru početne.

## Kako ću znati da je gotovo
- U sekciji „Više" više nema slike aksolotla.
- Na njezinom mjestu je slika dva neurona koji se dodiruju, ista kao u zaglavlju Početne.

## Dodatne napomene
Claudeovo prepoznavanje (provjereno pregledom slika, ipak provjeri):
- Aksolotl u „Više" je `_mascot(5)` u `_moreView` (`lib/ui/home.dart`); slika se nasumično bira iz `assets/images/Axol 1–14.png` (`lib/data/mascot_selection.dart`, 6 stranica).
- Slika dva neurona u zaglavlju Početne: `assets/images/header_neurons.png` / `header_neurons_mob.png` (`lib/ui/design.dart`); izvornik je `assets/branding/neuron-pair-master.png`.
- Mijenja se samo slika u „Više"; aksolotli na ostalim sekcijama ostaju dok korisnik ne kaže drugačije. Pripazi da promjena ne pokvari spremljeni odabir maskota (`FileMascotStore` provjerava točno 6 različitih maskota).

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-22 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-22. 012 čeka korisnički izbor; radim samo 013. Zamjenjujem prikaz maskote u Više postojećim neuronima iz zaglavlja Početne, bez izmjene izvornog PNG-a ili spremljenog odabira šest maskota. Bez pakiranja.

### M002 | 2026-11-22 | codex → claude | čeka odgovor

Čeka: claude — pregled male zamjene slike bez uređivanja. Repozitorij vladocilic/deez-neurons, grana codex/013-neuroni-vise, puni commit 8bf3c1494c751ceb2e178c1d97dc4d549a133695, baza 698f629cdfe0fa685dae40716203aed960694ff3.

Više koristi iste assets/images/header_neurons.png i header_neurons_mob.png kao zaglavlje Početne, s istim izborom platforme i omjerom. Izvorni PNG-ovi, odabir šest maskota i FileMascotStore nisu izmijenjeni. Uklonjen je samo nepozvani _mascot helper nakon zamjene njegova zadnjeg poziva. 25 testova mascot/navigation/app_artwork_icon prolazi, završna analiza home/mascot_test bez nalaza. Stari test očekivanja aksolotla sada provjerava neuron header i položaj iznad Pohrane i dijeljenja. Opseg: docs/collab/013-neuroni-vise.md. Bez promjene pohrane, novog pakiranja ili instalacije; incident podataka ostaje otvoren.
