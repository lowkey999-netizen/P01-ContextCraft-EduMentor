# Git Workflow and Contribution Rules

## Purpose

This document defines the GitHub workflow for P01-ContextCraft-EduMentor.

The goal is to keep `main` stable, make individual contributions traceable, and ensure changes are reviewed before being merged.

---

## 1. Main Branch

`main` is the protected branch and represents the shared project state.

### Rules

- Do not develop directly on `main`.
- Do not push directly to `main`.
- Do not force-push to `main`.
- Do not delete `main`.
- Changes to `main` must go through a Pull Request.
- A Pull Request requires at least one approval from another reviewer.
- Review conversations must be resolved before merging.
- Pull Requests should be kept focused on the related task.

---

## 2. Branches

Development work should be done on short-lived branches created from `main`.

### Branch naming convention

Use:

```text
<type>/<short-description>
````

Examples:

```text
feature/document-loader
feature/rag-retrieval
fix/api-validation
docs/setup-guide
test/retrieval-evaluation
refactor/context-builder
```

Keep branch names short and descriptive.

Do not use vague names such as:

```text
my-branch
test
changes
new
final
stuff
```

---

## 3. Basic Workflow

The standard workflow is:

```text
main
  ↓
Create a branch
  ↓
Make changes
  ↓
Commit changes
  ↓
Push branch to GitHub
  ↓
Create Pull Request
  ↓
Another teammate reviews it
  ↓
Address review comments
  ↓
Approval
  ↓
CI checks
  ↓
Squash and merge into main
```

The author of a Pull Request should not approve their own Pull Request.

---

## 4. Commits

The project uses Conventional Commits.

### Format

```text
type(scope): description
```

### Allowed types

| Type       | Use                                                    |
| ---------- | ------------------------------------------------------ |
| `feat`     | New functionality                                      |
| `fix`      | Bug fix                                                |
| `docs`     | Documentation changes                                  |
| `style`    | Formatting/style changes that do not alter behaviour   |
| `refactor` | Code restructuring without changing intended behaviour |
| `test`     | Adding or modifying tests                              |
| `chore`    | Maintenance or repository/tooling changes              |

### Examples

```text
feat(retrieval): add document chunking
fix(api): handle empty query
docs(readme): add local setup instructions
style(frontend): format response component
refactor(pipeline): separate retrieval stage
test(retrieval): add chunking tests
chore(github): add pull request template
```

Avoid vague commit messages such as:

```text
update
changes
fix
final
done
stuff
```

Where applicable, commits should reference the relevant backlog item so that individual contributions can be traced.

---

## 5. Pull Requests

Every change intended for `main` should be submitted through a Pull Request.

### PR author responsibilities

The author should:

* Clearly describe what changed.
* Explain why the change was needed.
* Explain how the change was tested.
* Complete the PR checklist.
* Ensure no secrets were committed.
* Respond to reviewer comments.
* Keep the PR focused and reasonably small.

### Reviewer responsibilities

The reviewer should:

* Be someone other than the PR author.
* Understand the purpose of the change.
* Check that the implementation is appropriate.
* Check for unnecessary or unrelated changes.
* Check tests where applicable.
* Check for accidentally committed secrets.
* Review documentation where applicable.
* Leave useful comments when something needs attention.
* Approve only after the changes are satisfactory.

The repository's Pull Request template and review checklist should be used for every applicable PR.

---

## 6. Merging

The repository is configured to use **Squash and merge**.

Squashing combines the commits belonging to a Pull Request into a single commit when the PR is merged into `main`.

This keeps the shared `main` history concise while allowing developers to make multiple commits during development.

Only merge a PR after the required review and repository checks have been satisfied.

---

## 7. Secrets and Sensitive Information

Never commit:

* API keys
* Passwords
* Access tokens
* Private credentials
* `.env` files containing secrets
* Other confidential credentials

The repository is public, so anything committed to it should be treated as publicly visible.

If a secret is accidentally committed, do not assume that deleting the file from the latest commit makes it safe. Report the issue immediately and rotate/revoke the affected credential.

---

## 8. CI

Continuous Integration (CI) will automatically check changes before they are merged.

The planned project CI workflow includes:

```text
Lint
  ↓
Secret scan
  ↓
Tests
  ↓
Docker build validation
```

Additional checks may be introduced as the project develops.

CI is not yet required as a branch status check during the initial repository skeleton setup because the application and CI workflow have not yet been created.

---

## 9. Contribution Evidence

Every team member should have meaningful commits in the project history.

Commits should be attributable to the person who actually performed the work.

Avoid having one person author nearly all commits on behalf of the team.

Where applicable, backlog identifiers should be referenced so that GitHub history can be used as evidence of individual contributions.

---

## 10. Quick Reference

### Before starting work

```text
Update local main
Create a short-lived branch
```

### While working

```text
Make focused changes
Commit using Conventional Commits
Push the branch
```

### Before merging

```text
Open Pull Request
Complete PR description/checklist
Get another teammate to review
Address review comments
Get approval
Wait for required checks
Squash and merge
```

### Never

```text
Push directly to main
Force-push main
Approve your own PR
Commit secrets
Use vague commit messages
Merge unrelated work into a PR
```
