# AI-Assisted Development Handbook

A best-practices reference for setting up projects to maximize AI coding tools like **Google Antigravity**, **GitHub Copilot**, and **Claude**.

---

## Why Prompt Engineering Matters for AI Coding

AI coding assistants are powerful, but they come with inherent limitations that can derail productivity if not properly managed. Understanding these challenges is the first step to working effectively with AI tools.

### Core Challenges

#### 1. Context Window Limits ("AI Amnesia")
AI models function as **"Staff Engineers with Amnesia"** — they possess vast general knowledge but have limited memory regarding your specific project.

- After ~10-15 conversation turns, the model begins to "forget" the original architecture
- Long conversations pollute the context with failed attempts and tangents
- The AI becomes "confused" by its own previous wrong answers

**Strategy**: 
- Use **explicit file tagging** (`@filename`) to load specific context into the conversation
- Define `context_files.md` rules to specify which files the AI must read
- Force "fresh chats" or "context dumps" to ensure the model works from a clean, accurate state

#### 2. Feature Creep & Overengineering
AI models tend to "future-proof" code by adding unnecessary abstractions, extra files, or architectural layers unless explicitly told not to.

- Generates unused utility functions "just in case"
- Creates elaborate class hierarchies for simple problems
- Adds configuration options nobody asked for

**Strategy**: Include "negative constraints" in prompts (e.g., "Do NOT add new files," "Do NOT use Tailwind," "Keep it simple").

#### 3. Improvised Architecture (Spec-First Workflow)
If you simply ask an AI to "build feature X," it will invent the structure on the fly, often leading to circular dependencies, inconsistent patterns, or "hacky" fixes.

- No clear separation of concerns
- Conflicting design patterns within the same codebase
- Tight coupling that makes future changes painful

**Strategy**: Enforce a mandatory **"Implementation Plan" Artifact** that must be approved before any code is generated. The AI must produce a design document, get user sign-off, and only then proceed to implementation.

#### 4. Hallucinations
Because models are "eager to please," they often hallucinate solutions rather than admitting limitations.

- Import libraries that don't exist
- Use methods that were deprecated years ago
- Invent variables to make a code block "compile"
- Reference non-existent files or APIs

**Strategy**: Always verify imports, run the code, and cross-check against official documentation.

#### 5. Silencing Bugs
AI tools often take the path of least resistance to make code run.

- Delete error handling to avoid exceptions
- Remove logging statements to hide warnings
- Hardcode variables to bypass configuration bugs
- Catch-all exception handlers that swallow real errors

**Strategy**: Review generated code carefully for removed safety measures. Insist on proper error handling in prompts.

#### 6. Tool Misalignment
Using the wrong AI tool for the task leads to poor results.

- Using **completion tools** (Copilot) to architect modules → disjointed code lacking "whole project" vision
- Using **reasoning tools** (Claude) for minor syntax edits → inefficient use of powerful capabilities
- Using **chat tools** for repetitive file edits → better suited for agentic tools with file access

**Strategy**: Match the tool to the task. Use agentic tools for multi-file changes, completion tools for line-by-line coding, and reasoning tools for design decisions.

#### 7. Conversational Rabbit Holes ("Anti-Rabbit Hole" Protocol)
The most common failure mode: you ask for a fix, the AI breaks something else, and after multiple turns, the code becomes unrecognizable.

- Context gets polluted with failed attempts
- AI starts guessing ("try this instead") rather than analyzing root cause
- Each fix introduces new bugs in a degrading spiral

**Strategy**:
- Apply a **"Stop Loss" rule**: If a fix fails 3 times, STOP and reset the conversation
- **Spawn fresh agents** for every new task to avoid context pollution
- Use workflows that enforce structured checkpoints rather than open-ended chat

---

## What This Repository Provides

This handbook implements a **structured `.agent/` configuration** that guides AI tools to produce better, safer code through explicit constraints and workflows.

### 📁 Project Structure

```
.agent/
├── skills/       # Role-based AI personas with specialized expertise
├── rules/        # Global constraints & governance (always active)
├── workflows/    # Step-by-step development processes (triggered on demand)
├── prompts/      # Pre-built prompt templates for common scenarios
└── checklists/   # Verification checklists for quality gates
```

---

## 🎭 Skills (Role-Based Personas)

Skills define **specialized AI roles** that can be invoked for specific tasks. Each skill has focused expertise and behavioral constraints.

| Skill | Purpose | When to Use |
|-------|---------|-------------|
| **Architect** | Design solutions, produce specs, define boundaries | Starting new features, major refactors |
| **Implementer** | Write code strictly following specs | After architecture is approved |
| **Tester** | Generate tests, enforce TDD, cover edge cases | Before or alongside implementation |
| **Reviewer** | Find security flaws, style violations, anti-patterns | Before merging code |
| **Debugger** | Root cause analysis with minimal, targeted fixes | When something breaks |
| **Security Expert** | OWASP principles, input validation, threat modeling | Security-sensitive features |
| **Explainer** | Generate documentation, clarify complex logic | Onboarding, knowledge sharing |

