# <Project Name> Specification

Status: Draft v1

Purpose: <One-sentence description of what this project exists to do.>

## Normative Language

The key words `MUST`, `MUST NOT`, `REQUIRED`, `SHOULD`, `SHOULD NOT`, `RECOMMENDED`, `MAY`, and `OPTIONAL` in this document are to be interpreted as described in RFC 2119.

`Implementation-defined` means the behavior must be selected and documented by the implementation. Once documented, the selected behavior is part of the implementation contract.

## 1. Problem Statement

<Describe the user, product, or operational problem this project solves.>

The project exists to:

- <Problem or need>
- <Problem or need>
- <Problem or need>

The project does not attempt to solve:

- <Adjacent problem outside the initial version>
- <Adjacent problem outside the initial version>

## 2. Goals and Non-Goals

### 2.1 Goals

- <Goal>
- <Goal>
- <Goal>

### 2.2 Non-Goals

- <Non-goal>
- <Non-goal>
- <Non-goal>

## 3. Initial Project Boundary

This specification defines the initial version of the project.

Target users:

- <User type>
- <User type>

Primary workflows:

- <Workflow>
- <Workflow>
- <Workflow>

Supported platforms or environments:

- <Operating system, browser, device class, hosting environment, or deployment target>
- <Operating system, browser, device class, hosting environment, or deployment target>

Initial deployment shape:

- <Local tool, web app, service, CLI, desktop app, library, etc.>

Explicit exclusions:

- <Feature, platform, workflow, integration, or scale requirement excluded from v1>
- <Feature, platform, workflow, integration, or scale requirement excluded from v1>

## 4. Implementation Profile

This section is normative. Agent-generated implementation work MUST follow this profile unless this specification is amended.

### 4.1 Technical Context

- Language/version: <Go 1.23, Python 3.12, Swift 6, TypeScript 5.8, or NEEDS CLARIFICATION>
- Primary dependencies: <FastAPI, React, SwiftUI, Drizzle, none, or NEEDS CLARIFICATION>
- Storage: <PostgreSQL, SQLite, files, browser storage, none, or NEEDS CLARIFICATION>
- Testing: <go test, pytest, XCTest, bun test, Playwright, or NEEDS CLARIFICATION>
- Target platform: <Linux server, local macOS, iOS 17+, browser, WASM, or NEEDS CLARIFICATION>
- Project type: <library, CLI, web service, web app, mobile app, desktop app, or NEEDS CLARIFICATION>
- Performance goals: <Domain-specific goal, none, or NEEDS CLARIFICATION>
- Constraints: <Domain-specific constraint, none, or NEEDS CLARIFICATION>
- Scale/scope: <Domain-specific scale or scope, or NEEDS CLARIFICATION>

### 4.2 Additional Technology Decisions

- <Decision>: <Choice, rationale if needed, or NEEDS CLARIFICATION>
- <Decision>: <Choice, rationale if needed, or NEEDS CLARIFICATION>

### 4.3 Repository Layout

The project SHOULD use this structure:

```txt
src/
  app/
  core/
  components/
  integrations/
  tests/
docs/
```

Project-specific layout rules:

- <Layout rule>
- <Layout rule>

### 4.4 Code Style and Agent Rules

Implementations MUST:

- Treat this document as the source of truth.
- Preserve the boundaries and contracts defined here unless the spec is amended.
- Keep names consistent with the domain model.
- Prefer small, focused modules.
- Avoid hidden global state.
- Update tests when behavior changes.
- Surface material ambiguities as open questions.

Implementations MUST NOT:

- Add features listed as non-goals or explicit exclusions.
- Replace approved libraries or frameworks without a spec amendment.
- Introduce unrelated architecture patterns.

### 4.5 Dependency Policy

- New production dependencies MUST be justified before introduction.
- Approved dependencies SHOULD be preferred over new alternatives.
- Large framework changes MUST be reflected in this specification before implementation.

## 5. System Overview

### 5.1 Main Components

1. `<Component Name>`
   - <Primary responsibility>
   - <Secondary responsibility, if needed>

2. `<Component Name>`
   - <Primary responsibility>
   - <Secondary responsibility, if needed>

3. `<Component Name>`
   - <Primary responsibility>
   - <Secondary responsibility, if needed>

### 5.2 Component Boundaries

- `<Component>` owns <responsibility>.
- `<Component>` MUST NOT own <excluded responsibility>.
- `<Component>` communicates with `<Component>` through <interface, API, event, function call, etc.>.
- Shared behavior SHOULD be placed in <shared layer/module/concept>, not duplicated across components.

### 5.3 External Dependencies

- <External API, service, database, filesystem, model provider, package, hosted platform, etc.>
- <External dependency>
- <External dependency>

## 6. Core Domain Model

Omit this section only if the project has no meaningful domain model.

### 6.1 Entities

#### 6.1.1 `<Entity Name>`

<Short definition of the entity.>

Fields:

- `id` (<type>): <Description>
- `<field>` (<type>): <Description>
- `<field>` (<type>): <Description>

#### 6.1.2 `<Entity Name>`

<Short definition of the entity.>

Fields:

- `id` (<type>): <Description>
- `<field>` (<type>): <Description>

### 6.2 Relationships

- `<Entity>` contains `<Entity>`.
- `<Entity>` references `<Entity>`.
- `<Entity>` owns <state/data/behavior>.
- `<Entity>` derives <state/data> from `<Entity>`.

