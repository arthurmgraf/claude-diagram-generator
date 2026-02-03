# Claude Diagram Generator

Agente que gera diagramas Excalidraw automaticamente a partir do seu código.

Ele lê seu projeto, detecta as tecnologias e gera arquivos `.excalidraw` com as logos certas.

## Instalação

```bash
git clone https://github.com/arthurmgraf/claude-diagram-generator.git

cp -r claude-diagram-generator/.claude/ seu-projeto/
```

## Uso

No Claude Code:

```
/generate-diagrams
```

Os diagramas vão pra `diagrams/generated/`

Abre no [excalidraw.com](https://excalidraw.com), edita e exporta PNG/SVG.

## Opções

```
/generate-diagrams architecture    # só infraestrutura
/generate-diagrams data-flow       # pipelines
/generate-diagrams data-model      # star schema / ERD
/generate-diagrams --force         # regenera tudo
```

## Logos incluídas

GCP (BigQuery, Cloud Storage, Cloud Functions), PostgreSQL, Docker, Airflow, Redis, Superset, Kubernetes, Spark, e mais.

Quer adicionar? Edita `.claude/kb/diagram-generation/logos/custom.md`

## Estrutura

```
.claude/
├── commands/workflow/generate-diagrams.md   # o comando
└── kb/diagram-generation/
    ├── style-guide.md                       # cores, fontes
    ├── layout-patterns.md                   # layouts
    ├── logos/                               # SVGs em base64
    └── examples/
```

## Exemplos

Pasta `examples/` tem 5 diagramas gerados:
- `docker_compose_stacks.excalidraw`
- `bigquery_gold_star_schema.excalidraw`
- `airflow_dag_execution.excalidraw`
- `ci-cd-pipeline.excalidraw`
- `etl-architecture.excalidraw`

## Compatibilidade

Testado no Claude Code. Cursor/Windsurf/Cline provavelmente funciona, mas não testei.

## Licença

MIT. Logos do [Simple Icons](https://simpleicons.org/) (CC0).

---

**Arthur Graf** - [LinkedIn](https://linkedin.com/in/arthurmgraf) | [GitHub](https://github.com/arthurmgraf)
