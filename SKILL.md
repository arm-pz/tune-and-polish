---
name: tune-and-polish
description: Tune a skill's trigger and boundaries with Tune-Skill, then audit its discoverability and polish it with Findable-Polish. Use when the user wants to fix a skill that isn't triggering correctly or overlaps with siblings, and also wants its repo description, README, and site page polished for discovery — in one pass. Chains tune-skill (fine-tune) → findable-polish (audit+polish) in one workflow. Not for creating skills from scratch (use draft-skill).
version: 1.0.0
argument-hint: "[skill name | SKILL.md path]"
user-invocable: true
metadata:
  version: "1.0.0"
---

# Tune-And-Polish

Chain two existing skills into a single workflow: **Tune-Skill** fine-tunes a skill's description, command routing, and sibling boundaries so it triggers correctly, then **Findable-Polish** audits its discoverability surfaces (repo description, topics, README opening, site page) and generates polished alternatives.

## Invocation

```text
/tune-and-polish findable
/tune-and-polish ~/.qoder/skills/wordsmith/SKILL.md
Fix my skill's triggering and polish its discovery surfaces.
```

If no target is provided, ask the user for the skill name or SKILL.md path.

## Workflow

### Phase 1: Run Tune-Skill Audit

Invoke the **Tune-Skill skill** with the provided target:

1. Read the real SKILL.md and all sibling skills' SKILL.md files.
2. Map descriptions, commands, references, and handoff contracts.
3. Audit for: description mismatches, overlapping triggers, stale names/counts, broken handoffs, missing reference files.
4. Make minimal evidenced edits to fix each finding.
5. Validate with `check_skill.py` script.
6. Output: a report of what changed, corrections to earlier claims, and next steps.

**Handoff rule:** Capture tune-skill's full report, especially the list of edits made and any remaining WARNings from the check script.

### Phase 2: Run Findable-Polish on the Skill's Repo

Pass the tuned skill's repo/path to the **Findable-Polish skill**:

1. Findable audits the repo's discoverability: derives search queries, identifies gaps in description/topics/README opening.
2. Wordsmith generates 2–3 polished alternatives for each gap found.
3. Output: audit findings + rewrite options side-by-side.

Use this instruction for Wordsmith:

```
The Tune-Skill skill just fixed this skill's internal triggering and boundaries.
Now audit its external discoverability surfaces and generate polished alternatives.

Focus on:
- GitHub About text and topics that match the tuned description
- README opening line that reflects the new scope and boundaries
- Site page entry that aligns with sibling skills (no overlap)
- Any stale counts or feature claims that drifted after the tune

Tune-Skill report:
[Paste tune-skill's full report here]

Target repo/page:
[Path to the skill's repo or site page]
```

### Phase 3: Present Results

Return a three-part response:

1. **Tune-Skill Changes** (what was edited internally, what validations passed)
2. **Findable-Polish Alternatives** (external surfaces with options labeled)
3. **Recommended Actions** (which combination to apply + copy-paste commands for `gh repo edit`, in 2–3 sentences)

Format the alternatives so the user can apply them directly to their repo metadata.

## Boundaries

- **Does not** create new skills from scratch (use draft-skill).
- **Does not** push changes to GitHub — drafts fixes and hands over commands.
- **Does not** retune a skill that already passes validation cleanly (only use if there are actual triggering issues).

## Dependencies

This skill requires `tune-skill` and `findable-polish` (which itself requires `findable` + `wordsmith`) to be installed. If any are missing, tell the user and stop.
