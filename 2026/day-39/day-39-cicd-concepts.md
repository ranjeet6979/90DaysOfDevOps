# Day 39 – What is CI/CD?

## Task
Before writing a single pipeline, understand **why CI/CD exists** and what it actually does.

Today is a research and diagram day — no pipelines yet. Get the concepts right first.

---

## Expected Output
- A markdown file: `day-39-cicd-concepts.md`
- A pipeline diagram (hand-drawn or text-based)

---

## Challenge Tasks

### Task 1: The Problem
Think about a team of 5 developers all pushing code to the same repo manually deploying to production.

Write in your notes:
1. What can go wrong?
   <br>if all developers push code to the same repo manually deploying to production, there are possibility of conflict between changes pushed by them also overwrite or removing others change.
   
2. What does "it works on my machine" mean and why is it a real problem?
   <br>**"It works on my machine"** means an application runs successfully on a developer's local system because it uses specific software versions, libraries, dependencies, and configurations available there. When the code is moved to another environment, such as testing or production, it may fail or behave unexpectedly if those dependencies or configurations are different.
<br><br>This is a real problem because it can cause deployment failures, bugs, and delays in troubleshooting. Containerization technologies such as Docker help solve this issue by packaging the application with all its dependencies, ensuring consistent behavior across different environments.

3. How many times a day can a team safely deploy manually?
   <br>There are only a limited number of times a team can safely deploy manually in a day because each deployment requires coordination among team members. Developers need to ensure they are not overwriting each other's changes and that all code has been properly tested. As the number of deployments increases, the risk of human error, missed changes, and deployment failures also increases.

---

### Task 2: CI vs CD
Research and write short definitions (2-3 lines each):
#### 1. **Continuous Integration** — what happens, how often, what it catches
   <br>this involves code and integrating the code in version control systems (VCS) like Git/GitHub, building the code to create a deployable package/executable, performing automated testing.
   <br>In this, developers frequently merge code into a central repository multiple times a day. Each merge triggers automated builds and tests to catch bugs and integration conflicts immediately.
   <br>Software Example: Multiple developers work on a ride-sharing app. When a developer pushes code for a new "fare estimator" feature, an automated server instantly builds the app and runs tests to ensure it does not break the existing login or GPS systems.

#### 2. **Continuous Delivery** — how it's different from CI, what "delivery" means
   <br>This involves pushing the code to VCS, build/compile the code, testing pushed code and make it ready to deploy. However, it is not deployed until manual approval to deploy.
   <br>This extends CI by automatically building, testing, and preparing code changes for release. The software is always in a deployable state, but actual deployment to live users requires a final manual approval.
   <br>Software Example: A healthcare platform updates its patient portal. The system automatically tests the new code and moves it to a staging environment. The product manager then reviews it and manually clicks "Deploy" during a weekend maintenance window.
   
#### 3. **Continuous Deployment** — how it differs from Delivery, when teams use it
   <br>This involces pushing the code to VCS, build/compile the code, testing pushed code and deploy the code.
   <br>This removes human intervention entirely from the release pipeline. Every code change that passes all automated testing stages is automatically deployed directly to production and live users within minutes.
   <br>Software Example: Streaming platforms like Netflix use this approach. If a developer fixes a minor UI bug on the video player page, the code passes automated tests and goes live to millions of users worldwide immediately without needing a manager's sign-off.
   
---

### Task 3: Pipeline Anatomy
A pipeline has these parts — write what each one does:
- **Trigger** — what starts the pipeline
  <br>A pipeline trigger is a condition or event that starts an automated pipeline that performs build, test, deployment, or other operational workflows.
- **Stage** — a logical phase (build, test, deploy)
  <br>Groups related tasks into a major phase of the lifecycle, ensuring the build phase passes before testing begins.
- **Job** — a unit of work inside a stage
  <br>A job is a sequential set of steps executed on the same runner or agen
- **Step** — a single command or action inside a job
  <br>A step is a single, specific task that runs inside a larger automated process (a job)
- **Runner** — the machine that executes the job
  <br>Provides the underlying physical server, virtual machine, or container environment that actually runs the job.
- **Artifact** — output produced by a job
  <br>Jobs can output an archive of files and directories. This output is known as a job artifact. Artifacts can include build output or report files.


---

### Task 4: Draw a Pipeline
Draw a CI/CD pipeline for this scenario:
> A developer pushes code to GitHub. The app is tested, built into a Docker image, and deployed to a staging server.

Include at least 3 stages. Hand-drawn and photographed is perfectly fine.

---

### Task 5: Explore in the Wild
1. Open any popular open-source repo on GitHub (Kubernetes, React, FastAPI — pick one you know)
2. Find their `.github/workflows/` folder
3. Open one workflow YAML file
4. Write in your notes:
   - What triggers it?
   - How many jobs does it have?
   - What does it do? (best guess)

---

## Hints
- CI/CD is a practice, not just a tool
- GitHub Actions, Jenkins, GitLab CI, CircleCI — all are tools that implement CI/CD
- A pipeline failing is not a problem — it's CI/CD doing its job

---

## Documentation
Create `day-39-cicd-concepts.md` with:
- Your CI vs CD vs CD definitions
- Pipeline anatomy notes
- Your pipeline diagram
- What you found in the open-source repo

---

## Submission
1. Add your `day-39-cicd-concepts.md` to `2026/day-39/`
2. Commit and push to your fork

---

## Learn in Public
Share your pipeline diagram on LinkedIn — even a rough hand-drawn one gets engagement.

`#90DaysOfDevOps` `#DevOpsKaJosh` `#TrainWithShubham`

Happy Learning!
**TrainWithShubham**
