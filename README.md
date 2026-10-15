# Repolex Knowledge Graph of Textualize/trogon

RDF knowledge graph data for [Textualize/trogon](https://github.com/Textualize/trogon), parsed by [repolex](https://repolex.ai).

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
rlex download Textualize/trogon
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── eaa9e68c403cae6aff0a80957d8876b284fd76b0
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── eaa9e68c403cae6aff0a80957d8876b284fd76b0
│           └── chunk-001.nq.gz
├── blob
│   ├── 0475b52c48925af2c0306fa9b1b9463258e31546.nq.gz
│   ├── 07f5e64e9b4c63e507cde097a0685ec639624a50.nq.gz
│   ├── 14d24520a7e86b156cf76d81d6e699048490727c.nq.gz
│   ├── 1d5eab7a3b32221977f956bb21bfd9e6b16f9131.nq.gz
│   ├── 31f4351ab02f2aa69f78c8222cfd660452adbc5b.nq.gz
│   ├── 3fe8244977876df314ceee124fbfd7907a11f045.nq.gz
│   ├── 4a0fb6aea40a0b65ae6dff0c0db4535ec634518f.nq.gz
│   ├── 6639af6e22a7bf4231a6764c6922edb64440906b.nq.gz
│   ├── 665d5e772ffaaef435bad4bfc63bd8282f8df617.nq.gz
│   ├── 6e757a7e8d165e02bd85ed127e290b9107814d5d.nq.gz
│   ├── 79a8ffe3da8a969cdb8b936d028b91bf34d39425.nq.gz
│   ├── 88ac493500d550ff722dc2ea41f7b8303dc594dd.nq.gz
│   ├── 8f6f0f6c38c2e3d11478d735a8ca5d1c44b4967d.nq.gz
│   ├── 97613a549650ccded43973e55a042733cd542bf0.nq.gz
│   ├── 9d63d38b948a2c7f526c0138d77df4b56ae7b329.nq.gz
│   ├── 9f4491f296f5c42fa7e40cbce673af71e03bdade.nq.gz
│   ├── ad4d8834efb339850b3da41d1ceccedadc47f903.nq.gz
│   ├── afb7c0c9bae456de068999ece79ac265afe64274.nq.gz
│   ├── b084c3e56b494d188deeef77daf2022ec07b69bd.nq.gz
│   ├── c2b07afeb6d2b88b73d74ace6cdc2ee05bd1ac1f.nq.gz
│   ├── c9f559af943fd0ba8272ae78239a8139c99f9625.nq.gz
│   ├── cb6c2d1f010ab73f60d6f22871b6011c50a5a0f3.nq.gz
│   ├── d200fa40389560811786c499c3aa72a8b639e4c0.nq.gz
│   ├── dedbf70a6a2ec046cfbb439cca9df13a31cc98e6.nq.gz
│   ├── e36eb51e6651468aae4cf8687d5b5a7f3d2fd94f.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── f428be007efb4204225a33e1b467216215da0795.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── eaa9e68c403cae6aff0a80957d8876b284fd76b0.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 35 files
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

[Textualize/trogon](https://github.com/Textualize/trogon)

---
*Parsed on 2026-10-15 by [repolex](https://repolex.ai)*