### How Skills Work

Skills are defined in `SKILL.md` files that instruct the AI:
- What role to assume
- What process to follow
- What constraints to respect
- What output format to produce

**Example**: The Architect skill explicitly states "Do NOT generate implementation code until the plan is approved" — preventing the common failure of jumping straight into coding.

---

## 📋 Rules (Global Constraints)

Rules are **always-on guardrails** that the AI must follow in every interaction. They act as the "governance layer" that prevents common AI failure modes.

| Rule File | Purpose |
|-----------|---------|
| `universal_core_rules.md` | Spec-first workflow, TDD mandate, security-first implementation |
| `context_files.md` | Which files to read for project context (prevents hallucinations) |
| `roles.md` | Available persona definitions and switching protocols |
| `java_governance.md` | Language-specific constraints (strict typing, JavaDoc requirements) |

### Key Principles from Universal Rules

1. **Specification-First**: Draft a clear plan before writing any code
2. **Test-Driven Development**: Write tests BEFORE implementation
3. **Context Awareness**: Read provided docs to avoid hallucinations
4. **No Reinventing the Wheel**: Respect existing abstractions
5. **Security-First**: Assume all output is untrusted
6. **Safe Refactoring**: Preserve behavior unless explicitly told otherwise

---

## 🔄 Workflows (Development Processes)

Workflows define **repeatable, step-by-step procedures** for common development tasks. They ensure consistency and prevent skipped steps.

| Workflow | Use Case | Key Steps |
|----------|----------|-----------|
| `/greenfield_development` | New project from scratch | Init → Architecture → Scaffold → Implement |
| `/feature_development` | Adding features to existing code | Context Load → Arch Check → Tests → Implement → Review |
| `/bug_fixing` | Debugging with stack traces | Reproduce → Root Cause → Minimal Fix → Regression Test |
| `/refactoring` | Safe behavior-preserving refactors | Snapshot → Transform → Verify Equivalence |
| `/code_review` | Structured code analysis | Security → Style → Logic → Performance |

### Workflow Anatomy

Each workflow typically includes:
1. **Context Loading** — Read relevant specs and code
2. **Planning Phase** — Propose approach, get approval
3. **Test-First Entry** — Write failing tests first
4. **Implementation** — Write code to pass tests
5. **Verification** — Review against guidelines

---

## How It All Works Together

```
User Request
     │
     ▼
┌─────────────┐
│  Workflow   │  ← Defines the PROCESS (what steps to follow)
│  Selected   │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│   Rules     │  ← Enforces CONSTRAINTS (what NOT to do)
│  Applied    │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│   Skill     │  ← Provides EXPERTISE (how to think about it)
│  Activated  │
└──────┬──────┘
       │
       ▼
  Guided Output
```

**Example Flow**:
1. User: "Add user authentication"
2. `/feature_development` workflow is triggered
3. Universal rules require spec-first approach
4. **Architect** skill drafts the authentication design
5. User approves the plan
6. **Tester** skill writes auth test cases
7. **Implementer** skill writes code to pass tests
8. **Reviewer** skill validates security patterns

---

## Quick Start

### 1. Copy Configuration
```bash
cp -r .agent/ /path/to/your/project/
```

### 2. Customize for Your Stack
- Edit `rules/` files for your language/framework constraints
- Add language-specific governance (e.g., `python_governance.md`)
- Customize `context_files.md` to point to your key files

### 3. Use Workflows
Trigger workflows using slash commands:
```
/feature_development Add a payment processing module
/bug_fixing Error: NullPointerException in UserService.java:42
```

### 4. Invoke Skills
Switch AI personas by referencing skills:
```
"Act as the Architect and design a caching layer"
"As the Security Expert, review this auth implementation"
```

---

## Anti-Pattern Prevention

This configuration specifically prevents common AI failure modes:

| Failure Mode | Prevention Mechanism |
|--------------|---------------------|
| Conversational drift | Workflows enforce structured steps |
| Hallucinated imports | Context files specify real dependencies |
| Overengineering | Negative constraints in rules |
| Skipped tests | TDD mandate in universal rules |
| Security holes | Security-first rule + Security Expert skill |
| Architectural chaos | Spec-first workflow + Architect skill |

---

## Contributing

Feel free to add new skills, rules, or workflows that help tame AI coding assistants. Contributions that address additional AI failure modes are especially welcome!

### Adding a New Skill
1. Create folder: `.agent/skills/your_skill/`
2. Add `SKILL.md` with frontmatter (name, description) and instructions
3. Define the role, process, constraints, and expected output

### Adding a New Workflow
1. Create file: `.agent/workflows/your_workflow.md`
2. Add frontmatter with description
3. Define numbered steps with clear entry/exit criteria
