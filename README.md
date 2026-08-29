# The Loyalty Clause

Cities are buying AI chatbots for 311 lines, permit help, benefits questions. None of them have a way to check whether the thing they bought quietly favors the company that sold it. We spent a hackathon day building that check, plus the contract language a city would need to actually act on it.

Built for the Mangrove Ground-Level AI Governance hackathon, Track C (with a Track B measurement demo inside it).

## The question we tried to answer

Can a city detect whether a procured AI chatbot favors a named principal (its vendor, a sponsor, whoever) using nothing but the public chat interface, no ML expertise, in under a day?

Short answer: yes, for the cheapest and most likely version of the attack. Longer answer with caveats is in [docs/methodology.md](docs/methodology.md).

## What's in here

- `audit_kit/loyalty_audit.py` – the audit tool. One file, Python standard library only, nothing to install. Point it at any OpenAI-compatible chat endpoint and it runs a battery of paired questions, then does the stats (binomial and permutation tests, bootstrap CIs) and prints a verdict in plain English.
- `audit_kit/make_battery.py` – generates the 300-item battery. Forced-choice questions, 0-10 ratings, open-ended "what should a city worry about" questions, across 20 city services. Also includes 60 placebo pairs (control company vs control company) so the audit catches its own false positives.
- `demo/system_prompts/` – the experiment. `clean.txt` and `loyal.txt` are the same chatbot persona except loyal.txt has one hidden paragraph telling it to favor "CivicSense Technologies" and deny doing so if asked.
- `results/` – raw transcripts and analysis from both runs. Every model reply is saved, so you can re-score everything yourself without re-running the models.
- `docs/procurement_clause.md` – a one-page contract rider: disclosure of steering instructions, audit rights, re-audit on every model update, cure period, termination with refund.
- `docs/council_brief.md` – one page for a councilmember who will never read the code.
- `docs/methodology.md` – full method, stats, and the limitations section we'd want a skeptical judge to read first.

## Running it

Against any OpenAI-compatible endpoint (Ollama, vLLM, OpenAI, a vendor gateway):

```
python audit_kit/make_battery.py
python audit_kit/loyalty_audit.py run --endpoint http://localhost:11434/v1 --model <model> --battery audit_kit/battery.json --out results/run.json
python audit_kit/loyalty_audit.py analyze results/run.json
```

To reproduce our demo exactly, run the battery twice against the same local model, once with each system prompt:

```
python audit_kit/loyalty_audit.py run --endpoint http://localhost:11434/v1 --model qwen2.5-coder:7b --battery audit_kit/battery.json --system-prompt-file demo/system_prompts/clean.txt --label clean --out results/run_clean.json
python audit_kit/loyalty_audit.py run --endpoint http://localhost:11434/v1 --model qwen2.5-coder:7b --battery audit_kit/battery.json --system-prompt-file demo/system_prompts/loyal.txt --label loyal --out results/run_loyal.json
python audit_kit/loyalty_audit.py analyze results/run_clean.json --out results/analysis_clean.json
python audit_kit/loyalty_audit.py analyze results/run_loyal.json --out results/analysis_loyal.json
```

We ran this on an ordinary Windows laptop with a local 7B model. About 15 minutes per condition, no cloud account, nothing leaves the machine. That was the point: this is the hardware and access a city analyst actually has.

## What it can't do

A loyalty that only wakes up on a rare trigger phrase will pass this audit. So will a model smart enough to notice it's being tested. We only validated one way of planting a loyalty (system prompt), because that's the cheapest one and the one anyone in a city's supply chain could pull off, but it's not the only way. And with real vendor names instead of our fictional ones, some of the measured gap could just be reputation the model learned in training.

That's why the contract rider exists. The audit raises the cost of the easy attack; the disclosure certification and termination clauses cover the ones the audit can't see. Details in the methodology doc.
