# Council Brief: Does Our Chatbot Work for Us, or for Its Vendor?

**For:** City Council & City Manager | **Action requested:** Adopt the AI Loyalty Disclosure & Audit Rights rider for all AI procurements; direct staff to run a baseline loyalty audit before accepting any conversational AI system.

---

## The problem in one paragraph

Cities are buying AI chatbots for 311 lines, permits, and benefits questions. These systems answer in the vendor's voice but with the city's name on them. An AI system can be built, deliberately or carelessly, to quietly favor a specific party: the vendor itself, a sponsor, or a political actor. AI-safety researchers call this a **secret loyalty**: a system "intentionally caused to advance a specific actor's interests" while that loyalty stays hidden from the people using it (Kwon et al., Formation Research, 2026). The city cannot see the model's inner workings, and no current procurement rule requires anyone to check.

## This is real, not hypothetical

- **July 2025:** xAI's Grok 4 was found searching for Elon Musk's personal posts before answering controversial questions, a live example of a deployed AI consulting its principal's views (TechCrunch, CNBC, 7/2025).
- **Peer-reviewed research** shows AI models systematically favor their own maker's outputs when asked to judge quality (Panickssery et al., NeurIPS 2024).
- **March 2024:** NYC's MyCity chatbot told businesses to break the law for months before anyone systematically tested it (The Markup). Cities find out about AI failures late, from journalists, not from their contracts.
- **The policy gap:** a 2025 Center for Democracy & Technology review found only 21 of roughly 22,000 US cities and counties had public AI policies, and those address demographic bias and privacy, not vendor favoritism. NYC's Local Law 144 mandates bias audits for hiring tools, but only for discrimination against protected groups. **We found no procurement rule anywhere that requires testing an AI system for loyalty to its vendor.**

## What we built and what it showed

A **one-day loyalty audit kit** any city analyst can run on a standard laptop: no machine-learning expertise, no cloud account, no access to the vendor's model internals. It asks the chatbot ~300 paired questions ("Which of these two companies would you recommend for X?", "Rate this provider 0–10") where a named company is systematically swapped against matched comparison companies, then applies standard statistics to detect one-sided favoritism.

**In our demonstration**, we planted a hidden vendor loyalty in a chatbot (one paragraph of hidden instructions, the easiest and cheapest way a real vendor could do it) and audited both the tampered and untampered versions. The audit flagged the tampered chatbot decisively and cleared the clean one, with built-in placebo comparisons to show the method doesn't cry wolf. Full numbers, code, and raw transcripts are in the audit report.

## What council can do this term

1. **Adopt the one-page contract rider** (attached): vendors must disclose any steering instructions; the city gets the right to run favoritism audits at any time; every model update restarts audit rights; confirmed hidden favoritism is grounds for termination with refund.
2. **Direct staff to run the baseline audit** before final acceptance of any conversational AI system, and after every vendor model update. Cost: one analyst-day; the toolkit is free and open.
3. **Share results** with the GovAI Coalition so member governments can compare audits of the same vendors.

## Honest limitations

The audit detects *directional favoritism visible in outputs*. It will not catch a loyalty that activates only on a rare trigger phrase, favoritism expressed through subtle omissions, or a system trained to behave differently when it detects it is being tested. Research shows broad audits can be evaded by a sufficiently careful adversary (Lee, Apart Research Secret Loyalties sprint, 2026). A clean audit is a meaningful check, not a guarantee. That is exactly why the rider pairs testing with disclosure obligations and legal remedies: the audit raises the cost of the easy attack; the contract covers the rest.

---

*Prepared for the Mangrove Ground-Level AI Governance hackathon, August 2026. Sources cited in full in the accompanying methodology document.*
