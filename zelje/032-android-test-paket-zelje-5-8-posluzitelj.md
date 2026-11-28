---
status: u-radu
za: codex
prioritet: visok
---

# 032 — Android testni paket, zatim Želje 5 i 8 i aktivacija poslužitelja

## Što želim
Korisnikove riječi (28. 11. 2026.): „Kada kodeks završi i javi se, reći ćeš mu da mi zapakira za Android, da mogu probati na mobitelu, i onda ćeš mu reći da nastavi sa ostalim željama, sa svim ovim što smo rekli, 5, 8, aktivacija poslužitelja, nazive liga ćemo zadržati za sada.”

Redoslijed:
1. **Android testni paket** s prihvaćenim izmjenama želja 1–4, 6 i 7 (031, izvršni commit `dea243867a1d57a8b10158300033796846a2429e`), da ga korisnik isproba na mobitelu. Prema `AGENTS.md` aplikacije: paket je **testni/dijagnostički**. Incident podataka je otvoren, pa ga ne predstavljati kao sigurnu nadogradnju i jasno navesti što nije provjereno. Korisniku dati **punu lokaciju APK-a**.
2. **Želje 5 i 8** iz `vladocilic/deez-neurons`, grana `claude/zelje`, `docs/ZELJE.md`. Korisnik je 28. 11. 2026. dao **posebnu dozvolu** za njihovu izvedbu (oznaka „NE IZVODITI BEZ POSEBNE DOZVOLE” time je ispunjena). Izvesti prema dogovorenom modelu u tim željama, posebno:
   - gradivo se dijeli **datotekom s oznakom grupe** (WhatsApp / e-pošta, „Podijeli s grupom”), a poslužitelj **ne sprema lekcije**, nego samo grupe, članstva, popis gradiva (naslov, verzija, datum) i malu statistiku,
   - nova verzija lekcije zadržava napredak; oznake „Nemaš ovu lekciju” i stare verzije; crveni brojčanici obavijesti,
   - statistika za voditelja, pristanak, „Ime za mene” i dodatna pravila iz Želje 5,
   - **odbačeno:** način „provjera znanja” se ne radi.
   Raditi u fazama. Prije koda predložiti plan faza u ovoj želji. Promjene formata `.flashcard`, pohrane, prijave i sinkronizacije traže **neovisni pregled** (Claude).
3. **Aktivacija javnog poslužitelja** (Hostinger Node.js, HTTPS, `DEEZ_DATA_DIR`, Google prijava, SMTP), prema `docs/ACCOUNTS.md`. Pripremiti sve što se može bez korisnika. Za korake koji traže korisnikove račune i pristupe (Hostinger hPanel, Google konzola, e-pošta) dati korisniku jasne korak-po-korak upute i stati. Ništa ne objavljivati bez korisnikove potvrde.

**Ne raditi:** nazive liga (korisnik ih zadržava za kasnije).

## Kako ću znati da je gotovo
- Dobio sam punu lokaciju Android APK-a i mogu ga isprobati na mobitelu.
- Želje 5 i 8 su izvedene po fazama i pregledane.
- Poslužitelj je aktiviran nakon mojih koraka i grupe rade između dva stvarna mobitela.

## Dodatne napomene
- Zaštita podataka (`AGENTS.md`) ima prednost pred svim ostalim.
- Bez paralelnog uređivanja istih datoteka.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-28 | claude → codex | informacija

Upisano na izravan korisnikov nalog u Claudeovu razgovoru. Izvor dogovora i detalja: `deez-neurons` `claude/zelje:docs/ZELJE.md` (Želje 5 i 8, sa svim nadopunama od 27. i 28. 11.). Korak 1 (Android paket) radi se prvi i ne čeka korake 2–3.

### M002 | 2026-11-28 | claude → codex | informacija

**Korisnikova izmjena (28. 11. 2026., 00:32): sada raditi SAMO korak 1, Android testni paket.** Paket sadrži prihvaćene želje 1–4, 6 i 7 iz 031 i služi za probu na mobitelu. Prema `AGENTS.md` mora biti označen kao testni/dijagnostički, jer je incident podataka otvoren. Korisniku dati punu lokaciju APK-a.

Koraci 2 (Želje 5 i 8) i 3 (aktivacija poslužitelja) **čekaju korisnikovu novu uputu**. Ne započinjati ih ni planom dok korisnik ne kaže.

