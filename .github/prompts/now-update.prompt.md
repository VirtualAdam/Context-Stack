------# NOW (Notes On Work) Management Prompt

---
description: Create or update NOW.md file with minimal project state for seamless context recovery
tools: [read_file, create_file, replace_string_in_file, semantic_search, file_search]
mode: agent
---
Analyze the current codebase and recent conversation to create or update a minimal NOW.md file that captures essential project state for seamless context recovery.

## Analysis Steps

1. Review conversation history for problems being solved, decisions made, and tasks discussed
2. Check for existing NOW.md at repository root to determine if creating or updating
3. Scan codebase structure to understand the project (README, package.json, etc.)
4. Check for test files and results in common locations (tests/, reports/, .github/workflows/)

## NOW.md Structure

Generate/update the NOW.md file with this EXACT structure (keep under 500 words total):

```yaml
# NOW - Notes On Work
# Generated: <current UTC timestamp>
# Purpose: Minimal context for seamless project resumption

## META
canonical: true
updated: <YYYY-MM-DD>
version: <increment if updating, start at 0.1>

## STATE  
problem_solving: "<One sentence: what core problem does this repo solve?>"
current_focus: "<One sentence: what specific aspect/feature are we working on right now?>"
blocked_by: "<What's preventing progress? Be specific. Or 'nothing' if unblocked>"

## EVIDENCE
tests_passing:
  unit: <true | false | not_implemented>
  integration: <true | false | not_implemented>  
  evidence: "<path/to/last/test/report or 'none'>"
  last_run: "<YYYY-MM-DD or 'never'>"

## NEXT
immediate_task:
  intent: "<Single concrete task to do next - be specific>"
  done_when: "<Specific measurable outcome that proves completion>"
  evidence_required: ["<specific file/artifact that must exist when done>"]
  status: <pending | active | done>

## CONTEXT
key_decisions:
  - "<Only include decisions that would confuse someone reading the code>"
  - "<Keep list to 3 or fewer items>"
abandoned_approaches:
  - "<Approaches tried and rejected - prevent others from retrying>"
  - "<Keep list to 3 or fewer items>"
architecture: "<path/to/architecture/doc or 'none'>"
```



## Field Generation Rules

* **problem_solving** : Extract from README, package.json description, or conversation history. One clear sentence.
* **current_focus** : Based on most recent conversation/commits. What were we JUST working on?
* **blocked_by** : Look for mentioned errors, missing dependencies, waiting states. Be specific.
* **tests_passing** : Check for test files existence. Look for CI configs. Check reports/ or coverage/ directories.
* **immediate_task** : Pull from conversation or last TODO mentioned. Single, concrete action.
* **done_when** : Objectively verifiable (e.g., "when X file exists", "when Y test passes", "when API returns Z")
* **evidence_required** : Specific filename(s) that prove task completion
* **key_decisions** : Only non-obvious architectural choices that affect current development
* **abandoned_approaches** : Only what's necessary to prevent re-attempting failed solutions

## Quality Requirements

* Total file must be <500 words
* Each field must be filled (use "none", "not_implemented", or "nothing" rather than leaving blank)
* No markdown formatting beyond the structure shown
* No emojis
* Dates in YYYY-MM-DD format
* Paths relative to repo root
* This document is for GitHub Copilot to consume first, humans second. Prioritize clarity and brevity over completeness. The goal is instant reorientation, not comprehensive documentation.

## Output Format

After creating/updating NOW.md, provide a brief summary:

NOW.md has been [created/updated]. Key points:
- problem_solving: <brief statement>
- current_focus: <brief statement>
- blocked_by: <blocker or "nothing">
- immediate_task: <next action>

You can now safely step away from this project. Use /now-status when you return.
