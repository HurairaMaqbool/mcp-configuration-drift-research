# MCP Configuration Drift Research

[![Full Article](https://img.shields.io/badge/Read-Full%20Article-blue)](https://aisec.university/blog/mcp-configuration-drift)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

Independent security research examining how **configuration drift** — the gradual, undocumented divergence of a system from its approved baseline — behaves differently, and more dangerously, inside **Model Context Protocol (MCP)** deployments than it does in traditional infrastructure.

📄 **Full write-up:** [MCP Configuration Drift — AISec University](https://aisec.university/blog/mcp-configuration-drift)

---

## Overview

Configuration drift isn't a new problem. IT teams have spent decades chasing forgotten firewall rules, cloud resources that wander from their infrastructure-as-code definitions, and servers that slowly diverge from their approved image.

MCP inherits that same failure mode — but with a critical difference. **MCP's discovery protocol doesn't wait to be found.** It actively broadcasts whatever state a server is currently in to every connected client, the moment a client asks. A permission that gets quietly widened, or a "temporary" tool scope that never gets revoked, isn't sitting passively waiting for an audit — it's advertised across every connected tenant and can be acted on almost immediately by an autonomous agent.

On a multi-tenant deployment, that turns one small, well-intentioned engineering decision into exposure across every connected organization simultaneously.

## What This Research Covers

- **How MCP discovery works** — tool registration, permission scoping, and why the protocol's "advertise what's available" design is the core amplifier of drift risk
- **Real-world incident analysis** — a recurring pattern traced across four production disclosures (full detail in [`notes/incidents.md`](notes/incidents.md)):
  | Incident | Type | Impact |
  |---|---|---|
  | Nginx-UI — CVE-2026-33032 | Unauthenticated RCE via MCP endpoint | CVSS 9.8 |
  | OX Security MCP SDK disclosure | Supply-chain / architectural flaw | ~200,000 vulnerable instances |
  | MCP Inspector — CVE-2025-49596 | RCE in Anthropic's own dev tooling | Critical |
  | postmark-mcp | First documented malicious MCP server | ~300 organizations affected |
- **Why MCP drift is structurally different** from traditional IT/cloud drift — shared infrastructure, agents that act on whatever they discover, and inconsistent tenant isolation
- **Practical mitigations** — version-controlled configuration, continuous drift detection, tenant-scoped short-lived credentials, isolated execution contexts, and centralized MCP gateway policy enforcement

## Key Takeaway

> If your organization treats MCP tool and permission changes with less rigor than a firewall rule change, you already have configuration drift — the only open question is whether anyone has found it yet.

## Repository Contents

```
mcp-configuration-drift-research/
├── README.md            → this file
├── notes/
│   └── incidents.md     → detailed breakdown of the four incidents referenced above
└── references.md        → full source list
```

## References

Full source list, including the NSA AI Security Center's MCP guidance, the OWASP MCP Top 10 project, and the academic red-team study cited in the article, is available in [`references.md`](references.md).

## About the Author

Written after completing AI Security University's *MCP Security Fundamentals* course. Focus areas: AI/agent security, the Model Context Protocol, and retrieval-augmented generation (RAG) systems.

- **Full article:** https://aisec.university/blog/mcp-configuration-drift
- **LinkedIn:** https://www.linkedin.com/in/huraira-maqbool-b696a5277/
- **GitHub:** https://github.com/HurairaMaqbool
