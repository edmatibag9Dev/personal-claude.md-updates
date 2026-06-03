# Ed's Cowork Instructions
# Last updated: 2026-06-02

---

## ⚠️ ROUTING RULES — READ FIRST EVERY SESSION

### Rule 1: DISPATCH MODE
If Ed's message starts with **"dispatch:"** (case-insensitive), or if content is described as a "dispatch upload":
- Route ALL content **exclusively to Open Brain** using the `capture_thought` tool
- **NEVER write dispatch content to CLAUDE.md or any memory/ file**
- **NEVER add dispatch information to working memory**
- Confirm the save and ask if Ed wants a Day One entry (see Day One workflow below)

### Rule 2: OPEN BRAIN CAPTURE TRIGGERS
Watch for any of the following trigger phrases anywhere in a message (case-insensitive):
- **Remember**
- **Remember this**
- **Save This**
- **Save to the Brain**
- **To open brain**

When a trigger is detected:
1. Capture everything after the trigger phrase into Open Brain using `capture_thought`
   - Include all text, attachments, images, or file content (describe or transcribe them)
   - Write the thought as a clear, standalone statement that will make sense when retrieved later
2. Confirm the save with a brief message
3. Immediately ask: "Would you like me to also create a Day One journal entry for this?"
4. If yes, ask which journal (see Day One Journals section below)
5. Create the Day One entry using `create_journal_entry` with the same content

> These triggers work from both regular chat AND dispatch sessions.

### Rule 3: CLAUDE.md IS NOT A GENERAL NOTEPAD
- Only update CLAUDE.md when Ed explicitly says to (e.g., "add this to your instructions" or "update CLAUDE.md")
- Do NOT add project details, task notes, or session findings here automatically
- Do NOT add anything from a dispatch session here

### Rule 4: memory/ FILES
- Only write to files in the `memory/` folder when Ed explicitly asks to update memory
- Dispatch content never goes into memory/ files
- Memory is for Ed's preferences, context, and reference information — not incoming data

---

## Day One Journals

Ed's available journals for the capture workflow:
- **AI Journey** — AI and automation experiences, insights, experiments
- **Ed Journal** — General personal journal
- **Options Trading Journal** — Options trading notes and records
- **Short Selling Trading Journal** — Short selling trades and analysis

Other journals (not part of the capture workflow unless specified):
- Freshwater Fishing Journal
- Saltwater Fishing Journal
- Instagram

---

## About Ed

- **Name:** Ed Matibag
- **Email:** edmatibag9@gmail.com
- **Workspace folder:** ~/Documents/Claude (always select this as the Cowork folder)

---

## Projects (reference)

- **AI MCP server and AI connections to apps local** — AI tooling, MCP server setup, automation workflows
- **Dsy Trading Analysis** — Trading analysis work

---

## GitHub Repository Standards

At the start of any task involving a GitHub repository:
1. Check repo for `CONTRIBUTING.md` and `AGENTS.md` — if either is missing, push canonical version from `~/.claude/` before doing anything else
2. Read both files completely, then follow their standards for all commits and READMEs

**Commits:** `feat`/`fix` require subject + body with ≥ 3 bullets. No one-liners.
**README:** Create or update on every `feat`, `fix`, or `data` commit. All 9 sections, ≥ 400 words.
**Sandbox push:** Use GitHub Contents API. New file: `PUT` with base64 content. Update: `GET` sha first, then `PUT` with sha — missing sha = 409.

Full rules: `~/.claude/CONTRIBUTING.md` and `~/.claude/AGENTS.md`

---

## Trigger Phrases (master list)

| Trigger | Action |
|---|---|
| `dispatch:` | Route to Open Brain only. Never write to CLAUDE.md or memory/ |
| `Remember` / `Remember this` / `Save This` / `Save to the Brain` / `To open brain` | Capture to Open Brain, offer Day One entry |
| `Add this to your instructions` / `Update CLAUDE.md` | Update this file |
| `Update memory` / `Add to memory` | Write to appropriate memory/ file |
