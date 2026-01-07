# Merge Automation for GitHub Repositories

## Overview

This project provides an automated and controlled mechanism to synchronize changes from long lived feature or release branches into the main branch across multiple GitHub repositories.

It is designed for platform, infrastructure, and DevOps teams that manage multiple repositories and require a consistent, auditable, and repeatable process to promote validated changes into the main branch while maintaining operational stability and compliance.

The automation is implemented using GitHub Actions and GitHub CLI and supports dry run execution, multi repository orchestration, and built in safety checks.

---

## Why This Project Exists

In enterprise environments, feature or release branches such as `feature-0.1` are often used to stabilize changes before they are promoted to the main branch. These branches typically contain validated infrastructure updates, configuration changes, and documentation that must eventually become the source of truth in `main`.

Manually merging feature branches back into `main` across multiple repositories introduces significant risk and operational overhead.

Common challenges include:

- Inconsistent promotion of changes across repositories  
- Human error during repetitive merge operations  
- Missed repositories during release promotion  
- Lack of traceability and audit evidence  
- Authentication failures during non interactive merges  
- Unclear visibility into merge conflicts  

This project addresses these challenges by providing a standardized, automated workflow to promote changes from feature branches into `main` in a controlled and auditable manner.

---

## Key Challenges Addressed

- **Multi Repository Coordination**  
  Centralizes merge execution and applies the same promotion logic across all repositories involved in a release.

- **Safe Execution with Dry Run**  
  Allows teams to validate merge behavior without pushing changes, reducing the risk of unintended updates to `main`.

- **Authentication and Non Interactive Git Operations**  
  Uses secure GitHub personal access tokens to ensure reliable and repeatable automation without manual intervention.

- **Branch Validation and Consistency**  
  Verifies the existence of both source and target branches before attempting a merge, preventing partial or invalid executions.

- **Conflict Visibility and Diagnostics**  
  Surfaces merge conflicts clearly through workflow logs, enabling fast identification and resolution.

- **Auditability and Compliance**  
  Provides a clear execution trail through GitHub Actions logs and standardized commit messages.

---

## Problems Solved

- Ensures validated changes in feature or release branches are consistently promoted to `main`  
- Eliminates manual merge effort during release finalization  
- Prevents silent failures caused by missing authentication or misconfigured dry runs  
- Provides clear diagnostics when merges fail or conflicts occur  
- Improves audit readiness through traceable automation logs  
- Reduces operational burden on platform and infrastructure teams  

---

## How the Solution Works

1. The workflow identifies the list of repositories to process either from a repository list file or manual input.  
2. Each repository is cloned using authenticated access via GitHub CLI.  
3. The `main` branch is checked out and synchronized with the remote repository.  
4. The feature branch `feature-0.1` is merged into `main` using a standard merge strategy.  
5. If dry run mode is disabled, the merged changes are pushed back to the `main` branch.  
6. Results are logged per repository to ensure traceability and transparency.  

---

## Key Features

- Supports multiple repositories in a single workflow execution  
- Configurable source and target branches  
- Dry run mode for safe testing and validation  
- Secure authentication using GitHub personal access tokens  
- Clear and actionable error reporting  
- Idempotent execution suitable for repeated runs  

---

## Prerequisites

- GitHub Actions enabled for the repository or organization  
- GitHub personal access token with repository and workflow permissions  
- Repositories following a consistent branching strategy  
- GitHub CLI available in the runner environment  

---

## When to Use This Project

This solution is ideal for:

- Infrastructure as code repositories  
- Platform engineering and DevOps teams  
- Organizations managing multiple Terraform or Cloud Build repositories  
- Release workflows that require controlled promotion into `main`  
- Teams seeking to reduce manual Git operations and release risk  

---

## Future Improvements

Potential enhancements include:

- Automatic issue creation on merge conflicts  
- Notifications via Slack or email for merge outcomes  
- Per repository merge strategy configuration  
- Integration with release tagging and versioning workflows  
- Support for protected branch workflows using pull requests  

---

## Conclusion

This project standardizes and automates the promotion of changes from feature or release branches into the `main` branch across multiple repositories.

By removing manual steps, enforcing consistency, and providing clear diagnostics and audit trails, it significantly improves reliability, compliance, and confidence in enterprise scale release and infrastructure management workflows.
