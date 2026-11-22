---
status: nova          # nova | u-radu | pitanje | gotovo
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
