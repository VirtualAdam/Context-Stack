# NOW (Notes On Work)

**Prevent AI-generated code projects from becoming archaeological sites.**

## The Problem

You're working on a project. AI helps you generate code fast. You switch to another project. A week/month/year later, you come back and have no idea:

- What problem you were solving
- What was blocking you
- What you were about to try next
- Whether the tests actually pass or AI just claimed they did

Multiply this across dozens of AI-accelerated projects and you end up abandoning perfectly good code because the context is lost.

## The Solution

**One minimal file (`NOW.md`) at the root of every repo that:**

- Takes 30 seconds to generate/update via `/now-update` command
- Takes <5 minutes to read and fully reorient
- Prevents false "task completed" claims via evidence requirements
- Designed for GitHub Copilot to read and explain to humans

## Quick Start

### 1. Install NOW in Your Project

```bash
# Clone this repo
git clone https://github.com/VirtualAdam/now.git

# Copy .prompt folder into your project root
cp -r now/.prompt /path/to/your-project/
```

### 2. Create Your First NOW

In your project (with GitHub Copilot enabled):

```
You: /now-update
```

Copilot will analyze your codebase and conversation history and generate `NOW.md` at your repo root.

### 3. Update Before You Leave

At the end of your work session:

```
You: /now-update
```

Copilot updates the NOW with current state, blockers, and next steps.

### 4. Resume Work Later

When you return (tomorrow or next year):

1. Type `/now-status` to get instant reorientation from copilot using NOW.md
2. You now know exactly where you left off and what to do next

## What's in the NOW?

A minimal 5-section structure (<500 words):

```yaml
META          # Version, last updated
STATE         # What problem, current focus, what's blocking
EVIDENCE      # Test status with proof (no false claims)
NEXT          # Single immediate task with completion criteria
CONTEXT       # Key decisions & failed approaches (optional)
```

See [NOW.md](NOW.md) for the complete schema specification.

## Commands Reference

| Command         | What It Does                              | When to Use                                       |
| --------------- | ----------------------------------------- | ------------------------------------------------- |
| `/now-update` | Generate/update NOW.md with current state | First time setup or end of work session           |
| `/now-status` | Read and summarize existing NOW.md        | When returning to project for quick reorientation |

## Design Principles

1. **Ruthlessly minimal** - If it's not essential for reorientation, it's cut
2. **Evidence-based** - Claims require proof (files must exist)
3. **Machine-first** - Optimized for AI parsing, human-readable second
4. **Single source of truth** - Only one NOW per repo (canonical: true enforced)
5. **Force focus** - One immediate task at a time prevents diffusion
6. **No archaeology** - Small enough to read in one sitting

---

**TL;DR:** Copy `.prompt/` folder to your project. Type `/now-update` before you stop working. Never lose context again.
