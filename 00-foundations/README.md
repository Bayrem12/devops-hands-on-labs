# 00 — DevOps Foundations

This module covers the foundational architectural mindset behind modern software delivery and operations.

## What Is Inside
- **`12-factor-app/`**: Notes and small hands-on examples on the **Twelve-Factor App** methodology—designing applications with externalized config, declared dependencies, stateless processes, port binding, graceful shutdown, stream logs, and one-off admin tasks.

## Why Foundations Matter Before Linux, Git, Bash, and Docker
- **Code & Config Separation:** Knowing why environment variables belong outside code prepares you for Linux environment files, `systemd` services, and container configuration.
- **Stateless Processes & Backing Services:** Understanding why state belongs in external stores (like Redis or databases) rather than local disk or memory makes scaling and container restarts safe.
- **Logs & Lifecycle:** Writing logs to `STDOUT`/`STDERR` and handling shutdown signals cleanly connects directly to service managers and container runtimes.
