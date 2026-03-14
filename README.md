<!-- ---
!-- Timestamp: 2026-03-14
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
  <a href="https://pypi.org/project/scitex/">pip install scitex</a>
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
| **SciTeX-Engine** | Emacs interface for Claude Code with auto-response, vterm integration, and session management | [emacs-claude-code](https://github.com/ywatanabe1989/emacs-claude-code) |
| **SciTeX-Cloud** | Django-based, self-hostable browser application for scientific research | [scitex-cloud](https://github.com/ywatanabe1989/scitex-cloud) |

<details>
<summary><b>Integrated Packages</b></summary>

Standalone packages usable independently or via unified `scitex` interface.

| Package | scitex Module | Description |
|---------|---------------|-------------|
| [figrecipe](https://github.com/ywatanabe1989/figrecipe) | `scitex.plt` | Reproducible, publication-ready scientific figures with mm-precision layouts and 47 plot types |
| [scitex-stats](https://github.com/ywatanabe1989/scitex-stats) | `scitex.stats` | Publication-ready statistical testing with 23 tests, effect sizes, and power analysis |
| [scitex-io](https://github.com/ywatanabe1989/scitex-io) | `scitex.io` | Universal scientific data I/O with plugin registry (30+ formats) |
| [scitex-writer](https://github.com/ywatanabe1989/scitex-writer) | `scitex.writer` | LaTeX manuscript compilation with automatic versioning and diff generation |
| [scitex-scholar](https://github.com/ywatanabe1989/SciTeX-Scholar) | `scitex.scholar` | Scientific literature search and analysis |
| [crossref-local](https://github.com/ywatanabe1989/crossref-local) | `scitex.scholar.crossref` | Local CrossRef database with 167M+ papers and full-text search |
| [openalex-local](https://github.com/ywatanabe1989/openalex-local) | `scitex.scholar.openalex` | Local OpenAlex database with 284M+ papers and semantic search |
| [scitex-dataset](https://github.com/ywatanabe1989/scitex-dataset) | `scitex.dataset` | Unified API for neuroscience datasets (OpenNeuro, DANDI, PhysioNet) |
| [scitex-clew](https://github.com/ywatanabe1989/scitex-clew) | `scitex.clew` | Verifiable knowledge graph for scientific experiments |
| [scitex-linter](https://github.com/ywatanabe1989/scitex-linter) | `scitex.linter` | AST-based linter enforcing reproducible research patterns |
| [scitex-audio](https://github.com/ywatanabe1989/scitex-audio) | `scitex.audio` | Text-to-Speech with multiple backend fallback |
| [socialia](https://github.com/ywatanabe1989/socialia) | `scitex.social` | Unified social media management |
| [scitex-container](https://github.com/ywatanabe1989/scitex-container) | `scitex.container` | Unified container management for Apptainer and Docker |
| [scitex-tunnel](https://github.com/ywatanabe1989/scitex-tunnel) | `scitex.tunnel` | Persistent SSH reverse tunnel for NAT traversal |
| [scitex-dev](https://github.com/ywatanabe1989/scitex-dev) | `scitex.dev` | Shared developer utilities for the SciTeX ecosystem |
| [scitex-app](https://github.com/ywatanabe1989/scitex-app) | `scitex.app` | Write-once interface for local + cloud apps |

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