# audit-n8n-workflows

Comprehensive audit of the 404notfoundred/n8n-workflows repository.

## Contents

- **AUDIT-REPORT.md** - Complete categorization and findings
  - Active systems summary (AI Enablement, Weekly Status)
  - Obsolete systems scheduled for removal (Project Lifecycle, XFN, CopyCheck v0)
  - Systems under review and pending clarification
  - Cleanup checklist and recommendations

## Key Findings

### Active Systems (Keep)
- ✅ AI Enablement Program (`circle/ai-enablement/v1/`)
- ✅ Weekly Status Digest (`circle/weekly-status/v1/`)

### Obsolete Systems (Remove)
- ❌ Project Lifecycle System (entire umbrella: Handoff, Builder, Core)
- ❌ XFN System (migrated to Circle laptop)
- ❌ CopyCheck v0 (migrated to Circle laptop)

### Pending Clarification
- ⚠️ Resource Capture (check if standalone or dependent on removed systems)
- ❓ Router MCP (clarify if should stay in this repo or move to infrastructure repo)

### In Planning
- Marketing Data Platform (keep for future reference)

## Cleanup Action Items

The audit identified ~80+ workflow files across 3 systems that should be removed to reflect the strategic shift from n8n workflows to agents/skills/skill packages.

See AUDIT-REPORT.md for complete cleanup checklist.

## Generated

February 25, 2026  
By: OpenClaw Assistant  
For: Carol @ 404notfound / Circle Internet Financial
