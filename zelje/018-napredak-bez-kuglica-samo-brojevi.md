---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 018 — Napredak: bez kuglica, samo ukupni brojevi na kraju sadržaja

## Što želim
Korisnikove riječi (2026-11-23), doslovno:

> Sada zapiši ovu želju. Znači, želim da se uklone loptice sa napretka, sa dna ekrana i da ostane samo broj neurona, ukupni broj neurona koje smo probudili i one koje smo povezali. I neka to nije pričvršćeno za dno ekrana, nego da se mora scrollati do tog rezultata na dnu.
> U stvari bilo bi bolje da je vidljiv cijelo vrijeme taj rezultat. Možda bi bilo dobro da je on... Ne, neka bude na dnu.

Na Claudeovo pitanje (stalno pri dnu ekrana ili na kraju sadržaja) korisnik je odgovorio:

> Do brojeva se mora scrollati.

## Kako ću znati da je gotovo
- U Napretku više nema posude ni kuglica.
- Ostaju samo ukupni brojevi: povezani neuroni i probuđeni neuroni (ukupno do sada).
- Brojevi **nisu pričvršćeni** za dno ekrana; nalaze se na kraju sadržaja Napretka i do njih se dolazi pomicanjem (scroll).
- Ostali dijelovi Napretka (kalendar dnevnog niza 010, tablica, grafovi, „Znanje kroz vrijeme") ostaju.

## Dodatne napomene
- Mijenja odluke iz želje 008 (posuda s kuglicama, „stalno pri dnu ekrana"). Posuda se uklanja; `pinned_neuron_vessel.dart` / `neuron_vessel.dart` više nisu potrebni u Napretku.
- Kalendar iz 010 bio je smješten „iznad posude"; neka ostane iznad ukupnih brojeva.
- Brojčanici neka zadrže postojeće značenje (povezani; probuđeni koji čekaju povezivanje, uključujući arhivu obrisanih lekcija), bez dvostrukog prikaza istih brojeva.
- Nema promjene pohrane.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-23 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-23 nakon predaje visokog prioriteta 029. Uklanjam posudu i pričvršćeni panel iz Napretka; postojeća ukupna značenja ostaju u jednom brojčanom prikazu na kraju scroll sadržaja, ispod kalendara. Bez pohrane ili pakiranja. Odgođene podsjetnike 017/019 ne pokrećem.
