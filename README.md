## Angela Rubia · Systems-first AI & Automation Engineer

I design the system before I choose the tool: where the manual work is, what data exists, what must never go wrong, and who approves what. Then I build it in n8n with PostgreSQL, Python and AI steps, so it runs on its own, tells me when it breaks, and keeps a person in charge of anything that matters.

Every system below is public, running, and shipped with its full workflow and documentation.

---

### SOL Lead Engine · live, runs daily
**▶ [Explore the live workflow](https://anruops.github.io/sol-lead-engine/)** · [repo](https://github.com/anruops/sol-lead-engine)

A lead engine for appointment businesses, pointed at yoga and pilates studios around Austin, Texas. Every morning it finds local businesses that customers struggle to reach online, audits each website the way a customer would experience it, and scores the gap out of 100 with deterministic rules in a tested Python service (the same business always gets the same score, every point explained, 11 unit tests). Each lead worth a look reaches me as a Telegram card, where I check the facts and how the site actually feels to book on before deciding.

`n8n` `PostgreSQL` `Python` `Telegram Bot API` `OpenStreetMap Overpass`

### Business Brain (RAG) · live, runs daily
**▶ [Explore the live workflow](https://anruops.github.io/business-brain-rag/)** · [repo](https://github.com/anruops/business-brain-rag)

A retrieval-augmented generation (RAG) knowledge base over a notes vault. It stores the meaning of each note in PostgreSQL with pgvector and answers questions using only those notes, citing the exact source. A similarity threshold, not the model, decides whether to answer, so when nothing matches closely enough it says "not in your vault" instead of guessing. A 9-point self-test runs weekly and a health check runs every day.

`n8n` `PostgreSQL` `pgvector` `Google Gemini`

### Content Engine · live since September 2026, v2 rebuild in progress
[repo](https://github.com/anruops/content-engine)

Reads 4 industry news feeds, drafts on-brand posts with an LLM, waits for my approval, then publishes to Facebook and Instagram through the Meta Graph API. A status machine, where every post is always in exactly 1 named state, means a crashed run never posts twice, and if Facebook posts but Instagram fails, only Instagram is retried.

`n8n` `Google Gemini` `Meta Graph API` `Google Apps Script`

---

### How I build
- **Deterministic rules decide; AI reads.** Rules make the decisions I'd have to explain to a client line by line; AI only reads messy text, and its output is checked before use.
- **Human-in-the-loop on anything risky.** Anything with a client's name, money, legal weight, or that can't be undone waits for a person to approve it.
- **No duplicates, ever.** Every record is upserted on a stable key, so running a workflow twice gives the same result as running it once (idempotent).
- **Errors are planned for.** Every workflow breaks at some point: where a retry can't cause harm it retries on its own (safe retries), where it could it stops and says exactly what to restart, and every failure reaches me on Telegram or Slack within a minute.
- **Documented so someone else can run it.** Each repo ships with a system guide, setup steps, a runbook of real incidents and a release routine.

**How I work with AI:** Claude is my guide and reviewer. I design each system, build and wire every node, run every test, and make every scope decision.

**Contact:** arubia.business@gmail.com
