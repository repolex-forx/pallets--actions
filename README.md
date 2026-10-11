# Repolex Knowledge Graph of pallets/actions

RDF knowledge graph data for [pallets/actions](https://github.com/pallets/actions), parsed by [repolex](https://repolex.ai).

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
rlex download pallets/actions
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 3255f16f0e8beb235859a5a82035717d5ebcb549
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 3255f16f0e8beb235859a5a82035717d5ebcb549
│           └── chunk-001.nq.gz
├── blob
│   ├── 23217cba2624dd9d59c4809907450e857e64f4a4.nq.gz
│   ├── 24e296be4da21d56ea441612a62c17f50d07e0ab.nq.gz
│   ├── 61eb42d3bd2c625f94c72967da8585c9bb7d6186.nq.gz
│   ├── 778d5a8070c0d5b2f06819cca7394ed1ceaed517.nq.gz
│   ├── 99d8156e4bc8d1305f4352c95f1ee1339fd8c0e9.nq.gz
│   ├── d7bc9672fe24078b86e100221d83a14882b0f6cf.nq.gz
│   └── e4653d38d1fd58d85141c9eb10a74773c113feb7.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 3255f16f0e8beb235859a5a82035717d5ebcb549.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 13 files
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

[pallets/actions](https://github.com/pallets/actions)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
