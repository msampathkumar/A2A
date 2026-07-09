# 1. Introduction & Setup

Welcome to the Agent2Agent (A2A) Python Quickstart. This guide will get you from zero to running your first A2A-compliant agent.

## Core Concepts
A2A agents are defined by their **Skills** (what they do) and **Agent Cards** (how they describe themselves). They interact with a server, providing a standardized protocol for task execution, streaming, and multi-turn dialogues.

## Prerequisites
- Python 3.10+
- Git
- Recommended: VS Code or similar

## Installation
First, clone the samples repository:

```bash
git clone https://github.com/a2aproject/a2a-samples.git -b main --depth 1
cd a2a-samples
```

Create a virtual environment and install the dependencies:

=== "Mac/Linux"
    ```sh
    python -m venv .venv
    source .venv/bin/activate
    ```
=== "Windows"
    ```powershell
    python -m venv .venv
    .venv\Scripts\activate
    ```

```bash
pip install -r samples/python/requirements.txt
```

Verify the installation by importing the package:

```bash
python -c "import a2a; print('A2A SDK imported successfully')"
```
