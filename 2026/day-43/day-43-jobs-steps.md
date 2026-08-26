# Day 43 – Jobs, Steps, Env Vars & Conditionals

## Task
Today you learn how to **control the flow** of your pipeline — multi-job workflows, passing data between jobs, environment variables, and running steps only when certain conditions are met.

---

## Expected Output
- New workflow files in your `github-actions-practice` repo
- A markdown file: `day-43-jobs-steps.md`

---

## Challenge Tasks

### Task 1: Multi-Job Workflow
Create `.github/workflows/multi-job.yml` with 3 jobs:
- `build` — prints "Building the app"
- `test` — prints "Running tests"
- `deploy` — prints "Deploying"

Make `test` run only **after** `build` succeeds.
Make `deploy` run only **after** `test` succeeds.

**Verify:** Check the workflow graph in the Actions tab — does it show the dependency chain?

```yaml
name: multi job
on:
  workflow_dispatch:

jobs:
  build:
    name: build job
    runs-on: ubuntu-latest
    steps:
      - name: build
        run: echo "build..."
  test:
    name: test job
    needs: build
    runs-on: ubuntu-latest
    steps:
      - name: test
        run: echo "test..."  
  deploy:
    name: deploy job
    needs:
      - build
      - test
    runs-on: ubuntu-latest
    steps:
      - name: deploy
        run: echo "deploy..."  
```


<img width="1342" height="372" alt="image" src="https://github.com/user-attachments/assets/e3e465cb-36de-4ddf-8d32-314dbcd81025" />

---

### Task 2: Environment Variables
In a new workflow, use environment variables at 3 levels:
1. **Workflow level** — `APP_NAME: myapp`
2. **Job level** — `ENVIRONMENT: staging`
3. **Step level** — `VERSION: 1.0.0`

Print all three in a single step and verify each is accessible.

Then use a **GitHub context variable** — print the commit SHA and the actor (who triggered the run).

```yaml
name: env variable print

on:
  workflow_dispatch

env:
  APP_NAME: myapp

jobs:
  variable-job:
    runs-on: ubuntu-latest
    env:
      ENVIRONMENT: staging
    steps:
      - name: "print workflow, job and step env variables"
        run: echo "$APP_NAME $ENVIRONMENT $VERSION"
        env:
          VERSION: 1.0.0
      - name: "print github content"
        run: echo ${{ github.sha }}
      - name: "print github actor"
        run: echo ${{ github.actor }}
```        

<img width="1449" height="591" alt="image" src="https://github.com/user-attachments/assets/de0d237e-5382-4811-a8cd-7457b9922ac6" />

---

### Task 3: Job Outputs
1. Create a job that **sets an output** — e.g., today's date as a string
2. Create a second job that **reads that output** and prints it
3. Pass the value using `outputs:` and `needs.<job>.outputs.<name>`

Write in your notes: Why would you pass outputs between jobs?

```yaml
name: job-output
on: workflow_dispatch

jobs:
  job1:
    runs-on: ubuntu-latest
    outputs:
      date: ${{ steps.step1.outputs.date }}
    steps:
      - id: step1
        run: echo "date=$(date)" >> $GITHUB_OUTPUT
  job2:
    runs-on: ubuntu-latest
    needs: job1
    steps:
      - env:
          OUTPUT1: ${{ needs.job1.outputs.date }}
        run: echo "$OUTPUT1"
```

<img width="1450" height="414" alt="image" src="https://github.com/user-attachments/assets/4a2fb5b6-f9ec-4801-ba69-23190695d92d" />

<img width="1451" height="459" alt="image" src="https://github.com/user-attachments/assets/d58dd0c1-016d-4428-aa09-a05ef9de9956" />

---

### Task 4: Conditionals
In a workflow, add:
1. A step that only runs when the branch is `main`
2. A step that only runs when the previous step **failed**
3. A job that only runs on **push** events, not on pull requests
4. A step with `continue-on-error: true` — what does this do?

```yaml
name: conditional
on: 
  push:
    branches: main

jobs:
  conditional-job1:
    runs-on: ubuntu-latest
    steps:
      - name: check if main
        if: github.ref == 'refs/heads/main'
        run: echo "this runs only if it is main branch"

      - name: failed step
        id: demo
        run: exit 1

      - name: run if previous step failed
        if: ${{ failure() && steps.demo.conclusion == 'failure' }}
        run: echo "this runs if previous step fails" 

  conditional-job2:
    runs-on: ubuntu-latest
    steps:
      - name: on-push event
        if: contains(fromJSON('["push"]'), github.event_name)
        run: echo "this runs only if it is push event"
```

<img width="1448" height="429" alt="image" src="https://github.com/user-attachments/assets/b15039fa-6d13-4c30-97b5-c2577a95318d" />

---

### Task 5: Putting It Together
Create `.github/workflows/smart-pipeline.yml` that:
1. Triggers on push to any branch
2. Has a `lint` job and a `test` job running in parallel
3. Has a `summary` job that runs after both, prints whether it's a `main` branch push or a feature branch push, and prints the commit message

```yaml
name: smart-pipeline
on:
  push:

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - name: lint-step
        run: echo "this is lint job"

  test:
    runs-on: ubuntu-latest
    steps:
      - name: test-step
        run: echo "this is test job"

  summary:
    runs-on: ubuntu-latest
    needs:
      - lint
      - test
    steps:
      - name: summary-step
        run: echo "this is summary job and commit message was ${{  github.event.commits[0].message }}"
```

<img width="1447" height="513" alt="image" src="https://github.com/user-attachments/assets/b77b7212-5d1d-4da2-8875-cfeea932bd11" />

<img width="1448" height="421" alt="image" src="https://github.com/user-attachments/assets/32786fa7-6b57-4dc2-934e-a3661c623461" />

<img width="1446" height="413" alt="image" src="https://github.com/user-attachments/assets/119762f7-96b7-48ca-8ad4-7c12d916fe70" />

<img width="1446" height="420" alt="image" src="https://github.com/user-attachments/assets/78ce7be8-3e19-48f6-9c86-3710ed00e2b2" />

---

## Hints
- Job dependency: `needs: [job-name]`
- Set output: `echo "date=$(date)" >> $GITHUB_OUTPUT`
- Read output: `${{ needs.job-name.outputs.date }}`
- Conditionals: `if: github.ref == 'refs/heads/main'`
- Commit message: `${{ github.event.commits[0].message }}`

---

## Documentation
Create `day-43-jobs-steps.md` with:
- Key workflow snippets
- What `needs:` and `outputs:` do in your own words

---

## Submission
1. Add `day-43-jobs-steps.md` to `2026/day-43/`
2. Commit and push to your fork

---

## Learn in Public
Share the dependency chain diagram from your multi-job workflow on LinkedIn.

`#90DaysOfDevOps` `#DevOpsKaJosh` `#TrainWithShubham`

Happy Learning!
**TrainWithShubham**
