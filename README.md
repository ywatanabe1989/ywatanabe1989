<!-- ---
!-- Timestamp: 2026-06-10
!-- Author: ywatanabe
!-- File: /home/ywatanabe/proj/ywatanabe1989/README.md
!-- --- -->

## SciTeX Ecosystem

<p align="center">
  <a href="https://scitex.ai">
    <img src="./docs/images/scitex-logo-blue-cropped.png" alt="SciTeX Logo" width="400">
  </a>
</p>

<p align="center">
  <a href="https://scitex.ai">scitex.ai</a> |
  <a href="https://pypi.org/project/scitex/">uv pip install scitex[all]</a>
</p>

(Demo) Automated Research with SciTeX MCP Server in 40 min. Literature Search → Analysis → Graphing → Manuscript → Revision Letter

<p align="center">
  <a href="https://scitex.ai/demos/watch/scitex-automated-research/">
    <img src="./docs/images/scitex-demo.gif" alt="SciTeX Demo" width="800">
  </a>
</p>

---

| Component | Description | Repository |
|-----------|-------------|------------|
| **SciTeX-Python** | Modular Python toolkit for scientific research with 200+ MCP tools | [scitex-python](https://github.com/ywatanabe1989/scitex-python) |
| **SciTeX-Hub** (Live at <a href="https://scitex.ai">scitex.ai</a>) | Django-based, self-hostable browser application for scientific research | [scitex-hub](https://github.com/ywatanabe1989/scitex-hub) |

### Architecture — 6-layer dependency cascade (+ orthogonal platform peers)


```
                       ┌──────────────────────────┐
   L5 — umbrella       │   scitex   (re-export)   │
                       └────────────┬─────────────┘
                                    ▼
   ┌──────────────────────────────────────────────────────────────┐
   │  L4 — observers / UX            (depend ↓, never ↑)          │
   │  scitex-clew  scitex-audit  scitex-notification  scitex-audio│
   └────────────────────────────┬─────────────────────────────────┘
                                ▼
   ┌──────────────────────────────────────────────────────────────┐
   │  L3 — workflow producers        (apps + orchestrators)       │
   │  scitex-app · -browser · -genai · -ml · -notebook · -repro · │
   │  -scholar · -seizure-metrics · -session · -todo · -ui · -web │
   │  · -writer · socialia                                        │
   └────────────────────────────┬─────────────────────────────────┘
                                ▼
   ┌──────────────────────────────────────────────────────────────┐
   │  L2 — domain producers          (peer ⇄ peer optional)       │
   │  figrecipe ⇄ scitex-stats · scitex-plt · -pd · -nn · -dsp ·  │
   │  -cv · -linalg · -math · -tex · -msword · -benchmark ·       │
   │  -capture · -events · -git · -hpc · -template                │
   └────────────────────────────┬─────────────────────────────────┘
                                ▼
   ┌──────────────────────────────────────────────────────────────┐
   │  L1 — IO + data leaves          (no peer deps)               │
   │  scitex-io · -db · -dataset · -ssh                           │
   │  crossref-local · openalex-local                             │
   └────────────────────────────┬─────────────────────────────────┘
                                ▼
   ┌──────────────────────────────────────────────────────────────┐
   │  L0 — tooling leaves            (no peer deps; used by all)  │
   │  scitex-types · -path · -str · -dict · -logging · -etc ·     │
   │  -compat · -dev · -config · -core · -context · -datetime ·   │
   │  -decorators · -gen · -gists · -introspect · -os · -parallel │
   │  · -repl · -resource · -sh                                   │
   └──────────────────────────────────────────────────────────────┘

   Orthogonal (orchestration / platform — not in the cascade):
     scitex-hub   scitex-orochi   scitex-agent-container
     scitex-container   newb
```

<details>
<summary><b>All 68 active packages — single table with layer + dependency view</b></summary>

Sourced from [`scitex_dev._ecosystem._registry.ECOSYSTEM`](https://github.com/ywatanabe1989/scitex-dev/blob/main/src/scitex_dev/_ecosystem/_registry.py)

| Package | scitex Module | Layer | Depends on (scitex-* runtime) | Description |
|---------|---------------|-------|--------------------------------|-------------|
| [scitex](https://github.com/ywatanabe1989/scitex) | — *(umbrella)* | L5 | *re-exports the full ecosystem (≈40 peers)* | A comprehensive Python library for scientific computing and data analysis |
| [scitex-audio](https://github.com/ywatanabe1989/scitex-audio) | `scitex.audio` | L4 | dev | Text-to-Speech with multiple backends for scientific workflows |
| [scitex-audit](https://github.com/ywatanabe1989/scitex-audit) | `scitex.audit` | L4 | — | Security audit orchestrator (bandit, shellcheck, pip-audit, GitHub alerts) |
| [scitex-clew](https://github.com/ywatanabe1989/scitex-clew) | `scitex.clew` | L4 | — | Verifiable knowledge graph for scientific experiments |
| [scitex-notification](https://github.com/ywatanabe1989/scitex-notification) | `scitex.notification`, `scitex.notify` | L4 | dev | Multi-backend notification system for SciTeX |
| [scitex-app](https://github.com/ywatanabe1989/scitex-app) | `scitex.app` | L3 | — | SciTeX App SDK — write-once interface for local + cloud apps |
| [scitex-browser](https://github.com/ywatanabe1989/scitex-browser) | `scitex.browser` | L3 | config, logging | Browser automation for scholarly paper access |
| [scitex-genai](https://github.com/ywatanabe1989/scitex-genai) | `scitex.genai` | L3 | dev, io, str | Modality-organised generative-AI provider abstraction (LLM, agents, image/audio/video stubs) |
| [scitex-ml](https://github.com/ywatanabe1989/scitex-ml) | `scitex.ml` | L3 | context, dev, io, logging, plt, repro, str, types | Machine learning, classification, and training utilities |
| [scitex-notebook](https://github.com/ywatanabe1989/scitex-notebook) | `scitex.notebook` | L3 | clew | Jupyter notebook verification, compilation, and DAG-based conversion |
| [scitex-repro](https://github.com/ywatanabe1989/scitex-repro) | `scitex.repro` | L3 | — | Reproducibility utilities (random state, timestamps, hashing) |
| [scitex-scholar](https://github.com/ywatanabe1989/scitex-scholar) | `scitex.scholar` | L3 | browser, io, logging, session | Scientific paper search, enrichment, download, and management |
| [scitex-seizure-metrics](https://github.com/ywatanabe1989/scitex-seizure-metrics) | `scitex.seizure_metrics` | L3 | — | Standardised evaluation metrics for epileptic seizure detection and forecasting |
| [scitex-session](https://github.com/ywatanabe1989/scitex-session) | `scitex.session` | L3 | dict, io, logging, plt, repro, str | `@session` decorator + lifecycle (auto-CLI, output dir tree, RandomStateManager) |
| [scitex-todo](https://github.com/ywatanabe1989/scitex-todo) | `scitex.todo` | L3 | — | Canonical YAML task store with pluggable adapters (mermaid dependency graphs) |
| [scitex-ui](https://github.com/ywatanabe1989/scitex-ui) | `scitex.ui` | L3 | — | Shared frontend UI components for the SciTeX ecosystem |
| [scitex-web](https://github.com/ywatanabe1989/scitex-web) | `scitex.web` | L3 | dev | Web scraping (URLs, images), PubMed search, URL summarization helpers |
| [scitex-writer](https://github.com/ywatanabe1989/scitex-writer) | `scitex.writer` | L3 | dev, ui | LaTeX manuscript compilation with automatic versioning and diff generation |
| [socialia](https://github.com/ywatanabe1989/socialia) | `scitex.social` | L3 | config, dev | Unified social media management (posting, analytics, and insights) |
| [figrecipe](https://github.com/ywatanabe1989/figrecipe) | `scitex.fig`, `scitex.diagram`, `scitex.plt` | L2 | app, config, dev | Reproducible matplotlib wrapper with mm-precision layouts and 47 plot types |
| [scitex-benchmark](https://github.com/ywatanabe1989/scitex-benchmark) | `scitex.benchmark` | L2 | — | Performance benchmarking, runtime monitoring, and profiling helpers |
| [scitex-capture](https://github.com/ywatanabe1989/scitex-capture) | `scitex.capture` | L2 | — | Session-based screen capture (screenshots, multi-frame GIFs, grid overlays, monitor info) |
| [scitex-cv](https://github.com/ywatanabe1989/scitex-cv) | `scitex.cv` | L2 | — | cv2/Pillow image-processing (load/save, resize/rotate/crop, blur/sharpen/edge, drawing) |
| [scitex-dsp](https://github.com/ywatanabe1989/scitex-dsp) | `scitex.dsp` | L2 | decorators, gen, nn | Digital signal processing (PAC, Hilbert, Wavelet, filters, demo signals) |
| [scitex-events](https://github.com/ywatanabe1989/scitex-events) | `scitex.events` | L2 | config | General-purpose async event bus (file-backed, JSON Lines) |
| [scitex-git](https://github.com/ywatanabe1989/scitex-git) | `scitex.git` | L2 | — | Git + GitHub Actions utilities (clone, branch, commit, retry, gh secrets) |
| [scitex-hpc](https://github.com/ywatanabe1989/scitex-hpc) | `scitex.hpc` | L2 | config, ssh | Generic SLURM dispatch (srun, sbatch, sync, poll, fetch) |
| [scitex-linalg](https://github.com/ywatanabe1989/scitex-linalg) | `scitex.linalg`, `scitex.torch` | L2 | dev | Linear-algebra helpers (distance, geometric median, cosine, nannorm) |
| [scitex-math](https://github.com/ywatanabe1989/scitex-math) | `scitex.math` | L2 | — | Mathematical utilities (parity helpers, etc.) |
| [scitex-msword](https://github.com/ywatanabe1989/scitex-msword) | `scitex.msword` | L2 | — | `.docx` reader/writer with journal-style profiles (MDPI, IEEE, Springer, Elsevier, RESNA, IOP) |
| [scitex-nn](https://github.com/ywatanabe1989/scitex-nn) | `scitex.nn` | L2 | config, decorators, gen | Neural network building blocks (BNet, Hilbert, PAC, Wavelet, filters) |
| [scitex-pd](https://github.com/ywatanabe1989/scitex-pd) | `scitex.pd` | L2 | types | Pandas helpers (force_df, melt_cols, find_pval, mv, slice, sort, round) |
| [scitex-plt](https://github.com/ywatanabe1989/scitex-plt) | `scitex.plt` | L2 | figrecipe | SciTeX plotting module (alias for `figrecipe`) |
| [scitex-stats](https://github.com/ywatanabe1989/scitex-stats) | `scitex.stats` | L2 | config, dev, logging | Publication-ready statistical testing with 23 tests, effect sizes, power analysis, MCP server |
| [scitex-template](https://github.com/ywatanabe1989/scitex-template) | `scitex.template` | L2 | config, dev | Project template cloner + code snippet library (six templates vendored, shallow-cloned on demand) |
| [scitex-tex](https://github.com/ywatanabe1989/scitex-tex) | `scitex.tex` | L2 | dev | LaTeX helpers — export to `.tex`, render preview images, vector formatting |
| [crossref-local](https://github.com/ywatanabe1989/crossref-local) | `scitex.scholar.crossref` | L1 | config, dev | Local CrossRef database with 167M+ works and full-text search |
| [openalex-local](https://github.com/ywatanabe1989/openalex-local) | `scitex.scholar.openalex` | L1 | — | Local OpenAlex database with 284M+ works, abstracts, and semantic search |
| [scitex-dataset](https://github.com/ywatanabe1989/scitex-dataset) | `scitex.dataset` | L1 | config, dev | Multi-domain dataset fetcher (OpenNeuro, DANDI, PhysioNet, GEO, ChEMBL, ClinicalTrials) |
| [scitex-db](https://github.com/ywatanabe1989/scitex-db) | `scitex.db` | L1 | core | Database utilities for scientific computing with SQLite3 and PostgreSQL |
| [scitex-io](https://github.com/ywatanabe1989/scitex-io) | `scitex.io` | L1 | dev, logging | Universal scientific data I/O with plugin registry (30+ formats) |
| [scitex-ssh](https://github.com/ywatanabe1989/scitex-ssh) | `scitex.ssh`, `scitex.tunnel` | L1 | — | SSH primitives (exec/copy/attach/tunnel) with per-host allowlist |
| [scitex-compat](https://github.com/ywatanabe1989/scitex-compat) | `scitex.compat` | L0 | — | Backward compatibility shims and deprecation wrappers |
| [scitex-config](https://github.com/ywatanabe1989/scitex-config) | `scitex.config` | L0 | — | Config + path management (direct → yaml → env → default cascade; per-package state-dir resolver) |
| [scitex-context](https://github.com/ywatanabe1989/scitex-context) | `scitex.context` | L0 | — | Execution-context detection (script vs Jupyter vs IPython) + stdout/stderr suppression |
| [scitex-core](https://github.com/ywatanabe1989/scitex-core) | `scitex.core` | L0 | — | Core infrastructure and fundamental utilities |
| [scitex-datetime](https://github.com/ywatanabe1989/scitex-datetime) | `scitex.datetime` | L0 | dev | Datetime helpers (linspace, normalize_timestamp, format helpers) |
| [scitex-decorators](https://github.com/ywatanabe1989/scitex-decorators) | `scitex.decorators` | L0 | compat, config, dev | Decorator library — numpy/torch/pandas/xarray type converters, caching, batching, deprecation |
| [scitex-dev](https://github.com/ywatanabe1989/scitex-dev) | `scitex.dev` | L0 | newb, config, logging | Shared developer utilities and AST linter (absorbs `scitex-linter`) |
| [scitex-dict](https://github.com/ywatanabe1989/scitex-dict) | `scitex.dict` | L0 | dev | Dictionary utilities (DotDict, safe_merge) |
| [scitex-etc](https://github.com/ywatanabe1989/scitex-etc) | `scitex.etc`, `scitex.media` | L0 | — | Cross-cutting utilities (interactive keyboard input, parameter-grid iteration, regex, media display) |
| [scitex-gen](https://github.com/ywatanabe1989/scitex-gen) | `scitex.gen` | L0 | context, decorators, dev, dict, introspect, os, session, sh, stats, str | General utilities (caching, env detection, normalization, mat→npy, xml→dict, TimeStamper) |
| [scitex-gists](https://github.com/ywatanabe1989/scitex-gists) | `scitex.gists` | L0 | — | SigmaPlot macro conversion utilities for matplotlib |
| [scitex-introspect](https://github.com/ywatanabe1989/scitex-introspect) | `scitex.introspect` | L0 | — | IPython-style introspection (signatures, docstrings, members, source, call graphs, class hierarchy) |
| [scitex-logging](https://github.com/ywatanabe1989/scitex-logging) | `scitex.logging`, `scitex.errors` | L0 | — | Logging utilities |
| [scitex-os](https://github.com/ywatanabe1989/scitex-os) | `scitex.os` | L0 | — | Host check + safe file move |
| [scitex-parallel](https://github.com/ywatanabe1989/scitex-parallel) | `scitex.parallel` | L0 | — | Thread/process pool parallel execution utilities |
| [scitex-path](https://github.com/ywatanabe1989/scitex-path) | `scitex.path` | L0 | — | Scientific project path utilities (find, split, symlink, versioning) |
| [scitex-repl](https://github.com/ywatanabe1989/scitex-repl) | `scitex.repl` | L0 | — | Interactive REPL helpers (embed, less, paste) |
| [scitex-resource](https://github.com/ywatanabe1989/scitex-resource) | `scitex.resource` | L0 | dev | System resource info, processor usage logging, RAM limit |
| [scitex-sh](https://github.com/ywatanabe1989/scitex-sh) | `scitex.sh` | L0 | — | Safe subprocess wrapper (list-only, no shell injection) with stream/timeout support |
| [scitex-str](https://github.com/ywatanabe1989/scitex-str) | `scitex.str` | L0 | dev, dict, logging | Text processing (LaTeX formatting, colored output, string parsing, plot text helpers) |
| [scitex-types](https://github.com/ywatanabe1989/scitex-types) | `scitex.types` | L0 | dev | Scientific type definitions (ArrayLike, ColorLike) and validation |
| [newb](https://github.com/ywatanabe1989/newb) | — | Orthogonal | — | "A fresh AI agent tries to use your package" — pytest-style; if it succeeds, your docs work |
| [scitex-agent-container](https://github.com/ywatanabe1989/scitex-agent-container) | `scitex.agent_container` | Orthogonal | config, container, logging, ssh | Declarative YAML framework for managing AI coding agent instances |
| [scitex-container](https://github.com/ywatanabe1989/scitex-container) | `scitex.container` | Orthogonal | config, dev | Unified container management for Apptainer and Docker |
| [scitex-hub](https://github.com/ywatanabe1989/scitex-hub) | `scitex.cloud`, `scitex.module`, `scitex.project` | Orthogonal | app, config, dev, session, writer | SciTeX Hub — deployment and management CLI |
| [scitex-orochi](https://github.com/ywatanabe1989/scitex-orochi) | `scitex.orochi` | Orthogonal | config, resource | Agent communication hub |

</details>

---

## Scientific Research Projects

| Title | Code |
|-------|------|
| A deep learning model for the detection of various dementia and MCI pathologies based on resting-state electroencephalography data | [eeg-dementia-classification](https://github.com/yanagisawa-lab/eeg-dementia-classification) |
| Towards threshold invariance in defining hippocampal ripples | [Code](https://github.com/ywatanabe1989/towards-threshold-invariance-in-defining-hippocampal-ripples), [pip](https://github.com/ywatanabe1989/ripple_detector_CNN) |
| Hippocampal neural fluctuations during working memory | [ripple-wm-code](https://github.com/ywatanabe1989/ripple-wm-code) |
| gPAC: GPU-accelerated phase-amplitude coupling analysis (341x faster than TensorPAC) | [gPAC](https://github.com/ywatanabe1989/gPAC) |
| Intestelligence: A pharmacological neural network using intestine data | [intestelligence](https://github.com/ywatanabe1989/intestelligence) |

---

## Emacs Packages

| Category | Package | Description |
|----------|---------|-------------|
| **AI** | [emacs-claude-code](https://github.com/ywatanabe1989/emacs-claude-code) | Claude Code integration (SciTeX-Engine) |
| | [emacs-llm](https://github.com/ywatanabe1989/emacs-llm) | LLM chat client in Elisp |
| | [genai](https://github.com/ywatanabe1989/genai) | LLM chat interface with streaming and conversation history |
| | [emacs-whisper-live](https://github.com/ywatanabe1989/emacs-whisper-live) | Real-time speech transcription with Whisper |
| | [emacs-mcp-server](https://github.com/ywatanabe1989/emacs-mcp-server) | MCP server for Emacs |
| **Dev** | [elisp-test](https://github.com/ywatanabe1989/elisp-test) | Testing framework for Elisp |
| | [elisp-linter](https://github.com/ywatanabe1989/elisp-linter) | Linter for Elisp |
| | [emacs-python-import-manager](https://github.com/ywatanabe1989/emacs-python-import-manager) | Python import management |
| | [emacs-python-config](https://github.com/ywatanabe1989/emacs-python-config) | Python environment configuration |
| **UI** | [emacs-tab-manager](https://github.com/ywatanabe1989/emacs-tab-manager) | Tab management |
| | [emacs-buffer-navigation](https://github.com/ywatanabe1989/emacs-buffer-navigation) | Buffer navigation |
| | [emacs-recentf-project](https://github.com/ywatanabe1989/emacs-recentf-project) | Project-aware recent files |
| | [emacs-spinner](https://github.com/ywatanabe1989/emacs-spinner) | Spinner animations |
| **Tools** | [emacs-header-footer-manager](https://github.com/ywatanabe1989/emacs-header-footer-manager) | Header/footer management |
| | [emacs-slack](https://github.com/ywatanabe1989/emacs-slack) | Slack integration |
| | [emacs-message](https://github.com/ywatanabe1989/emacs-message) | Toggle print/message |
| | [emacs-gif-screencast](https://github.com/ywatanabe1989/emacs-gif-screencast) | GIF screencast & capture |
| | [emacs-password-manager](https://github.com/ywatanabe1989/emacs-password-manager) | GPG-encrypted password manager |

---

## Resources

| Resource | Description |
|----------|-------------|
| [agents](https://github.com/ywatanabe1989/agents) | Sync MCP servers, skills, and instructions across AI coding tools |
| [automated-research-demo](https://github.com/ywatanabe1989/automated-research-demo) | Demo: AI-driven autonomous research from data to manuscript |
| [.dotfiles-public](https://github.com/ywatanabe1989/.dotfiles-public) | Linux configuration |
| [ai-ielts.app](https://ai-ielts.app/) | IELTS speaking/writing practice |
| [Programming advice (EN)](./docs/advice-for-my-younger-myself-en.md) / [(JA)](./docs/advice-for-my-younger-myself-ja.md) | Tips for younger self |

---

<p align="center">
  <a href="https://scitex.ai" target="_blank"><img src="./docs/images/scitex-icon.png" alt="SciTeX" width="40"/></a>
  <br>
  ywatanabe@scitex.ai
</p>

<!-- EOF -->
