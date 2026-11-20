# These Neurons – radni prostor

Ovaj repozitorij je zajedničko mjesto gdje vlasnik projekta zapisuje želje,
a AI agenti (Claude i Codex) iz njega uzimaju posao.

## Kako to radi

1. Vi upišete želju u mapu [`zelje/`](zelje/) – jedna datoteka po želji
   (kopirajte [`zelje/_PREDLOZAK.md`](zelje/_PREDLOZAK.md)).
2. Agent (Claude ili Codex) pročita mapu, uzme želju sa statusom `nova`,
   promijeni status u `u-radu` i radi na njoj.
3. Kad završi, agent upiše što je napravio i postavi status `gotovo`
   (ili `pitanje` ako mu nešto od vas treba).

Pravila za agente su u [`WORKFLOW.md`](WORKFLOW.md).
Codex ih čita preko [`AGENTS.md`](AGENTS.md), a Claude preko [`CLAUDE.md`](CLAUDE.md).

## Upisivanje želje s mobitela

U aplikaciji GitHub ili na github.com: otvorite mapu `zelje/` →
**Add file → Create new file** → nazovite je npr. `003-tamni-nacin.md` →
zalijepite predložak i ispunite ga → **Commit**.
