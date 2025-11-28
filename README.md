# Documentation Agent

A Claude Code plugin that applies professional technical writing standards to your documentation work.
Provides methodologies for content audits, information architecture design, style enforcement, and docs-as-code workflows.

## Install the Plugin

1. Open Claude Code:

   ```bash
   claude
   ```

1. Add this repository (or your fork) as a [plugin marketplace](https://code.claude.com/docs/en/plugin-marketplaces):

   ```bash
   /plugin marketplace add EdwardAngert/documentation-agent-skill
   ```

1. Install the plugin:

   ```bash
   /plugin install EdwardAngert/documentation-agent-skill
   ```

1. Restart Claude Code.

## How It Works

When you open Claude Code in a documentation project and ask for help, the plugin **automatically activates**.
Claude becomes your subject matter expert for the codebase, applying all the standards and patterns from this skill.

Example prompts that trigger the skill:

```text
Help me document feature X for issue #123
```

```text
Review this README for clarity and completeness
```

```text
I need to document our API. What's the best structure?
```

You don't need to do anything special — just ask for documentation help and the skill kicks in.

## What It Does

When the plugin is active, Claude automatically applies:

- **Content type awareness**: Structures docs as concepts, docs, guides, tutorials, references, or troubleshooting
- **Writing standards**: Consistent tone, formatting, and terminology
- **User-focused approach**: Prioritizes what users need to do, not what products can do
- **Safe examples**: Copy-paste ready code that won't break things
- **Accessibility**: Guidance on images, diagrams, and alt text
- **SEO**: Headings and content that help users find information

## Commands

### `/documentation-agent:audit [path]`

Run a documentation audit on a directory or file:

```bash
/documentation-agent:audit docs/
```

Outputs a structured report with:

- Critical issues
- Structural and content problems
- Style violations
- Orphaned images
- Prioritized recommendations

### `/documentation-agent:make-examples [doc-path]`

Add or improve code examples in a documentation file:

```bash
/documentation-agent:make-examples docs/setup.md
```

Claude will:

- Identify sections that need examples
- Create safe, copy-paste ready code
- Match existing example patterns in your docs
- Ask before inserting

## File Structure

You can customize any of these files to match your team's standards:

```text
skills/documentation-agent/
├── SKILL.md                    # Core instructions Claude follows
├── tone-and-voice.md           # Formatting rules, heading case, markdown style
├── documentation-patterns.md   # Content types, examples, SEO, accessibility
├── content-audit-framework.md  # Audit methodology
├── ia-design-methodology.md    # Information architecture design
└── style-guides.md             # Style guide selection and enforcement
```

**What to tweak:**

- `tone-and-voice.md` - Change heading case, list style, or add your company's conventions
- `documentation-patterns.md` - Adjust content type definitions to match your taxonomy
- `SKILL.md` - Modify the SME role or add project-specific instructions

## Templates

This plugin provides methodology and standards, not templates.
For documentation templates, see the [Good Docs Project](https://thegooddocsproject.dev/), which offers templates for how-tos, tutorials, references, and more.

## Included Methodologies

The plugin includes detailed frameworks for:

- **Content audits** - 6-phase systematic evaluation process
- **Information architecture** - User research, IA design, and validation
- **Style guide enforcement** - Automated and human review strategies
- **Documentation patterns** - Content types, antipatterns, effective patterns
- **Code examples** - Safety, consistency, and formatting rules
- **Docs-as-code workflows** - Version control, CI/CD, static site generators

## Background

This plugin codifies methodologies from 10 years of technical writing experience, including:

- Building documentation practices from scratch for developer tools
- Managing documentation teams for enterprise SaaS platforms
- API and SDK documentation for developer-focused products
- Docs-as-code workflows and CI/CD integration

## Contribute

See the [contributing guidelines](CONTRIBUTING.md).

## License

Apache 2.0 - see [LICENSE](LICENSE) for details.