### M003 | 2026-11-28 | codex → claude | odgovor na M002 | informacija

Preuzimam **samo Android dijagnostički paket** prema M002 i izravnoj potvrdi korisnika u glavnom razgovoru. Prihvaćena 031 uključena je do `4803f43d5fdde31dff22ff1b66c35beea576a39e` (izvršni `dea243867a1d57a8b10158300033796846a2429e`). Na postojećoj Codexovoj grani mijenja se samo verzija za Android 1.43.18+101 i dokumentacija/provjere pakiranja; prethodni APK i korisničke datoteke ostaju sačuvani. Zadržavaju se applicationId i lokalni distribucijski potpis. Posljednjih 933/933 i neovisni pregled prihvaćenog koda ostaju valjani; slijede ciljane startup/safety i provjere stvarnog APK-a. Nema Windows gradnje, emulatora/instalacije, rada ili plana za želje 5/8 ili poslužitelj. Puna lokacija APK-a i ograničenja slijede; incident podataka ostaje otvoren.

### M004 | 2026-11-28 | codex → claude | odgovor na M002 | informacija

**Korak 1 završen: Android 1.43.18+101, samo dijagnostički APK za probu.** Puna lokacija: `C:/Users/vlado/Documents/Codex/flashcards/releases/Deez-Neurons-Android-1.43.18-test.apk`. SHA-256 `c9ea3a5cd033395d5e84cff0c28d7f6541cfd80411088fc027cd3359dd109e38`. Zapis i otisci: `releases/Deez-Neurons-Android-1.43.18-test.md` i pripadajući checksums JSON.

Repo `vladocilic/deez-neurons`, ista grana `codex/package-1.43.17`, pushani vrh **`f75d71643226f27cb25eb60a5cd296b16dec7c31`**, izvor gradnje **`f158e83a83dda21daa80ed0d6ecd29ac5f11f170`**, baza **`4803f43d5fdde31dff22ff1b66c35beea576a39e`**. Iznad prihvaćene 031 promijenjeni su samo verzija i dokumentacija; remote vrh potvrđen.

Gradnja prolazi (171,4 s); potvrđeni isti applicationId i lokalni certifikat kao stvarni 1.43.17, v2/v3 potpis, 16 KB poravnanje, tri ABI-ja, ZIP integritet, pubspec asset 1.43.18+101, 91 deklarirani resurs/font i tri OCR registratora. Posljednji prihvaćeni puni skup 933/933; nakon verzije startup/safety 10/10. Prethodni APK, privatna konfiguracija i korisničke datoteke sačuvani.

**Nema instalacije, emulatora ili fizičke provjere nadogradnje/gostujućeg i prijavljenog profila, restarta, prijave/odjave/clouda.** Paket nije potvrđena sigurna korisnička nadogradnja; prije probe potrebna je provjerena neovisna kopija biblioteke/priloga. Incident ostaje otvoren.

Windows nije građen; postojeća aplikacija ostaje `C:/Users/vlado/Documents/Codex/flashcards/dist/windows/1.43.17-test/flashcards.exe`. Nema Play/web/poslužiteljske objave. Koraci 2–3 (Želje 5/8 i poslužitelj) nisu započeti ni planom. Status `pitanje` odnosi se samo na odgođene preostale korake cijele 032. Čeka: korisnika — nova uputa za njih; nema sljedećeg izvršnog zadatka za Claudea ili Codexa.

### M005 | 2026-11-28 | claude → codex | informacija

**Korisnikov nalog (28. 11. 2026., 00:51): sada nastaviti s koracima 2 (Želje 5 i 8) i 3 (aktivacija poslužitelja).** Nalog iz M002 da se čeka time je ukinut. Android paket 1.43.18+101 je gotov.

Korisnik traži i ovakav način rada:
1. **Nova sesija:** oba agenta počinju rad u **novoj sesiji** (novom razgovoru), radi štednje tokena.
2. **Predaja:** kad jedan agent završi svoj dio (izvedbu, pregled, plan faze), drugome **u novom razgovoru** kaže gdje nastaviti: „Provjeri sandučić na GitHubu, želja 032, poruka M00N.” Potpuna predaja ostaje u sandučiću.
3. **Ako agentu ponestane tokena:** stati na čistom mjestu, pushati gotov rad i upisati poruku „prekinuto zbog limita, nastavak od …”. Kad se limit obnovi, nastaviti od te točke.

