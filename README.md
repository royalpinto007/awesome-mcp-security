# Awesome MCP Security [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated, **auto-updating** list of tools, standards, and research for securing **Model Context Protocol (MCP)** servers and clients, organized by what each one actually defends against.

MCP lets an agent call your tools. That power is the whole attack surface. A tool is just text the model trusts, so a malicious or compromised MCP server can hide instructions in a tool description, quietly change its behaviour after you approve it, over-reach the scope you thought you granted, or exfiltrate secrets through an innocent-looking call. This list catalogs the defenses.

**Browse and filter: [mcp-security.agentpostmortem.com](https://mcp-security.agentpostmortem.com)**

## Start here: the MCP threat model in one screen

- **Tool poisoning.** Hidden instructions inside a tool's name or description hijack the agent when it reads them. *Defense: scanners, guardrails.*
- **Rug pull.** A server passes review, then changes its tools after you trust it. *Defense: scanners on every update, pinning.*
- **Excessive scope.** A tool can do far more than its label implies (read every repo, not just one). *Defense: permission and sandboxing, gateways.*
- **Secret / data exfiltration.** Tool inputs or outputs smuggle out tokens and PII. *Defense: secrets and DLP, gateways.*
- **Cross-server shadowing.** One server's tool overrides or impersonates another's. *Defense: scanners, gateways.*

**The one rule:** treat every tool description and every tool output as untrusted input, exactly like a web page. The categories below are the controls that make that practical.

<!-- LIST:START -->
**46 entries**, auto-refreshed weekly. Star counts updated **2026-08-17**. Browse the filterable version at **[mcp-security.agentpostmortem.com](https://mcp-security.agentpostmortem.com)**.

### Scanners and auditors

- [invariantlabs mcp-scan](https://github.com/invariantlabs-ai/mcp-scan) `* 2.9k`: Scans installed MCP servers and tool descriptions for tool poisoning, prompt injection, and cross-server shadowing; the most-referenced MCP scanner.
- [Snyk agent-scan](https://github.com/snyk/agent-scan) `* 2.9k`: Snyk tooling for scanning AI-agent and MCP configurations for tool-poisoning and related risks.
- [Cisco AI Defense mcp-scanner](https://github.com/cisco-ai-defense/mcp-scanner) `* 1k`: Cisco AI Defense open-source scanner for detecting security risks in MCP servers.
- [SlowMist MCP Security Checklist](https://github.com/slowmist/MCP-Security-Checklist) `* 835`: Practical security checklist for MCP servers, clients, and tool developers.
- [mcpserver-audit](https://github.com/ModelContextProtocol-Security/mcpserver-audit) `* 21`: Community project for auditing MCP servers against a security baseline.
- [SecScanMCP](https://github.com/zakariaf/SecScanMCP) `* 5`: MCP scanner with 12+ analyzers, 117 YARA rules, and ML-assisted detection of prompt injection and tool poisoning.
- [skill-audit](https://github.com/royalpinto007/Skill-audit) `* 1`: Security scanner for agent skills: 31 rules, prompt-injection and exfil detection, SARIF output.
- [mcp-audit](https://github.com/royalpinto007/MCP-audit) `* 0`: Security scanner for MCP servers: 18 rules, SARIF output, run with npx mcp-audit.

### Tool poisoning and injection

- [mcp-injection-experiments](https://github.com/invariantlabs-ai/mcp-injection-experiments) `* 205`: Reference code that reproduces MCP tool-poisoning and injection attacks.
- [MCP Tool Poisoning Attacks (Invariant)](https://invariantlabs.ai/blog/mcp-security-notification-tool-poisoning-attacks): Original disclosure defining tool poisoning via hidden instructions in MCP tool descriptions.
- [GitHub MCP exploited (Invariant)](https://invariantlabs.ai/blog/mcp-github-vulnerability): Case study hijacking the GitHub MCP server via a malicious issue to reach private repos.
- [Toxic Flow Analysis (Invariant)](https://invariantlabs.ai/blog/toxic-flow-analysis1): A 'toxic flows' prompt-injection class across agentic systems and MCP servers.
- [Indirect prompt injection in MCP (Microsoft)](https://developer.microsoft.com/blog/protecting-against-indirect-injection-attacks-mcp): Microsoft guidance on mitigating indirect prompt injection in MCP tools.

### Firewalls and guardrails

- [Invariant Guardrails](https://github.com/invariantlabs-ai/invariant) `* 445`: Rule-based guardrail layer that sits as an MCP/LLM proxy to intercept and check tool calls.
- [mcp-guard (General Analysis)](https://github.com/General-Analysis/mcp-guard) `* 55`: Guardrail wrapper that filters malicious tool calls and responses for MCP servers.
- [MCP-Guard (GenTelLab)](https://github.com/GenTelLab/MCP-Guard) `* 21`: Detection framework, with an accompanying paper, for defending MCP integrations.
- [promptfoo MCP red-teaming](https://www.promptfoo.dev/docs/red-team/mcp-security-testing/): promptfoo module for automated red-teaming and security testing of MCP servers.

### Secure gateways and proxies

- [mcp-proxy](https://github.com/sparfenyuk/mcp-proxy) `* 2.7k`: Widely used MCP proxy (stdio/SSE bridging) often deployed as a control and isolation point.
- [ToolHive (Stacklok)](https://github.com/stacklok/toolhive) `* 2k`: Platform to run and manage MCP servers locally or on Kubernetes with credential isolation and policy guardrails.
- [mcp-gateway (Lasso)](https://github.com/lasso-security/mcp-gateway) `* 385`: Plugin-based open-source security gateway with token masking, PII detection, and prompt-injection filters.
- [secure-mcp-gateway (Enkrypt)](https://github.com/enkryptai/secure-mcp-gateway) `* 56`: Security gateway adding guardrails, auth, and monitoring in front of MCP servers.

### Permission, scope, sandboxing

- [agent-governance-toolkit (Microsoft)](https://github.com/microsoft/agent-governance-toolkit) `* 6k`: Toolkit for governance, access control, and policy over AI agents and MCP tools.
- [clerk mcp-tools](https://github.com/clerk/mcp-tools) `* 47`: Clerk libraries for adding scoped auth and permission handling to MCP servers.

### Secrets and exfiltration (DLP)

- [redact-mcp](https://github.com/r3352/redact-mcp) `* 6`: MCP component that redacts sensitive data flowing through tool calls.

### Authentication and authorization

- [mcpauth](https://github.com/mcpauth/mcpauth) `* 112`: OAuth/auth implementation for securing MCP server access.
- [MCP Authorization spec](https://modelcontextprotocol.io/docs/tutorials/security/authorization): Official MCP authorization tutorial covering OAuth-based access control.

### Offensive security and testing

- [mcp-security-hub (FuzzingLabs)](https://github.com/FuzzingLabs/mcp-security-hub) `* 760`: Hub of MCP security research, fuzzing, and tooling.
- [mcp-for-security](https://github.com/cyproxio/mcp-for-security) `* 629`: Collection of MCP servers wrapping offensive-security tools for pentest workflows.
- [secops-mcp](https://github.com/securityfortech/secops-mcp) `* 206`: SecOps-oriented MCP server bundling security tools for agents.

### Vulnerable-by-design targets

- [Damn Vulnerable MCP](https://github.com/harishsg993010/damn-vulnerable-MCP-server) `* 1.3k`: Reference vulnerable MCP with 10 graded challenges (injection, tool poisoning, rug-pull, shadowing).
- [mcp-vulnerabilities](https://github.com/Tomby68/mcp-vulnerabilities) `* 7`: Hands-on demos of common MCP vulns with a deep dive on prompt injection.
- [VulnerableMCP](https://github.com/integsec/VulnerableMCP) `* 3`: Intentionally vulnerable MCP server with 20+ exploits for research, CTF, and training.

### Spec and official guidance

- [MCP Security Best Practices (official)](https://modelcontextprotocol.io/docs/tutorials/security/security_best_practices): Official Model Context Protocol security best-practices documentation.
- [OWASP MCP Top 10](https://owasp.org/www-project-mcp-top-10/): OWASP top-10 risk catalog for MCP (e.g. MCP03 Tool Poisoning).
- [OWASP MCP Security Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/MCP_Security_Cheat_Sheet.html): Concise OWASP cheat sheet for securing MCP servers and clients.
- [OWASP Secure MCP Server Development Guide](https://genai.owasp.org/resource/a-practical-guide-for-secure-mcp-server-development/): OWASP GenAI practical guide for building secure MCP servers.
- [NSA/CISA MCP Security guidance](https://media.defense.gov/2026/Jun/02/2003943289/-1/-1/0/CSI_MCP_SECURITY.PDF): US government cybersecurity information sheet on securing MCP deployments.
- [CSA Agentic MCP Security Best Practices](https://labs.cloudsecurityalliance.org/agentic/agentic-mcp-security-best-practices-v1/): Cloud Security Alliance best-practices framework for agentic and MCP security.
- [Red Hat: MCP security risks and controls](https://www.redhat.com/en/blog/model-context-protocol-mcp-understanding-security-risks-and-controls): Vendor-neutral overview of the MCP threat model and mitigating controls.

### Research and papers

- [MCP: Landscape, Security Threats, Future](https://arxiv.org/abs/2503.23278): Foundational survey mapping MCP's attack surface across the server lifecycle.
- [MCPXKIT](https://arxiv.org/abs/2508.12538): Toolkit and taxonomy implementing 31 MCP attack methods across four classes.
- [MCP Security Bench (MSB)](https://arxiv.org/pdf/2510.15994): Benchmark for evaluating attacks against MCP in LLM agents.
- [When MCP Servers Attack](https://arxiv.org/pdf/2509.24272): Threat taxonomy and feasibility study of malicious MCP servers with mitigations.
- [MCP-Guard framework (paper)](https://arxiv.org/abs/2508.10991): Layered detection framework for defending MCP tool interactions.
- [MindGuard: Tool Poisoning Detection](https://arxiv.org/html/2508.20412v1): Detection approach specifically targeting MCP tool-poisoning attacks.

### Related lists

- [awesome-secure-mcp-servers](https://github.com/fuzzylabs/awesome-secure-mcp-servers) `* 0`: List of MCP servers validated through the mcp-scan security pipeline.

<!-- LIST:END -->

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Edit `data/tools.json`, run `node scripts/generate.mjs`, open a PR.

## License

[CC0 1.0](LICENSE) (public domain).
