# 🔄 Merge Automation for GitHub Repositories

## Overview
This project provides an automated and controlled way to synchronize changes from the **main branch** to long-lived **feature** or **release branches** across multiple GitHub repositories.  
It is designed for teams managing infrastructure and platform repositories where consistent branch alignment is critical for stability, release management, and compliance.

The automation is implemented using **GitHub Actions** and **GitHub CLI**, with support for:
- Dry-run execution
- Multi-repository orchestration
- Safety checks

---

## Why This Project Exists
In large infrastructure and platform environments, multiple repositories often share a common release cadence. Documentation updates, configuration changes, and infrastructure definitions are usually merged into the `main` branch first, but must also be propagated to release or feature branches such as `feature-0.1`.

Manual merges introduce risks:
- Human error during repetitive merge operations
- Inconsistent branch states across repositories
- Forgotten repositories during release preparation
- Lack of traceability and auditability
- Accidental overwrites or unresolved conflicts

This project eliminates these risks by providing a **repeatable, auditable, and automated merge process**.

---

## Key Challenges Addressed
- **Multi-Repository Coordination**: Centralizes merge logic and applies it consistently across all repositories.  
- **Safe Execution with Dry Run**: Preview merge results without pushing changes.  
- **Authentication & Non-Interactive Git Operations**: Uses secure tokens for reliable automation.  
- **Branch Consistency & Verification**: Validates source and target branches before merging.  
- **Conflict Visibility**: Surfaces conflicts clearly in logs, with optional issue creation.

---

## Problems Solved
- Ensures documentation/configuration changes in `main` are consistently reflected in feature/release branches  
- Eliminates manual merge steps during release cycles  
- Prevents silent failures caused by missing authentication or dry-run execution  
- Provides clear diagnostics when merges fail  
- Improves auditability through GitHub Actions logs and commit history  
- Reduces operational overhead for platform and infrastructure teams  

---

## How the Solution Works
1. Workflow identifies the list of repositories to process  
2. Each repository is cloned using GitHub CLI with authenticated access  
3. Target branch is checked out and synchronized with remote  
4. Source branch is merged using a standard merge strategy  
5. If dry-run mode is disabled, changes are pushed back to GitHub  
6. Results are logged per repository for traceability  

---

## Key Features
- ✅ Support for multiple repositories in a single workflow run  
- ✅ Configurable source and target branches  
- ✅ Dry-run mode for safe testing  
- ✅ Secure authentication using GitHub personal access tokens  
- ✅ Clear and actionable error reporting  
- ✅ Idempotent execution suitable for re-runs  

---

## Prerequisites
- GitHub Actions enabled for the organization or repository  
- GitHub personal access token with repository & workflow permissions  
- Repositories following a consistent branching strategy  
- GitHub CLI available in the runner environment  

---

## When to Use This Project
This solution is ideal for:
- Infrastructure-as-code repositories  
- Platform engineering teams  
- Organizations with multiple Terraform or Cloud Build repositories  
- Release management workflows requiring strict branch alignment  
- Teams that want to reduce manual Git operations  

---

## Future Improvements
- 🔹 Automatic issue creation on merge conflicts  
- 🔹 Slack or email notifications for merge results  
- 🔹 Per-repository merge strategy customization  
- 🔹 Integration with release tagging workflows  
- 🔹 Support for protected branch workflows via pull requests  

---

## Conclusion
This project standardizes and automates a critical but often overlooked part of the development and release lifecycle.  
By removing manual steps, enforcing consistency, and providing clear diagnostics, it significantly improves reliability and confidence when managing changes across multiple repositories.
