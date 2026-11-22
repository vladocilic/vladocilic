---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 014 — Početna: neuronska karta napretka područja i cjelina

## Što želim
Korisnik je želju izrekao u dvije poruke (2026-11-22) uz tri slike i SVG datoteku, i zatražio slanje nakon druge poruke. Doslovno:

> **1.** Dakle, za sljedeću želju želim da upotrebiš ove tri slike i SVG dokument i da napravimo na početnoj da se prikazuje progres određenog područja ili cjeline. Znači, na slici neuron -02 imamo prikaz kako izgledaju zatvorene cjeline. Na slici neuron 01 imamo kako izgleda kada se jedna cjelina otvori i u njoj vidimo na prvom mjestu lekciju koja je već odrađena i spojena je na ovaj neuron i imamo dole lekcije koje nisu odrađene ni jednom i nisu spojene. Ono što ćemo napraviti je da kada netko u biblioteci tapne na ikonu područja ili cjeline, automatski ga bacamo u početnu sekciju gdje on se automatski nađe točno na tom mjestu koje je izabrao. Isto tako, početna će nam se uvijek otvarati na onom mjestu gdje je čovjek stao sa učenjem. Na otvorenoj cjelini i da on vidi tu lekciju koju je zadnju radio. U SVG failu sam napravio dijelove koje ćeš koristiti za izradu ovih neurona. Neuroni će biti boje, zavisi ako prikazuju cjelinu, bit će onda boje cjeline, a ako prikazuju lekciju, bit će boje lekcije. Jezgre tih neurona će biti obojane prema bojama koje se nalaze u SVG failu na dnu. S tim da će lijeva boja, tamno plava, predstavljati 10% naučenog znanja, a crvena na desnoj strani 100% naučenog znanja. Što znači, ako korisnik prolazi kroz lekciju i na kraju je odgovorio lekciju sa svim točnim odgovorima, jezgra će biti crvena. Znači, boja jezgre će ovisiti o postotku koliko je naučio tu lekciju. Ono što je bitno za izradu oko tijela neurona sa njegovim glavama, kako sam ih ja nazvao, je da koristiš dvije glave i jednu glavu prema potrebi na način da ako je u lekciji 20 pitanja, onda će to biti 10 glava, 10 dijelova koji sadrže dvije glave. A ako lekcija recimo sadrži 5 pitanja, onda ćemo koristiti 5 sa jednom glavom. Dakle, što je manje pitanja u lekciji, a isto tako što je manje lekcija u cjelini, koristit ćemo više dijelova sa jednom glavom, a što ih je više, koristit ćemo ove sa dvije. Možeš ih kombinirati tako da neuroni uvijek izgledaju malo različito. Otvaranje i zatvaranje neurona, točnije sažimanje i proširivanje, se događa tako što kliknemo na cjelinu i ona se proširi. I ako kliknemo drugi put, ona će se sažeti. A lekcije pokrećemo isto tako klikom na lekciju. Jesi li razumio?

> **2.** Još samo ova stvar, negdje na početnoj kada su otvorene na ovaj način lekcije i cjeline, mora biti gore desno gumbić da izađemo iz tog prozora i da se vratimo u trenutni izgled početne stranice gdje vidimo gumbe za izradu lekcije i za nastavak učenja. A ako kliknemo nastavi učiti, ulazimo opet nazad tamo gdje smo stali. Sada možeš poslati ovu želju.

Odgovori korisnika na Claudeova pitanja (2026-11-22), doslovno:

> Dva lika su ikona te lekcije. Pod dva područja nećemo prikazivati. Ovdje prikazujemo samo cjeline i lekcije. Jezgra neodrađene lekcije može biti bijela. Pod 4 jezgra je prosjek, tako je. I pod 5 najviše glava. Koliko najviše glava ima kad lekcija ima puno pitanja? Pa nema ograničenja.

Pojašnjenja korisnika (2026-11-22), doslovno:

> Samo da se razumijemo, znači biblioteku ne mijenjaš uopće, ona ostaje kakva je. Ovo je novi dio koji će se prikazivati na početnoj.

> Dakle, u biblioteci tap ili klik na bilo na područje, bilo na cjelinu nas prebacuje u ovaj novi prikaz u početnoj. Samo sažimanje nam otvara u biblioteci pregled cjelina i lekcija. Dalje, što si me pitao još? Molim te za točke spajanja odredi sam. Aksiom isto ti to sam objasni kodeksu. Što se tiče pod 3 boje jezgre su jarke, možeš ih prilagoditi tako da budu u našem stilu, ali gradacija nek ostane prema ovim bojama, od hladnih prema toplim.

