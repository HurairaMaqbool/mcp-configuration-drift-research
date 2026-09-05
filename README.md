# MCP Configuration Drift Research

Independent security research on how configuration drift affects Model Context Protocol (MCP) deployments in multi-tenant AI agent systems.

Full write-up published on AISec University: [MCP Configuration Drift — Full Article](https://aisec.university/blog/mcp-configuration-drift)

## The Problem

Configuration drift — permissions, tool scopes, or settings quietly diverging from an approved baseline — isn't new. IT teams have dealt with it for years in the form of forgotten firewall rules and servers that slowly drift from their approved image.

MCP changes the stakes. Its discovery protocol doesn't wait to be found — it actively broadcasts whatever state a server is currently in to every connected client. So when a permission gets quietly widened, or a "temporary" tool scope is never revoked, that drifted state isn't sitting there passively waiting for an audit. It's advertised to every connected agent and can be acted on almost immediately.

On a multi-tenant deployment, that turns one small, well-intentioned configuration change into exposure across every connected organization.

## What This Research Covers

- How MCP discovery works — tool registration, permission scoping, and why the protocol's "advertise what's available" design is the core amplifier of drift risk
- Real-world incidents analyzed for a recurring pattern (see [notes/incidents.md](notes/incidents.md)):
  - Nginx-UI (CVE-2026-33032) — unauthenticated command execution via MCP
  - OX Security's MCP SDK supply-chain disclosure — architectural flaw affecting an estimated 200,000 instances
  - MCP Inspector RCE (CVE-2025-49596)
  - postmark-mcp — the first documented malicious MCP server
- Why MCP drift is structurally different from traditional IT/cloud configuration drift — shared infrastructure, agents that act on what they discover, and weak tenant isolation
- Practical mitigations for teams running MCP servers — version-controlled configuration, continuous drift detection, tenant-scoped short-lived credentials, isolated execution contexts, and MCP gateway policy enforcement

## Key Takeaway

> If your organization treats MCP tool and permission changes with less rigor than a firewall rule change, you already have configuration drift — the only open question is whether anyone has found it yet.

## Contents

- [`notes/incidents.md`](notes/incidents.md) — summary of the production incidents referenced in the research
- [`references.md`](references.md) — full source list

## References

See [references.md](references.md) for the complete list.

## About

Written after completing AISec University's MCP Security Fundamentals course. Focus areas: AI/agent security, Model Context Protocol, and retrieval-augmented generation (RAG) systems.

- Full article: https://aisec.university/blog/mcp-configuration-drift
- LinkedIn: https://www.linkedin.com/in/huraira-maqbool-b696a5277/
- GitHub: https://github.com/HurairaMaqbool