### 6.3 Identifiers and Normalization Rules

- `<Identifier Name>` is used for <purpose>.
- `<Identifier Name>` is derived from <source>.
- `<Identifier Name>` MUST be stable across <condition>.
- `<Value>` MUST be normalized by <rule>.

## 7. Component Specifications

This section defines concrete behavior contracts for the major components listed in Section 5.

Each component specification SHOULD include only the subsections relevant to that component.

### 7.1 `<Component Name>`

#### 7.1.1 Purpose

<Describe why this component exists.>

#### 7.1.2 Responsibilities

This component MUST:

- <Requirement>
- <Requirement>
- <Requirement>

This component MUST NOT:

- <Prohibited responsibility>
- <Prohibited responsibility>

#### 7.1.3 Inputs and Outputs

Inputs:

- `<Input>`: <Description>
- `<Input>`: <Description>

Outputs:

- `<Output>`: <Description>
- `<Output>`: <Description>

#### 7.1.4 Behavior

- <Behavior requirement>
- <Behavior requirement>
- <Behavior requirement>

#### 7.1.5 Validation and Failure Handling

- <Validation rule>
- <Validation rule>
- <Failure case>: <Required behavior>
- <Failure case>: <Required behavior>

#### 7.1.6 Observability

This component SHOULD expose:

- <Log/event/metric/debug output>
- <Log/event/metric/debug output>

### 7.2 `<Component Name>`

#### 7.2.1 Purpose

<Describe why this component exists.>

#### 7.2.2 Responsibilities

This component MUST:

- <Requirement>
- <Requirement>

This component MUST NOT:

- <Prohibited responsibility>

#### 7.2.3 Inputs and Outputs

Inputs:

- `<Input>`: <Description>

Outputs:

- `<Output>`: <Description>

#### 7.2.4 Behavior

- <Behavior requirement>
- <Behavior requirement>

#### 7.2.5 Validation and Failure Handling

- <Validation rule>
- <Failure case>: <Required behavior>

## 8. Interfaces and Integration Contracts

Include this section only when the project exposes APIs, consumes external services, defines protocols, or integrates with third-party systems.

### 8.1 `<Interface or Integration Name>`

#### 8.1.1 Purpose

<Describe why this interface or integration exists.>

#### 8.1.2 Required Operations

- `<operation>`: <Description>
- `<operation>`: <Description>

#### 8.1.3 Input Contract

<Describe required input shape, fields, methods, messages, or parameters.>

Example shape:

```json
{
  "field": "value"
}
```

#### 8.1.4 Output Contract

<Describe required output shape, fields, messages, events, or return values.>

Example shape:

```json
{
  "result": "value"
}
```

#### 8.1.5 Error Handling Contract

- <Error case>: <Required behavior>
- <Error case>: <Required behavior>

## 9. Cross-Cutting Requirements

Include only subsections that apply across multiple components.

### 9.1 Data Persistence

The system MUST persist:

- <Data>
- <Data>

The system MUST NOT persist:

- <Data>
- <Data>

Implementation-defined:

- <Storage detail>
- <Schema or storage initialization strategy>
- <Backup or retention policy>

### 9.2 Error Handling and Recovery

- Errors shown to users MUST be actionable and safe to display.
- Recoverable failures SHOULD preserve user work or system state where possible.
- Irrecoverable failures MUST fail clearly and avoid silent data corruption.
- Retried operations MUST be safe to retry or explicitly documented as non-idempotent.

Project-specific recovery requirements:

- <Recovery behavior>
- <Recovery behavior>

### 9.3 Security and Permissions

The system MUST:

- Protect secrets and credentials.
- Validate untrusted input.
- Restrict privileged operations.
- Avoid logging sensitive values.

Permission rules:

- <Actor/system> MAY <operation>.
- <Actor/system> MUST NOT <operation>.
- <Operation> requires <approval/auth/permission>.

### 9.4 Observability

The system SHOULD expose:

- Structured logs for <behavior>
- Metrics for <behavior>
- Debug information for <behavior>
- Operator-visible errors for <behavior>

### 9.5 Configuration

If the project supports configuration, implementations MUST document:

- Configuration sources.
- Precedence rules.
- Defaults.
- Validation behavior.
- Reload behavior, if applicable.

## 10. Acceptance Criteria

The implementation is considered complete when:

- <Outcome that must be true>
- <Outcome that must be true>
- <Outcome that must be true>

The implementation is not acceptable if:

- <Unacceptable outcome>
- <Unacceptable outcome>

## 11. Verification Plan

This section defines how the implementation should be verified.

Automated tests:

- <Test coverage requirement>
- <Test coverage requirement>

Manual checks:

- <Manual check>
- <Manual check>

Integration checks:

- <Integration check>
- <Integration check>

Regression checks:

- <Regression check>
- <Regression check>

## 12. Definition of Done

Use this section as completion bookkeeping, not as an implementation sequence.

Required for completion:

- <Required component implemented>
- <Required contract implemented>
- <Tests added or updated>
- <Documentation updated>
- <Lint/typecheck/build passes>

Recommended but not required:

- <Recommended improvement>
- <Recommended improvement>

Out of scope for initial implementation:

- <Deferred item>
- <Deferred item>

## 13. Open Questions

- <Open question>
- <Open question>
- <Open question>

## Appendices

Use appendices only for optional extensions, reference algorithms, examples, or future implementation profiles.

### Appendix A. <Optional Extension or Reference Material>

<Content>
