# Repository Health Automation

A beginner-friendly GitHub Actions project that automatically validates repository health whenever code is pushed to GitHub.

## Overview

This project demonstrates how GitHub Actions and shell scripting can automate basic repository validation tasks.

The workflow checks whether a required `README.md` file exists at the root of the repository. It reports success when the file is present and fails the workflow when the file is missing.

## How It Works

1. **Trigger:** The workflow runs on every `push` event.
2. **Runner:** GitHub Actions provisions an Ubuntu runner.
3. **Checkout:** `actions/checkout` makes the repository files available in the runner workspace.
4. **File validation:** A shell script uses the `find` command to check for `README.md` at the repository root.
5. **Conditional logic:** The script captures the command's output in a shell variable and checks whether the result is empty.
6. **Result:** The workflow succeeds if the file exists and fails with exit code `1` if it is missing.
7. **Branch information:** The workflow prints the name of the branch associated with the triggering run using the GitHub Actions context.

## Concepts Learned

### GitHub Actions Fundamentals
- Workflow triggers and the `push` event.
- Jobs, steps, and GitHub-hosted runners.
- Using `actions/checkout` to access repository files.
- Executing shell commands with `run`.
- Accessing workflow information through GitHub contexts and expressions.

### Shell Scripting
- Searching for files with `find`.
- Capturing command output using command substitution: `$(...)`.
- Storing values in shell variables.
- Checking whether a string is empty using `-n`.
- Using `if`, `else`, and `fi` for conditional execution.
- Using `exit 1` to indicate failure.

### Understanding Conditional Execution

This project helped me understand the difference between:

- **GitHub Actions conditions:** Evaluated by GitHub Actions to determine whether a step should run.
- **Shell conditions:** Evaluated by the shell while a script is executing, allowing decisions based on values calculated during that execution.

## Workflow Structure

```text
Repository Health Automation
└── .github/
    └── workflows/
        └── repo-health-check.yml
```

The workflow checks the repository root for `README.md`.

## Expected Results

| Scenario | Expected outcome |
|---|---|
| `README.md` exists at the repository root | Health check passes |
| `README.md` is missing | Health check fails |
| Workflow is triggered by a push to a branch | Branch name is printed |

## Future Improvements

- Validate multiple required files, such as `.gitignore`.
- Check for required directories.
- Generate a consolidated health-check report.
- Add more repository configuration and consistency checks.

## Purpose

This project was built as a hands-on learning exercise to understand GitHub Actions, shell scripting, command execution, conditional logic, and workflow failure handling through a practical automation task.
