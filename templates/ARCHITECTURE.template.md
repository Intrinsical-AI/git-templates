
# [PROJECT_NAME] — Architecture Spec

> **Owners:** [OWNERS]
> **Scope:** [WHAT_IS_COVERED] / **Out of scope:** [WHAT_IS_NOT_COVERED]

---

## 0) TL;DR (90 seconds)

- **What:** [ONE_PARAGRAPH]
- **Why:** [ONE_PARAGRAPH]
- **How:** [3-7 BULLETS: key components + flows]
- **Non-negotiables:** [3-7 invariants / constraints]

---

## 1) Goals, Non-goals, Constraints

### 1.1 Goals (prioritized)
1. ...
2. ...

### 1.2 Non-goals
- ...

### 1.3 Constraints (hard)
- Legal / regulatory: [CONSTRAINT]
- Budget / latency / throughput: [CONSTRAINT]
- Team: [CONSTRAINT]
- Tech (languages, runtime, hosting): [CONSTRAINT]

### 1.4 Quality attributes

| Attribute    |     Target | Measured by   |
| ------------ | ---------: | ------------- |
| Latency p95  |     [MS]ms | [BENCHMARK]   |
| Availability |   [99.X]%  | [SLO]         |
| Consistency  | [MODEL]    | [TESTS]       |
| Cost         | [EUR]/mo   | [BILLING]     |

---

## 2) Domain model

### 2.1 Glossary (ubiquitous language)
- **[TERM_A]:** [DEFINITION]
- **[TERM_B]:** [DEFINITION]

### 2.2 Bounded contexts

| Context      | Responsibility | Owns data? | External deps | Public APIs |
| ------------ | -------------- | ---------: | ------------- | ----------- |
| [CONTEXT_A]  | ...            |    Yes/No  | ...           | ...         |

### 2.3 Entities & value objects

#### Entity: `[ENTITY_NAME]`
- **Identity:** [ID_RULES]
- **Lifecycle:** [STATES_AND_TRANSITIONS]
- **Invariants:** (see §4)
- **Context:** [OWNING_CONTEXT]
- **Storage:** [TABLE_OR_COLLECTION]

#### Value Object: `[VO_NAME]`
- **Equality:** [RULE]
- **Validation:** [RULE]

---

## 3) Data model

### 3.1 Storage overview
- Primary DB: [DB_TYPE]
- Cache: [CACHE_TYPE]
- Search / vector index: [INDEX_TYPE]
- Files / blobs: [STORAGE_TYPE]

### 3.2 Schemas
> Link to migrations / schema files.
- `schema/[FILE]` or `migrations/[FILE]`

### 3.3 DTOs / Contracts
- Location: `src/[PACKAGE]/dto/`
- Versioning: [STRATEGY]

#### DTO: `[DTO_NAME]`
- **Purpose:** request / response / event
- **Fields:** [TYPE, REQUIRED, CONSTRAINTS]
- **Backward compat:** [RULES]
- **Example:**

```json
{ "[FIELD]": "[VALUE]" }
```

### 3.4 Mapping rules (DTO <-> Domain <-> Persistence)
- DTO -> Domain: [WHERE, VALIDATIONS]
- Domain -> Persistence: [ORM/SQL, TRANSACTIONS]
- Forbidden shortcuts: [RULES]

---

## 4) Invariants & validation

### 4.1 Global invariants
- [INVARIANT_1]
- [INVARIANT_2]

### 4.2 Per-aggregate invariants

| Aggregate    | Invariant    | Enforced where   | Test coverage        |
| ------------ | ------------ | ---------------- | -------------------- |
| [AGGREGATE]  | ...          | domain/service/db| unit/property/integration |

### 4.3 Failure semantics
- Validation errors: [TYPES_AND_STATUS_CODES]
- Idempotency: [RULES]
- Retry safety: [RULES]
- Consistency model per operation: [STRONG_OR_EVENTUAL]

---

## 5) Architecture style & layers

### 5.1 Style
- [HEXAGONAL / CLEAN / LAYERED / MODULAR_MONOLITH]
- Rationale: [WHY]
- Tradeoffs: [KNOWN]

### 5.2 Layers

| Layer        | Responsibilities              | Must NOT contain     |
| ------------ | ----------------------------- | -------------------- |
| Domain       | invariants, entities, logic   | I/O, DB, HTTP        |
| Application  | use cases, orchestration      | framework code       |
| Adapters     | DB, HTTP clients, queues      | domain rules         |

### 5.3 Dependency rules
```
Domain       -> (nothing)
Application  -> Domain
Adapters     -> Application + Domain
UI / API     -> Application
```
Rule: no upward imports. Enforce with import-linter / deptry / custom tests.

---

## 6) Components & interactions

### 6.1 Component diagram
> `docs/diagrams/components.[png|svg|mmd]`

- **[COMPONENT_A]:** [RESPONSIBILITY, INPUTS, OUTPUTS]

### 6.2 Main flows

#### Flow: `[USE_CASE_NAME]`
- Trigger: [TRIGGER]
- Steps: [SEQUENCE]
- Side effects: [EFFECTS]
- Failure modes: [MODES]

---

## 7) Interfaces: APIs, events, commands

### 7.1 Public API
- Protocol: [REST / gRPC / CLI]
- Auth: [AUTHN_AUTHZ]
- Rate limiting: [STRATEGY]

### 7.2 Events & messaging
- Broker: [BROKER]
- Topics: [TOPICS]
- Delivery: [AT_LEAST_ONCE / EXACTLY_ONCE]
- Consumer idempotency: [STRATEGY]

---

## 8) Security, privacy, compliance

- Threat model: [WHO_ATTACKS_WHAT]
- Secrets management: [STRATEGY]
- PII handling: [RULES]
- Log redaction: [RULES]
- Supply-chain: [DEPS_PINNING, SBOM]

---

## 9) Performance, scalability, capacity

- Workload assumptions: [ASSUMPTIONS]
- Bottlenecks: [KNOWN]
- Benchmarks: [HOW_TO_RUN]
- Scaling strategy: [HORIZONTAL / VERTICAL / AUTO]

---

## 10) Observability

- Logs: [STRUCTURE]
- Metrics (golden signals): [METRICS]
- Tracing: [STRATEGY]
- Alerting thresholds: [THRESHOLDS]

---

## 11) Testing strategy

| Type     | Scope       | Tools     | Required gates |
| -------- | ----------- | --------- | -------------- |
| Unit     | domain      | [TOOL]    | [GATE]         |
| Integration | DB/IO    | [TOOL]    | [GATE]         |
| E2E      | system      | [TOOL]    | [GATE]         |
| Property | invariants  | [TOOL]    | [GATE]         |

---

## 12) Deployment & environments

- Environments: dev / staging / prod
- Config strategy: 12-factor
- Migrations: [STRATEGY]
- Rollback plan: [PLAN]

---

## 13) Repo layout & conventions

```
[PACKAGE]/          # flat layout (default); for src layout use src/[PACKAGE]/
  domain/
  application/
  adapters/
tests/
docs/
  architecture.md
  adr/
```

- Naming: [CONVENTIONS]
- Error handling: [CONVENTIONS]
- Code style: [CONVENTIONS]

---

## 14) Architecture decisions (ADRs)

Each ADR must include: alternatives, tradeoffs, consequences.

---

## 15) Notes for new developers

- How to run locally: [INSTRUCTIONS]
- How to run tests: [INSTRUCTIONS]
- Where to add a new feature: [EXAMPLE]
- Common pitfalls: [PITFALLS]
