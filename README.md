# MLOps Coding Skills

Welcome to the **MLOps Coding Skills** repository! 🚀

This project contains a collection of **[Agent Skills](https://agentskills.io/home)** designed to accompany the [MLOps Coding Course](https://mlops-coding-course.fmind.dev/). These skills are tailored to help AI coding assistants (like Antigravity, Gemini CLI, GitHub Copilot, and Claude Code) understand and guide you through the best practices of MLOps, from prototyping to production.

## 🧠 What are Agent Skills?

[Agent Skills](https://agentskills.io/home) are specialized context or instructions that you can load into your AI assistant. Each skill is a folder containing a `SKILL.md` file (YAML frontmatter + Markdown instructions) that provides the "Know-How" for a specific task, ensuring the AI follows the course's methodology, standards, and patterns.

## 📚 Skills in this repository

Each skill derives from one chapter of the [MLOps Coding Course](https://mlops-coding-course.fmind.dev/):

| Skill                     | Course chapter     | Focus                                                                       |
| ------------------------- | ------------------ | --------------------------------------------------------------------------- |
| `mlops-initialization`    | 1. Initializing    | Set up a robust project structure with `uv`, `git`, and VS Code.            |
| `mlops-prototyping`       | 2. Prototyping     | Write clean, reproducible Jupyter notebooks and prevent data leakage.       |
| `mlops-industrialization` | 3. Productionizing | Turn prototypes into a distributable package (src layout, hybrid paradigm). |
| `mlops-validation`        | 4. Validating      | Add typing (`ty`), linting (`ruff`), testing (`pytest`), logging, scans.    |
| `mlops-automation`        | 5. Refining        | Automate tasks, containers, CI/CD, and experiment tracking (MLflow).        |
| `mlops-collaboration`     | 6. Sharing         | Prepare the project for sharing: license, docs, templates, releases.        |
| `mlops-observability`     | 7. Observability   | Add reproducibility, lineage, monitoring, alerting, and explainability.     |

## 🛠️ Installation & Usage

Skills follow the open `SKILL.md` standard, so most agents discover them from a well-known folder. The workspace-standard location is `.agents/skills/`; each tool then reads from its own path (see the table below).

### Recommended setup (symlinks)

1. **Clone this repository** to a location on your machine (e.g. `~/mlops-coding-skills`).
1. **Create the skills directory** in your target project or workspace, then **symlink** the skills you need:

   ```bash
   mkdir -p .agents/skills
   # Symlink every MLOps skill (or pick individual folders):
   ln -s ~/mlops-coding-skills/mlops-* .agents/skills/
   ```

1. **Expose them to your agent** using the per-tool path below.

### Per-tool install paths

| Tool           | Workspace path                                             | Setup                                                                                    |
| -------------- | ---------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Antigravity    | `.agents/skills/`                                          | Discovers the linked folders directly.                                                   |
| Gemini CLI     | `.agents/skills/` or `.gemini/skills/`                     | Discovers the linked folders; remote installation is an alternative.                     |
| Claude Code    | `.claude/skills/`                                          | Link the shared directory: `mkdir -p .claude && ln -s ../.agents/skills .claude/skills`. |
| GitHub Copilot | `.agents/skills/`, `.github/skills/`, or `.claude/skills/` | Discovers skills and loads relevant instructions on demand.                              |

For a Gemini-managed workspace installation instead of symlinks:

```bash
gemini skills install https://github.com/MLOps-Courses/mlops-coding-skills --scope workspace
```

Claude personal skills can live in `~/.claude/skills/`; plugin skills live under the plugin's `skills/`. In Claude Desktop, add the relevant files to Project Knowledge.

See the current [Antigravity](https://antigravity.google/docs/skills), [Gemini CLI](https://geminicli.com/docs/cli/skills/), [Claude Code](https://code.claude.com/docs/en/skills), and [Copilot](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills) documentation for host-specific behavior.

## 🤝 Contributing

We welcome contributions! If you have a new MLOps pattern or improvement, please open a Pull Request.

Install the pinned toolchain and git hooks once with `mise install && mise run install`, then run the gate before pushing:

```bash
mise run all # format, then check — CI runs this exact task and nothing else
```

`mise run check` covers formatting (`dprint`), workflow linting (`actionlint`, `zizmor`), secret scanning (`gitleaks`), a filesystem scan (`trivy`), the frontmatter rule (`name` equals the folder name), and validation against the Agent Skills specification (`gh skill publish --dry-run`).

See [`CONTRIBUTING.md`](CONTRIBUTING.md) and [`AGENTS.md`](AGENTS.md) for the repository conventions.

Happy Coding! 🤖✨

Release tags matching `v*` are protected by the [active release-tag ruleset](https://github.com/MLOps-Courses/mlops-coding-skills/rules/24938495): existing tags cannot be updated or deleted, and there are no bypass actors. Create a new version tag for corrections; this rule permits new tag creation and does not publish a release.
