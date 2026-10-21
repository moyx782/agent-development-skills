# Agent Development Skills

Reusable, framework-agnostic skills for initializing software projects and designing frontend experiences. Both skills are written in English. **When interacting with an end user, the agent responds in the user's language**, unless the user requests a different language.

## Skills

| Skill | Use when | Main workflow |
| --- | --- | --- |
| [`project-initialization`](project-initialization/SKILL.md) | Starting a new project, taking over an existing repository, or setting up development rules and entry points | Inspect → Scope → Operating mode → Minimal setup → Verify and hand off |
| [`frontend-design-workflow`](frontend-design-workflow/SKILL.md) | Creating or changing frontend flows, pages, interaction states, or visual interfaces | Context → User Flow → UX → UI → Implementation → Design Consistency Check |

The skills are independent but can be used together. Initialize only when initialization is actually needed; routine feature development should not repeatedly reinitialize the repository.

## Principles

- **Outcome first.** Understand the requested behavior and existing implementation before adding structures or documents.
- **Minimal necessary changes.** Reuse architecture, dependencies, components, conventions, and user flows when appropriate.
- **Mode-neutral skills.** Supervised and autonomous modes control when to escalate decisions; neither skill grants permissions or overrides the host environment.
- **Design is not a bureaucracy.** A small UI change may reuse the current flow and UX without drafting a new design document.
- **Truthful state and reporting.** Never invent backend capabilities, progress, successful checks, or results.
- **Language follows the user.** Instructions, templates, and repository documentation remain English; end-user replies follow the language of the user's request by default.

## Repository layout

```text
agent-development-skills/
├── README.md
├── LICENSE
├── project-initialization/
│   ├── SKILL.md
│   └── references/
│       ├── agent-policy.md
│       └── modes.md
└── frontend-design-workflow/
    ├── SKILL.md
    ├── references/
    │   ├── design-consistency.md
    │   ├── ux-patterns.md
    │   └── generative-image-ux.md
    └── assets/
        └── DESIGN.template.md
```

## Usage

Place each skill directory under the skill-discovery location supported by your agent host, or reference the relevant `SKILL.md` according to that host's documentation. Some hosts discover `.agents/skills/`, but **paths, activation, and permissions are host-specific**. Copying a directory does not guarantee that a host has enabled it.

Examples:

- “Take over this repository and perform only the setup needed to develop this feature.” → `project-initialization`
- “Design the user flow for this feature and implement its screen.” → `frontend-design-workflow`
- “Create a new app and its first functional screen.” → Run project initialization first, then the frontend workflow.

No third-party runtime dependencies, installation scripts, or particular language/framework are required by either skill.

### Optional agent-policy integration

Use the active agent policy to choose supervised or autonomous behavior. A concise pointer in a project's agent instructions is enough:

```md
For repository setup, use `project-initialization` when relevant.
For frontend changes, follow `frontend-design-workflow`.
Respond to the user in their language unless they request otherwise.
```

The skills do not require a project to create `DESIGN.md`. Record only meaningful, durable, project-specific design decisions there when appropriate. Build checks, functional tests, performance requirements, and release acceptance remain governed by the project and task requirements, not by the design-consistency step alone.

## License

MIT. See [LICENSE](LICENSE).