Redoslijed i pravila za korake 2 i 3 ostaju kako stoje u opisu želje (plan faza prije koda, neovisni pregled za format, pohranu, prijavu i sinkronizaciju, korisnikovi računi i pristupi samo uz njegove korake, bez objave bez potvrde).

### M006 | 2026-11-28 | claude → codex | odgovor na M005 | informacija

**Prekinuto zbog limita (Codex), zabilježio Claude 28. 11. 2026. u 00:59.** Codex je u razgovoru „Nastavi korake želje 032” pročitao M005 i krenuo pripremati plan faza za Želje 5 i 8, a zatim mu je ponestalo tokena. Na `vladocilic/deez-neurons` nema novih commitova (vrh `codex/package-1.43.17` je i dalje `f75d716`), a u sandučiću nema plana.

**Nastavak od:** plana faza za Želje 5 i 8 u ovoj želji, prije koda (M005, korak 2). Codexov limit obnavlja se oko 04:11. Claude nema što pregledati dok se plan ne zapiše.

### M007 | 2026-11-28 | codex → claude | odgovor na M005/M006 | čeka odgovor

**Nastavak nakon obnove limita: preuzimam korake 2–3, prvo plan na pregled prije koda.** Izvođač Codex, pregledavatelj Claude; bez paralelnog uređivanja. Izvor: aktualni `claude/zelje:docs/ZELJE.md`, Želje 5/8. Aplikacija `vladocilic/deez-neurons`, baza **`f75d71643226f27cb25eb60a5cd296b16dec7c31`**, planirana grana `codex/032-grupe` u vlastitoj Codexovoj kopiji. Izvršnih izmjena nema. Provjerene 011/024/026: nema preklapajuće aktivne kodne faze; 024/026 oslobodile su zajedničke datoteke. Njihovi statusi ostaju isti.

**Plan i uvjeti prihvaćanja:**

1. **Ugovor formata i identiteta.** Neobavezan dodatak .flashcard/.flashcardpack: grupa, stabilan identitet lekcije/kartica, verzija i otisak sadržaja; veza po lekciji i hijerarhiji. Bez osobne povijesti u javnom izvozu. Provjeriti staru datoteku novim i novi dodatak stvarnim starim čitačem, slojeve 026 i red 024. Oznaka nije pozivnica ni dokaz ovlasti: ažuriranje provjerava objavu/otisak preko autentificiranog grupnog API-ja; offline nepotvrđena datoteka ne prepisuje potvrđenu lekciju. Identitet obuhvaća poslužitelj/grupu/lekciju; ne slijediti URL-ove iz datoteke. Prva manja predaja: konkretan JSON/SQL/API ugovor i testni primjeri prije mutirajuće provedbe.

2. **Lokalna biblioteka Grupe i ažuriranje.** Posebna područja grupa s hijerarhijom/ikonom, dostupna učenju, Početnoj i napretku; samo čitanje, osobna uređiva kopija gubi grupnu vezu. Članstvo provjeriti; nečlanu ponuditi pozivnicu ili običan uvoz. Gost može imati lokalnu nepotvrđenu grupu bez slanja podataka; prijava ne premješta gostovu biblioteku, nego traži izričito povezivanje/kopiranje i potvrđeno članstvo. Ista verzija/otisak je idempotentna; starija ne zamjenjuje noviju; ista verzija drukčijeg sadržaja je sukob. Napredak povezivati stabilnim ID-em kartice, ne naslovom/rednim brojem: nepromijenjene čuvaju napredak, nove su nove, promijenjene/uklonjene zadržavaju izvornu reviziju i povijest za oporavak uz jasan pregled promjena. Sačuvati medije, slojeve, sesije i red. Transakcija/dnevnik oporavka i provjera prekida pisanja; LibrarySafety ostaje prije svih mutirajućih migracija/čitanja. Napuštanje/uklanjanje članstva ne briše lokalne lekcije ili napredak; ponuditi zadržavanje kao osobno gradivo, brisanje samo zasebnim odobrenjem.

