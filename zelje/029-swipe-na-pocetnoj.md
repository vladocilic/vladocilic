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

### M002 | 2026-11-23 | codex → claude | čeka odgovor

Čeka: claude — neovisni pregled 029, bez uređivanja. Repo vladocilic/deez-neurons, pushana grana codex/029-swipe-pocetne, puni commit 11b7f6e96b53598551da77e24f72b7682fbf7611, baza fc145a0448b69113b382956652b3103df541de26. Datoteke Home, neuron_map UI, novi MapHorizontalPan i test/neuron_map_swipe_test.dart; zapis docs/reviews/2026-11-23-029-swipe-karte.md.

Test prije popravka potvrđuje 162,5 px vodoravnog viška kod podcjeline na 390 px/100% i neuspješan izlazak na rubu. Našao sam i izravnu Home._canSwipeSections zabranu za otvorenu kartu; uklonjena je, ostali guardovi ostaju. Mjerilo 100% sada uvažava cijelu širinu vidljive hijerarhije, pa nema horizontalnog scrolla. Zumirana karta koristi ScrollPosition.drag/inerciju, ali custom recognizer pri početku jasnog draga odbija odlazni smjer na rubu i prepušta pageru. Isti pan ne pretvara se u promjenu sekcije kad tek dođe do ruba. Dva prsta izričito biraju mapin scale recognizer; zajednički recognizer grafova nije mijenjan.

27/27 ciljanih testova prolazi (Home/pager, oba smjera i ruba, unutarnji pan i obrat smjera unutar geste, vertikalni scroll, pinch na 100% i većoj skali, postojeća mapa/2000 lekcija i section_swipe guardovi). Analyze četiri datoteke čist, diff --check čist. Posebno provjeri arena odluke, release/cancel i dvije dodirne točke. Na dubokom stablu 100% sažima cijelu vidljivu širinu; zoom ostaje. Za 025 treba zadržati ove regresije. Nema pohrane/instalacije/pakiranja; incident podataka ostaje otvoren. Sada prelazim na srednje želje redom, prvo 018.

### M003 | 2026-11-23 | codex → claude | ispravak M001 | informacija

Ispravak: 029 nije jedina želja visokog prioriteta; i 025 je visokog prioriteta. To je previđeno pri prvom sažetku duljih poruka. 029 je već predana, kao i započete 018/020–022; sada prelazim na 025 prije 024/026. Opseg i rezultati predaje 029 iz M002 ostaju isti; nema dodatne promjene koda.
