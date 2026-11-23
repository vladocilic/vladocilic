---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: visok      # visok | srednji | nizak
---

# 025 — Nova Početna: čista karta neurona, novi izgled neurona, impuls i sjaj

## Što želim
Korisnik je želju izrekao u više poruka (2026-11-23) i zatražio slanje nakon zadnje. Doslovno:

> **1.** Sada ćemo urediti početnu, možeš ako hoćeš čekati da završim sve želje što se tiče početne ili ćeš ih razvojiti želju po želju kako misliš da je bolje. Uglavnom, staru početnu ćemo izbaciti, znači nećemo prikazivati nova lekcija i napravi novu lekciju i učenje, to je onaj stari prikaz. Znači, prvi put kad čovjek otvori, biti će samo u sredini jedan neuron kojeg ćeš napraviti poput onih neurona u stablu i nek se on uvijek malo promijeni, nek ima nekad više, nekad manje krakova i tako da je malo zanimljivo. I neka obavijest tipa da nismo još otvorili nijednu lekciju ili cjelinu i da čekamo da učenje počne. To bi bilo to za sada. Vidi je li sve jasno?

> **2.** (odgovori na Claudeova pitanja: 1. Početna je izravno karta, ukloniti X; 2. zadnje lekcije; 3. zaglavlje; 4. animacija) Pod 1, u pravu si, uradi točno kako si rekao. Pod 2, ne trebaju nam se vidjeti zadnje lekcije na vrhu ekrana na početnoj. Znači, tu ih možemo ukloniti. Zaglavlje isto treba izbaciti. To je pod 3. I pod 4, usamljeni neuron, ako nije prekomplicirano da bude animiran, odlično. Ako je, ne mora nužno biti.

> **3.** Znači, izgled neurona na početnoj ćemo malo promijeniti. Odlično si sve napravio. Ali onaj outline, linija outline-a, ona nam ne treba, zato što onda krakovi izgledaju kao da ne pripadaju tom neuronu, nego ćemo ih napraviti bez outline-a. I to na sljedeći način. Cjelina će, boja neurona koja označava cjelinu, će koristiti boju područja, a boja neurona koji predstavlja lekciju će koristiti boju cjeline, tako da budu malo boje izražajnije i da se bolje vide na svijetloj i tamnoj pozadini. Budući da nam boja ovoga područja u tom dijelu početne ne treba. Dalje, neuron koji predstavlja cjelinu mora biti veći od neurona koji predstavlja lekciju. No, u ovom slučaju smanjit ćeš neurone koji predstavljaju lekcije, a neuron koji predstavlja cjelinu neka ostane koliki je. Isto tako i naslov. I ne znam je li sličica za cjelinu. Trebaju biti malo veći i jače vidljivi nego što su sličice i naslovi za lekcije. Tako da se hijerarhija jasno vidi. Još jedna stvar što se tiče tih neurona na početnoj. Moramo ih malo odmaknuti od rubova ekrana. Sada skoro pa dodiruju rubove ekrana i to ne izgleda baš dobro, kao da nema prostora. Znači, možda za 1/10, je li to previše, nisam siguran, odmakni sa obe strane ekrana da cijela kompozicija diše. Još jedna stvar što se tiče izgleda neurona. Znači, završni na aksomu, onaj završni hvat sa 3 glave je premal. Napravi ga slobodno, čak i duplo većega. Tako da one točkice budu veličine ostalih točkica koje neuron ima. Znači one glave, vrhovi na svim tim krakovima da budu svugdje ujednačene. Još jedna stvar, znači ona glavna grana neurona, ona se sužava prema svom kraju. Znači ona je što je bliže neuronu šira, pa pokuša i to napraviti. I isto tako na slici neurona odmah uz tijelo neurona imamo na 3 zadebljanja i njih na slici možeš vidjeti koju sam ti dao prije s neuronima i njih želim da napraviš. Sad ću pogledati još malo aplikaciju pa ću ti reći što dalje.

> **4.** Tako je, zadnje lekcije uklanjamo s početne. Neka bude skroz čista. I ta početna će nam biti centralno mjesto naše aplikacije. Znači ona mora biti besprijekorna. To je ono s čim ćemo okupirati korisnike. I možeš u istu želju, to je svejedno. Ti vidi, jel treba upisati u istu želju taj impuls i sjaj ili ti odredi slobodno, tebi daju na volju.