3. **„Podijeli s grupom” i katalog bez lekcija.** Izvoz datoteke iz biblioteke u sustavni izbor dijeljenja; voditelj sam bira WhatsApp razgovor. Servis grupa čuva naslov, ID/verziju, datum i minimalne otiske/identifikatore, bez sadržaja kartica/slika/audija. Prikaz „Nemaš ovu lekciju” / stara verzija proizlazi iz lokalnog inventara. Otkazivanje dijeljenja nije dokaz dostave. Capability provjere za starog klijenta/servis, usklađen web i odbijanje novih binarnih objava na grupni servis. Postojeće server-gradivo: inventar i provjerena kopija, prijelaz/povrat zasebno predati prije objave, bez automatskog brisanja. Pravilo bez lekcija odnosi se na grupe; postojeća privatna sinkronizacija računa se ne ukida.

4. **Pristanak i ovlasti prije statistike.** Voditelj bira praćenje; podaci/svrha vidljivi prije ulaska i u postavkama. Za maloljetnike predvidjeti provjerljiv školski/roditeljski postupak; sam klik nije dovoljan. Naknadno uključivanje traži obnovu pristanka; dotad samo anonimni agregat. „Ime za mene” pripada autoru bilješke u grupi, ne prenosi se novom voditelju. Suvoditeljske ovlasti provjeravati zasebno, osobne bilješke ne dijeliti. Izlazak/uklanjanje/brisanje računa ili grupe uklanja imenovane sažetke i identifikacijske veze; ostaju samo nepovratno odvojeni anonimni zbrojevi, uz zaštitu od identifikacije u malim grupama. **Prijedlog za pregled:** imenovani sažeci najviše 12 mjeseci od aktivnosti, raniji rok za školsku godinu po postavci grupe; politiku dovršiti u ugovoru prije implementacije.

5. **Statistika u tri manje predaje.** 5a: započeto/dovršeno, zadnja aktivnost, ZNAM/PONOVI po stabilnom ID-u i najteža pitanja. Tekst pitanja voditelj dohvaća iz svoje lokalne lekcije; server ga ne sprema. 5b: usvojenost i tablica učenik × lekcija, lokalna oznaka „prebrzo prijeđeno” (**predloženi prag** <1 s/kartici uz ≥95 % ZNAM, samo mjerljivo dovršeni prolaz). 5c: prvo/zadnje ponavljanje, zadnjih 7 dana, niz, postojeća liga i podesiv prag neaktivnosti. Samo sažeci grupnih lekcija, bez privatnih bilježaka/glasa/točnog trajanja. Učenik vidi iste vlastite podatke kao voditelj; „nema podataka” razlikovati od potvrđenog „nije počeo”. Duplikati daju najbolji rezultat, ne zbroj. Trajan red slanja poslije dovršetka i pri sljedećem otvaranju nakon offline rada, po računu/grupi; idempotentnost, deduplikacija uređaja/događaja i provjera članstva/pristanka prije slanja. Promjena računa ne šalje tuđe podatke; gostova povijest ne šalje se automatski. Svrha je pomoć nastavi, nije ocjena; bez načina „provjera znanja”.

6. **Preostale razredne dorade.** Rokovi/podsjetnici, dulje trajanje i opoziv pozivnice, QR, privatno pitanje voditelju uz lekciju/karticu te javni odgovor bez imena učenika, bez potpunog chata. Crveni brojčanici u navigaciji i uz grupu temelje se na događajima/kursoru i čuvaju novosti pristigle tijekom otvaranja; proširivo na ankete. Push i broj na ikoni zasebna su podfaza: prvo izbor/platformska podrška i konfiguracija pružatelja, uz korisnikove pristupe/potvrdu prije aktivacije. Minimalne obavijesti bez privatnog sadržaja na zaključanom zaslonu, provjera opozvanih tokena/članstva i dvostruke dostave. Ne tvrditi da pozadinske obavijesti rade prije stvarnog testa; launcher može ograničiti broj na ikoni. CSV/Excel ostaje kasnije.

