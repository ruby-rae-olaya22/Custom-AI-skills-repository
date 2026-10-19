# Custom AI Skills Repository

This repository contains reusable AI skills for Playwright and BDD test
automation. Each skill is a folder under `.agents/skills/` with a `SKILL.md`
file that defines its purpose, when to use it, required inputs, workflow, and
expected output.

## Repository contents

```text
.
├── README.md
├── USING-SKILLS.md
└── .agents/
    └── skills/
        ├── bdd-feature-generator/
        │   └── SKILL.md
        ├── bdd-step-definition-generator/
        │   └── SKILL.md
        └── pom-generator/
            └── SKILL.md
```

### Root documentation

- [`USING-SKILLS.md`](./USING-SKILLS.md) explains how to choose a skill, provide
  useful inputs, and invoke skills in a compatible chat host.
- [`README.md`](./README.md) is this repository overview.

### Skills

| Skill | File | Purpose |
| --- | --- | --- |
| `bdd-feature-generator` | [`.agents/skills/bdd-feature-generator/SKILL.md`](./.agents/skills/bdd-feature-generator/SKILL.md) | Turns a feature description into assumptions, product clarification questions, and comprehensive Playwright-BDD-compatible Gherkin scenarios, including edge, security, and API/network coverage. |
| `bdd-step-definition-generator` | [`.agents/skills/bdd-step-definition-generator/SKILL.md`](./.agents/skills/bdd-step-definition-generator/SKILL.md) | Maps an existing Gherkin feature to Playwright-BDD TypeScript step definitions that use existing page objects, and identifies missing page-object coverage. |
| `pom-generator` | [`.agents/skills/pom-generator/SKILL.md`](./.agents/skills/pom-generator/SKILL.md) | Generates Playwright-TypeScript page objects with resilient locators and registers them in `PageObjectManager`, following project conventions. |

## Typical workflow

For a UI test feature, the skills can be used as a sequence:

1. Use `bdd-feature-generator` to identify assumptions and questions and draft
   Gherkin scenarios.
2. Use `pom-generator` to create the page object and register it with
   `PageObjectManager`.
3. Use `bdd-step-definition-generator` with the feature and page object to
   generate mapped step definitions.

Each skill is independently usable when its required inputs are available.
Consult its `SKILL.md` for scope boundaries and output requirements. Skills
guide the assistant; they do not themselves provide application code, execute
tests, or guarantee that generated output matches a project's conventions
without inspecting that project.
