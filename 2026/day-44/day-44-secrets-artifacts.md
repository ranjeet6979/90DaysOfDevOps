# Day 44 – Secrets, Artifacts & Running Real Tests in CI

## Task
Today your pipeline starts doing **real work** — storing sensitive values securely, saving build outputs, and running actual tests from your previous days.

---

## Expected Output
- New workflow files in your `github-actions-practice` repo
- A markdown file: `day-44-secrets-artifacts.md`
- A passing test run in CI

---

## Challenge Tasks

### Task 1: GitHub Secrets
1. Go to your repo → Settings → Secrets and Variables → Actions
2. Create a secret called `MY_SECRET_MESSAGE`
3. Create a workflow that reads it and prints: `The secret is set: true` (never print the actual value)

```yaml
name: secrets-check

on: workflow_dispatch

jobs:
  secret-job:
    runs-on: ubuntu-latest
    steps:
    - name: secret step
      env:
        SUPER_SECRET: ${{ secrets.MY_SECRET_MESSAGE }}
      if: env.SUPER_SECRET != ''
      run: |
        echo "The secret is set: true"
        echo "$SUPER_SECRET"
```

<img width="1448" height="516" alt="image" src="https://github.com/user-attachments/assets/71b0263f-c366-4ce2-8cb8-18ae0e513dd3" />

4. Try to print `${{ secrets.MY_SECRET_MESSAGE }}` directly — what does GitHub show?
It will show *** output instead of printing actual secret.

Write in your notes: Why should you never print secrets in CI logs?
<br>   GitHub masks secrets with ***, but if a secret is reversed, split, or encoded (like Base64), GitHub will not recognize it and will print it in plain text.
<br>   **Artifact exposure:** If a step prints a secret to a file and that file is saved as a workflow artifact, anyone with repository access can download and read it.
<br>   **Best Practice:** Always pass secrets directly as environment variables (env: SECRET_TOKEN: ${{ secrets.GITHUB_TOKEN }}) to the specific step or action that needs them, instead of using echo or run commands to view them.

---

### Task 2: Use Secrets as Environment Variables
1. Pass a secret to a step as an environment variable
2. Use it in a shell command without ever hardcoding it
3. Add `DOCKER_USERNAME` and `DOCKER_TOKEN` as secrets (you'll need these on Day 45)

---

### Task 3: Upload Artifacts
1. Create a step that generates a file — e.g., a test report or a log file
2. Use `actions/upload-artifact` to save it
3. After the workflow runs, download the artifact from the Actions tab

**Verify:** Can you see and download it from GitHub?

---

### Task 4: Download Artifacts Between Jobs
1. Job 1: generate a file and upload it as an artifact
2. Job 2: download the artifact from Job 1 and use it (print its contents)

Write in your notes: When would you use artifacts in a real pipeline?

---

### Task 5: Run Real Tests in CI
Take any script from your earlier days (Python or Shell) and run it in CI:
1. Add your script to the `github-actions-practice` repo
2. Write a workflow that:
   - Checks out the code
   - Installs any dependencies needed
   - Runs the script
   - Fails the pipeline if the script exits with a non-zero code
3. Intentionally break the script — verify the pipeline goes red
4. Fix it — verify it goes green again

---

### Task 6: Caching
1. Add `actions/cache` to a workflow that installs dependencies
2. Run it twice — observe the time difference
3. Write in your notes: What is being cached and where is it stored?

---

## Hints
- Secrets: `${{ secrets.SECRET_NAME }}`
- Upload artifact: `uses: actions/upload-artifact@v4`
- Download artifact: `uses: actions/download-artifact@v4`
- Cache: `uses: actions/cache@v4`
- GitHub masks secret values in logs automatically

---

## Documentation
Create `day-44-secrets-artifacts.md` with:
- Screenshots of artifact download
- Screenshot of your passing test run
- What you learned about secrets management

---

## Submission
1. Add `day-44-secrets-artifacts.md` to `2026/day-44/`
2. Commit and push to your fork

---

## Learn in Public
Share your first real test run passing in CI on LinkedIn.

`#90DaysOfDevOps` `#DevOpsKaJosh` `#TrainWithShubham`

Happy Learning!
**TrainWithShubham**
