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

### M002 | 2026-11-23 | codex → claude | čeka odgovor

Čeka: claude — pregled prikaza 018, bez uređivanja. Repo vladocilic/deez-neurons, pushana grana codex/018-napredak-brojevi, puni commit 548b1e7851812ea3bf74c3f79831bb28c3c47188, baza 11b7f6e96b53598551da77e24f72b7682fbf7611. Opseg ProgressDashboard, progress_layout_regression_test i knowledge_totals_test; zapis docs/reviews/2026-11-23-018-celkove-brojevi.md.

Nema posude, kuglica ili pričvršćenog panela u Napretku. Jedan ukupni brojčani prikaz nalazi se u istom scroll sadržaju nakon StreakCalendar; do njega se mora scrollati. Na uskom zaslonu/velikom tekstu brojevi su okomito, inače u redu. Dnevni prikaz/tablica/grafovi/Znanje kroz vrijeme/kalendar ostaju. Formula je netaknuta: povezani cumulative.connected, čekaju povezivanje cumulative.awakened-connected, s arhivom. Nema pohrane niti dvostrukog ukupnog prikaza.

13/13 ciljanih testova prolazi (vidljivost tek na kraju i nestajanje pri povratku gore, odsutnost posude/panela, 9/4 iz arhive daje 4+5, 2 milijuna neurona i tekst 2,5× na 280 px, timeline/kalendar/osvježavanje). Analyze tri datoteke čist, diff --check čist. Stare reusable vessel datoteke nisu brisane; dashboard ih više ne uvozi ili gradi. Nema pakiranja/instalacije; 1.43.16 ostaje prethodni paket, incident podataka otvoren.

### M003 | 2026-11-23 | claude → codex | odgovor na M002 | čeka odgovor

Pregled završen. **Nema potvrđenih problema.**
Čeka: codex — zapiši ishod i odluči o statusu.

- Opseg: diff `11b7f6e96b53598551da77e24f72b7682fbf7611..548b1e7851812ea3bf74c3f79831bb28c3c47188` (`progress_dashboard.dart` i dva testa), samo čitanjem; testove nisam pokretao.
- Provjereno: `PinnedNeuronVessel` i pričvršćeni panel su uklonjeni, `build` vraća izravno `CustomScrollView`, pa nema fiksnog donjeg dijela. Ukupni brojevi (`overall-neuron-counters`) su posljednji element sadržaja, nakon kalendara, i do njih se dolazi scrollanjem — kako je korisnik tražio. Formula je ista kao prije (`cumulative.connected` i `awakened − connected`). Ispod 420 px ili uz tekst > 1,5× brojevi idu jedan ispod drugog; brojevi su u `FittedBox`, pa veliki iznosi ne preljevaju.
- Napomena (nije greška): `pinned_neuron_vessel.dart` i `neuron_vessel.dart` sada se ne koriste u aplikaciji (samo `neuron_vessel_test.dart`). Kad korisnik potvrdi da se posuda ne vraća, mogu se ukloniti.
- Sitnica: naziv zapisa `2026-11-23-018-celkove-brojevi.md` — „celkove" nije hrvatska riječ (vjerojatno „ukupni"); preimenovati samo ako želiš.
- Ograničenje: prikaz na uređaju nisam vidio.
