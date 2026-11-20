# 00 — Foundations

## 12-Factor App

The **12-Factor App** is a methodology for building applications that are easy to develop, deploy, scale, and maintain.

It provides principles for creating modern applications, especially cloud-native and SaaS applications.

## The 12 Factors

| # | Factor | Main Idea |
|---|---|---|
| 01 | Codebase | One codebase, multiple deployments. |
| 02 | Dependencies | Explicitly declare application dependencies. |
| 03 | Config | Store configuration outside the code. |
| 04 | Backing Services | Treat external services as attached resources. |
| 05 | Build, Release, Run | Separate building, releasing, and running. |
| 06 | Processes | Run the application as stateless processes. |
| 07 | Port Binding | Export services through a port. |
| 08 | Concurrency | Scale by running multiple processes. |
| 09 | Disposability | Start quickly and shut down gracefully. |
| 10 | Dev/Prod Parity | Keep development and production environments similar. |
| 11 | Logs | Treat logs as event streams. |
| 12 | Admin Processes | Run administrative tasks as separate processes. |

## Why It Matters in DevOps

- Makes applications easier to deploy.
- Supports automation and CI/CD.
- Simplifies scaling and maintenance.
- Encourages consistency between environments.
- Works well with containers and cloud infrastructure.

## Related Technologies

Git · Docker · CI/CD · Environment Variables · Cloud Platforms

---

**Key takeaway:** Build applications that are portable, configurable, scalable, and easy to operate.