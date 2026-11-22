---
status: nova          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 014 — Početna: neuronska karta napretka područja i cjelina

## Što želim
Korisnik je želju izrekao u dvije poruke (2026-11-22) uz tri slike i SVG datoteku, i zatražio slanje nakon druge poruke. Doslovno:

> **1.** Dakle, za sljedeću želju želim da upotrebiš ove tri slike i SVG dokument i da napravimo na početnoj da se prikazuje progres određenog područja ili cjeline. Znači, na slici neuron -02 imamo prikaz kako izgledaju zatvorene cjeline. Na slici neuron 01 imamo kako izgleda kada se jedna cjelina otvori i u njoj vidimo na prvom mjestu lekciju koja je već odrađena i spojena je na ovaj neuron i imamo dole lekcije koje nisu odrađene ni jednom i nisu spojene. Ono što ćemo napraviti je da kada netko u biblioteci tapne na ikonu područja ili cjeline, automatski ga bacamo u početnu sekciju gdje on se automatski nađe točno na tom mjestu koje je izabrao. Isto tako, početna će nam se uvijek otvarati na onom mjestu gdje je čovjek stao sa učenjem. Na otvorenoj cjelini i da on vidi tu lekciju koju je zadnju radio. U SVG failu sam napravio dijelove koje ćeš koristiti za izradu ovih neurona. Neuroni će biti boje, zavisi ako prikazuju cjelinu, bit će onda boje cjeline, a ako prikazuju lekciju, bit će boje lekcije. Jezgre tih neurona će biti obojane prema bojama koje se nalaze u SVG failu na dnu. S tim da će lijeva boja, tamno plava, predstavljati 10% naučenog znanja, a crvena na desnoj strani 100% naučenog znanja. Što znači, ako korisnik prolazi kroz lekciju i na kraju je odgovorio lekciju sa svim točnim odgovorima, jezgra će biti crvena. Znači, boja jezgre će ovisiti o postotku koliko je naučio tu lekciju. Ono što je bitno za izradu oko tijela neurona sa njegovim glavama, kako sam ih ja nazvao, je da koristiš dvije glave i jednu glavu prema potrebi na način da ako je u lekciji 20 pitanja, onda će to biti 10 glava, 10 dijelova koji sadrže dvije glave. A ako lekcija recimo sadrži 5 pitanja, onda ćemo koristiti 5 sa jednom glavom. Dakle, što je manje pitanja u lekciji, a isto tako što je manje lekcija u cjelini, koristit ćemo više dijelova sa jednom glavom, a što ih je više, koristit ćemo ove sa dvije. Možeš ih kombinirati tako da neuroni uvijek izgledaju malo različito. Otvaranje i zatvaranje neurona, točnije sažimanje i proširivanje, se događa tako što kliknemo na cjelinu i ona se proširi. I ako kliknemo drugi put, ona će se sažeti. A lekcije pokrećemo isto tako klikom na lekciju. Jesi li razumio?

> **2.** Još samo ova stvar, negdje na početnoj kada su otvorene na ovaj način lekcije i cjeline, mora biti gore desno gumbić da izađemo iz tog prozora i da se vratimo u trenutni izgled početne stranice gdje vidimo gumbe za izradu lekcije i za nastavak učenja. A ako kliknemo nastavi učiti, ulazimo opet nazad tamo gdje smo stali. Sada možeš poslati ovu želju.

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

**Boje i oblik**
- Tijelo neurona cjeline je u boji cjeline, a tijelo neurona lekcije u boji lekcije.
- Jezgra je obojena prema postotku naučenog, ljestvicom iz SVG-a: krajnja lijeva tamnoplava = 10 %, krajnja desna crvena = 100 % (lekcija riješena sa svim točnim odgovorima ima crvenu jezgru).
- Broj „glava" oko tijela: kod lekcije odgovara broju pitanja, kod cjeline broju lekcija (npr. 20 pitanja → 10 dijelova s dvije glave; 5 pitanja → 5 dijelova s jednom glavom). Što je manje pitanja/lekcija, više je dijelova s jednom glavom; što je više, više s dvije. Dijelovi se kombiniraju tako da neuroni izgledaju malo različito.

**Navigacija**
- Tap na područje ili cjelinu u Biblioteci prebacuje u Početnu, točno na to područje/cjelinu.
- Neuronski prikaz otvara se na mjestu gdje je korisnik stao: otvorena cjelina s vidljivom zadnjom lekcijom.
- Gore desno u neuronskom prikazu je gumb koji ga zatvara i vraća sadašnji izgled Početne (gumbi za izradu lekcije i nastavak učenja).
- Gumb „Nastavi učenje" na Početnoj vraća u neuronski prikaz, na mjesto gdje je korisnik stao.

## Dodatne napomene
Otvorena pitanja (Claude ih je postavio; korisnik je zatražio slanje bez odgovora na njih — pitaj ga prije izvedbe dijela koji o njima ovisi):
1. **Dva lika na crti** (muškarac i žena na slikama): što predstavljaju — mjesto za sliku cjeline/lekcije, članove grupe ili nešto drugo?
2. **Područje:** kako izgleda u neuronskom prikazu? Je li „neuron 02" prikaz jednog područja s njegovim cjelinama, i kako se prikazuje više područja?
3. **Jezgra ispod 10 %** (neodrađena lekcija): bijela kao `jezgra` u SVG-u?
4. **Jezgra cjeline:** prosjek naučenosti njenih lekcija?
5. **Mnogo pitanja:** gornja granica broja dijelova oko tijela (npr. lekcija sa 60 pitanja)?

Napomene (Claude):
- Ljestvica ima 10 boja; preslikavanje je pretpostavljeno kao 10 %, 20 %, … 100 % po jednoj boji. Uskladiti s načinom na koji aplikacija već računa naučenost (Napredak, „povezani/probuđeni neuroni").
- Povezano sa željama 004/009 (ponašanje Biblioteke na tap) i 008/010 (boje u Napretku). Tap na područje/cjelinu u Biblioteci danas otvara mapu u Biblioteci; ova želja to mijenja u skok na Početnu — paziti da se ne izgubi pristup sadržaju mape u Biblioteci (npr. preko strelica proširivanja).
- „Zadnje mjesto učenja" vjerojatno treba spremati; ako je to novi spremljeni podatak, vrijedi `AGENTS.md` aplikacije i neovisni pregled.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta
