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
  
* It will show *** output instead of printing actual secret.

Q: Why should you never print secrets in CI logs?

* **Masking Limitations:** GitHub masks secrets with `***`. However, if a secret is reversed, split, or encoded (like Base64), GitHub will not recognize it and will print it in plain text.
* **Artifact Exposure:** If a step prints a secret to a file and that file is saved as a workflow artifact, anyone with repository access can download and read it.
* **Best Practice:** Always pass secrets directly as environment variables (`env: SECRET_TOKEN: ${{ secrets.GITHUB_TOKEN }}`) to the specific step or action that needs them, instead of using `echo` or `run` commands to view them.

---

### Task 2: Use Secrets as Environment Variables
1. Pass a secret to a step as an environment variable
2. Use it in a shell command without ever hardcoding it
3. Add `DOCKER_USERNAME` and `DOCKER_TOKEN` as secrets (you'll need these on Day 45)

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

    - name: Use secrets as environment variables
      env:
        DOCKER_USERNAME: ${{ secrets.DOCKER_USERNAME }}
        DOCKER_TOKEN: ${{ secrets.DOCKER_TOKEN }}
      run: |
        echo "Docker username is $DOCKER_USERNAME"
        echo "Docker token length: ${#DOCKER_TOKEN}"

```

<img width="1343" height="444" alt="image" src="https://github.com/user-attachments/assets/82c245d6-1205-41ae-bff1-1d0fb152d7dd" />

---

### Task 3: Upload Artifacts
1. Create a step that generates a file — e.g., a test report or a log file
2. Use `actions/upload-artifact` to save it
3. After the workflow runs, download the artifact from the Actions tab

```yaml
name: artifact-upload
on: workflow_dispatch

jobs:
  artifact-job:
    runs-on: ubuntu-latest
    steps:
      - name: generate file
        run: echo "test file" >> artifact-test-file.txt
      - uses: actions/upload-artifact@v7
        with:
          name: my-artifact
          path: artifact-test-file.txt
```

<br><img width="1327" height="573" alt="image" src="https://github.com/user-attachments/assets/854cae00-5b60-4a03-8c93-18a72b2f93c5" />


**Verify:** Can you see and download it from GitHub?

---

### Task 4: Download Artifacts Between Jobs
1. Job 1: generate a file and upload it as an artifact
2. Job 2: download the artifact from Job 1 and use it (print its contents)

```yaml
name: artifact-upload
on: workflow_dispatch

jobs:
  artifact-job:
    runs-on: ubuntu-latest
    steps:
      - name: generate file
        run: echo "test file" >> artifact-test-file.txt
      - uses: actions/upload-artifact@v7
        with:
          name: my-artifact
          path: artifact-test-file.txt
```

<img width="1326" height="533" alt="image" src="https://github.com/user-attachments/assets/8342684d-a5b9-4406-8a0e-1949ae645ede" />

<img width="1327" height="573" alt="image" src="https://github.com/user-attachments/assets/df456a54-cf6d-451c-92b7-ce040b5e83c3" />


Write in your notes: When would you use artifacts in a real pipeline?

Artifacts are files generated during a workflow and saved for later use.

#### Common Use Cases

- **Share build outputs** between jobs (e.g., JAR, WAR, ZIP files)
- **Store test reports** for review after pipeline execution
- **Save logs** for troubleshooting failed jobs
- **Preserve security scan results** (Trivy, OWASP, etc.
- **Store deployment packages** for release and deployment stages

#### Example Flow

```text
Build Job
↓
Upload Artifact (app.jar)
↓
Test Job
↓
Download Artifact
↓
Deploy Job
```

#### Key Benefit

Artifacts ensure the **same build output** is used across all pipeline stages without rebuilding the application.

---

### Task 5: Run Real Tests in CI
Take any script from your earlier days (Python or Shell) and run it in CI:
1. Add your script to the `github-actions-practice` repo

#### calculator_test.py

```python
import numpy as np
numbers = np.array([10, 20, 30, 40])
total = np.sum(numbers)
assert total == 100, f"Expected 100 but got {total}"
print("✅ Calculator test passed")
```

#### requirements.txt

```text
numpy
```

2. Write a workflow that:
   - Checks out the code
   - Installs any dependencies needed
   - Runs the script
   - Fails the pipeline if the script exits with a non-zero code
  
```yaml

name: Run python Tests

on:
  workflow_dispatch:

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Code
        uses: actions/checkout@v7

      - name: Set Up Python
        uses: actions/setup-python@v7
        with:
          python-version: '3.13'

      - name: Install Dependencies
        run: pip install -r python-app/requirements.txt

      - name: Run Test Script
        run: python python-app/calculator_test.py

```
    <img width="1323" height="582" alt="image" src="https://github.com/user-attachments/assets/85183a1b-76a7-4451-b165-5accf617756b" />


3. Intentionally break the script — verify the pipeline goes red

Changed the code so that total is not 100

#### calculator_test.py

```python

import numpy as np
numbers = np.array([10, 20, 30, 30])
total = np.sum(numbers)
assert total == 100, f"Expected 100 but got {total}"
print("✅ Calculator test passed")

```

#### requirements.txt

```text
numpy
```

<img width="1323" height="574" alt="image" src="https://github.com/user-attachments/assets/ceaeb043-756f-4d8c-9928-39dc697d085c" />

4. Fix it — verify it goes green again

---

### Task 6: Caching
1. Add `actions/cache` to a workflow that installs dependencies
2. Run it twice — observe the time difference

```yaml
name: Run python Tests

on:
  workflow_dispatch:

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Code
        uses: actions/checkout@v7

      - name: Set Up Python
        uses: actions/setup-python@v7
        with:
          python-version: '3.13'

      - uses: actions/cache@v6
        with:
          path: ~/.cache/pip
          key: ${{ runner.os }}-pip-${{ hashFiles('python-app/requirements.txt') }}
          restore-keys: |
            ${{ runner.os }}-pip-

      - name: Install Dependencies
        run: pip install -r python-app/requirements.txt

      - name: Run Test Script
        run: python python-app/calculator_test.py
```

<img width="1314" height="387" alt="image" src="https://github.com/user-attachments/assets/1ecc7516-8ab4-47cf-8bfc-411780cb5bd6" />

3. Write in your notes: What is being cached and where is it stored?

#### What Is Being Cached and Where Is It Stored?

##### What Is Being Cached?

The following configuration caches Python packages downloaded by `pip`:

```yaml
- uses: actions/cache@v6
  with:
    path: ~/.cache/pip
```

This cache contains:
- Downloaded Python packages
- Package metadata
- Files required by `pip install`

##### Where Is It Stored?

```text
~/.cache/pip
```

On the GitHub Actions runner, this expands to:

```text
/home/runner/.cache/pip
```

##### How It Works

1. First workflow run:
   - Dependencies are downloaded from PyPI.
   - Cache is created and saved.

2. Subsequent workflow runs:
   - Cache is restored using the cache key.
   - Previously downloaded packages are reused.
   - Workflow runs faster.

##### Cache Key

```yaml
key: ${{ runner.os }}-pip-${{ hashFiles('python-app/requirements.txt') }}
```

- `runner.os` identifies the operating system.
- `hashFiles()` creates a hash of `requirements.txt`.
- If `requirements.txt` changes, a new cache is created automatically.

##### Benefits

- Faster workflow execution
- Reduced dependency download time
- Lower network usage
- More efficient CI/CD pipelines

<img width="622" height="155" alt="image" src="https://github.com/user-attachments/assets/89cf8c77-4574-40fb-b804-879c88edd34e" />

<img width="625" height="140" alt="image" src="https://github.com/user-attachments/assets/294ee963-fb56-4ad3-8a79-335ab92462e3" />

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
