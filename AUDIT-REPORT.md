# n8n Workflows Repository Audit Report

**Date:** February 25, 2026  
**Audited By:** OpenClaw Assistant  
**Repo:** https://github.com/404notfoundred/n8n-workflows.git  
**Status:** Read-only audit, no modifications made

---

## Executive Summary

The n8n-workflows repository is being consolidated as the team transitions to an **agents/skills/skill packages strategy** for internal tooling. Current assessment:

- **2 Active Systems** (AI Enablement, Weekly Status) — Keep and maintain
- **3 Obsolete Systems** (Project Lifecycle, XFN, CopyCheck v0) — **Remove from repo**
- **1 Planning System** (Marketing Data Platform) — Keep for future reference
- **1 Ambiguous System** (Router MCP) — Clarify ownership/location

**Key Recommendation:** Delete `internal/project-lifecycle/v1/`, `circle/xfn/v2/`, and `circle/copycheck/v0/` to reflect the active migration to agents/skills architecture.

---

## Repository Structure Overview

```
n8n-workflows/
├── config/                          # Centralized configuration
├── internal/                        # 404/Zenflow systems
│   ├── project-lifecycle/v1/        # ❌ OBSOLETE - Remove
│   ├── resource-capture/            # ⚠️  Under review
│   ├── router-mcp/                  # ❓ UNKNOWN - Clarify
│   ├── claude-skills/               # Reference only
│   └── claude-code-setup/           # Reference only
├── circle/                          # Circle client systems
│   ├── xfn/v2/                      # ❌ OBSOLETE - MIGRATED to Circle laptop
│   ├── copycheck/v0/                # ❌ OBSOLETE - MIGRATED to Circle laptop
│   ├── ai-enablement/v1/            # ✅ ACTIVE
│   ├── weekly-status/v1/            # ✅ ACTIVE
│   └── marketing-data-platform/     # PLANNING
├── archive/                         # Deprecated migrations
└── internal-docs/                   # Internal documentation
```

---

## Detailed Categorization

### ✅ ACTIVE SYSTEMS (Keep)

#### 1. **AI Enablement Program** (`circle/ai-enablement/v1/`)
- **Status:** ACTIVE
- **Purpose:** Marketing AI Enablement Program - AI Tips, Newsletter, Events automation
- **Last Updated:** In projects.json
- **Workflows:** 7 workflows listed (WF-AE-001 through WF-AE-007)
- **Assessment:** Keep as-is.

#### 2. **Weekly Status Digest** (`circle/weekly-status/v1/`)
- **Status:** ACTIVE
- **Purpose:** Automated weekly status digest generation from Slack and GitHub
- **Last Updated:** 2026-01-04 (recent backups)
- **Workflows:** 6 workflows
- **Assessment:** Keep as-is.

---

### ⚠️ UNDER REVIEW

#### 1. **Resource Capture** (`internal/resource-capture/`)
- **Status:** Unclear (appears active but linked to Project Lifecycle)
- **Purpose:** Slack resource capture and Notion indexing
- **Workflows:** WF-050
- **Note:** If this is a standalone utility, keep. If dependent on Project Lifecycle system (which is OBSOLETE), remove.
- **Action:** Clarify purpose and dependencies before cleanup.

---

### ❌ OBSOLETE SYSTEMS (Remove from Repo)

#### 1. **Project Lifecycle System (Entire Umbrella)** (`internal/project-lifecycle/v1/`)
- **Status:** OBSOLETE - Strategy shifted to agents/skills
- **Components:** 
  - Handoff (WF-001 to WF-011, WF-Session-Cache)
  - Builder (WF-002, WF-002A to WF-002G)
  - Core (WF-014 to WF-050)
- **Purpose:** Project intake, lifecycle management, workflow version control
- **Assessment:** The entire internal tooling strategy is shifting from n8n workflows to agents/skills/skill packages. This system is superseded.
- **Action:** **DELETE `internal/project-lifecycle/v1/` directory entirely.**
- **Files to Remove:** ~41 workflow files across handoff, builder, and core components

#### 2. **XFN System** (`circle/xfn/v2/`)
- **Status:** OBSOLETE - MIGRATED to Circle laptop
- **Purpose:** Cross-functional team approvals for Circle
- **Assessment:** MIGRATED to Circle's n8n instance. No longer needed in this repo.
- **Action:** **DELETE `circle/xfn/v2/` directory entirely.**
- **Files to Remove:** ~20 workflow backup files

#### 3. **CopyCheck v0** (`circle/copycheck/v0/`)
- **Status:** OBSOLETE - MIGRATED to Circle laptop
- **Purpose:** Document compliance with pgvector prototype
- **Assessment:** MIGRATED to Circle's n8n instance and replaced by Vertex AI approach. No longer needed.
- **Action:** **DELETE `circle/copycheck/v0/` directory entirely.**
- **Files to Remove:** ~20+ workflow backup files

