# Security Agent Skills

A collection of security-focused agent skills following the [Agent Skills](https://agentskills.io) open standard. These skills enable AI agents to perform security analysis, compliance assessments, and remediation tasks.

## Available Skills

| Skill | Description |
|-------|-------------|
| [mesh-security](./skills/mesh-security/) | Analyze Istio, Consul, and Linkerd service mesh configurations for security vulnerabilities with NIST 800-53 control mappings |

## Installation

### Claude Code

Copy the skill directories to your Claude Code skills folder:

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/security-agent-skills.git

# Copy skills to Claude Code
cp -r security-agent-skills/skills/* ~/.claude/skills/

# Install dependencies
cd ~/.claude/skills/mesh-security && npm install
```

### Other Compatible Agents

These skills follow the [Agent Skills specification](https://agentskills.io/specification) and work with any compatible agent platform including:
- Gemini CLI
- Cursor
- VS Code
- GitHub Copilot
- And more

## Skills Overview

### mesh-security

Comprehensive security analysis for service mesh configurations:

- **Supported Meshes:** Istio, Consul, Linkerd
- **Security Checks:** mTLS, RBAC/ACL, TLS settings, certificate management, traffic policies
- **Compliance:** NIST 800-53 Rev 5 control mappings, FedRAMP reports
- **Output:** Findings with severity levels, remediation guidance, compliance reports

**Sub-skills included:**
- `mesh-remediation` - Generate and apply security fixes
- `mesh-compliance-reporter` - Generate FedRAMP/NIST compliance reports

**Quick Start:**
```bash
# Analyze a mesh config
node ~/.claude/skills/mesh-security/lib/analyzer-wrapper.js ./istio-config.yaml

# Generate remediation plan
node ~/.claude/skills/mesh-security/lib/remediation-engine.js ./consul-config.json

# Create FedRAMP compliance report
node ~/.claude/skills/mesh-security/lib/report-generator.js ./linkerd-config.yaml --fedramp
```

## Contributing

Contributions welcome! To add a new security skill:

1. Create a new directory under `skills/`
2. Add a `SKILL.md` following the [specification](https://agentskills.io/specification)
3. Include any supporting scripts in `lib/`
4. Add reference documentation in `references/`
5. Submit a pull request

## License

MIT License - see [LICENSE](./LICENSE) for details.

## Related Projects

- [Agent Skills Specification](https://agentskills.io)
- [Anthropic Skills Examples](https://github.com/anthropics/skills)
- [mesh-config-analyzer](https://github.com/YOUR_USERNAME/mesh-config-analyzer) - The underlying analysis engine