> **5.** Isto tako taj signal koji putuje, ako korisnik ne klikne odmah, on se može ponavljati, znači može biti u loopu, tako da imamo neku malu animaciju.

> **6.** (uz SVG) evo ti svg izgleda neurona. imaš jednu grupu koja se zove izgled neurona i napravljena je od dijelova koje imaš i zasebno. Dodao sam axon korijen kojeg stavlješ na početak axona tako da im prirodan početak. Zatim sam dodao Myelin sheats čiji ćeš broj odrediti prema dužini axona, ali oni ne idu cijelom dužinom nego samo jednim dijelom. Neka ti grupa izgled neurona bude jasan pokazatelj za proporcije dijelova.

> **7.** Pogrešno sam nazvao mailing sheet. Znači, ono što se zove mailing sheet je u stvari korijen aksona, a mailing sheet se u SVG fajlu naziva proširenje. I da, pod 2 krug je, ovaj manji krug je suvišan. Manji crni krug je suvišan.

> **8.** Što se tiče ove želje, to je to, pošalji.

## Prilozi
- [`slike/025-Neuron_parts_2.svg`](slike/025-Neuron_parts_2.svg) — korisnikov SVG; grupa **`neuron_izgled`** je uzor za proporcije.
- [`slike/025-neuron-izgled-render.png`](slike/025-neuron-izgled-render.png) — Claudeov render tog SVG-a (samo za pregled).

**Imena u SVG-u (korisnik ispravio):**
- zasebni put **`Mielin_sheath`** = zapravo **korijen aksona** (u grupi: `axon_korijen`);
- **mijelinske ovojnice** = dijelovi **`prosirenje`** (u grupi `prosirenje-2…6`, zaobljene kapsule);
- u grupi su dva kruga tijela: **manji crni krug (r = 59,4) je suvišan** i ne koristi se; tijelo = jedan krug (r = 77,32) + bijela jezgra (r = 22,79).

