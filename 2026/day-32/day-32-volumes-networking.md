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

2. Create some data inside it (a table, a few rows — anything)
   <br><img width="882" height="422" alt="image" src="https://github.com/user-attachments/assets/29165c88-9a52-46ef-abe1-05a6a87380d5" />
   <br> <img width="877" height="299" alt="image" src="https://github.com/user-attachments/assets/c1e52f93-b537-40bd-8700-3884e5862245" />

3. Stop and remove the container
   <br><img width="1059" height="103" alt="image" src="https://github.com/user-attachments/assets/98bc5e57-cdec-4ce3-b14d-edcf1dbe7ce7" />

4. Run a new one — is your data still there?
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
2. Run the same database container, but this time **attach the volume** to it
   <br><img width="1011" height="297" alt="image" src="https://github.com/user-attachments/assets/8b3e4f9e-23ed-4644-aa19-416a6723f3c8" /><br>
3. Add some data, stop and remove the container
   <br><img width="875" height="269" alt="image" src="https://github.com/user-attachments/assets/757db6c9-ef07-44e9-afeb-1a3dd1fa76f7" /><br><img width="1067" height="108" alt="image" src="https://github.com/user-attachments/assets/b1b553c1-c29e-46f8-8950-a37f52d3698a" /><br>

4. Run a brand new container with the **same volume**
   <img width="1009" height="296" alt="image" src="https://github.com/user-attachments/assets/f3639952-8884-420d-b317-3b473d310bf1" />


5. Is the data still there?
   <br>Yes data exist as docker volume of host machine was attached to the container while creating and same volume was attached again while creating new container. 

**Verify:** `docker volume ls`, `docker volume inspect`

---

### Task 3: Bind Mounts
1. Create a folder on your host machine with an `index.html` file
   <br><img width="475" height="55" alt="image" src="https://github.com/user-attachments/assets/2ad5ac91-6c68-42c3-9d94-10b90e42b004" />

2. Run an Nginx container and **bind mount** your folder to the Nginx web directory
   <br><img width="980" height="83" alt="image" src="https://github.com/user-attachments/assets/a9721d61-06b0-45ab-8d25-65c9da580d38" />

3. Access the page in your browser
   <br><img width="1175" height="329" alt="image" src="https://github.com/user-attachments/assets/8a7a5c37-560d-4d3b-b239-8eafa9038e8b" />

4. Edit the `index.html` on your host — refresh the browser
   <br><img width="1016" height="102" alt="image" src="https://github.com/user-attachments/assets/dddb0acd-dffc-4181-b336-013059b60573" />
   <br><img width="1193" height="345" alt="image" src="https://github.com/user-attachments/assets/d1289029-dd2d-451f-93a8-0cf9319acf6f" />

5. Write in your notes: What is the difference between a named volume and a bind mount?
      <br>Docker: Named Volumes vs. Bind Mounts

      <br>Management
         <br>Named Volume:** Managed entirely by Docker. Files live in Docker's internal directory.
         <br>Bind Mount:** Managed by you. Links a specific, exact path from your computer.

   <br>Docker: Named Volumes vs. Bind Mounts (Behavior with Existing Files)

      <br>When mounting storage to a Docker container, how Docker handles existing files inside the container's target directory depends entirely on whether you use a **Named Volume** or a **Bind Mount**.

      <br>Named Volume (Initialization & Copying)
      <br>How it works: If the named volume is newly created and completely empty, Docker will automatically **copy** all existing files from the container's target directory into your volume on the host.
