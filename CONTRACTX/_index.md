# CONTRACTX/ — Artifact Index

Navigation for all CONTRACTX root artifacts.

## Structure

| Folder | Purpose |
|---|---|
| `gaps/` | CX-NNN gap tracking — open/ and resolved/ |
| `audits/` | Periodic chain audit reports |
| `cross-cutting/` | Contracts spanning 2+ directories |
| `refs/` | Reference patterns for CONTRACTX maintenance |

## Gap lifecycle

```
OPEN → SHIPPED (fix commit) → RESOLVED (handoff verified)
```

Gaps move from `open/` to `resolved/`. Never deleted. Audit trail is permanent.

## When to escalate

If a CONTRACTX gap reveals a domain-level contradiction (e.g., "CASCADE_CONTRACT says X but lib/CONTRACTX.md says Y"), escalate to `docs/MASTER_CONTRACT.md` as a G-NNN entry.
