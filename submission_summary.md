# Git & GitHub Assignment — Submission Summary

**Student Name:** Avnish Raman
**GitHub Repository (public):** https://github.com/47AVNISH/Assignment

---

## Question 1: Git & GitHub Workflow (10 Marks)

### Step 1: Local Repository Setup (2 Marks)
- Created the project folder `git-github-assignment/` on the local machine.
- Added two HTML pages: `index.html` (home page) and `about.html` (about page).
- Initialized a Git repository inside the folder using `git init`.
- The repository was created locally first; the GitHub repository was created
  only afterwards (Step 5), as required.

### Step 2: Git Workflow Execution (4 Marks)
Commands used, in sequence (full list with explanations in `git_commands.txt`):
1. `git add .` and `git commit -m "Initial commit: add index.html and about.html"`
   — recorded the initial state of the project.
2. Modified `about.html`, then `git add` + commit
   — second commit recorded the modification.
3. `git branch feature` — created a new branch named `feature`.
4. `git switch feature` — switched to the feature branch.
5. Modified `index.html` and committed it on the feature branch.
6. `git switch main` — switched back to the main branch.
7. `git merge feature` — merged the feature branch into main
   (fast-forward merge).
8. Made a second change on `feature` and merged with
   `git merge feature --no-ff -m "Merge feature branch into main"`
   so a dedicated merge commit is visible in the history.
9. `git log --oneline --graph --all --decorate` — displayed the full
   commit history showing all commits, the branch, and the merge.

The final history graph (also visible on GitHub):
```
* a2fa1b9 (HEAD -> main, origin/main) Update git_commands.txt with actual repository URL
* 6d66c8c Add git command documentation and login test case table
* 1ed7bc9 Add .gitignore to exclude .log files and temp folder
*   3e99070 Merge feature branch into main
|\
| * ef3f0d2 (origin/feature, feature) Add features list note to about page
|/
* bfd5eaa Add highlights section to home page (feature branch)
* 6a19ad3 Update about.html with project workflow details
* 85fcd37 Initial commit: add index.html and about.html
```

### Step 3: .gitignore Implementation (1 Marks)
- Created a `.gitignore` file configured to ignore:
  - `*.log` — all log files
  - `temp/` — the temp folder
- Verified with `git check-ignore debug.log temp\notes.txt` and
  `git status` that matching files were correctly ignored.

### Step 4: Undo Operation using Git (1 Marks)
- Created an additional commit changing the footer text of `index.html`.
- Undid it with `git reset --hard HEAD~1`, which moved HEAD and the
  `main` branch back one commit.
- Effect on repository state: the temporary commit disappeared from
  `git log`, and `git status` / `git diff HEAD` confirmed the working
  tree was restored to the previous commit's state (the footer change
  was removed from the file as well).

### Step 5: GitHub Integration (1 Marks)
- Created a **public** repository on GitHub:
  **https://github.com/47AVNISH/Assignment**
- Connected the local repository:
  `git remote add origin https://github.com/47AVNISH/Assignment.git`
- Pushed both branches: `git push -u origin main` and `git push origin feature`.
- The complete commit history (including branching and merging) is
  visible on GitHub.

### Step 6: Command Documentation File (1 Marks)
- `git_commands.txt` contains every Git command used in the assignment
  with a 1–2 line explanation for each, organised by step.

---

## Question 2: Test Case Design (10 Marks)

Full deliverable: **`test_cases_login.md`** (also included in the GitHub repo).

- 10 test cases in a formatted table with the required columns:
  Test Case ID | Test Scenario | Input Data | Expected Output
- Covers all 5 functional requirements (non-empty username, minimum
  6-character password, successful login with valid credentials,
  specific error messages for invalid credentials, account lock after
  3 consecutive failed attempts).
- Edge cases included: empty username, whitespace-only username,
  empty password, password shorter than 6 characters (5 chars),
  password exactly 6 characters, password longer than 6 characters,
  exactly 3 failed attempts (lock boundary), and a 4th attempt on a
  locked account.
- Expected outputs are precise and specific (exact messages and
  outcomes, e.g. "Password must be at least 6 characters long",
  "Account is locked due to 3 failed login attempts. Please contact
  support."), with no vague terms.
