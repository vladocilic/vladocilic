---
status: nova          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 010 — Napredak: kalendar dnevnog niza (daily streak) u bojama

## Što želim
Korisnikove riječi (2026-11-21), doslovno:

> Sljedeća želja se odnosi na to da pratimo daily streak. Znači, je li osoba svaki dan vježbala. To ćemo učiniti na način tako što ćemo prikazati kao kalendar na kojem taj dan je označen bojom. Ako nije bilo nijednog ponavljanja, boja će biti bijela. Ako je bilo jedno ponavljanje, bit će svjetlo plava, pa ćemo tako ići na tamno plavu, pa na tamno zelenu, na svjetlo zelenu, pa zeleno žuta, pa naranđasta, pa crvena. Crvena će značiti najveći broj ponavljanja. Možemo to, ne znam koliko sam izbrojao boja, ali može to ići do 10. 10 ponavljanja da bude crvena boja, a 0 ponavljanja je bijela boja. Boje, kako sam ih naveo redom, su između, a ti nadodaj još neku nijansu ukoliko je potrebno. Uglavnom, to je gradacija od plave prema crvenoj. Taj dio praćenja će biti isto u napretku, ali gore iznad ovih kuglica koje će prikazivati sveukupni broj neurona koje smo do sada povezali ili ti ga probudili.

## Kako ću znati da je gotovo
- U sekciji Napredak, iznad posude s kuglicama (želja 008), nalazi se kalendar.
- Svaki dan u kalendaru obojen je prema broju ponavljanja tog dana:
  - 0 ponavljanja: bijela;
  - 1 ponavljanje: svijetloplava;
  - zatim redom prema većem broju: tamnoplava, tamnozelena, svijetlozelena, zelenožuta, narančasta;
  - 10 ili više ponavljanja: crvena.
- Iz kalendara se vidi je li se vježbalo svaki dan.

## Dodatne napomene
Prijedlog ljestvice za 1–10 (korisnik je dopustio dodati nijanse; konačni izgled neka korisnik potvrdi na testnoj verziji):

| Ponavljanja | Boja |
|---|---|
| 0 | bijela |
| 1 | svijetloplava |
| 2 | plava |
| 3 | tamnoplava |
| 4 | tamnozelena |
| 5 | zelena |
| 6 | svijetlozelena |
| 7 | zelenožuta |
| 8 | narančasta |
| 9 | crvenonarančasta |
| 10+ | crvena |

Otvoreno / pretpostavke (pitaj korisnika ako je potrebno):
- „Ponavljanje" je pretpostavljeno kao jedno dovršeno učenje lekcije, isto što Napredak već broji kao „dovršena učenja". Provjeri da je to korisnikova namjera.
- Korisnik nije odredio raspon kalendara (tekući mjesec, zadnjih nekoliko tjedana, listanje po mjesecima) ni prikazuje li se i broj dana u nizu. Odaberi razumno rješenje i zapiši ga; ako treba odluka, postavi pitanje.
- Ovisi o želji 008 (položaj iznad kuglica); ako se 008 još ne radi, kalendar staviti na vrh Napretka.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta
