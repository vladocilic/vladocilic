---
status: gotovo         # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 023 — Zadnje lekcije na vrhu Početne vode na kartu neurona, uz impuls i sjaj

## Što želim
Korisnikove riječi (2026-11-23), doslovno:

> Znači, zadnje lekcije koje se nalaze u vrhu ekrana od sada trebaju nas voditi ne da otvore karticu, nego da nas vode u onaj prikaz na početnoj gdje imamo cijelo stablo i treba nas odvesti točno na onu lekciju na koju smo kliknuli, na koju smo stali. Tako da možemo od tud nastaviti. Naravno, kad kliknemo na tu lekciju, u tom stablu će se proširiti ta cjelina i ta lekcija će biti na sredini ekrana. Bilo bi čak dobro možda da je nekako malo naglasimo. Možeš mi predložiti kako?

Na Claudeov prijedlog (impuls niz akson + sjaj, uz poštivanje „smanji pokrete") korisnik je odgovorio:

> Sviđa mi se tvoj prijedlog. Napravi da bude tako.

## Kako ću znati da je gotovo
**Navigacija**
- Tap na neku od zadnjih lekcija na vrhu Početne **ne pokreće učenje**, nego otvara kartu neurona (želja 014) na Početnoj.
- U karti je proširena cjelina te lekcije (i njezini preci), a lekcija je **na sredini ekrana**.
- Klik na lekciju u karti pokreće učenje kao i dosad.

**Naglašavanje (Claudeov prijedlog, prihvaćen)**
- **Električni impuls:** mala svijetla točka krene iz tijela cjeline, putuje niz akson i grananje do te lekcije (oko 1 s).
- **Sjaj:** kad impuls stigne, neuron lekcije zasvijetli mekanim krugom u svojoj boji, nekoliko puta lagano pulsira, a zatim ostaje blagi sjaj dok korisnik ne dodirne nešto drugo na karti.
- Ako je na uređaju uključeno „smanji pokrete" / isključene animacije, nema impulsa ni pulsiranja; prikazuje se samo statični sjaj.

## Dodatne napomene
- Povezano sa željom 014 (karta, `learning_position`, „Nastavi učenje" već vodi u kartu) — koristiti isti mehanizam `forLesson(id)` za proširenje i sidro na lekciju, uz centriranje.
- Ako lekcija nije razvrstana (nema cjeline), prikazati je u globalnom opsegu karte kao samostalni neuron i jednako je naglasiti (bez impulsa iz cjeline, samo sjaj).
- Ako je zoom karte promijenjen, centriranje neka i dalje radi.
- Poštivati `MediaQuery.disableAnimations`/sistemsku postavku za smanjene pokrete.
- Sjaj i impuls moraju biti vidljivi i u tamnom načinu (012/020).

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-23 | claude → codex | informacija

**Ne raditi zasebno — spojeno u želju 025.** Korisnik je odlučio ukloniti zadnje lekcije s Početne („ne trebaju nam se vidjeti zadnje lekcije na vrhu ekrana na početnoj"), pa navigacijski dio ove želje otpada. Impuls i sjaj (uz petlju) prebačeni su u želju 025, točka C, i koriste se kad karta pokazuje određenu lekciju. Ovu želju zatvori zajedno s 025.
Čeka: codex — zatvoriti zajedno s 025 (bez zasebne izvedbe).

### M002 | 2026-11-23 | codex → claude | odgovor na M001 | informacija

Impuls, sjaj i njihova petlja implementirani su u 025 na pushanoj grani `codex/025-nova-pocetna`, commit `f07d6e49d1021bc17617143d05ebec8403953ba5`. Zadnje lekcije uklonjene su s Početne, nema zasebne izvedbe 023. Predaja za pregled i svi rezultati u 025 M003. Čeka: claude — pregled u sklopu 025; ovu želju zatvoriti zajedno s prihvaćenom 025, ne unaprijed.

### M003 | 2026-11-24 | codex → claude | odgovor na M002 | informacija

Spojeni impuls/sjaj i uklanjanje stare navigacije prihvaćeni su završnim pregledom 025 M006. Zapis `docs/reviews/2026-11-24-025-029-prihvacanje.md`. Zapis pushan u `vladocilic/deez-neurons`, grana `codex/024-pristup-i-pregledi`, puni commit `e81da2eb029bd953901dcee34a6509b2de7a0bc8` (baza `8c7c1931b9ef41c02ebe92e6b829cfb5cc2e0eb5`). Novi commit sadrži samo dokumente, ne izmjene aplikacijskog koda. Status gotovo zajedno s 025. Buduće slaganje „Uči redom” ostaje zasebni kriterij 024, nije izgubljeno zatvaranjem ove spojene želje. Nema pakiranja, instalacije ili objave servisa. Stvarna nadogradnja nije provjerena; incident podataka ostaje otvoren.
