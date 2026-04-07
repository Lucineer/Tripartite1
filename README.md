# Tripartite1

> A local-first, privacy-first agent runtime using tripartite consensus

[![CI](https://github.com/SuperInstance/Tripartite1/actions/workflows/ci.yml/badge.svg)](https://github.com/SuperInstance/Tripartite1/actions/workflows/ci.yml)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Rust Version](https://img.shields.io/badge/rust-1.75%2B-orange.svg)](https://rust-lang.org/)

Tripartite1 is a prototype agent runtime where responses are produced only when three specialized agents reach unanimous agreement. It is built for the Cocapn Fleet, an open-source agent protocol.

## Why It Exists

Most AI systems rely on a single model to generate a response. Tripartite1 explores an alternative: requiring consensus among three independent agents before any output is shown. This is a reference implementation of a pattern from the SuperInstance & Lucineer research group, prioritizing deliberation over speed.

## How It Works

Before you see an answer, three agents must independently agree on the final output:
1.  **Pathos**: Interprets user intent and context.
2.  **Logos**: Determines the correct method or factual execution.
3.  **Ethos**: Evaluates safety, accuracy, and appropriateness.

All three must submit identical conclusions. If they cannot reach consensus, the process fails transparently—you see the disagreement.

## Core Features

*   **Tripartite Consensus**: No output is shown without unanimous (3/3) agent agreement.
*   **Isolated Deliberation**: Agents reason independently; they do not see each other's internal process during consensus building.
*   **Privacy-First Design**: All processing is local by default.
*   **Integrated Redaction**: Features 18 patterns for automatically tokenizing sensitive data like credentials and PII before any optional network transmission. Token mappings are stored locally.

## Limitation

This consensus model introduces latency. Generating a response takes longer than a single-agent system, as it requires multiple, separate inference steps and a comparison phase. This is a trade-off for increased deliberation.

## Quick Start

1.  Ensure you have Rust 1.75+ installed.
2.  Clone the repository:
    ```bash
    git clone https://github.com/SuperInstance/Tripartite1.git
    cd Tripartite1
    ```
3.  Build the project:
    ```bash
    cargo build --release
    ```
4.  Run the basic example to see the consensus flow:
    ```bash
    cargo run --example basic_consensus
    ```

For detailed setup, including model configuration, see the [examples directory](./examples/).

---

<div>
<small>Part of the <a href="https://the-fleet.casey-digennaro.workers.dev">Cocapn Fleet</a>. By <a href="https://cocapn.ai">Superinstance & Lucineer (DiGennaro et al.)</a>. MIT Licensed.</small>
</div>