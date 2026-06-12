# Cross-Cutting Contracts

Contracts that span 2+ directories. One source of truth, referenced from each affected CONTRACTX.md.

## Index

| Contract | Affected directories | File |
|---|---|---|
| — | No cross-cutting contracts yet | — |

## When to create one

A contract belongs here when:
- It describes behavior that spans 2+ top-level directories
- Changing it requires coordinated edits in multiple places
- It's referenced by multiple directory CONTRACTX.md files

## Template

```markdown
# <name>.md — <title>

## Affected directories
- `lib/auth.py`, `web-ui/main_server.py`

## Contract
### <rule>
- ...
```
