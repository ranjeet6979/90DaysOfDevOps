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
   (br>**"It works on my machine"** means an application runs successfully on a developer's local system because it uses specific software versions, libraries, dependencies, and configurations available there. When the code is moved to another environment, such as testing or production, it may fail or behave unexpectedly if those dependencies or configurations are different.
<br><br>This is a real problem because it can cause deployment failures, bugs, and delays in troubleshooting. Containerization technologies such as Docker help solve this issue by packaging the application with all its dependencies, ensuring consistent behavior across different environments.

3. How many times a day can a team safely deploy manually?
   <br>There are only a limited number of times a team can safely deploy manually in a day because each deployment requires coordination among team members. Developers need to ensure they are not overwriting each other's changes and that all code has been properly tested. As the number of deployments increases, the risk of human error, missed changes, and deployment failures also increases.

---

### Task 2: CI vs CD
Research and write short definitions (2-3 lines each):
1. **Continuous Integration** — what happens, how often, what it catches
   <br>this involves code and integrating the code in version control systems (VCS) like Git/Github, building the code to create a deployable package/executable, performing automated testing.

2. **Continuous Delivery** — how it's different from CI, what "delivery" means
   <br>This involces pushing the code to VCS, build/compile the code, testing pushed code and make it ready to deploy. However it is not deploy until manual approval to deploy.
   
3. **Continuous Deployment** — how it differs from Delivery, when teams use it
   <br>This involces pushing the code to VCS, build/compile the code, testing pushed code and deploy the code.

Write one real-world example for each.

---

### Task 3: Pipeline Anatomy
A pipeline has these parts — write what each one does:
- **Trigger** — what starts the pipeline
- **Stage** — a logical phase (build, test, deploy)
- **Job** — a unit of work inside a stage
- **Step** — a single command or action inside a job
- **Runner** — the machine that executes the job
- **Artifact** — output produced by a job

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
