# Reference Patterns

## Gap format

```markdown
# CX-NNN — Short title

- **Status:** OPEN | SHIPPED | RESOLVED
- **Affects:** `path/to/CONTRACTX.md`
- **Discovered:** YYYY-MM-DD
- **Contradiction:** <one line describing the problem>
- **Recommended resolution:** <one line describing the fix>
- **Owner:** <who fixes it>
- **Resolved:** YYYY-MM-DD (commit <sha>)
```

## Folder vs. single file threshold

| Directory size | Format |
|---|---|
| ≤5 files, ≤2 concerns | Single CONTRACTX.md |
| 6–25 files, 3–4 concerns | CONTRACTX.md + CONTRACTX/ folder (2–4 sub-contracts) |
| 26+ files, 5+ concerns | CONTRACTX.md + CONTRACTX/ folder (4–6 sub-contracts) |

## Audit checklist

See `CONTRACTX/audits/_index.md` for the full checklist.
