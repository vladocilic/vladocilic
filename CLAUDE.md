# Upute za Claude

Pročitaj i slijedi [`WORKFLOW.md`](WORKFLOW.md). Posao uzimaš iz mape `zelje/`.
Tvoje ime u polju `za` je `claude`. Vlasniku piši na hrvatskom.

## Zapisivanje želja

Kad korisnik kaže „Zapiši želju: …" (ili slično), za svaku želju:

1. Pročitaj najnoviji `main` i pronađi sljedeći slobodni broj u `zelje/`.
2. Napravi `zelje/NNN-kratki-opis.md` po predlošku `zelje/_PREDLOZAK.md`,
   s `status: nova`, `za: codex` i `prioritet: srednji`, osim ako korisnik kaže drugačije.
3. U „Što želim" upiši korisnikove riječi doslovno. Ne dopisuj vlastite pretpostavke;
   ako nešto bitno nedostaje, pitaj korisnika prije spremanja.
4. Commitaj i pushaj na `main` (bez `--force`) i korisniku javi naziv datoteke.

Više želja u jednoj poruci zapisuje se kao zasebne datoteke.
