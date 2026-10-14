# Git & GitHub Merge Conflict Resolution Practice

A hands-on practice project focused on understanding, creating, and resolving Git merge conflicts locally and through GitHub Pull Requests.

## Project Overview

This project documents practical exercises completed using **Git Bash, Git branches, merge operations, GitHub repositories, and Pull Requests**. The goal was to understand why merge conflicts occur, how to resolve them safely, and how to maintain synchronization between local and remote branches.

**Repository:** [GitHub-conflicts-practice](https://github.com/Jabir-Chowdhury/GitHub-conflicts-practice)

## Learning Objectives

- Understand Git branches and branch-based development workflows.
- Distinguish local branches, remote branches, and remote-tracking branches.
- Create and resolve different types of Git merge conflicts.
- Understand Git staging, commits, pushes, pulls, and merges.
- Practice GitHub Pull Request creation and merging.
- Resolve competing changes using GitHub's conflict editor.
- Synchronize the local `main` branch with the remote `main` branch.
- Verify repository status and confirm a clean working tree.

---

## Part 1: Local Git Merge Conflict Practice

The first part focused on creating and resolving three types of merge conflicts locally using Git Bash.

### 1. Content Conflict

**Scenario:** Two branches modify the same line of a file with different content.

**Branches used:**
- `feature-a`
- `feature-b`

**What I practiced:**
- Creating separate branches from a common base.
- Modifying the same line differently on each branch.
- Merging branches and identifying the conflict.
- Reviewing conflict markers and choosing the final content.
- Staging the resolved file and committing the merge.

**Conflict markers:**

```text
<<<<<<< HEAD
Content from the current branch
=======
Content from the incoming branch
>>>>>>> feature-branch
```

**Key learning:** Git cannot always determine which competing change is correct. The developer must review the changes and select the intended final content.

### 2. Modify-Delete Conflict

**Scenario:** One branch modifies a file while another branch deletes the same file.

**Branches used:**
- `modify-delete-a`
- `modify-delete-b`

**What I practiced:**
- Modifying a file in one branch.
- Deleting the same file in another branch.
- Merging the branches and identifying the modify-delete conflict.
- Choosing to keep the modified file.
- Staging the resolution and completing the merge.

**Key learning:** When one branch modifies a file and another deletes it, Git needs a decision about whether the file should remain or be removed.

### 3. Add-Add Conflict

**Scenario:** Two branches independently create a file with the same filename but different content.

**Branches used:**
- `add-add-a`
- `add-add-b`

**What I practiced:**
- Creating the same file independently on two branches.
- Adding different content to the file in each branch.
- Merging the branches and resolving the conflict.
- Preserving both relevant lines in the final file.
- Committing the resolved result.

**Key learning:** Git may require manual resolution when independently created files have the same path but incompatible content.

### Local Git Concepts Practiced

| Concept | Purpose |
|---|---|
| `git switch -c` | Create and switch to a new local branch |
| `git status` | Inspect the working tree and staging state |
| `git add` | Stage changes or mark conflict resolutions |
| `git commit` | Record changes in local Git history |
| `git merge` | Integrate changes from another branch |
| `git log --oneline --graph` | Inspect commit history and branch relationships |
| `git push` | Send local commits to a remote repository |
| `git pull` | Fetch and integrate changes from a remote branch |

---

## Part 2: GitHub Pull Request Practice

The second part focused on using GitHub Pull Requests to propose changes, merge branches, and resolve a conflict caused by competing changes.

### 1. Creating a Pull Request

Created a dedicated feature branch and pushed it to GitHub.

**Branch:** `github-pr-practice`

**Workflow:**

```bash
git switch main
git pull origin main
git switch -c github-pr-practice

git add pr-practice.txt
git commit -m "Add GitHub PR practice file"

git push -u origin github-pr-practice
```

Then created a Pull Request with:
- **Base branch:** `main`
- **Compare branch:** `github-pr-practice`

After reviewing the proposed changes, merged the PR and updated the local `main` branch.

**Key learning:** A Pull Request proposes changes from one branch to another. Pushing a branch to GitHub does not automatically merge its changes into `main`.

### 2. Creating Two Competing Pull Requests

To practice a real GitHub PR conflict, created two feature branches that independently changed the same line in `pr-practice.txt`.

**Branches used:**
- `pr-conflict-feature`
- `pr-conflict-second`

**First branch change:**

```text
Change from PR feature branch.
```

**Second branch change:**

```text
Change from the second PR branch.
```

Both branches were pushed to GitHub, and separate Pull Requests were created with `main` as the base branch.

The first PR was merged while the second PR remained open. GitHub then identified the competing changes in the second PR and displayed a merge conflict.

**Key learning:** A PR can become conflicted when the base branch changes in a way that competes with changes proposed by the PR branch.

### 3. Resolving the GitHub Pull Request Conflict

Used GitHub's **Resolve conflicts** editor to resolve the conflicting changes in `pr-practice.txt`.

**Original conflict:**

```text
<<<<<<< pr-conflict-second
Change from the second PR branch.
=======
Change from PR feature branch.
>>>>>>> main
```

**Final resolved content:**

```text
Both PR changes were reviewed and conflict resolved.
```

The resolution process was:

1. Open the second Pull Request.
2. Click **Resolve conflicts**.
3. Review the competing changes.
4. Remove the conflict markers.
5. Write the intended final content.
6. Click **Mark as resolved**.
7. Click **Commit merge** to commit the resolution to the PR branch.
8. Verify that the conflict was resolved.
9. Click **Merge pull request** and confirm the merge.

**Key learning:** Resolving a conflict and merging a Pull Request are separate steps. The conflict must first be resolved and committed before the PR can be merged.

For more details, see the official [GitHub guide to resolving merge conflicts](https://docs.github.com/en/pull-requests/how-tos/merge-and-close-pull-requests/resolving-a-merge-conflict-on-github).

---

## Part 3: Local and Remote Branches

Understanding branch terminology was an important part of this practice.

| Term | Meaning |
|---|---|
| Local `main` | The `main` branch on my computer |
| Remote `main` | The `main` branch stored on GitHub |
| `origin/main` | The local remote-tracking reference representing the last fetched or otherwise updated known state of the remote `main` branch |
| Local feature branch | A branch created and worked on locally |
| Remote feature branch | The corresponding branch pushed to GitHub |
| Base branch | The destination branch of a Pull Request |
| Compare branch | The branch containing the proposed changes |

### Commands Used to Synchronize `main`

```bash
git switch main
git pull origin main
git status
```

The final status confirmed:

```text
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

This confirmed that the local `main` branch was up to date with `origin/main` and the working tree had no uncommitted changes.

---

## Key Takeaways

Through these exercises, I gained practical experience with:

- Diagnosing content, modify-delete, and add-add merge conflicts.
- Resolving conflicts manually rather than relying only on automatic merging.
- Working with multiple branches and understanding their relationships.
- Creating, reviewing, and merging GitHub Pull Requests.
- Understanding how competing changes can block a PR merge.
- Resolving conflicts through GitHub's web-based editor.
- Using Git commands to inspect repository state and synchronize branches.
- Verifying a clean working tree after completing a workflow.

## Conclusion

This project strengthened my foundational understanding of Git version control and GitHub collaboration workflows. By deliberately creating conflicts and resolving them, I learned how Git handles competing changes, why manual decisions are sometimes necessary, and how Pull Requests support controlled integration of code changes.

**Next learning goals:** Practice more complex conflicts, resolve conflicts using the command line, and explore collaborative workflows involving code reviews, branch synchronization, and merge strategies.

---

*Project type: Hands-on learning and practice*  
*Tools: Git, Git Bash, GitHub, Markdown*  
*Focus: Version control, branching, merge conflicts, and Pull Request workflows*