# Day 40 – Your First GitHub Actions Workflow

## Task
Today you write your **first GitHub Actions pipeline** and watch it run in the cloud.

This is the moment CI/CD stops being a concept and becomes real.

---

## Expected Output
- A workflow file: `.github/workflows/hello.yml`
- A markdown file: `day-40-first-workflow.md`
- Screenshot of your first green pipeline run

---

## Challenge Tasks

### Task 1: Set Up
1. Create a new **public** GitHub repository called `github-actions-practice`
2. Clone it locally
3. Create the folder structure: `.github/workflows/`

   <img width="1338" height="488" alt="image" src="https://github.com/user-attachments/assets/6b922d29-df4c-46e7-9104-3dcecf365c24" />

---

### Task 2: Hello Workflow
Create `.github/workflows/hello.yml` with a workflow that:
1. Triggers on every `push`
2. Has one job called `greet`
3. Runs on `ubuntu-latest`
4. Has two steps:
   - Step 1: Check out the code using `actions/checkout`
   - Step 2: Print `Hello from GitHub Actions!`

Push it. Go to the **Actions** tab on GitHub and watch it run.

```yaml
name: hello workflow

on:
  workflow_dispatch:

jobs:
  greet-job:
    name: greet-job-name
    runs-on: ubuntu-latest
    steps:
    - name: checkout-code
      uses: actions/checkout@v7
    - name: echo-hello
      run: echo "Hello from GitHub Actions!"
```



**Verify:** Is it green? Click into the job and read every step.

# GitHub Actions Run Output

# GitHub Actions Workflow Output

<details>
<summary>✅ Set up job</summary>

```text
Current runner version: '2.336.0'

▼ Runner Image Provisioner
  Hosted Compute Agent
  Version: 20260729.566
  Commit: cf7153fe6e25b664e8693c24944bf2b00355d109
  Build Date: 2026-07-29T19:17:02Z
  Worker ID: {fd2e2b3b-61aa-4e15-bffd-624c517f9f33}
  Azure Region: eastus

▼ Operating System
  Ubuntu
  24.04.4
  LTS

▼ Runner Image
  Image: ubuntu-24.04
  Version: 20260810.271.1
  Included Software:
    https://github.com/actions/runner-images/blob/ubuntu24/20260810.271/images/ubuntu/Ubuntu2404-Readme.md

  Image Release:
    https://github.com/actions/runner-images/releases/tag/ubuntu24%2F20260810.271

▼ GITHUB_TOKEN Permissions
  Contents: read
  Metadata: read
  Packages: read

Secret source: Actions
Prepare workflow directory
Prepare all required actions
Getting action download info

Download action repository 'actions/checkout@v7'
  SHA: 3d3c42e5aac5ba805825da76410c181273ba90b1

Complete job name: greet-job-name
```

</details>

<details>
<summary>✅ checkout-code</summary>

```text
▼ Run actions/checkout@v7

  with:
    repository: ranjeet6979/GitHub-actions-practice
    token: ***
    ssh-strict: true
    ssh-us**: git
    persist-credentials:**rue
    clean: true
    sparse-ch**kout-cone-mode: true
    fetch-de**h: 1
    fetch-tags: false
** **how-progress: true
    lfs: false**   submodules: false
    set-safe**irectory: true
    allow-unsafe-p**checkout: false

Syncing reposito**:
  ranjeet6979/GitHub-actions-pr**tice

▼ Getting Git version**nfo

  Working directory:
    /ho**/runner/work/GitHub-actions-pract**e/GitHub-actions-practice

  /usr**in/git version
  git version 2.54**

Tem**r**ily overriding HOME before making**lobal git config changes

Adding**epository directory to temporary **t global config
  /usr/bin/git co**ig --global --add safe.directory **  /home/runner/work/GitHub-action**practice/GitHub-actions-practice
**eleting repository contents

▼ De**rmining repository object format
** Initializing repository

  /usr/**n/git init
**Initialized empty Git repository
** /usr/bin/git remote add origin
 **ttps://github.com/ranjeet6979/GitHub-actions-practice

▼ Disabling a**omatic garbage collection

  /usr**in/git config --local gc.auto 0

**Setting up auth

  Removing SSH c**mand configuration
  Removing HTT**extra header
  Removing includeIf**ntries

▼ Fetching the repository**  /usr/bin**it**etch --depth=1

  From:
    https://github.com/ranjeet6979/GitHub-actions-practice

  [new ref]
    66b**545bc4b77c9b8463546b96d770705e7a2** -> origin/main

▼ Determining ch**kout info

▼ Checking out the ref**  /usr/bin/git checkout --force -**main

  Switched to a new branch **ain'
  Branch 'main' set up to tr**k 'origin/main'

▼ Latest Commit
** 66bd0545bc4b77c9b8463546b96d7707**e7a277
```

</details>

<details>**summary>✅ echo-hello</summary>

`**text
Run echo "Hello from GitHub **tions!"

  shell: /usr/bin/bash -**{0}

Hello from GitHub Actions!
`**

</details>

<details>
<summary>**Post checkout-code</summary>

```**xt
Post job cleanup

git version **54.0

Removing SSH command config**ation
Removing HTTP extra header
**moving includeIf entries

Removing credentials config:
  /home/runner/work/_temp/git-credentials-xxxx.config
```

</details>

<details>
<summary>✅ Complete job</summary>

```text
Complete job

Cleaning up orphan processes
```

</details>

---

### Task 3: Understand the Anatomy
Look at your workflow file and write in your notes what each key does:
- `on:`
- `jobs:`
- `runs-on:`
- `steps:`
- `uses:`
- `run:`
- `name:` (on a step)

---

### Task 4: Add More Steps
Update `hello.yml` to also:
1. Print the current date and time
2. Print the name of the branch that triggered the run (hint: GitHub provides this as a variable)
3. List the files in the repo
4. Print the runner's operating system

Push again — watch the new run.

---

### Task 5: Break It On Purpose
1. Add a step that runs a command that will **fail** (e.g., `exit 1` or a misspelled command)
2. Push and observe what happens in the Actions tab
3. Fix it and push again

Write in your notes: What does a failed pipeline look like? How do you read the error?

---

## Hints
- Workflow files live in `.github/workflows/` and must end in `.yml`
- `uses: actions/checkout@v4` checks out your code onto the runner
- `run:` executes shell commands
- GitHub provides built-in variables like `${{ github.ref_name }}` for branch name
- Every push triggers a new run — check the Actions tab

---

## Documentation
Create `day-40-first-workflow.md` with:
- Your workflow YAML
- Screenshot of the green run
- What each `on:`, `jobs:`, `steps:` key does (your own words)

---

## Submission
1. Add `day-40-first-workflow.md` to `2026/day-40/`
2. Commit and push to your fork

---

## Learn in Public
Share your first green pipeline screenshot on LinkedIn. That green checkmark hits different.

`#90DaysOfDevOps` `#DevOpsKaJosh` `#TrainWithShubham`

Happy Learning!
**TrainWithShubham**
