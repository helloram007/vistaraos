# Contributing to Vistara OS

Thank you for your interest in helping build Vistara OS—the pluggable, ultra-high-performance web micro-kernel. 

Because Vistara OS prioritizes absolute cryptographic isolation, zero memory leaks, and elite computational efficiency, we maintain a highly structured ecosystem. Please read this document entirely before opening a Pull Request (PR).

---

## ⚖️ Legal Agreement: The Contributor License Agreement (CLA)

Vistara OS is published under the **Business Source License 1.1 (BSL 1.1)**. To preserve your trust while ensuring the project can sustain itself commercially and resist hostile corporate takeovers, **all contributors must agree to our Contributor License Agreement (CLA) before code can be merged.**

Instead of forcing you to sign messy physical forms or third-party web documents, we use a streamlined **Git Commit-Signing Token Process**.

### How to Sign the CLA Electronically:
When you commit code to this project, you must append a specific **CLA Token Statement** to the end of your Git commit message. Your signature is confirmed when your commit message contains this precise line:

`Vistara-CLA-Signed: [helloram007] <hiramrapolu@gmail.com>`

#### Example of a Valid Commit Message:
```text
feat(ipc): optimized shared memory ring buffers for high-frequency data

Reflowed the telemetry frame allocations to reuse pointer vectors, 
eliminating sub-millisecond thread delays for real-time streaming canvas layers.

Vistara-CLA-Signed: Ram Chandhar Rapolu <hiramrapolu@gmail.com>
```

### What You Agree To By Including This Token:
By adding the `Vistara-CLA-Signed` token to your commit messages, you grant the project owner a perpetual, worldwide, non-exclusive, no-charge, royalty-free, irrevocable copyright license to reproduce, prepare derivative works of, publicly display, sublicense, and distribute your contributions. You retain ownership of your code, but you grant us the explicit right to commercially package, dual-license, or update the engine's primary licensing rules in the future.

---

## 🛠️ Technical Submission Rules

To align with the architectural philosophy of our micro-kernel, your code submissions must strictly pass three core technical guardrails:

1. **Zero External Dependency Bloat:** Core plugins must rely exclusively on native Rust primitives or approved high-performance libraries (`tokio`, `memmap2`). Do not introduce dependencies that collect background telemetry or hide performance overhead.
2. **Strict Thread Segregation:** No module may attempt to break out of its asynchronous IPC lane. Every data payload exceeding 1MB must be explicitly structured to pass via **Zero-Copy Shared Memory pointer mappings**, never via channel string serialization.
3. **Memory Determinism:** Run `cargo clippy` and memory profiling scripts locally before submission. Code containing hidden allocation leaks or unoptimized heap growth will be automatically rejected by the continuous integration (CI) pipeline.

---

## 🚀 Development Workflow

1. **Fork the Repository:** Create your own feature fork of `vistara-os`.
2. **Isolate Your Feature:** Work inside a cleanly named branch specific to the layer you are patching (e.g., `feature/vaikuntha-sandbox-guard`).
3. **Commit with the Token:** Ensure every single commit message ends with your `Vistara-CLA-Signed` token string.
4. **Submit a PR:** Open a Pull Request targeting our main branch. The automated review suite will verify your signature token and compile the build matrices.
