# 12-Factor App — Quick Reference

## 01 — Codebase

**One codebase, multiple deployments.**

- Keep application source code in version control.
- Deploy the same codebase to different environments.

**Example:** One Git repository deployed to Development, Staging, and Production.

**Remember:** One codebase does not mean one deployment.

---

## 02 — Dependencies

**Explicitly declare and isolate dependencies.**

- Declare everything the application needs.
- Avoid relying on software installed manually on the host.
- Use dependency management tools.

**Example:** `requirements.txt` for Python or `package.json` for Node.js.

**Remember:** An application should know exactly what it depends on.

---

## 03 — Config

**Store configuration outside the application code.**

- Separate configuration from source code.
- Use environment variables for environment-specific settings.
- Never hardcode passwords or secrets.

**Example:**

```bash
DB_HOST=localhost
DB_PORT=5432
```

**Remember:** Same code, different configuration.

---

## 04 — Backing Services

**Treat external services as attached resources.**

- Databases, caches, and message brokers are backing services.
- Connect to them through configuration.
- Applications should not depend on a specific service instance.

**Example:** PostgreSQL used as an external database service.

**Remember:** Services should be replaceable without changing application code.

---

## 05 — Build, Release, Run

**Separate the application lifecycle into three stages.**

- **Build:** Convert source code into an executable package.
- **Release:** Combine the build with configuration.
- **Run:** Execute the release.

**Example:** CI builds a Docker image, a release uses that image with configuration, and a container runs it.

**Remember:** Build once, release, then run.

---

## 06 — Processes

**Run the application as stateless processes.**

- Do not store important persistent data inside the application process.
- Store persistent data in databases or external storage.
- Processes should be replaceable.

**Example:** User-uploaded files are stored in external storage instead of the container filesystem.

**Remember:** Application processes should not depend on local persistent state.

---

## 07 — Port Binding

**Expose services through port binding.**

- Applications should provide their own network service.
- They should listen on a configured port.
- Avoid depending on a separate web server to provide the application interface.

**Example:**

```bash
python app.py
```

The application listens on its configured port.

**Remember:** The application should be able to serve requests through its own port.

---

## 08 — Concurrency

**Scale by running multiple processes.**

- Run multiple instances to handle more workload.
- Scale horizontally instead of relying only on bigger machines.
- Different process types can handle different tasks.

**Example:** Run multiple web application instances behind a load balancer.

**Remember:** More workload can be handled by adding processes.

---

## 09 — Disposability

**Processes should start quickly and shut down gracefully.**

- Applications should be easy to start and stop.
- Handle shutdown signals properly.
- Avoid losing important work during shutdown.

**Example:** A container receives a stop signal and finishes active requests before exiting.

**Remember:** Processes should be replaceable at any time.

---

## 10 — Dev/Prod Parity

**Keep development and production environments similar.**

- Avoid differences in software versions and dependencies.
- Reduce the time between development and deployment.
- Use consistent environments.

**Example:** Use Docker to run the same application environment locally and in production.

**Remember:** Fewer environment differences mean fewer deployment surprises.

---

## 11 — Logs

**Treat logs as event streams.**

- Applications should write logs to standard output.
- Let the execution environment handle log collection and storage.
- Avoid managing log files inside the application.

**Example:**

```bash
docker logs my-container
```

**Remember:** Applications generate logs; the platform manages them.

---

## 12 — Admin Processes

**Run administrative tasks as separate processes.**

- Keep maintenance tasks separate from the main application.
- Use the same codebase and configuration.
- Run tasks when needed.

**Example:** A database migration or one-time maintenance script.

**Remember:** Administrative tasks should use the same application environment.