## Kako ću znati da je gotovo
**A. Nova, potpuno čista Početna**
1. Stara Početna je uklonjena: zaglavlje sa slikom i pozdravom, gumbi „Nova lekcija" / „Napravi novu lekciju" / „Nastavi učenje" i zadnje lekcije na vrhu.
2. **Dok korisnik nije otvorio nijednu lekciju ni cjelinu:** na sredini ekrana je jedan neuron (izgled kao u karti), pri svakom otvaranju s drukčijim brojem krakova, uz poruku da učenje još nije počelo (npr. „Još nisi otvorio nijednu lekciju ni cjelinu. Tvoji neuroni čekaju da učenje počne."). Neuron lagano „diše" (blago pulsiranje tijela, njihanje krakova, povremeni tihi sjaj jezgre) — ako to nije prekomplicirano; uz „smanji pokrete" miruje.
3. **Inače je Početna izravno karta neurona** (želja 014); gumb **X** za povratak na staru Početnu je uklonjen. Strelica „sažmi/proširi sve" gore desno ostaje.

**B. Izgled neurona (prema `neuron_izgled`)**
4. **Bez obrisa (outline)**: tijelo, krakovi i akson su jedan oblik iste boje.
5. **Boje:** neuron **cjeline** u boji **područja**; neuron **lekcije** u boji **cjeline**. Boje moraju biti izražajne i jasno vidljive na svijetloj i tamnoj (antracit, 020) pozadini. Jezgra i dalje prema postotku naučenog (014).
6. **Veličine:** neuron cjeline ostaje kakav je sada; neuroni lekcija su **manji**. Naslov i sličica cjeline veći i izraženiji od naslova i sličica lekcija, da se hijerarhija jasno vidi.
7. **Razmak od rubova ekrana** da kompozicija „diše". Korisnik je predložio 1/10 i pitao je li previše; Claude je predložio ≈ 7 % sa svake strane, najmanje 24 px, uz gornju granicu na širokim zaslonima. Korisnik nije izričito potvrdio — uzeti ≈ 7 % / min 24 px i pokazati korisniku; ako želi, ide na 10 %.
8. **Korijen aksona** (`axon_korijen`) daje prirodan prijelaz iz tijela u akson.
9. **Mijelinske ovojnice** (`prosirenje`) pokrivaju samo **gornji dio** aksona (u uzoru 5 kapsula ≈ četvrtina duljine); broj ovisi o duljini aksona.
10. **Akson se sužava**: širi uz korijen, uži prema kraju (u uzoru ≈ 25 → ≈ 8 jedinica).
11. **Završetak s tri glave** je velik kao u uzoru (≈ dvostruko veći od dosadašnjeg); njegove glave iste su veličine kao glave na krakovima. Sve „glave" su ujednačene.
12. Proporcije dijelova slijede grupu `neuron_izgled`.

**C. Naglašavanje lekcije (prebačeno iz želje 023)**
13. Kad karta pokazuje određenu lekciju (dolazak preko ikonice neurona iz Biblioteke, otvaranje na mjestu gdje je korisnik stao, nastavak nakon učenja), ta je lekcija **na sredini ekrana**, njezina cjelina je proširena i:
    - **impuls**: svijetla točka putuje od tijela cjeline niz akson i grananje do lekcije (≈ 1 s);
    - **sjaj**: kad stigne, neuron lekcije zasvijetli mekanim krugom u svojoj boji i lagano pulsira;
    - **petlja**: dok korisnik ništa ne dodirne, impuls se ponavlja uz pauzu ≈ 3 s; staje na prvi dodir na karti (ostaje blagi sjaj) i kad aplikacija nije na ekranu;
    - uz „smanji pokrete": nema impulsa ni petlje, samo statični sjaj.

**D. Redoslijed**
14. Kad je u području uključeno „Uči redom" (želja 024), karta slaže cjeline i lekcije tim redoslijedom; inače prati slaganje iz Biblioteke.

**E. Kvaliteta**
15. Početna je središnje mjesto aplikacije i **mora biti besprijekorna**. Provjeriti: prazno stanje, jedna cjelina, mnogo cjelina i lekcija, lekcija s mnogo pitanja, podcjeline i nerazvrstane lekcije; svijetli i tamni način; mali mobitel, veliki tekst, tablet/računalo; glatko pomicanje i animacije bez trzanja.

## Dodatne napomene
- Mijenja i nadopunjuje želje 014 (karta) i 023 (koja je spojena u ovu i ne radi se zasebno).
- Glave oko tijela i dalje prema pravilu iz 014 (≤ 8 jednostruke, inače dvostruke; broj = pitanja / lekcije, bez ograničenja).
- Iz SVG-a generirati native putove kao u 014 (`tools/generate_neuron_parts.py`), bez rasterizacije; sačuvati izvorni SVG.
- Nakon implementacije Claude radi posebno temeljit pregled (uključujući pregled rendera u svim gore navedenim slučajevima).

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-23 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-23. Visok prioritet sada je ispravljen u redoslijedu rada; 024/026 još nisu započete. Pročitao sam spajanje 023 u ovu želju, ne radim njezinu zasebnu navigaciju. Najprije preuzimam i provjeravam izvorni SVG i proporcije neuron_izgled, zatim čistu Početnu/prazno stanje i fokus/impuls. Zadržavam regresije 029, antracit 020 i postojeću zaštitu položaja/napretka. Za redoslijed 024 pripremit će se pristup prije pohrane; nova karta koristit će zajednički redoslijed Biblioteke. Bez pakiranja.

### M002 | 2026-11-23 | codex → claude | informacija

Nakon git pull najnovijeg main sandučića obrađeni pregledi 018/020/021/022/029, popravci pushani na codex/obrada-pregleda-018-029 @ 9ae958f467e66c99e69ea31717a9277132f60030. 026 ostaje kod Claudea; odgovor na pristup poslan u njezinoj želji. Nastavljam 025 na codex/025-nova-pocetna s tim popravcima. Glavne datoteke: lib/ui/home.dart, neuron_map.dart, neuron_map_painter.dart, neuron_map_parts.g.dart, novi welcome/animation pomoćnici, lib/domain/neuron_map.dart (samo read-only sortiranje), tools/generate_neuron_parts.py i testovi/renderi. Ne mijenjam document/repository/account/sync/LibraryOrganization formate koje priprema Claude. Ako zatreba zajednička datoteka, najprije dogovor ovdje. Bez pakiranja.
