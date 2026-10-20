# Repolex Knowledge Graph of simonw/llm-meta-ai

RDF knowledge graph data for [simonw/llm-meta-ai](https://github.com/simonw/llm-meta-ai), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download simonw/llm-meta-ai
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 01c0990973ac6d25ab925a6bf19f6e51ba8f14b4
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 01c0990973ac6d25ab925a6bf19f6e51ba8f14b4
│           └── chunk-001.nq.gz
├── blob
│   ├── 04e5aa36712572f2467078d7177afee003da14e2.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 2899e5302129540b6aff4139abeac1903d00127e.nq.gz
│   ├── 360a323c3f45e452317ff7f09394cbcf79b34e57.nq.gz
│   ├── 4864d3d143ad6934ae946669170123978dddca59.nq.gz
│   ├── 49efa25ce83d3709d35f5f589dbc69b8de511a8d.nq.gz
│   ├── 714f9608d714e5dd0a6770e4653b61fc96db097d.nq.gz
│   └── b153abf1135a5c4c35fd22c18ac4763448e99582.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 01c0990973ac6d25ab925a6bf19f6e51ba8f14b4.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 15 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[simonw/llm-meta-ai](https://github.com/simonw/llm-meta-ai)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
