# humanize

A Claude Code plugin that strips robot-sounding language from user-facing content.

## What it does

Detects and removes 15 categories of machine-generated writing patterns:

- **Em-dashes** used for dramatic effect
- **Corporate jargon** ("leverage", "robust", "seamless", "ecosystem")
- **Passive voice** ("is processed by", "was created")
- **Hedge phrases** ("might potentially", "could perhaps")
- **Buzzword clusters** ("optimized, scalable, future-proof")
- **Stiff constructions** ("It is important to note that...")
- **Redundancy** ("advance planning", "past history")
- **Over-formal transitions** ("Furthermore", "Moreover")
- **Plural first person in solo contexts** ("we" when "I" is correct)
- **LLM attribution** (removes references to the model as author)
- And more

Each pattern has a confidence score. High-confidence patterns are auto-fixed, medium-confidence patterns generate suggestions, and low-confidence patterns are flagged for human review.

## Install

```bash
claude plugin add lukeslp/skill-humanize
```

## Usage

In Claude Code, invoke the slash command:

```
/humanize:humanize
```

Or ask Claude Code to humanize your content:

```
Humanize the README before I publish this project
```

## Safety

- Never modifies code blocks
- Never changes URLs or citations
- Preserves technical specifications
- Creates git checkpoints before making changes
- Shows diff previews for all changes

## License

MIT

## Author

Luke Steuber ([luke@dr.eamer.dev](mailto:luke@dr.eamer.dev))