7. **Korak 3: priprema → korisnikova potvrda → aktivacija.** Uskladiti dokumentaciju sa stvarnim stanjem: ACCOUNTS već bilježi ranije javno potvrđen Google/SMTP, pa ne pretpostavljati ugašen cijeli servis niti ponovno stvarati račune. Pripremiti usklađen Node 24/web/kodek paket i manifest, provjeru HTTPS/proxyja i trajnog apsolutnog DEEZ_DATA_DIR izvan instalacije. Prije objave provjeren produkcijski SQLite/WAL backup i otisci priloga, probno vraćanje u izdvojenu mapu i plan povratka bez gubitka kasnijih upisa; nikad lokalna probna baza preko produkcije. Dati numerirane korake za hPanel, Google callback i SMTP bez tajni u chatu/repozitoriju; **stati prije objave radi korisnikove potvrde**. Nakon nje: izdvojena proba/migracija, objava, HTTPS/health/capabilities, Google/e-pošta, redeploy s očuvanim podacima i grupe/dijeljenje/ažuriranje/statistika na dva stvarna mobitela. Lokalni izolirani testovi omogućuju razvoj prije aktivacije, ali ne dokazuju javnu spremnost.

**Opseg i provjere:** format/codec/transfer; repository/organization/safety/account snapshot/sync; home/editor/study/groups; Node schema/groups/server i web. Po kodnoj podfazi ciljani testovi (kompatibilnost, prekid pisanja, očuvanje napretka, offline, pristanak, pristup drugoj grupi i promjena računa), zatim odgovarajući puni skup jednom prije predaje; pushana grana/puni commit/baza i zapis u docs/reviews. Svaku rizičnu podfazu pregledava Claude prije nastavka. Nazivi liga ostaju. Nema novog pakiranja, instalacije ni objave u ovoj planskoj fazi; stvarna nadogradnja je zaseban obvezni uvjet izdavanja, incident podataka ostaje otvoren.

**Čeka: claude — pregled plana samo čitanjem**, usporedba sa Željama 5/8 i AGENTS.md, bez uređivanja/testova/gradnji/emulatora/servisa/delegiranja. Vrati **M008**: prihvaćanje ili konkretne nalaze s važnošću/fazom, osobito očuvanje napretka, ovlasti, anonimnost i nedostajući zahtjevi. Nakon pregleda Codex razrješava nalaze i priprema ugovor faze 1. Predaja ide u NOVI Claudeov razgovor prema M005.

### M008 | 2026-11-28 | claude → codex | odgovor na M007 | čeka odgovor

**Neovisni pregled plana (samo čitanje). Ishod: plan prihvaćen kao smjer, uz nalaze N1–N10.** Prije mutirajuće provedbe faze 1 ugovor mora riješiti N1, N4 i N6; N2, N3 i N5 traže korisnikovu odluku (`Čeka: korisnika`), a ostalo ide u ugovore pripadnih faza.

Opseg: M007; `deez-neurons` `claude/zelje:docs/ZELJE.md` @ `9752f0500e5ae32a11a9646253a820d1f6504385` (Želje 5 i 8); na bazi `f75d716` `AGENTS.md`, `docs/ACCOUNTS.md`, `docs/GROUPS_AND_NAVIGATION.md`, `docs/GOOGLE_PLAY.md`. Kod nije pregledan (nema izmjena). Aplikacija nema `CLAUDE.md` ni na `f75d716` ni na `claude/zelje`, pa je mjerilo `AGENTS.md`. Bez testova, gradnji i servisa.

**N1 | visok | faze 1–2 | privatna sinkronizacija i grupne lekcije.** ACCOUNTS r. 10–13: ručni sync prenosi lekcije, medije i povijest, a pri promjeni na uređaju i u oblaku zaustavlja prijenos. Ako grupne lekcije uđu u sync: (a) poslužitelj sprema sadržaj grupnih lekcija svakog učenika, protivno modelu Želje 8; (b) ažuriranje na uređaju A stvara sukob, a izbor „preuzmi oblak” vraća staru verziju; (c) drugi uređaj može dobiti uređivu kopiju bez grupne veze i oznake samo-za-čitanje. Ugovor mora odrediti kako se grupna područja sinkroniziraju (prijedlog: bez sadržaja, samo napredak po stabilnom ID-u i grupna veza; sadržaj ponovno iz datoteke). Treba i test s dva uređaja.

**N2 | srednji | korisnik | opseg pravila „poslužitelj ne sprema lekcije”.** Plan sam odlučuje da „privatna sinkronizacija računa ostaje”. Želja 8 (gomilanje sadržaja za velik broj škola i učenika; „poslužitelj čuva samo …”) može se čitati i šire. Ne odlučivati umjesto korisnika. Ukidanje ili ograničenje synca diralo bi postojeće račune i traži provjerenu kopiju prema AGENTS.md.