Result: No data is lost. The container retains its default files (e.g., Nginx's default splash screen), and they safely populate your volume.

      <br>Bind Mount (Overwriting / Hiding)
      <br>How it works:** A bind mount forces a specific path from your host machine onto the container's target directory. Docker overwrites or hides the container's internal directory with your host folder.
      <br>Result: If your host folder is empty, the container's directory instantly becomes empty. Any pre-existing files built into the container image are hidden, which can cause services like Nginx to crash if critical files disappear.

---

---

### Task 4: Docker Networking Basics
1. List all Docker networks on your machine
   <br><img width="451" height="75" alt="image" src="https://github.com/user-attachments/assets/ebd0216d-054b-44e1-9b09-49c8f50adef5" />

2. Inspect the default `bridge` network
   <br><img width="579" height="657" alt="image" src="https://github.com/user-attachments/assets/d7a5ab2c-1502-4c33-8dfc-68f372be0bca" />
   <br><img width="690" height="357" alt="image" src="https://github.com/user-attachments/assets/41ced28e-7f3e-4996-8ade-47c9a635998c" />

3. Run two containers on the default bridge — can they ping each other by **name**?
4. Run two containers on the default bridge — can they ping each other by **IP**?
   <br><img width="639" height="199" alt="image" src="https://github.com/user-attachments/assets/b93df2e5-6353-4ce4-977b-525121ef2b84" />
   <br><img width="695" height="777" alt="image" src="https://github.com/user-attachments/assets/205ce9f5-807c-436d-9235-6b6486f978a7" />
   <br><img width="636" height="72" alt="image" src="https://github.com/user-attachments/assets/cbcfef36-978a-44df-b912-97fcab6253e0" />
   <br>Ping doesn't work with container name when on default bridge network. It works only with IP address
   <br><img width="513" height="278" alt="image" src="https://github.com/user-attachments/assets/2066f93d-3c79-4e3b-9d64-8dca6c3e0e58" />
   <br>Additional observation, they can ping each other if on same bridged network also they can ping host machine IP and www.google.com i.e. internet.
   <br><img width="500" height="35" alt="image" src="https://github.com/user-attachments/assets/514d1e94-0445-4319-8bf7-7f274c56c5c0" />
   <br><img width="492" height="107" alt="image" src="https://github.com/user-attachments/assets/f4860cfc-54c6-4fda-898b-dac7c22ab34f" />
   <br><img width="462" height="134" alt="image" src="https://github.com/user-attachments/assets/38483999-c5a3-443e-bde5-78fca756debf" />
---

### Task 5: Custom Networks
1. Create a custom bridge network called `my-app-net`
   <br><img width="545" height="127" alt="image" src="https://github.com/user-attachments/assets/906cb2c9-429e-4a66-8b81-76186bd2228f" />

3. Run two containers on `my-app-net`
   <br><img width="749" height="120" alt="image" src="https://github.com/user-attachments/assets/0c50857e-c883-4ad6-af4b-0e2115e647db" />

5. Can they ping each other by **name** now?
   <br>from container funny_jemison to container objective_kowalevski
   <br><img width="652" height="186" alt="image" src="https://github.com/user-attachments/assets/634df5ee-73c2-4e02-bcb0-fb37119d7763" />
   <br>from container objective_kowalevski to container funny_jemison
   <br><img width="683" height="245" alt="image" src="https://github.com/user-attachments/assets/6cd57dd2-1ca4-464b-96d8-5265c1001f4c" />

7. Write in your notes: Why does custom networking allow name-based communication but the default bridge doesn't?
   <br>Custom Bridge: When you create a user-defined network, Docker automatically runs a scoped **Internal DNS Server** inside that network. It keeps a live registry of every container's name and its current IP address. When you type `ping container1`, Docker's DNS translates the name to the IP instantly.
   <br>Default Bridge: The default bridge does not have access to this built-in DNS service. It relies on the legacy `/etc/hosts` file mechanism, which cannot dynamic-map new containers as they start and stop.
---

### Task 6: Put It Together
1. Create a custom network
   <br><img width="671" height="123" alt="image" src="https://github.com/user-attachments/assets/03211f6f-3252-4308-8f6c-9bf9d58167c2" />
5. Run an **app container** (use any image) on the same network
   <br><img width="1030" height="78" alt="image" src="https://github.com/user-attachments/assets/6c8d200b-da2b-478b-b5bf-e675b9c19409" />
3. Run a **database container** (MySQL/Postgres) on that network with a volume for data
   <br><img width="521" height="40" alt="image" src="https://github.com/user-attachments/assets/83f41f25-a6d2-437b-a252-3e45a71f9b72" />
   <br><img width="967" height="34" alt="image" src="https://github.com/user-attachments/assets/885bfa31-1d87-4d77-8f56-ca9d553883a0" />
   <br><img width="697" height="712" alt="image" src="https://github.com/user-attachments/assets/e976d3c2-c44e-4f98-b9c4-8959e31443d4" />
   <br><img width="1041" height="280" alt="image" src="https://github.com/user-attachments/assets/b2084f62-2fa2-486e-99f9-6ed2c331e67c" />
   
7. Verify the app container can reach the database by container name
   <br> yes verified as per above image, it can reach by ping
   <br> one more observation, DB port 3306 is not exposed outside still other container can reach MySQL DB on port 3306
   <br><img width="875" height="138" alt="image" src="https://github.com/user-attachments/assets/3267c1e0-a46b-4194-bdd0-9029dea71beb" />

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
