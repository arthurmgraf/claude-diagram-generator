# Claude Diagram Generator

> Generate professional Excalidraw diagrams from your codebase using Claude Code

**Stop wasting hours drawing architecture diagrams.** This agent reads your project and generates editable `.excalidraw` files with proper technology logos.

![Example Diagram](examples/preview.png)

---

## Features

- **Automatic project analysis** - Detects technologies, patterns, and architecture
- **Multiple diagram types** - Architecture, data flow, pipelines, data models
- **Real technology logos** - BigQuery, PostgreSQL, Airflow, Docker, Redis, and 20+ more
- **Editable output** - Native `.excalidraw` files you can open and customize
- **Professional styling** - Clean, minimalist, presentation-ready

## Supported Technologies

| Category | Technologies |
|----------|-------------|
| **Cloud** | GCP (BigQuery, Cloud Storage, Cloud Functions), AWS, Azure |
| **Databases** | PostgreSQL, MySQL, MongoDB, Redis |
| **Orchestration** | Apache Airflow, Prefect, Dagster |
| **Containers** | Docker, Kubernetes |
| **BI Tools** | Apache Superset, Looker, Metabase |
| **Data** | Apache Spark, dbt, Pandas |

---

## Installation

### Option 1: Copy files manually

```bash
# Clone this repository
git clone https://github.com/YOUR-USERNAME/claude-diagram-generator.git

# Copy .claude folder to your project
cp -r claude-diagram-generator/.claude/ your-project/
```

### Option 2: Download and extract

1. Download this repository as ZIP
2. Extract the `.claude/` folder
3. Place it in your project root

---

## Usage

Open your project in **Claude Code** and run:

```bash
/generate-diagrams
```

That's it. The agent will:

1. **Analyze** your project structure, code, and configs
2. **Detect** technologies (Python, GCP, databases, etc.)
3. **Generate** diagrams in `diagrams/generated/`

### Generate specific diagram types

```bash
/generate-diagrams architecture      # Infrastructure only
/generate-diagrams data-flow         # Pipeline diagrams
/generate-diagrams data-model        # Star schema / ERD
/generate-diagrams pipeline          # Execution order
```

### Options

```bash
/generate-diagrams --force           # Regenerate all (overwrite)
/generate-diagrams --output docs/    # Custom output path
/generate-diagrams --style minimal   # Simplified style
```

---

## Output

Diagrams are saved to `diagrams/generated/`:

```
diagrams/generated/
├── architecture/
│   ├── infrastructure.excalidraw
│   └── docker_compose_stacks.excalidraw
├── data-flow/
│   └── medallion_pipeline.excalidraw
├── data-model/
│   ├── bigquery_bronze_schema.excalidraw
│   ├── bigquery_silver_schema.excalidraw
│   ├── bigquery_gold_star_schema.excalidraw
│   └── postgresql_schema.excalidraw
└── pipeline/
    ├── airflow_dag_execution.excalidraw
    └── cloud_functions_detail.excalidraw
```

### Open in Excalidraw

1. Go to [excalidraw.com](https://excalidraw.com)
2. File → Open → Select your `.excalidraw` file
3. Edit, customize, export to PNG/SVG

---

## Examples

### Architecture Diagram
![Architecture](examples/architecture.png)

### Data Pipeline (Medallion)
![Pipeline](examples/pipeline.png)

### Star Schema
![Star Schema](examples/star-schema.png)

---

## How It Works

The agent uses a **Knowledge Base** with:

- **Style guides** - Colors, fonts, spacing rules
- **Layout patterns** - Horizontal zones, vertical flows, hub-spoke
- **Logo library** - 25+ technology logos as base64 SVG
- **Excalidraw format** - JSON structure for valid diagrams

When you run `/generate-diagrams`:

1. Reads your codebase (configs, imports, structure)
2. Identifies technologies and patterns
3. Selects appropriate diagram types
4. Generates valid Excalidraw JSON with embedded logos
5. Writes files to output directory

---

## Customization

### Add custom logos

Edit `.claude/kb/diagram-generation/logos/custom.md`:

```markdown
## My Company Logo

### DataURL
\`\`\`
data:image/svg+xml;base64,PHN2Zy...
\`\`\`

### Element Template
\`\`\`json
{"id":"mylogo","type":"image","x":40,"y":15,"width":40,"height":40,"fileId":"my_logo"}
\`\`\`
```

### Modify style guide

Edit `.claude/kb/diagram-generation/style-guide.md` to change:

- Color palette
- Font sizes
- Spacing rules
- Layout preferences

---

## File Structure

```
.claude/
├── commands/
│   └── workflow/
│       └── generate-diagrams.md    # The command definition
└── kb/
    └── diagram-generation/
        ├── style-guide.md          # Visual style rules
        ├── layout-patterns.md      # Layout templates
        ├── excalidraw-format.md    # JSON format reference
        ├── icon-library.md         # Icon/emoji mappings
        ├── logos/
        │   ├── README.md           # How to add logos
        │   ├── gcp.md              # GCP service logos
        │   ├── general.md          # Common tech logos
        │   └── custom.md           # Your custom logos
        └── examples/
            └── alt2_handcrafted.md # Example diagram
```

---

## Requirements

- **Claude Code** (CLI or IDE extension)
- Any project with recognizable structure

Works best with projects that have:
- `README.md` describing the project
- Configuration files (yaml, json, toml)
- Clear directory structure
- Python/JavaScript/TypeScript code

---

## Compatibility

| Tool | Status |
|------|--------|
| Claude Code CLI | Tested |
| Claude Code VS Code | Tested |
| Cursor | Not tested (should work) |
| Windsurf | Not tested (should work) |

If you test with other tools, please open an issue or PR!

---

## Contributing

Contributions welcome:

- **New logos** - Add technology logos to the KB
- **Layout patterns** - New diagram layouts
- **Bug fixes** - Improve detection or generation
- **Examples** - Share your generated diagrams

---

## License

MIT License - Use freely, modify, distribute.

Logo SVGs are from [Simple Icons](https://simpleicons.org/) (CC0 license).

---

## Author

**Arthur Graf** - [LinkedIn](https://linkedin.com/in/arthurmgraf) | [GitHub](https://github.com/arthurmgraf)

Built with Claude Code for the MR. HEALTH Data Platform project.

---

## Related

- [Excalidraw](https://excalidraw.com) - The drawing tool
- [Simple Icons](https://simpleicons.org) - Technology logos
- [Claude Code](https://claude.ai/claude-code) - AI coding assistant
