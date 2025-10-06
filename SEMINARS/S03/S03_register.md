# S03 - Шаблон реестра NFR (Given-When-Then)

---

## Поля реестра (data dictionary)

* **ID** - короткий идентификатор, например `NFR-001`.
* **User Story / Feature** - к какой истории/фиче относится требование (ссылка допустима).
* **Category** - выберите из банка (напр.: `Performance`, `Security-AuthZ/RBAC`, `RateLimiting`, `Privacy/PII`, `Observability/Logging`, …).
* **Requirement (NFR)** - *измеримое* требование (числа/пороги/границы действия).
* **Rationale / Risk** - зачем это нужно, какой риск/ценность покрываем.
* **Acceptance (G-W-T)** - проверяемая формулировка: *Given … When … Then …*.
* **Evidence (test/log/scan/policy)** - чем подтвердим выполнение (тест, лог-шаблон, сканер, политика).
* **Trace (issue/link)** - ссылка на задачу, обсуждение, артефакт.
* **Owner** - ответственный.
* **Status** - `Draft` | `Proposed` | `Approved` | `Implemented` | `Verified`.
* **Priority** - `P1 - High` | `P2 - Medium` | `P3 - Low`.
* **Severity** - `S1 - Critical` | `S2 - Major` | `S3 - Minor`.
* **Tags** - произвольные метки (через запятую).

---

## Таблица реестра

| ID      | User Story / Feature      | Category                 | Requirement (NFR)                                                   | Rationale / Risk                     | Acceptance (G-W-T)                                                                                                    | Evidence (test/log/scan/policy)               | Trace (issue/link) | Owner  | Status   | Priority    | Severity   | Tags              |
| ------- | ------------------------- | ------------------------ | ------------------------------------------------------------------- | ------------------------------------ | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------- | ------------------ | ------ | -------- | ----------- | ---------- | ----------------- |
| NFR-001 | As a user I upload avatar | Security-InputValidation | Reject payloads >1 MiB; MIME из allowlist; **extra** поля запрещены | Защита от DoS/грязных входных данных | **Given** тело 2 MiB и неизвестные поля<br>**When** POST `/api/files/avatar`<br>**Then** 413 с RFC7807 + запрет extra | test: `e2e-upload-limit`; policy: schema/size | #123               | team-a | Proposed | P2 - Medium | S2 - Major | limits,validation |
| NFR-002 | As a client I call /api/* | Performance              | P95 ≤ 300 ms при 50 RPS в течение 5 мин                             | UX/SLO                               | **Given** сервис здоров<br>**When** 50 RPS на `/api/*` 5 минут<br>**Then** P95 ≤ 300 ms; error rate ≤ 1%              | test: `load-50rps`; log: latency quantiles    | #124               | team-a | Draft    | P1 - High   | S2 - Major | perf,slo          |

> Продолжайте ниже добавлять строки до достижения **8-10 NFR** (или больше, если нужно):

| ID | User Story / Feature | Category | Requirement (NFR) | Rationale / Risk | Acceptance (G-W-T) | Evidence (test/log/scan/policy) | Trace (issue/link) | Owner | Status | Priority    | Severity   | Tags |
| -- | -------------------- | -------- | ----------------- | ---------------- | ------------------ | ------------------------------- | ------------------ | ----- | ------ | ----------- | ---------- | ---- |
| NFR001   |                      |          |                   |                  |                    |                                 |                    |       | Draft  | P2 - Medium | S2 - Major |      |
|    |                      |          |                   |                  |                    |                                 |                    |       | Draft  | P2 - Medium | S2 - Major |      |
|    |                      |          |                   |                  |                    |                                 |                    |       | Draft  | P2 - Medium | S2 - Major |      |
|    |                      |          |                   |                  |                    |                                 |                    |       | Draft  | P2 - Medium | S2 - Major |      |
|    |                      |          |                   |                  |                    |                                 |                    |       | Draft  | P2 - Medium | S2 - Major |      |
|    |                      |          |                   |                  |                    |                                 |                    |       | Draft  | P2 - Medium | S2 - Major |      |
|    |                      |          |                   |                  |                    |                                 |                    |       | Draft  | P2 - Medium | S2 - Major |      |
|    |                      |          |                   |                  |                    |                                 |                    |       | Draft  | P2 - Medium | S2 - Major |      |

---