---

### ⚠️ PLANNING/AMBIGUOUS

#### 1. **Marketing Data Platform** (`circle/marketing-data-platform/`)
- **Status:** PLANNING
- **Purpose:** Marketing data inventory and platform integration
- **Assessment:** Not yet implemented. Keep as placeholder for future development.
- **Action:** Keep directory and any planning documents.

#### 2. **Router MCP** (`internal/router-mcp/`)
- **Status:** UNKNOWN - Needs clarification
- **Purpose:** MCP server for routing requests to backend services (Richard's project)
- **Type:** TypeScript/Node.js code (not n8n workflows)
- **Assessment:** Unclear whether this should be in n8n-workflows repo or separate infrastructure repo.
- **Action:** **Ask Carol** - Does this belong here, or should it move to a dedicated backend/infrastructure repository?

---

## Configuration & Documentation Status

### Configuration Files

| File | Status | Notes |
|------|--------|-------|
| `config/projects.json` | OBSOLETE | References obsolete Project Lifecycle system. Update after removing folders. |
| `config/users.json` | OBSOLETE | Likely obsolete since Project Lifecycle (handoff system) is obsolete. |
| `config/README.md` | REFERENCE | Keep as reference. |

### Documentation Files

| File | Status | Notes |
|------|--------|-------|
| `README.md` | UPDATE NEEDED | Update to reflect removal of obsolete systems |
| `CLAUDE.md` | UPDATE NEEDED | Update references to removed systems |
| `CHANGELOG.md` | KEEP | Maintain as historical record |
| `CREDENTIALS.md` | REVIEW | May reference removed systems |
| `KNOWN_ISSUES.md` | REVIEW | May reference removed systems |
| `internal-docs/` | KEEP | Reference documentation |

### Supporting Folders

| Folder | Status | Action |
|--------|--------|--------|
| `internal/claude-skills/` | REFERENCE | Keep as reference for Claude Code integration |
| `internal/claude-code-setup/` | REFERENCE | Keep as reference/setup docs |
| `archive/` | REVIEW | Consider cleanup of old migration scripts after main cleanup |

---

## Cleanup Checklist

**Before removing files:**
- [ ] Verify Project Lifecycle workflows are no longer in use on Carol's n8n instance
- [ ] Verify XFN workflows are fully migrated to Circle's n8n instance
- [ ] Verify CopyCheck v0 workflows are fully migrated to Circle's n8n instance
- [ ] Check if resource-capture has dependencies on removed systems
- [ ] Clarify Router MCP ownership (keep or move?)

**Deletion steps:**
- [ ] Delete `internal/project-lifecycle/v1/` directory (41 workflows, backups, logs)
- [ ] Delete `circle/xfn/v2/` directory (20 backup workflows)
- [ ] Delete `circle/copycheck/v0/` directory (20+ backup workflows)
- [ ] Update `config/projects.json` - remove obsolete project entries
- [ ] Update `README.md` - reflect current active systems
- [ ] Update `CLAUDE.md` - remove references to deleted systems
- [ ] Commit with message: `cleanup: remove obsolete n8n systems (Project Lifecycle, XFN, CopyCheck v0)`

**Post-cleanup:**
- [ ] Review and potentially remove `config/users.json` if no longer used
- [ ] Archive old backup snapshots or implement retention policy
- [ ] Decide on Router MCP location (keep or move to separate repo)

---

## Files Audited

- ✅ Repository structure
- ✅ README.md
- ✅ CHANGELOG.md
- ✅ config/projects.json
- ✅ internal/project-lifecycle/v1/ structure
- ✅ internal/resource-capture/ structure
- ✅ internal/router-mcp/ structure
- ✅ circle/xfn/v2/ structure
- ✅ circle/copycheck/v0/ structure
- ✅ circle/ai-enablement/v1/ structure
- ✅ circle/weekly-status/v1/ structure
- ✅ circle/marketing-data-platform/ structure
- ✅ archive/ structure

---

## Summary

**Active Systems to Keep:** 2  
**Systems to Remove:** 3  
**Systems Under Review:** 1  
**Systems in Planning:** 1  
**Systems Needing Clarification:** 1

**Total Estimated Deletions:**
- Directories: 3
- Workflow files: ~80+
- Backup snapshots: 20+

This cleanup reflects the team's strategic shift from n8n workflows to agents/skills/skill packages for internal tooling. After completion, the repo will contain only active Circle-facing workflows and planning documents.

---

**Audit Status:** Complete  
**Recommendation:** Proceed with cleanup after verifying migration status of deleted systems  
**Next Step:** Create new issue or task to execute cleanup checklist  

---

*Report Generated: February 25, 2026*  
*Auditor: OpenClaw Assistant*
