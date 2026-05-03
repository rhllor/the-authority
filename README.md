# The Authority

> _"The Spirit of the 21st Century"_

**The Authority** is a GitHub Copilot agent that orchestrates a team of specialized sub-agents to tackle complex software architecture problems. Inspired by Warren Ellis's comic series, each team member embodies a specific engineering domain and brings a distinct, uncompromising perspective.

Instead of a single generic AI response, you get a structured, multi-perspective architectural analysis — from domain design to security, infrastructure, performance, and integration.

## The Team

| Member | Domain | Expertise |
| --- | --- | --- |
| **Jenny Quantum** _(Authority)_ | Orchestration | Clarifies requirements, deploys the team, synthesizes decisions |
| **The Engineer** | Core Domain | DDD, Hexagonal Architecture, Microservices |
| **Midnighter** | Security & Edge Cases | Threat modeling, OWASP, Chaos Engineering, Observability |
| **Swift** | Integration & Velocity | Event-Driven Architecture, API Design, Async Workflows |
| **Jack Hawksmoor** | Cloud Infrastructure | Kubernetes, CI/CD, SRE, IaC |
| **Apollo** | Performance & Scalability | Performance tuning, Caching, Load testing, Capacity planning |
| **The Doctor** | Memory & Persistence | State management, Database design, CQRS, Event Sourcing |
| **The Carrier** | Permanent Documentation | ADR generation, Architecture specifications, Decision formalization |

## How It Works

The Authority follows a strict protocol before producing any output:

1. **Intelligence Gathering** — Jenny Quantum refuses to act on vague requirements. She asks structured clarifying questions until the problem is well-defined.
2. **Mission Briefing** — A shared context document is prepared and sent to each relevant team member.
3. **Team Deployment** — Specialists are invoked in sequence. Each one receives the briefing _plus_ the feedback already expressed by previous members, so later analyses build on earlier ones.
4. **Synthesis** — Jenny Quantum collects all perspectives, resolves tensions, and delivers a unified architectural recommendation.


## Installation

The Authority requires **GitHub Copilot** with **agent mode** enabled in VS Code.

The repository contains two types of files:

- `.github/agents/authority.agent.md` — the main agent definition
- `.github/skills/*/SKILL.md` — one skill file per team member

### Option 1 — Single Project

Copy the `.github/` folder from this repository into the root of your project:

```bash
# From inside your project
cp -r /path/to/the-authority/.github .
```

Or clone this repo and move the folder:

```bash
git clone https://github.com/your-org/the-authority.git
cp -r the-authority/.github your-project/
```

GitHub Copilot will automatically detect agents and skills inside `.github/agents/` and `.github/skills/` when you open the project in VS Code.

### Option 2 — Global (All Projects)

VS Code loads `.agent.md` and `SKILL.md` files from the user prompts folder (`~/.copilot/`) and makes them available across all workspaces. Copy the agent file there to register it globally.

**macOS / Linux:**

```bash
# Agent (global — available in all workspaces)
PROMPTS_DIR="$HOME/.copilot"
mkdir -p "$PROMPTS_DIR/agents"
cp .github/agents/authority.agent.md "$PROMPTS_DIR/agents/"
mkdir -p "$PROMPTS_DIR/skills"
cp -r .github/skills/* "$PROMPTS_DIR/skills/"
```

**Windows:**

```powershell
# Agent (global — available in all workspaces)
$promptsDir = "$HOME\.copilot"
New-Item -ItemType Directory -Force $promptsDir
New-Item -ItemType Directory -Force "$promptsDir\agents"
Copy-Item .github\agents\authority.agent.md "$promptsDir\agents\"
New-Item -ItemType Directory -Force "$promptsDir\skills"
Copy-Item -Recurse .github\skills\* "$promptsDir\skills\"
```

After copying, restart VS Code. The `authority` agent will appear in the Copilot agent picker in any workspace, and will use the skills present in that project's `.github/skills/` folder.

## Usage

1. Open the **GitHub Copilot Chat** panel in VS Code (`⌃⌘I` / `Ctrl+Alt+I`)
2. Switch to **Agent mode** using the mode selector at the bottom of the chat input
3. Select **`authority`** from the agent list
4. Describe your architectural problem

**Example prompts:**

```MARKDOWN
Design a scalable event-driven order processing system for an e-commerce platform
expecting 50k orders/day at peak.
```

```MARKDOWN
We need to migrate a monolithic Rails app to microservices. The team is 8 engineers,
we have a PostgreSQL database with 5 years of data, and we can't afford downtime.
```

```MARKDOWN
Review the security posture of our current API gateway design and suggest improvements.
```

Jenny Quantum will ask clarifying questions if the problem isn't well-specified, then deploy the relevant team members and synthesize their findings.

## Repository Structure

```
.github/
├── agents/
│   └── authority.agent.md       # Main agent — Jenny Quantum
└── skills/
    ├── the-engineer/
    │   └── SKILL.md             # DDD & Hexagonal Architecture
    ├── midnighter/
    │   └── SKILL.md             # Security & Chaos Engineering
    ├── swift/
    │   └── SKILL.md             # Integration & Event-Driven
    ├── jack-hawksmoor/
    │   └── SKILL.md             # Cloud & DevOps
    ├── apollo/
    │   └── SKILL.md             # Performance & Scalability
    ├── the-doctor/
    │   └── SKILL.md             # State & Persistence
    └── carrier/
        ├── SKILL.md             # ADR & Spec generation
        └── template/
            ├── adr.md           # ADR template
            └── spec.md          # Spec template
```

## Requirements

- VS Code 1.99 or later
- GitHub Copilot subscription with agent mode enabled
- The `run_skill` tool must be available (included in agent mode by default)
