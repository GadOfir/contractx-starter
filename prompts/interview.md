# CONTRACTX Interview Prompt

Give this prompt to your AI agent ONCE. It will deeply interview you about your project and build the entire CONTRACTX tree.

---

## Instructions for the AI agent

You are initializing a CONTRACTX tree for this project. Your goal: build a complete hierarchy of CONTRACTX.md files that will govern all future edits.

### Phase 1 — Project Survey (ask these questions, one at a time)

**Structure & boundaries**
1. What are the top-level directories and what does each one own? (e.g., "lib/ is the Python core, web-ui/ is the dashboard, k8s/ is infrastructure")
2. Which directories are "durable boundaries" — they have their own purpose, rules, and standards distinct from siblings?
3. Which directories are just containers — simple grouping with no distinct rules?

**Conventions & invariants**
4. What are the 3-5 most important code invariants that MUST never be broken? (e.g., "Dispatcher constructor is pure — no I/O", "init_tracing() before DispatcherFactory import")
5. What naming conventions are enforced? (file names, function prefixes, module patterns)
6. What import rules exist? (what can import from where, what's forbidden)

**Workflow & process**
7. How is testing done? (PROD only? local? CLI? specific commands?)
8. What's the deploy process? (auto-deploy on push? manual? specific workflows?)
9. What cross-directory contracts exist? (e.g., "HMAC version must match in lib/ + web-ui/")

**Tooling & verification**
10. What verification gates exist? (linting? static checks? baseline tests?)
11. What skills/tools does the agent already have? (list any existing .claude/skills/)
12. What documentation conventions exist? (contract files? MASTER_CONTRACT.md?)

**Gaps & pain points**
13. What rules do humans know but the agent keeps getting wrong?
14. What "why did it touch that file?!" moments have happened?
15. What invariants are currently undocumented and only live in someone's head?

### Phase 2 — Build the tree

After interviewing, build the CONTRACTX tree:

1. **Write root `CONTRACTX.md`** — project-wide rules, terminology, child index
2. **For each durable boundary** — create `CONTRACTX.md` with Purpose, Ownership, Local Contracts, Work Guidance, Verification, Child Index
3. **For directories with 10+ files and 3+ concerns** — also create `CONTRACTX/` folder with sub-contracts
4. **For small directories (≤5 files, 1 concern)** — single CONTRACTX.md, note "Why single file" at top
5. **Identify cross-cutting concerns** — create entries in `CONTRACTX/cross-cutting/` for contracts that span 2+ directories

### Phase 3 — Verify

After building:
1. Walk every CONTRACTX.md — verify child indexes are correct
2. Verify no child weakens a parent rule
3. Verify section order (Purpose→Ownership→Local Contracts→Work Guidance→Verification→Child Index)
4. Report: files created, boundaries identified, cross-cutting concerns found

### Rules during interview

- Ask ONE question at a time. Wait for the answer before asking the next.
- If an answer is vague, ask a clarifying follow-up. "Which specific files does that apply to?"
- If the user says "I don't know" — note it as a TBD and move on. Don't guess.
- If a directory has no distinct rules, DON'T create a CONTRACTX.md for it. Only durable boundaries get contracts.
- The goal is precision, not volume. 10 tight CONTRACTX.md files beat 50 vague ones.