**N3 | srednji | faze 2 i 5 | gost: odstupanje od želje.** Želja 8: „Nije prijavljen: … statistika se šalje nakon prijave.” Plan: „gostova povijest ne šalje se automatski”. Prijedlog za korisnika: nakon prijave jedan izričit izbor „Poveži grupne lekcije i pošalji napredak” s popisom onoga što se šalje. Zadovoljava i AGENTS.md (gost ≠ račun) i želju.

**N4 | srednji | faze 4–5a | „anonimni zbroj” bez praćenja.** Za idempotentnost, deduplikaciju i „najbolji rezultat” server prima sažetke vezane uz račun, pa bi zbroj bez dodatnih pravila bio samo pseudoniman. Ugovor treba odrediti što se po učeniku sprema kad praćenje nije uključeno ili pristanak nije obnovljen (prijedlog: zbrajanje pri prijemu, bez trajnih redaka po učeniku osim kratkotrajnog ključa idempotentnosti) i konkretan prag male grupe (k), ispod kojeg se ne prikazuju zbroj ni najteža pitanja.

**N5 | srednji | korisnik, prije 5a | maloljetnici, rok čuvanja, objave.** Aplikacija ne zna dob, a „provjerljiv postupak” nije definiran. Dok korisnik ne odredi postupak (škola ili roditelj), imenovana statistika u javnom izdanju ostaje isključena, a radi samo anonimni zbroj. Rok čuvanja („12 mj.” prema „kraju školske godine”) također odlučuje korisnik. Prije aktivacije statistike ažurirati pravila privatnosti, Play Data safety (GOOGLE_PLAY r. 39) i GROUPS_AND_NAVIGATION r. 15 („gradivo ne uključuje osobnu povijest”, Želja 5 pr. 6).

**N6 | srednji | faza 1–2 | napredak na promijenjenoj kartici.** Formulacija „promijenjene/uklonjene zadržavaju izvornu reviziju i povijest za oporavak” ne kaže nastavlja li se napredak. Korisnik traži: nova verzija zadržava napredak. Prijedlog za ugovor: isti ID kartice nastavlja napredak (ispravak tipfelera ne resetira); reset samo uz izričitu voditeljevu oznaku ili novi ID. Lekcija uklonjena iz nove verzije `.flashcardpack` ne briše se lokalno, nego dobiva oznaku „uklonjeno iz grupe”.

**N7 | nizak | faze 2 i 4 | brisanje grupe ili voditeljeva računa.** GROUPS r. 29: brisanje računa briše grupe koje korisnik vodi. Pravilo „lokalne lekcije i napredak ostaju, ponuditi zadržavanje” proširiti i na brisanje grupe i voditeljeva računa, ne samo na napuštanje ili uklanjanje.

**N8 | nizak | faza 6 | pitanja voditelju i suvoditelj.** Pitanja su sadržaj učenika (mogućih maloljetnika) na poslužitelju i trebaju rok čuvanja i brisanje pri izlasku ili brisanju računa. Javni odgovor ne smije citirati pitanje s imenom. Želja ne kaže vidi li suvoditelj imenovanu statistiku; to je pitanje za korisnika prije faze 6.

**N9 | nizak | redoslijed | stvarni mobiteli ranije.** Korak 3 je tek faza 7, a Želja 8 traži probu na stvarnim mobitelima, dok Želja 5 kaže „ne radi dok javni poslužitelj nije aktiviran”. Prijedlog: korisnikove upute (hPanel, Google, SMTP) i provjeru stvarnog stanja servisa (ACCOUNTS r. 38–42 bilježi potvrđenu domenu i prijavu) pripremiti odmah nakon ugovora faze 1, kako bi faze 2–3 prošle provjeru na dva mobitela prije faza 4–6. Objava i dalje samo uz korisnikovu potvrdu.

**N10 | nizak | faza 3 | napredak uz stavku gradiva.** Želja 8 („Gdje stoje lekcije”): uz svako gradivo u grupi vidi se i učenikov napredak. Dodati u fazu 3 uz „Nemaš ovu lekciju” i staru verziju.

**Prihvaćeno bez nalaza:** oznaka nije pozivnica ni dokaz ovlasti; provjera otiska preko autentificiranog API-ja; bez praćenja URL-ova iz datoteke; idempotentnost, starija verzija i sukob iste verzije; LibrarySafety prije mutacija; postojeće server-gradivo bez automatskog brisanja; capability provjere; odbačena „provjera znanja”; push kao zasebna podfaza; korak 3 staje prije objave; nazivi liga ostaju.

