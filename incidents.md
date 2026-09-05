# Production Incidents Referenced

A summary of the real-world MCP security incidents examined in the full research article. Each one traces back to the same pattern: a permissive default nobody revisited, a config left open "temporarily," or an older build silently redeployed over a patched one.

## Nginx-UI — CVE-2026-33032
- Disclosed by Yotam Perkal (Pluto Security), early 2026
- CVSS score: 9.8
- Root cause: the MCP message endpoint executed command-execution requests without requiring authentication

## OX Security MCP SDK Supply-Chain Disclosure
- Disclosed April 2026
- Architectural flaw in the official MCP SDKs, inherited by every downstream project built on the reference implementation
- Estimated 200,000 vulnerable instances, across a supply chain touching upward of 150 million package downloads
- Real-world impact included authenticated RCE against Letta AI, an unauthenticated takeover of LangFlow via exposed MCP configs, and a bypass of Flowise's security filters

## MCP Inspector RCE — CVE-2025-49596
- Disclosed by Oligo Security
- Critical remote-code-execution vulnerability in Anthropic's own MCP Inspector developer tool

## postmark-mcp — First Documented Malicious MCP Server
- Identified by Idan Dardikman (Koi Security)
- Moved roughly 1,500 downloads a week
- Reached an estimated 300 real organizations before detection
- Notable for demonstrating how MCP's discovery-driven distribution can spread a malicious package faster than traditional software supply chains
