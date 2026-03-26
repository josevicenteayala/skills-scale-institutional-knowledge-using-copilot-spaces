# GitHubCourse — Automated Student Progress Tracking

This directory contains the complete GitHub Actions workflow infrastructure to add **automatic student progress review** to the [`josevicenteayala/GitHubCourse`](https://github.com/josevicenteayala/GitHubCourse) repository.

The mechanism mirrors the [GitHub Skills exercise pattern](https://github.com/skills/exercise-toolkit) used in this repository: a dedicated tracking issue is created when the student starts the exercise, and each step's workflow posts automated pass/fail feedback as comments on that issue.

---

## How the Mechanism Works

```
Push to main
    └─▶ 0-start-exercise.yml
            Creates a tracking issue
            Posts Step 1 instructions
            Enables "Step 1" workflow
                │
                ▼
PR closed with changes in step-01-code-completion/**
    └─▶ 1-step.yml
            Runs Python unit tests (tests.test_step01)
            Checks copilot-evidence.md for required tokens
            Posts pass/fail table to the tracking issue
            On success: posts Step 2 instructions, enables Step 2
                │
                ▼
        (repeat for Steps 2 – 6)
                │
                ▼
PR closed with changes in step-07-debugging-assistance/**
    └─▶ 7-last-step.yml
            Validates final step
            Posts congratulations review (x-review.md)
            Calls finish-exercise to close the tracking issue
```

Each step workflow:
1. **Finds** the exercise tracking issue using `skills/exercise-toolkit`.
2. **Runs** `python3 -m unittest tests.test_stepXX` for functional correctness.
3. **Checks** `stepXX-*/copilot-evidence.md` for required Copilot usage tokens.
4. **Posts** a formatted results table as a comment on the tracking issue.
5. **Advances** to the next step (enables next workflow, disables current).

---

## Files in This Directory

```
githubcourse-implementation/
├── README.md                  ← this file
├── workflows/
│   ├── 0-start-exercise.yml   ← Initialize exercise (push to main)
│   ├── 1-step.yml             ← Step 01: Code Completion
│   ├── 2-step.yml             ← Step 02: Chat /explain /fix /generate
│   ├── 3-step.yml             ← Step 03: Refactor
│   ├── 4-step.yml             ← Step 04: Test Generation
│   ├── 5-step.yml             ← Step 05: Documentation Generation
│   ├── 6-step.yml             ← Step 06: Code Translation
│   └── 7-last-step.yml        ← Step 07: Debugging (final step)
└── steps/
    ├── 1-step.md              ← Instructions for Step 01
    ├── 2-step.md              ← Instructions for Step 02
    ├── 3-step.md              ← Instructions for Step 03
    ├── 4-step.md              ← Instructions for Step 04
    ├── 5-step.md              ← Instructions for Step 05
    ├── 6-step.md              ← Instructions for Step 06
    ├── 7-step.md              ← Instructions for Step 07
    └── x-review.md            ← Final congratulations review
```

---

## How to Apply This to GitHubCourse

### Step 1 — Copy the workflow files

Copy all files from `githubcourse-implementation/workflows/` into `.github/workflows/` in the GitHubCourse repository:

```bash
cp githubcourse-implementation/workflows/*.yml <path-to-GitHubCourse>/.github/workflows/
```

### Step 2 — Copy the step content files

Copy all files from `githubcourse-implementation/steps/` into `.github/steps/` in the GitHubCourse repository (create the folder if it does not exist):

```bash
mkdir -p <path-to-GitHubCourse>/.github/steps/
cp githubcourse-implementation/steps/*.md <path-to-GitHubCourse>/.github/steps/
```

### Step 3 — Disable all step workflows by default

Steps 1–7 should be **disabled** by default so only the start-exercise workflow runs initially. After copying the files, disable them via the GitHub UI or CLI:

```bash
cd <path-to-GitHubCourse>
gh workflow disable "Step 1"
gh workflow disable "Step 2"
gh workflow disable "Step 3"
gh workflow disable "Step 4"
gh workflow disable "Step 5"
gh workflow disable "Step 6"
gh workflow disable "Step 7"
```

### Step 4 — Verify the existing evaluate.yml

The existing `evaluate.yml` in GitHubCourse can remain in place. The new step workflows complement it by posting feedback to the tracking issue; the existing workflow continues to provide a quick local-style pass/fail on every push and PR.

### Step 5 — Trigger the start

Push any change to `main` in the GitHubCourse repository. The `0-start-exercise.yml` workflow will:
1. Create a new issue titled **"GitHub Copilot Hands-On Course"**.
2. Post Step 1 instructions as a comment.
3. Enable the Step 1 workflow.

The student then works through the steps, opening a PR for each step folder when they are done.

---

## Validation Logic per Step

| Step | Unit test module | Evidence tokens required |
|------|-----------------|--------------------------|
| 01 | `tests.test_step01` | `prompt` |
| 02 | `tests.test_step02` | `/explain`, `/fix`, `/generate` |
| 03 | `tests.test_step03` | `refactor` |
| 04 | student_tests.py (≥6 assertions, covers empty/duplicate/punctuation) | `test` |
| 05 | `tests.test_step05` | `documentation` |
| 06 | `tests.test_step06` | `translate` |
| 07 | `tests.test_step07` | `debug`, `/fix` |

---

## Dependencies

The workflows use the following GitHub Actions:

| Action | Purpose |
|--------|---------|
| `skills/exercise-toolkit/.github/workflows/start-exercise.yml@v0.8.1` | Creates the tracking issue |
| `skills/exercise-toolkit/.github/workflows/find-exercise-issue.yml@v0.8.1` | Finds the tracking issue number |
| `skills/exercise-toolkit/.github/workflows/finish-exercise.yml@v0.8.1` | Closes the tracking issue on completion |
| `skills/exercise-toolkit/actions/file-exists@v0.8.1` | (used in skills-scale; Python check used instead here) |
| `GrantBirki/comment@v2.1.1` | Posts/updates comments on the tracking issue |
| `peter-evans/find-comment@v3` | Finds the last comment to update it |
| `actions/checkout@v4` | Checks out the repository |
| `actions/setup-python@v5` | Sets up Python 3.11 |

No additional secrets are required beyond the default `GITHUB_TOKEN`.

---

## Comparison with skills-scale-institutional-knowledge-using-copilot-spaces

| Aspect | skills-scale repo | GitHubCourse (this implementation) |
|--------|------------------|-------------------------------------|
| Steps | 3 | 7 |
| Trigger | Push/issue/PR on `docs/**` | PR closed on `step-XX-*/` |
| Validation | File existence + keyphrase check | Python `unittest` + evidence tokens |
| Evidence | N/A | `copilot-evidence.md` per step |
| Toolkit | `skills/exercise-toolkit` (full) | `skills/exercise-toolkit` (issue management only) |
| Final step | `finish-exercise` | `finish-exercise` |
