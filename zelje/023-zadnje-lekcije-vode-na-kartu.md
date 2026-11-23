---
status: nova          # nova | u-radu | pitanje | gotovo
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
