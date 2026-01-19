---
description: Workflow for initializing a new project from scratch (Greenfield Development)
---

# Greenfield Development (New Project)

When initializing a new project (Greenfield), follow this specific sequence:

## 1. Spec & Architecture

Act as the **Architect**. Draft a project overview including:
- Goals and objectives
- High-level components (services, data models)
- Tech stack selection

Review and refine this with the user before proceeding.

## 2. Persist Context

Create a `SPEC.md` file containing the approved design.

> [!IMPORTANT]
> Treat `SPEC.md` as the **source of truth** for all subsequent code generation.

## 3. Skeleton Generation

Generate the project boilerplate based on `SPEC.md`:
- Build files (Maven `pom.xml` / Gradle `build.gradle`)
- Directory structure
- Package-by-feature layout

## 4. Test & CI Setup

Before writing business logic:
- Generate a suite of initial test stubs
- Create a CI configuration pipeline

> [!NOTE]
> This step enforces the 'Test-First' rule from the core rules.

## 5. Iterative Implementation

Implement one module at a time. For each feature, strictly follow the **Feature Development** workflow (`/feature_development`).
