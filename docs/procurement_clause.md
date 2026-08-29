# Model Contract Rider: AI Loyalty Disclosure & Audit Rights

*One page. Drop into any city AI procurement contract as a rider or exhibit. Drafted to complement the GovAI Coalition template vendor agreements, which cover transparency and data practices but do not currently address principal favoritism.*

---

## Section 1. Definitions

**1.1 "AI System"** means the software provided under this Agreement that generates text, recommendations, rankings, or decisions using a machine-learning model, whether developed by Vendor or licensed from a third party.

**1.2 "Principal Favoritism"** means any systematic tendency of the AI System to favor, promote, defend, or steer users toward any named person or entity (including Vendor, Vendor's affiliates, investors, or business partners, or any political actor) beyond what neutral treatment of comparable entities would produce.

**1.3 "Steering Instruction"** means any system prompt, fine-tuning objective, retrieval rule, filter, or configuration that instructs or trains the AI System to treat any named entity differently from comparable entities.

## Section 2. Disclosure

**2.1** Vendor shall disclose in writing, before contract execution and as a condition of acceptance, every Steering Instruction present in the AI System as delivered, including the full text of all system prompts and a description of any entity-specific training or retrieval behavior.

**2.2** Vendor certifies that, apart from disclosed Steering Instructions, the AI System has not been intentionally caused to advance the interests of any specific principal. This certification is a material representation; a false certification is grounds for termination for cause under Section 5.

## Section 3. Audit Rights

**3.1** City may test the AI System for Principal Favoritism at any time, using paired-prompt comparison of named entities against matched comparators or any substantially similar black-box method, without notice to Vendor. Such testing shall not be deemed a violation of any acceptable-use, anti-benchmarking, or reverse-engineering provision of this Agreement, all of which are waived for this purpose.

**3.2** Before final acceptance, City shall conduct (or engage a third party to conduct) a baseline favoritism audit covering, at minimum: Vendor's own name and affiliates, and any entity Vendor is required to disclose under Section 2.1. Vendor shall provide test access at no charge.

**3.3** Vendor shall give City fourteen (14) days' written notice before deploying any change to the AI System's model weights, model version, system prompts, or retrieval configuration. Each such change restarts City's audit rights under Section 3.2 prior to the change taking effect in production, except for emergency security patches, which may be audited retroactively.

## Section 4. Thresholds and Cure

**4.1** A favoritism finding is "Confirmed" when an audit under Section 3 finds statistically significant favoritism toward an undisclosed principal (at the audit's pre-registered significance level) on at least two independent measures, and the same audit's control-entity comparisons do not flag.

**4.2** Upon a Confirmed finding, Vendor shall have thirty (30) days to identify the cause, remediate, and pass a re-audit. During the cure period, City may suspend public-facing use of the AI System without penalty or payment obligation for the suspended service.

## Section 5. Remedies

**5.1** Failure to cure under Section 4.2, or any breach of the Section 2.2 certification, entitles City to: (a) terminate for cause with no early-termination fee; (b) a refund of fees paid for the affected service period; and (c) Vendor's cooperation, at Vendor's expense, in transitioning to a successor system, including export of City's data and configurations in a documented format.

**5.2** These remedies are in addition to, not in lieu of, any other remedy available at law.

---

*Model language for adaptation by counsel; not legal advice. Section 1.2's definition of a secretly loyal system follows Kwon et al., "A Research Agenda for Secret Loyalties" (Formation Research, 2026): a system "intentionally caused to advance a specific actor's interests" while that loyalty remains "undisclosed to operators, auditors, users, or other affected parties."*
