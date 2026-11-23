---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 021 — Biblioteka, „Hijerarhija sa slikama": veće ikone

## Što želim
Korisnikove riječi (2026-11-23), doslovno:

> Sljedeće želje u biblioteci kod hijerarhijskog prikaza sa slikama. Želim da se slike više vide, da im malo više širine, tako da se sadržaj bolje vidi.

Pojašnjenje korisnika, doslovno:

> Mislio sam pod sličicama ikone.

## Kako ću znati da je gotovo
- U prikazu Biblioteke „Hijerarhija sa slikama" ikone područja, cjelina i lekcija su veće i šire nego sada.
- Sadržaj ikone (slika) se jasnije vidi.
- Nazivi i mali gumbi (strelica, plus, tri točkice, ikonica neurona) i dalje stanu i ne preklapaju se, i na uskom mobitelu i s velikim tekstom.

## Dodatne napomene
- Odnosi se samo na prikaz „Hijerarhija sa slikama" (`viewMode == 'tree'`); ostali prikazi (kućice, mini kućice, kompaktno) ostaju kakvi jesu, osim ako korisnik kaže drugačije.
- Korisnik je rekao „malo više širine": umjereno povećanje, ne prevelike ikone. Zadržati omjer slike tako da se ne izobličuje i ne reže bitan dio.
- Uskladiti s obojenim okomitim trakama roditelja iz želje 016.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-23 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-23 nakon predaje 020. Povećavam i proširujem ikone samo u tree prikazu, uz očuvan omjer, nazive i male alate na uskom ekranu/velikom tekstu. Ostali prikazi i roditeljske trake ostaju. Bez pohrane ili pakiranja.

### M002 | 2026-11-23 | codex → claude | čeka odgovor

Čeka: claude — pregled 021, bez uređivanja. Repo vladocilic/deez-neurons, pushana grana codex/021-vece-ikone, puni commit c8f5ea25c3cda686da536e15feee5166f5304461, baza 8b513eedf282c11ca75328bc3cbe02de6da680d3. Izvršni opseg samo lib/ui/library_tile_header.dart; zapis docs/reviews/2026-11-23-021-vece-ikone.md, renderi assets/021-hijerarhija-mobitel.png i 021-hijerarhija-siroko.png.

Tree stupac slike do 80 px/25% umjesto 64/20%, simbol do 56 umjesto 40 px, uz sužavanje na uskom redu. Slike contain bez rezanja ili promjene bajtova. Uske kategorije bez vlastite fotografije imaju zaseban red alata ispod naziva/slike, široki redovi alate desno; Wrap izvan intrinsic visine sprječava otkriveni overflow. Vlastite pune sličice ostaju pune visine, kompaktni prikaz i kućice nisu mijenjani. Roditeljske lajsne i callbackovi ostaju.

45/45 postojećih ciljnih testova prolazi (puni thumbnail, boje, hijerarhija na 320/393/desktop, sva četiri prikaza, pretraga/IME/interakcije/navigacija), analyze datoteke čist, diff --check čist. Stvarni renderi 390/690 s učitanim providerima prolaze i pregledani su. Posebno pregledaj prostor naziva/alata i umjerenost veličine; sljedeća 022 zasebno uklanja plus, ovdje još nije uklonjen. Nema pohrane, pakiranja/instalacije; incident podataka otvoren.
