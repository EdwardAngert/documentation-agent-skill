# Code Review: reorient-sme-coaching Branch

**Branch**: `reorient-sme-coaching`
**Scope**: All commits since `main` — SKILL.md, four commands, frontmatter spec, llms.txt, README, plugin.json, and docs/
**Date**: 2026-02-26

---

## Critical Issues

Issues that break feature coverage or leave users without information they need.

---

### 1. README file tree missing `frontmatter-spec.md`

**File**: `README.md`, lines 117–124
**What's wrong**: The "What's Inside" file tree lists six skill files but omits `frontmatter-spec.md`, which was added in a later commit.
A user reading the README to understand what's in the plugin won't know the frontmatter spec exists.
`llms.txt`, `SKILL.md`, and `commands/draft.md` all reference it.

**Suggested fix**: Add `frontmatter-spec.md` to the file tree with a brief description.

---

### 2. `docs/set-up-documentation-standards-for-your-team.md` does not mention `/plan`

**File**: `docs/set-up-documentation-standards-for-your-team.md`, lines 71–72
**What's wrong**: The install section says "No special commands required — though `/documentation-agent:draft` walks through a more structured intake."
The `/plan` command exists and is the right entry point when someone needs to document a project from scratch — exactly the scenario this doc targets (docs leads setting up standards for a team).
A docs lead reading this doc has no idea `/plan` exists.

**Suggested fix**: Add a sentence or short paragraph after the install section directing docs leads to `/plan` for planning a full documentation set.

---

### 3. `docs/write-docs-with-the-documentation-agent.md` does not mention `/plan`

**File**: `docs/write-docs-with-the-documentation-agent.md`
**What's wrong**: This doc covers `/draft` and `/make-examples` but not `/plan`.
A contributor reading it will know how to write a single doc but won't know there's a command for planning a full documentation set.
The "Get the Most Out of It" section has subsections for draft and make-examples — `/plan` needs one too.

**Suggested fix**: Add a "Plan a Full Documentation Set" subsection in "Get the Most Out of It" that explains what `/plan` does and when to use it (for "we need docs for this project" moments vs single-doc contributions).

---

## High Issues

Style violations the plugin itself enforces — the plugin's own docs contradict the standards it applies to user docs.

---

### 4. SKILL.md: Gerund heading "Drafting a Single Doc"

**File**: `skills/documentation-agent/SKILL.md`, line 18
**What's wrong**: The heading "### Drafting a Single Doc" uses a gerund.
SKILL.md line 93 and `tone-and-voice.md` both specify "use imperative verbs, not gerunds" for headings.
The plugin's own headings should follow the plugin's own rules.

**Suggested fix**: Change to `### Draft a Single Doc`

---

### 5. SKILL.md: Gerund heading "Planning a Documentation Set"

**File**: `skills/documentation-agent/SKILL.md`, line 31
**What's wrong**: Same issue as above — gerund heading.

**Suggested fix**: Change to `### Plan a Documentation Set`

---

### 6. SKILL.md: Non-imperative heading "Writing Standards You Apply Automatically"

**File**: `skills/documentation-agent/SKILL.md`, line 71
**What's wrong**: "Writing Standards You Apply Automatically" is neither imperative nor concise.
The "You Apply Automatically" clause is redundant — the section itself makes clear these are the standards applied automatically.

**Suggested fix**: Change to `## Writing Standards`

---

### 7. SKILL.md: Gerund heading "When Reviewing Existing Docs"

**File**: `skills/documentation-agent/SKILL.md`, line 144
**What's wrong**: "When Reviewing" uses a gerund where an imperative would be clearer.

**Suggested fix**: Change to `## Review Existing Docs`

---

### 8. `frontmatter-spec.md`: Gerund heading "When Surveying Existing Docs"

**File**: `skills/documentation-agent/frontmatter-spec.md`, line 128
**What's wrong**: Gerund heading.

**Suggested fix**: Change to `### Survey Existing Docs`

---

### 9. `frontmatter-spec.md`: Gerund heading "When Auditing (`/audit`)"

**File**: `skills/documentation-agent/frontmatter-spec.md`, line 140
**What's wrong**: Gerund heading.

**Suggested fix**: Change to `### Audit with \`/audit\``

---

### 10. `frontmatter-spec.md`: Gerund heading "Adapting to Existing Repos"

**File**: `skills/documentation-agent/frontmatter-spec.md`, line 149
**What's wrong**: Gerund heading.

**Suggested fix**: Change to `## Adapt to Existing Repos`

---

### 11. `frontmatter-spec.md`: Gerund heading "Documenting the Mapping"

**File**: `skills/documentation-agent/frontmatter-spec.md`, line 174
**What's wrong**: Gerund heading.

**Suggested fix**: Change to `## Document the Mapping`

---

## Medium Issues

Incomplete content or minor inconsistencies that reduce accuracy or usefulness.

---

### 12. `documentation-patterns.md`: Content type heading "FAQ/Troubleshooting" inconsistent with `troubleshooting` used everywhere else

**File**: `skills/documentation-agent/documentation-patterns.md`, line 49
**What's wrong**: The content type heading is "### FAQ/Troubleshooting" but SKILL.md (line 65), `commands/draft.md` (line 76), and `frontmatter-spec.md` (line 41) all use `troubleshooting` as the canonical name and frontmatter value.
This creates ambiguity about whether the correct value is `troubleshooting` or `faq/troubleshooting`.

**Suggested fix**: Change the heading to `### Troubleshooting` to match the value used in the frontmatter spec and commands.

---

### 13. `frontmatter-spec.md`: SSG coverage names Jekyll and Astro but doesn't list their fields

**File**: `skills/documentation-agent/frontmatter-spec.md`, lines 152–163
**What's wrong**: The intro paragraph names "Docusaurus, Hugo, Jekyll, and Astro" but conflict resolution rule 3 only lists fields from Docusaurus and Hugo (`sidebar_position`, `slug`, `weight`, `layout`).
Jekyll and Astro are named but their specific fields aren't covered, leaving Claude to guess when it encounters them.

**Suggested fix**: Add Jekyll fields (`permalink`, `categories`, `published`) and Astro fields (`pubDate`, `heroImage`) to rule 3's list of SSG-required fields to preserve.

---

### 14. `commands/plan.md`: "Update the plan" is ambiguous

**File**: `commands/plan.md`, line 108
**What's wrong**: Step 6 says "As you write each doc, update the plan" but doesn't specify where the plan lives.
Is it in-memory? Written to a file? Kept in the conversation? Without an artifact to update, "update the plan" is unactionable.

**Suggested fix**: Specify that the plan should be written to a file (e.g., `docs/plan.md`) at the end of step 4, and that the file is updated as docs are completed.

---

## Low Issues

Minor polish items.

---

### 15. `docs/write-docs-with-the-documentation-agent.md`: "Won't commit changes" is ambiguous

**File**: `docs/write-docs-with-the-documentation-agent.md`, line 95
**What's wrong**: "It also won't commit changes without you reviewing them" could be read as referring to git commits (which Claude Code also does not do without approval), but the intended meaning is "write the file."
In a tool that also manages git commits, this phrasing will confuse some readers.

**Suggested fix**: Change to "It also won't write the file without you reviewing the draft."
