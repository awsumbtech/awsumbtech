# Brian Awsumb

**CTO / COO / CIO / CISO at [New Edge IT Services](https://newedge-it.com)**, an MSP/MSSP serving professional services firms (law, CPA, medical, financial) in the 10 to 300 user range.

I build the automation and AI tooling that lets a small IT team run like a much larger one. Most of my work sits at the intersection of the Microsoft security stack (Entra, Intune, Defender, Purview, CIPP/GDAP), MSP operations tooling, and AI agents that can actually operate those systems. I also lead our security service line, built around CIS Controls, the FTC Safeguards Rule, HIPAA, and vCISO delivery.

> Most of my production code lives in private repositories because it touches client environments. The case studies below describe that work; I'm happy to walk through any of it live.

---

## Featured work

### MCP server platform for MSP operations
**Problem:** Technicians were jumping between the PSA, the documentation platform, M365 tenant tooling, and security consoles to answer a single ticket. Context lived in five places, so steps got missed.

**What I built:** A set of [Model Context Protocol](https://modelcontextprotocol.io) servers that give AI agents direct, structured access to our real operations stack:
- **SuperOps MCP server**: TypeScript, MCP SDK + Zod schemas, full coverage of the SuperOps GraphQL API across 128 tools (tickets, assets, clients, contracts, scripts, knowledge base, billing)
- **Hudu MCP server**: TypeScript REST client covering companies, articles, assets, and procedures; the core was hand-built, and the remaining tool surface was written as a spec and generated with AI coding agents
- Agent access to CIPP/Microsoft Graph, Huntress, and Check Point Harmony alongside the above
- Hosted on Azure (East US 2) in our own tenant

**Result:** A technician can ask one plain-language question and get an answer that combines ticket history, documentation, and live tenant data. AI moved from a side chat window into the service delivery workflow. Next phase: an internal assistant with tool access controlled by the user's Entra identity.

**Stack:** TypeScript, Node.js, MCP SDK, Zod, GraphQL, REST, Azure

---

### Conditional Access audit tool (`ca_audit.py`)
**Problem:** Conditional Access policies drift. Exclusions pile up, new apps and users slip outside coverage, and the Entra portal makes it hard to see the whole picture at once.

**What I built:** A Python tool that pulls a tenant's Conditional Access configuration through Microsoft Graph and produces a self-contained HTML report: a coverage grid showing which users and apps each policy actually protects, plus an exclusion audit that surfaces every exception for review.

**Result:** A repeatable security assessment deliverable for client reviews, turning a manual portal crawl into a single report a client can read.

**Stack:** Python, Microsoft Graph API, Entra ID, HTML reporting

---

### Daily ticket report runbook
**Problem:** Leadership needed a daily view of open work without logging into the PSA and building filters.

**What I built:** An Azure Automation runbook that queries SuperOps over GraphQL, assembles a daily ticket summary, and delivers it by email through Microsoft Graph.

**Result:** A hands-off daily operations report that runs on schedule with no server to maintain.

**Stack:** PowerShell, Azure Automation, GraphQL, Microsoft Graph

---

### Browser phishing protection rollout across clients
**Problem:** Deploying a browser-based M365 phishing protection extension across many clients needed per-client allowlists that stayed accurate, auditable, and safe from accidental edits.

**What I designed:**
- Per-client allowlists in a version-controlled JSON file, each inheriting from a global baseline
- The global baseline locked inside the deployment template so only leadership can change it
- A documentation asset for every allowlist entry recording URL pattern, who validated it, how, why, the ticket reference, and date added
- Deployment through RMM scripts, applied immediately when an entry is added, plus a runtime pull so new devices always get the current list
- A ticket runbook whose tasks must all be completed before an allowlist request can close

**Result:** Fleet-wide phishing protection with a clear audit trail for every exception, delegated safely to L1 technicians.

**Stack:** PowerShell, SuperOps RMM, Hudu, GitHub Pages, JSON

---

### Endpoint and network tooling
- **Offboard-LocalAccount.ps1**: PowerShell endpoint offboarding script deployed through the RMM
- **Awsumb NetMon**: Python network discovery agent

---

## Architecture and consulting
- Designed a Revit-on-Azure Virtual Desktop architecture for an architecture/engineering firm
- Delivered RFP analysis and co-managed IT engagement planning for prospective clients
- Standardizing client PC deployment on Windows Autopilot

## Outside of work
I'm a solo game developer:
- **Crystals of Ruin**: a classic-style JRPG built in Godot 4
- **Frontier Outpost**: a browser game in React and TypeScript

---

## Toolbox
**Microsoft:** Entra ID, Intune, Defender, Purview, M365 Business Premium, CIPP/GDAP, Azure, Azure Automation, Microsoft Graph
**MSP and security:** SuperOps, Hudu, Huntress, Check Point Harmony, Axcient, Keeper, ScreenConnect, Cloudflare
**Languages and frameworks:** TypeScript, Python, PowerShell, GraphQL, Next.js, Godot
**AI:** MCP server development, AI coding agents, LLM APIs

## Contact
<!-- Add LinkedIn URL here, or delete this line -->
- Work: [New Edge IT Services](https://newedge-it.com)
