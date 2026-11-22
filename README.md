# hackIDLE Skills

> **Project moved.** The portable `iac-security-scanner` and `mesh-security` skills moved to [Open Control Tools](https://github.com/ethanolivertroy/open-ctrl-tools). In a monorepo checkout, start with `skills/skills/iac-security-scanner/SKILL.md` or `skills/skills/mesh-security/SKILL.md`. The generated Terrascan policy references and the insecure Terraform example stay in this archive. The `npx add-skill hackIDLE/skills` commands below install this archived snapshot.

A collection of security-focused agent skills from [hackIDLE](https://hackidle.com), following the [Agent Skills](https://agentskills.io) open standard. These skills enable AI agents to perform security analysis, compliance assessments, and remediation tasks.

## Available Skills

| Skill | Description |
|-------|-------------|
| [mesh-security](./skills/mesh-security/) | Analyze Istio, Consul, and Linkerd service mesh configurations for security vulnerabilities with NIST 800-53 control mappings |
| [iac-security-scanner](./skills/iac-security-scanner/) | Scan Terraform, K8s, CloudFormation, ARM, and Dockerfiles for security misconfigurations with NIST 800-53 mappings |

## Installation

### Quick Install (Recommended)

```bash
# Install all skills
npx add-skill hackIDLE/skills

# Or install a specific skill
npx add-skill hackIDLE/skills --skill mesh-security

# List available skills first
npx add-skill hackIDLE/skills --list
```

### Global vs Project Installation

```bash
# Global (available in all projects)
npx add-skill -g hackIDLE/skills

# Project-level (in current directory)
npx add-skill hackIDLE/skills
```

### Supported Agents

`add-skill` automatically detects and installs to:
- Claude Code (`~/.claude/skills/`)
- Cursor (`~/.cursor/skills/`)
- Codex (`~/.codex/skills/`)
- OpenCode (`~/.config/opencode/skill/`)
- Gemini CLI
- VS Code
- GitHub Copilot
- And more...

These skills follow the [Agent Skills specification](https://agentskills.io/specification) and work with any compatible agent platform.

### Manual Installation

If you prefer manual installation:

```bash
# Clone the repo
git clone https://github.com/hackIDLE/skills.git hackidle-skills

# Copy skills to Claude Code
cp -r hackidle-skills/skills/* ~/.claude/skills/

# Install dependencies (mesh-security only; iac-security-scanner has none)
cd ~/.claude/skills/mesh-security && npm install
```

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

### iac-security-scanner

Security scanning for Infrastructure as Code files:

- **Supported IaC:** Terraform (HCL), Kubernetes YAML, CloudFormation, ARM templates, Dockerfiles
- **Cloud Providers:** AWS (305 policies), Azure (178), GCP (234), Kubernetes (43), Docker (27), GitHub (3)
- **Total Policies:** 790 security checks derived from Terrascan
- **Compliance:** NIST 800-53 control mappings
- **Output:** Findings with severity levels, remediation guidance, compliance reports

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
- [mesh-config-analyzer](https://github.com/ethanolivertroy/mesh-config-analyzer) - The underlying analysis engine
