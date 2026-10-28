# Repolex Knowledge Graph of dask/dask-stories

RDF knowledge graph data for [dask/dask-stories](https://github.com/dask/dask-stories), parsed by [repolex](https://repolex.ai).

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
rlex download dask/dask-stories
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 880d9da9b16097a6f3bf1b7ecdf2d3660c400889
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 880d9da9b16097a6f3bf1b7ecdf2d3660c400889
│           └── chunk-001.nq.gz
├── blob
│   ├── 3aa0683cb42983196f025217c2cbd779a16f33a5.nq.gz
│   ├── 5020826b82f0e87aaa3f54e2305da53d9ebdba24.nq.gz
│   ├── 5166e48baa9e3c4cea2d3547c77650b0f12ca567.nq.gz
│   ├── 62105c5bc9a0085e80e6f824a655b1ca3fc23336.nq.gz
│   ├── 7fda449782006187f50c596a9e2a3eb2250f8176.nq.gz
│   ├── 802596c91fc3225b7b552f597bf9626b23a4ee5b.nq.gz
│   ├── 8350512e3cd30b5c4d939b9fd51a4af4db6d57ce.nq.gz
│   ├── 8d55f8259935920b96f4b7a2f5b156f0e709edb9.nq.gz
│   ├── 9542527df6c8661649ac989190440c21b7f6f5bb.nq.gz
│   ├── aa4b796e8dbc14c30e1fa912f9b91ffa25832881.nq.gz
│   ├── aa9af5dc783cf4602877c1bdd868fa89e9d5c9cc.nq.gz
│   ├── ab53caa7a4a94e2703bd3745b1576e6f7ac0f2c4.nq.gz
│   ├── ab6e4b5d1fae33e2f40965f52a1460aae76c5786.nq.gz
│   ├── c3026628e942082e92fc99d806ccfbee6c734bfa.nq.gz
│   ├── e84bd58922fee2a589b80bfa0e4961b2115371b4.nq.gz
│   ├── efc158d47bcd8d83926a2287380a79c1ad384166.nq.gz
│   ├── f4342f0e7db964040695eb122438ced98f3f2859.nq.gz
│   ├── f712da40cac19c7bdf45b8563124a585631fa37b.nq.gz
│   ├── f8a265401d46acfcdffc61a9828b5cc65c7e10bb.nq.gz
│   ├── f9bd726f9f8daa29d779451fa8d6846e9f0b8068.nq.gz
│   └── fa1efeb1a6c19e7a7999b5504c3d446ad3338036.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 880d9da9b16097a6f3bf1b7ecdf2d3660c400889.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 29 files
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

[dask/dask-stories](https://github.com/dask/dask-stories)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
