# Repolex Knowledge Graph of glue-viz/glue-yt

RDF knowledge graph data for [glue-viz/glue-yt](https://github.com/glue-viz/glue-yt), parsed by [repolex](https://repolex.ai).

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
rlex download glue-viz/glue-yt
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── a9f58814ac5d44010a9a77b3a9f7fc53d0307447
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── a9f58814ac5d44010a9a77b3a9f7fc53d0307447
│           └── chunk-001.nq.gz
├── blob
│   ├── 0af34288afa78f7aec06e2d1fe3c2e63f44165a6.nq.gz
│   ├── 0c811dca26e99be5573cc02e8ff6c8a69c579df8.nq.gz
│   ├── 29317940e096bd25319f50aa72cd5051a198210c.nq.gz
│   ├── 3f2b1306b6e51f3b1892a98a17bd598f9a22e4bd.nq.gz
│   ├── 760268b8a2b75cb4d38b03faa017647715ddd261.nq.gz
│   ├── 761f7ea47e6d45d26ab143d87bb0f3ce42c00486.nq.gz
│   ├── 8d445604a95ac6a51874b6a1cbc812920719839a.nq.gz
│   ├── 913fc002069e6fa15c71f5394ed9cb1302bda761.nq.gz
│   ├── a3db2a9c11fbc6e3efe2e6ad3fd41bed32a519a8.nq.gz
│   ├── acc3b8f7423b012d36b950447bc6bbdb2e2b125c.nq.gz
│   ├── d26353c6ca76fc3ebf415b6aca88d7573be5a19b.nq.gz
│   ├── d66d37795702713e058fd18d570b4a8e386d6acf.nq.gz
│   ├── dfceb2383c9f0ea76206d22b8433a2df32203d0b.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── a9f58814ac5d44010a9a77b3a9f7fc53d0307447.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 22 files
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

[glue-viz/glue-yt](https://github.com/glue-viz/glue-yt)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
