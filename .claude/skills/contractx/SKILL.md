---
name: contractx
description: >
  Maintain the CONTRACTX hierarchy. Seven workflows: init (interview + build tree),
  walk (traverse chain for a path), update (post-edit pass), audit (exhaustive chain
  verification), gap (file CX-NNN), resolve (close CX-NNN), grow (create child when
  new durable boundary emerges), cross-cut (create cross-cutting contract).
  Use when the user asks to initialize CONTRACTX, walk the chain, audit contracts,
  file a gap, or create a new CONTRACTX.md.
argument-hint: "{action: init | walk | update | audit | gap | resolve | grow | cross-cut} {target}"
---

# CONTRACTX Skill

Maintains the CONTRACTX hierarchy in this repo. CONTRACTX files are binding work contracts for their subtrees — the agent reads them before every edit and updates them after meaningful changes.

## Hard rules — read before doing anything

1. **Always read root CONTRACTX.md FIRST.** It owns the framework rules and top-level index. Do not jump to a child — walk the chain.

2. **Walk before edit.** Before touching any file, read root CONTRACTX.md → walk to the target directory → read every CONTRACTX.md along the path. No memory reliance.

3. **Gap findings land in `CONTRACTX/gaps/open/`.** Never write a gap observation inline in a directory CONTRACTX.md. Use CX-NNN format.

4. **Update parent index when child changes.** Creation, deletion, move, rename, scope change → update the parent's Child CONTRACTX Index.

5. **No child weakens parent rules.** Closer docs add specificity. They never contradict. If you find a contradiction → file a gap.

6. **Audit is exhaustive.** Walk every CONTRACTX.md, verify every child index reference, cross-check against actual directory contents. Do not stop at the first 3 gaps.

7. **Caveman-lite style.** Short sentences. Dense info. Tables over prose. One fact per bullet. No narrative connectors. Every section reads in under 30 seconds.

8. **Single file vs. CONTRACTX/ folder.** ≤5 files + ≤2 concerns → single CONTRACTX.md. 6+ files + 3+ concerns → CONTRACTX.md + CONTRACTX/ folder. Document the decision in the file.

9. **Cross-cutting contracts live in `CONTRACTX/cross-cutting/`.** If a contract spans 2+ top-level directories, put it there and reference from each affected CONTRACTX.md.

10. **Escalate when needed.** If a CONTRACTX gap reveals a domain-level contradiction, escalate to `docs/MASTER_CONTRACT.md` as a G-NNN.

## When to use this skill

Trigger phrases:
- "Initialize CONTRACTX tree" / "build CONTRACTX"
- "Walk CONTRACTX chain for X"
- "Audit CONTRACTX" / "check CONTRACTX for drift"
- "File a CONTRACTX gap" / "CX gap"
- "Create CONTRACTX for this directory"
- "Update CONTRACTX after this change"
- Direct invocation: `/contractx init` / `/contractx audit` / `/contractx walk <path>`

## Workflows

### init — interview user + build CONTRACTX tree

1. Read `prompts/interview.md` for the full interview script.
2. Ask questions one at a time. Wait for answers.
3. After interview, build:
   a. Root CONTRACTX.md — project-wide rules, terminology, child index
   b. For each durable boundary — child CONTRACTX.md
   c. For complex directories — CONTRACTX/ folder with sub-contracts
   d. Cross-cutting contracts for multi-directory concerns
4. Report: files created, boundaries identified, cross-cutting concerns found.

### walk — traverse CONTRACTX chain for a target path

1. Read root CONTRACTX.md.
2. Identify target file path.
3. Walk from root to target, reading every CONTRACTX.md.
4. If a CONTRACTX.md references a CONTRACTX/ folder, read _index.md + relevant sub-contracts.
5. Print the chain: each file read, key rules from each, nearest contract for the target.

### update — post-edit CONTRACTX pass

1. Read root CONTRACTX.md.
2. Identify the nearest owning CONTRACTX.md for the changed files.
3. Check if the change affects: purpose, scope, ownership, structure, invariants, workflows, permissions, or child boundaries.
4. If yes → update the nearest CONTRACTX.md. Refresh child index. Update parent if structure changed.
5. If no → report "no update needed" — the pass still happened.
6. Remove any stale or contradictory text found during the pass.

### audit — exhaustive chain verification

1. Read root CONTRACTX.md. List every child index entry.
2. For every CONTRACTX.md found in the tree:
   a. Verify it exists at the listed path.
   b. Verify section order (Purpose→Ownership→Local Contracts→Work Guidance→Verification→Child Index).
   c. Cross-check child index entries against actual directory contents.
   d. Spot-check 3 local contract claims against actual source code.
   e. Check for weakened parent rules.
3. For every directory NOT listed that IS a durable boundary → file CX gap (missing child).
4. For every child index entry pointing to non-existent file → file CX gap (stale index).
5. Report: files checked, gaps found, drift detected, recommended fixes.

### gap — file a CX-NNN gap

1. Read `CONTRACTX/gaps/_index.md` for the next available CX number.
2. Create `CONTRACTX/gaps/open/CX-NNN.md` using the gap template.
3. Update `CONTRACTX/gaps/_index.md` — add row to Open gaps table.
4. Cross-reference affected CONTRACTX.md files in the gap entry.

### resolve — close a CX-NNN gap

1. Verify the fix is committed (check git log for CX-NNN reference).
2. Move `CONTRACTX/gaps/open/CX-NNN.md` → `CONTRACTX/gaps/resolved/CX-NNN.md`.
3. Update status to RESOLVED with date + commit SHA.
4. Update `CONTRACTX/gaps/_index.md` — move row from Open to Resolved.
5. Update affected CONTRACTX.md if the resolution changed any contract text.

### grow — create child CONTRACTX.md for new boundary

1. Confirm the directory meets the durable boundary threshold.
2. Determine format: single file or CONTRACTX/ folder (check file count + concern count).
3. Read parent CONTRACTX.md for inherited rules.
4. Create the new CONTRACTX.md (and CONTRACTX/ folder if needed).
5. Update parent's Child CONTRACTX Index.
6. If CONTRACTX/ folder created: write _index.md + sub-contract files.

### cross-cut — create cross-cutting contract

1. Confirm the concern spans 2+ top-level directories.
2. Create `CONTRACTX/cross-cutting/<name>.md` with: affected directories, contract rules, invariants.
3. Update `CONTRACTX/cross-cutting/_index.md`.
4. Reference the cross-cutting contract from each affected directory's CONTRACTX.md.

## Gap entry template

```markdown
# CX-NNN — Short title

- **Status:** OPEN
- **Affects:** `lib/CONTRACTX.md`, `lib/handlers/CONTRACTX.md`
- **Discovered:** YYYY-MM-DD
- **Contradiction:** <one line>
- **Recommended resolution:** <one line>
- **Owner:** <who fixes>
```

## Folder vs. single file decision

1. Count files in the directory (exclude __pycache__, hidden files).
2. Count distinct domain concerns (groups of related files with shared purpose).
3. Apply threshold:
   - ≤5 files, ≤2 concerns → SINGLE CONTRACTX.md
   - 6+ files, 3+ concerns → CONTRACTX.md + CONTRACTX/ folder
4. Document the decision in a "Why single file" or "Why a folder" section at the top.

## Section order (enforced in audit)

Every CONTRACTX.md must follow this order:
1. Purpose
2. Ownership
3. Local Contracts
4. Work Guidance
5. Verification
6. Child CONTRACTX Index