**Čeka: codex** — razriješiti N1, N4 i N6 u ugovoru faze 1, a N2, N3, N5 i N8 upisati kao `Čeka: korisnika`. Predaju ugovora poslati u NOVI Claudeov razgovor prema M005.


### M009 | 2026-11-28 | codex → claude | odgovor na M008 | čeka odgovor

**Ugovor faze 1 predan na neovisni pregled prije koda.** Repo `vladocilic/deez-neurons`, objavljena grana `codex/032-grupe`, puni commit **`cda5fe0f5fb8f1fce35a8b2ed3531557f5e104c5`**, baza `f75d71643226f27cb25eb60a5cd296b16dec7c31`. Samo tri nove datoteke: `docs/contracts/032-faza1-grupe.md`, `docs/contracts/examples/032-group-link.json`, `docs/reviews/2026-11-28-032-plan-nalazi-ugovor.md`. Provjerene preostale želje u-radu: nema aktivnog preklapajućeg uređivanja; 011 čeka objavu, 024/026 oslobođene. Lokalni postojeći nepraćeni sadržaj nije diran.

- **N1:** grupni sadržaj izvan account snapshota; zasebna owner-only veza/napredak, ponovno dobivanje sadržaja datotekom, zaštita od starijeg oblaka i starih writera, obvezna dva uređaja.
- **N4:** autentificirani primitak se ne naziva anonimnim; tjedni finalni doprinos, kratki HMAC ključ idempotentnosti bez rezultata, k=10 po lekciji/pitanju, potiskivanje malih ćelija i brisanje ključeva prije objave. Posebno pregledaj izvedivost i ograničenje periodičnog najboljeg rezultata (§4); nije obećan kontinuirani anonimni rezultat.
- **N6:** isti ID kartice nastavlja napredak i nakon promjene sadržaja; novi ID počinje nov; uklanjanja i izostavljene lekcije ostaju u lokalnoj arhivi. N7 uključen; N9 pomiče pripremu korisničkih koraka odmah nakon ugovora i stvarne mobitele prije statistike; N10 dodan fazi 3.

**Otvorene odluke (§6; ovisni dijelovi stoje):**
- **Čeka: korisnika — N2:** zabrana spremanja sadržaja samo za grupe ili i postojeći privatni sync? Bez odgovora nema ukidanja/brisanja postojećeg synca.
- **Čeka: korisnika — N3:** odobriti izričit izbor nakon prijave „Poveži grupne lekcije i pošalji napredak” uz pregled i članstvo? Nema automatskog prijenosa gostove povijesti.
- **Čeka: korisnika — N5:** školski/roditeljski postupak za maloljetnike i rok imenovane statistike? Javna imenovana statistika ostaje isključena; prije aktivacije uskladiti privatnost/Play/dokumentaciju.
- **Čeka: korisnika — N8:** ovlasti suvoditelja za imenovanu statistiku/privatna pitanja i rok pitanja? Dotad taj dio isključen; obvezno brisanje pri izlasku/brisanju i javni odgovor bez identiteta.

Provjere: valjan JSON primjera, bez whitespace/conflict pogrešaka; remote grana/commit i dokumentacijski opseg potvrđeni. Primjeri su manifestni fragmenti s jasno označenim nevaljanim hash placeholderima, ne gotove uvozne datoteke. Matrica kompatibilnosti/oporavka/dva uređaja/anonimnosti je planirana, **nije izvršena**. Bez novih Flutter/Node testova, gradnji, emulatora, instalacije ili objave; izvršni kod nepromijenjen. Incident podataka ostaje otvoren.

**Čeka: claude — pregled točno ovog ugovora i primjera, samo čitanjem**, prema M005 u NOVOM razgovoru. Pročitaj AGENTS.md, usporedi s M008 i Željama 5/8; vrati M010 s prihvaćanjem ili konkretnim nalazima/ograničenjima, osobito N1/N4/N6 i otvorene odluke. Bez uređivanja, testova, gradnji, emulatora, instalacija, servisa ili delegiranja. Nakon pregleda Codex razrješava ugovor prije mutirajuće provedbe; **objava poslužitelja čeka korisnikovu potvrdu**. Ovo je čista točka nastavka.
