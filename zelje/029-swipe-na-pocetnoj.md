---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: visok      # visok | srednji | nizak
---

# 029 — Swipe između sekcija ne radi na Početnoj (karta neurona)

## Što želim
Korisnikove riječi (2026-11-23), doslovno:

> Još jedna stvar što se tiče početne. Sada kad izaberem neku lekciju ili cjelinu i ona me odvede na početnu u ono stablo hijerarhijsko sa neuronima, swipe mi ne radi više. Znači, ne mogu swipe-om izaći iz početne. Molim te, pregledaj to i popravi da swipe radi na početnoj kao što radi i na ostalim sekcijama.

## Kako ću znati da je gotovo
- Na Početnoj s kartom neurona povlačenje prstom lijevo/desno prelazi u susjednu sekciju, isto kao na ostalim sekcijama.
- Pomicanje karte gore-dolje i dalje radi; zumiranje s dva prsta i dalje radi.
- Ako je karta zumirana pa je šira od ekrana, vodoravno povlačenje najprije pomiče kartu, a kad karta dođe do svog ruba, sljedeće povlačenje u tom smjeru prelazi u susjednu sekciju.

## Dodatne napomene
Claudeova analiza uzroka (čitanjem koda, `lib/ui/neuron_map.dart`, grana `codex/014-oznaka-starih-rezultata`, commit `efcd527`; potvrdi testom):
- Karta je u vodoravnom `SingleChildScrollView` (`scrollDirection: Axis.horizontal`) čija je širina `math.max(viewportWidth, (960 + depth * 400) * scale)`. Već uz `scale = 1` sadržaj je širok najmanje 960, što je na mobitelu (≈ 390) uvijek šire od ekrana. Vodoravni scroll zato uvijek postoji i, kao unutarnji scrollable, **pobjeđuje u natjecanju gesti**, pa vodoravno povlačenje nikad ne stigne do pagera sekcija (`section_pager.dart`). Sa `ClampingScrollPhysics` to vrijedi i na rubu.
- Prijedlog: (a) uz zoom 1 karta neka **stane u širinu ekrana** (što traži i želja 025: razmak od rubova ≈ 7 %), bez vodoravnog pomicanja; (b) vodoravno pomicanje samo kad je karta zumirana; (c) na vodoravnom rubu zumirane karte prepustiti gestu pageru (isto rješenje kao kod vodoravnih traka u Biblioteci, 004/016, gdje to već radi ispravno).
- Regresijski test: swipe lijevo/desno na Početnoj s kartom mijenja sekciju; vertikalno pomicanje i pinch rade; zumirana karta na rubu predaje swipe.
- Povezano sa željom 025 (nova Početna) — uskladiti da se popravak ne izgubi u preuređenju.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-23 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-23 kao jedina želja visokog prioriteta, prije novih srednjih. Najprije potvrđujem uzrok regresijskim testom; cilj je swipe sekcija na početnoj karti, uz očuvano okomito pomicanje, pinch i predaju geste na rubu zumirane karte. Ne mijenjam pohranu niti pakiram novu verziju. Popravak treba ostati primjenjiv pri budućem preuređenju 025.
