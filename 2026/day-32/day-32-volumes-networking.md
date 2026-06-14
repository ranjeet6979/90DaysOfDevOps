# Day 32 – Docker Volumes & Networking

## Task
Today's goal is to **solve two real problems: data persistence and container communication**.

Containers are ephemeral — they lose data when removed. And by default, containers can't easily talk to each other. Today you fix both.

---

## Expected Output
- A markdown file: `day-32-volumes-networking.md`
- Screenshots of your experiments

---

## Challenge Tasks

### Task 1: The Problem
1. Run a Postgres or MySQL container
   <br><img width="787" height="306" alt="image" src="https://github.com/user-attachments/assets/8bcf90ee-fde8-43b0-9d94-cff974b8f3c4" />

3. Create some data inside it (a table, a few rows — anything)
   <br><img width="882" height="422" alt="image" src="https://github.com/user-attachments/assets/29165c88-9a52-46ef-abe1-05a6a87380d5" />
   <br> <img width="877" height="299" alt="image" src="https://github.com/user-attachments/assets/c1e52f93-b537-40bd-8700-3884e5862245" />

5. Stop and remove the container
   <br><img width="1059" height="103" alt="image" src="https://github.com/user-attachments/assets/98bc5e57-cdec-4ce3-b14d-edcf1dbe7ce7" />

7. Run a new one — is your data still there?
   <br> Data will be deleted as storage is temporary until volume is mapped to specific folder on the container.
   <br><img width="879" height="294" alt="image" src="https://github.com/user-attachments/assets/e4372738-31f6-4858-b944-5b5d940c51de" />


Write what happened and why.

---

### Task 2: Named Volumes
1. Create a named volume
   <br><img width="550" height="36" alt="image" src="https://github.com/user-attachments/assets/0203651e-0df6-44fd-af43-5c78ac58a666" />
   <br><img width="531" height="101" alt="image" src="https://github.com/user-attachments/assets/3505bed5-415e-4ab1-ab72-6d8991a13ec1" />
   <br><img width="561" height="183" alt="image" src="https://github.com/user-attachments/assets/d901a878-f835-4060-9913-5b0a2fe9ffe4" />
   <br>
3. Run the same database container, but this time **attach the volume** to it
   <br><img width="1011" height="297" alt="image" src="https://github.com/user-attachments/assets/8b3e4f9e-23ed-4644-aa19-416a6723f3c8" /><br>
5. Add some data, stop and remove the container
   <br><img width="875" height="269" alt="image" src="https://github.com/user-attachments/assets/757db6c9-ef07-44e9-afeb-1a3dd1fa76f7" /><br><img width="1067" height="108" alt="image" src="https://github.com/user-attachments/assets/b1b553c1-c29e-46f8-8950-a37f52d3698a" /><br>

7. Run a brand new container with the **same volume**
   <img width="1009" height="296" alt="image" src="https://github.com/user-attachments/assets/f3639952-8884-420d-b317-3b473d310bf1" />


9. Is the data still there?
   Yes data exist as docker volume of host machine was attached to the container while creating and same volume was attached again while creating new container. 

**Verify:** `docker volume ls`, `docker volume inspect`

---

### Task 3: Bind Mounts
1. Create a folder on your host machine with an `index.html` file
2. Run an Nginx container and **bind mount** your folder to the Nginx web directory
3. Access the page in your browser
4. Edit the `index.html` on your host — refresh the browser

Write in your notes: What is the difference between a named volume and a bind mount?

---

### Task 4: Docker Networking Basics
1. List all Docker networks on your machine
2. Inspect the default `bridge` network
3. Run two containers on the default bridge — can they ping each other by **name**?
4. Run two containers on the default bridge — can they ping each other by **IP**?

---

### Task 5: Custom Networks
1. Create a custom bridge network called `my-app-net`
2. Run two containers on `my-app-net`
3. Can they ping each other by **name** now?
4. Write in your notes: Why does custom networking allow name-based communication but the default bridge doesn't?

---

### Task 6: Put It Together
1. Create a custom network
2. Run a **database container** (MySQL/Postgres) on that network with a volume for data
3. Run an **app container** (use any image) on the same network
4. Verify the app container can reach the database by container name

---

## Hints
- Volumes: `docker volume create`, `-v volume_name:/path`
- Bind mount: `-v /host/path:/container/path`
- Networking: `docker network create`, `--network`
- Ping: `docker exec container1 ping container2`

---

## Submission
1. Add your `day-32-volumes-networking.md` to `2026/day-32/`
2. Commit and push to your fork

---

## Learn in Public
Share what happened when you deleted a container without a volume on LinkedIn. The "aha moment" is real.

`#90DaysOfDevOps` `#DevOpsKaJosh` `#TrainWithShubham`

Happy Learning!
**TrainWithShubham**