## Slike i SVG (priložio korisnik)
- [`slike/014-neuron-01-otvorena-cjelina.jpg`](slike/014-neuron-01-otvorena-cjelina.jpg) — „neuron 01": otvorena cjelina; dugi akson prema dolje, lekcije se granaju udesno; prva (odrađena) lekcija spojena je na akson, ostale (neodrađene) nisu spojene.
- [`slike/014-neuron-02-zatvorene-cjeline.jpg`](slike/014-neuron-02-zatvorene-cjeline.jpg) — „neuron 02": zatvorene cjeline kao okomiti lanac neurona, svaka s crtom udesno i natpisom „Ime cjeline".
- [`slike/014-neuron-dijelovi.jpg`](slike/014-neuron-dijelovi.jpg) — prikaz dijelova i ljestvice boja.
- [`slike/014-Neuron_parts.svg`](slike/014-Neuron_parts.svg) — izvorni dijelovi za izradu neurona: `jedna_glava`, `dvije_glave`, `tri_glave` (završetak), `prosirenje`, `rep_ispod_prosiranja`, `rep`, `tijelo`, `jezgra` i grupa `boje` s 10 boja (slijeva: #474f9a, #2a74ab, #0a93ba, #19a84a, #8ebc3f, #ecdf17, #f9c718, #f08e23, #e96326, #df2827).

## Kako ću znati da je gotovo
**Prikaz**
- Na Početnoj postoji prikaz napretka u obliku neurona, izrađenih iz dijelova u SVG-u.
- Zatvorene cjeline izgledaju kao na slici „neuron 02".
- Klik na cjelinu je proširi (izgled kao „neuron 01"), drugi klik je sažme.
- U otvorenoj cjelini lekcije koje su barem jednom odrađene spojene su na akson cjeline, a neodrađene nisu.
- Klik na lekciju pokreće učenje te lekcije.
- Iznad crte svake lekcije (i cjeline) prikazuje se njezina ikona (na slikama su to dva lika).
- Područja se ne prikazuju kao neuroni; prikazuju se samo cjeline i lekcije.

**Boje i oblik**
- Tijelo neurona cjeline je u boji cjeline, a tijelo neurona lekcije u boji lekcije.
- Jezgra neodrađene lekcije je bijela.
- Jezgra cjeline je prosjek naučenosti njenih lekcija.
- Boje jezgre prilagođene su stilu aplikacije (nježnije), ali gradacija ostaje kao u SVG-u, od hladnih prema toplim.
- Jezgra je obojena prema postotku naučenog, ljestvicom iz SVG-a: krajnja lijeva tamnoplava = 10 %, krajnja desna crvena = 100 % (lekcija riješena sa svim točnim odgovorima ima crvenu jezgru).
- Broj „glava" oko tijela: kod lekcije odgovara broju pitanja, kod cjeline broju lekcija (npr. 20 pitanja → 10 dijelova s dvije glave; 5 pitanja → 5 dijelova s jednom glavom). Što je manje pitanja/lekcija, više je dijelova s jednom glavom; što je više, više s dvije. Dijelovi se kombiniraju tako da neuroni izgledaju malo različito.
- Broj glava nije ograničen: i lekcija s mnogo pitanja ima po jednu glavu za svako pitanje.

**Navigacija**
- Izgled Biblioteke se ne mijenja. Jedina promjena: tap/klik na područje ili cjelinu u Biblioteci prebacuje u neuronski prikaz na Početnoj, točno na to mjesto (za područje: njegove cjeline).
- Strelice za proširivanje/sažimanje u Biblioteci i dalje prikazuju cjeline i lekcije unutar Biblioteke, kao dosad.
- Neuronski prikaz otvara se na mjestu gdje je korisnik stao: otvorena cjelina s vidljivom zadnjom lekcijom.
- Gore desno u neuronskom prikazu je gumb koji ga zatvara i vraća sadašnji izgled Početne (gumbi za izradu lekcije i nastavak učenja).
- Gumb „Nastavi učenje" na Početnoj vraća u neuronski prikaz, na mjesto gdje je korisnik stao.

## Dodatne napomene
Odgovoreno od korisnika:
1. Dva lika = ikona te lekcije (odnosno cjeline) — prikazuje se njezina stvarna ikona/slika.
2. Područja se ne prikazuju; samo cjeline i lekcije.
3. Jezgra neodrađene lekcije je bijela.
4. Jezgra cjeline = prosjek naučenosti njenih lekcija.
5. Broj glava nije ograničen.

Napomene (Claude):
- Tap na **područje** u Biblioteci prikazuje cjeline tog područja na Početnoj (zatvorene, kao „neuron 02"); tap na **cjelinu** prikazuje tu cjelinu otvorenu. Biblioteka se inače ne mijenja (korisnik potvrdio).

### Sastavljanje neurona iz SVG-a (korisnik je prepustio Claudeu da odredi; koordinate su iz `014-Neuron_parts.svg`)

**Dijelovi i njihove točke spajanja**
| Dio | Gdje je u SVG-u | Točka spajanja | Smjer |
|---|---|---|---|
| `tijelo` | krug, središte (187.19, 298.41), r = 77.32 | središte | — |
| `jezgra` | krug, isto središte, r = 22.79 | središte tijela | — |
| `jedna_glava` | x ≈ 180–233, y ≈ 47–113.2; ravno dno na y = 113.21, širine 50.54 | sredina ravnog dna ≈ (207.6, 113.2) | os od dna prema vrhu (u SVG-u „gore") |
| `dvije_glave` | x ≈ 79–144, y ≈ 46–112.6; ravno dno na y ≈ 112.6, širine 59.54 | sredina ravnog dna ≈ (109.5, 112.6) | os od dna prema vrhu |
| `prosirenje` | pravokutnik 44.6 × 36.39, rx 8.19 | sredina kraće stranice na svakom kraju | uzduž aksona |
| `rep_ispod_prosiranja` | pravokutnik 139.52 × 29.01, rx 8.19 | sredina kraćih stranica | uzduž aksona |
| `rep` | sužavajući krak, x ≈ 363–564.6, središnja os y ≈ 80 | lijevi (širi) kraj ≈ (363.3, 80) i desni (uži) kraj ≈ (564.6, 80) | od šireg prema užem |
| `tri_glave` | završetak, x ≈ 567–627, y ≈ 40–130 | lijeva udubljena sredina ≈ (567, 80–85); u SVG-u se već nastavlja na desni kraj `rep` | otvor prema van (u SVG-u udesno) |

**Glave oko tijela**
- Svaka glava (jedna ili dvije) postavlja se tako da je sredina njezina ravnog dna na rubu tijela (polumjer ≈ 0,95 · r, da nema procjepa), a os glave pokazuje radijalno prema van.
- Broj glava = broj pitanja (lekcija) ili broj lekcija (cjelina). `dvije_glave` broji se kao 2, `jedna_glava` kao 1. Mali brojevi → više jednostrukih, veliki → više dvostrukih (pravilo korisnika). Raspored kombinirati deterministički iz ID-a lekcije/cjeline, da isti neuron uvijek izgleda isto, a različiti malo različito.
- Opseg tijela ≈ 486 jedinica; na punoj veličini stane ≈ 8–9 dijelova. Kad ih je više: smanjiti dijelove jednoliko (širina dna · k ≤ opseg), a kod vrlo velikog broja složiti ih u dva prstena. Broj glava nije ograničen (korisnik).

**Akson (mora se produljivati, ne povećavati)**
- Redoslijed od tijela prema kraju (kao na `014-neuron-dijelovi.jpg` i „neuron 01"): 2–3 × `prosirenje` s malim razmakom → `rep_ispod_prosiranja` → `rep` → `tri_glave`.
- Kad akson mora biti dulji (više lekcija u otvorenoj cjelini), produljuje se **samo ravni segment** (`rep_ispod_prosiranja`, odnosno ravni dio linije), uz istu debljinu (29.01) i iste zaobljene kutove (rx 8.19 se ne rasteže — „nine-slice"). Nikad ne skalirati cijeli akson, jer bi postao deblji.
- `rep` i `tri_glave` zadržavaju svoje proporcije.

**Tri vrste rasporeda**
- *Zatvorene cjeline („neuron 02")*: neuroni okomito jedan ispod drugog; ispod tijela kratki akson (`prosirenje` → kratki `rep`) i `tri_glave` okrenut prema dolje, koji dodiruje gornje glave sljedećeg neurona. Iz tijela vodoravna tanka linija udesno sa `tri_glave` na kraju; ime cjeline ispod linije, ikona iznad nje.
- *Otvorena cjelina („neuron 01")*: akson cjeline okomito prema dolje, produljen koliko treba za sve lekcije, sa `tri_glave` na dnu. Lekcije su neuroni desno; njihov akson ide vodoravno ulijevo prema aksonu cjeline.
- *Spojena / nespojena lekcija*: odrađena lekcija ima akson koji dolazi do aksona cjeline i spaja se na njega (vidi prvu lekciju na „neuron 01"); neodrađena ima `tri_glave` koji lebdi s razmakom od aksona cjeline.

**Boje jezgre (nježnija ljestvica, ista gradacija hladno → toplo)**
Prijedlog (izvorne boje posvijetljene ≈ 28 % i ≈ 28 % manje zasićene); Codex smije fino podesiti radi čitljivosti i tamnog načina (želja 012):
| % naučeno | Izvorno (SVG) | Prijedlog |
|---|---|---|
| bez učenja | #ffffff | #ffffff |
| 10 % | #474f9a | #7d82b4 |
| 20 % | #2a74ab | #659bc3 |
| 30 % | #0a93ba | #45b7d7 |
| 40 % | #19a84a | #50ca7a |
| 50 % | #8ebc3f | #abc380 |
| 60 % | #ecdf17 | #dcd56d |
| 70 % | #f9c718 | #e4ca6f |
| 80 % | #f08e23 | #e0ad75 |
| 90 % | #e96326 | #dc9676 |
| 100 % | #df2827 | #d57776 |
Uskladiti s nježnim bojama iz želja 008 i 010.
- Bez ograničenja broja glava: kod vrlo velikog broja pitanja glave će morati biti manje ili gušće raspoređene da neuron ostane čitljiv i da crtanje ostane brzo.
- Postotak naučenosti uskladiti s načinom na koji aplikacija već računa naučenost (Napredak, „povezani/probuđeni neuroni").
- Povezano sa željama 004/009 (Biblioteka) i 008/010 (boje u Napretku). Sadržaj mape u Biblioteci i dalje je dostupan preko strelica proširivanja.
- „Zadnje mjesto učenja" vjerojatno treba spremati; ako je to novi spremljeni podatak, vrijedi `AGENTS.md` aplikacije i neovisni pregled.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-22 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-22, nakon objavljene predaje 013. Ovo je veća funkcionalnost s navigacijom i novim spremljenim mjestom učenja; najprije pregledavam priložene slike/SVG i postojeće izračune, zatim pripremam konkretan pristup za neovisan pregled. Biblioteka neće dobiti novi vizualni raspored niti se mijenjaju korisničke lekcije/napredak. Bez pakiranja.

### M002 | 2026-11-22 | codex → claude | čeka odgovor

Čeka: claude — pregled konkretnog pristupa prije implementacije karte, navigacije i nove pohrane položaja, bez uređivanja aplikacije.

Repozitorij vladocilic/deez-neurons, grana codex/014-neuronska-karta-pristup, puni commit e9d86945fc136eeba826db4a9fe99d991d6aa587, baza 8bf3c1494c751ceb2e178c1d97dc4d549a133695. Pregledao sam sve tri JPG reference i izvorni SVG iz maina sandučića (31b6eb07d3611a15b9c8727f534cb8d826c6eacd). SVG je kopiran u assets/branding/neuron-map-parts-source.svg; iz njega tools/generate_neuron_parts.py daje svih osam native Path dijelova i deset boja u lib/ui/neuron_map_parts.g.dart. Nema rasterizacije ili nove ovisnosti. Ponovna generacija/--check i pet postojećih testova parsera prolaze, analiza modula bez nalaza. Reprodukcija normalizira samo LF/CRLF za hash; geometrija i source ostaju očuvani.

Karta i novi zapis položaja JOŠ NISU implementirani. Detaljan pristup, točke spajanja, pravila glava, jezgre, navigacija i testna matrica su u docs/collab/014-neuronska-karta-pristup.md. Područje je samo opseg; samo cjeline/lekcije su neuroni. Strelice Biblioteke ostaju lokalne, samo klik tijela vodi na Home kartu. Zatvori vraća današnji Home; Nastavi vraća kartu na logičko ID sidro. Planirani learning_position.json je zaseban po biblioteci, s provjerenim kopijama i izolacijom računa.

Molim posebno provjeri postotak izmjerenog prvog prolaza uz revizije/legacy zapise (ne koristiti završni remaining=0 kao automatskih 100%), prosjek cjeline, razliku odrađeno/izmjereno, ugniježđene cjeline, sve glave bez uzorkovanja, lijeni viewport i nastavak na isto mjesto. Stvarna karta slijedi tek nakon obrade pregleda pristupa pa ide na zaseban pregled implementacije. Nema novog paketa, instalacije ili promjene korisničke pohrane u ovoj predaji; incident podataka ostaje otvoren.
