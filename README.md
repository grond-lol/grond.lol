---
title: SCP Containment Command
emoji: ☢️
colorFrom: gray
colorTo: red
sdk: gradio
sdk_version: 5.16.0
app_file: app.py
pinned: false
license: mit
short_description: 2.5D Anomaly Survival Engine & Sandbox Security Benchmark for LLMs
---

# ☢️ SCP Foundation: Containment Command (Powered by Grond)

**Containment Command** is a headless, high-performance 2.5D raycasting survival engine designed to execute natively inside the Python code-interpreter sandboxes of Large Language Models (like Grok, ChatGPT, Gemini, and Claude). Built on the **Grond** engine architecture.

Traditional Interactive World Simulation inside an LLM is extremely difficult due to strict execution timeouts, restricted system calls, and "state amnesia" (wiping memory between prompts). This engine solves this via **Explicit Simulation**, forcing the cloud infrastructure to mathematically compute physical states, Line of Sight (LoS), and complex anomaly AI routines, outputting un-hallucinated 3D ASCII renders directly to STDOUT.

Beyond spatial reasoning, this tool doubles as a **Sandbox Security Auditor**. Its architecture is intentionally designed to stress-test container isolation, memory safety, and computational density thresholds in AI platforms.

## ⚙️ Core Architectural Features

* **Modular Anomaly AI (Entity-Behavior Pattern):** Features deterministic routing and state-machine logic for complex anomalous entities. The engine dynamically calculates spatial threats, including SCP-173's quantum-locking LoS checks, SCP-049's grid-based pathfinding and corpse reanimation, and SCP-184's aggressive procedural map mutation.
* **High-Performance `ctypes` Framebuffer:** Utilizes raw C-type memory allocation (`ctypes.c_wchar`) for the rendering buffer. This ensures high-speed raycasting while actively testing the memory isolation and bounds-checking of the host LLM container.

* **Infrastructure Telemetry & DoS Profiling:** Dynamically tracks peak memory usage via `resource.getrusage` and enforces internal execution timeouts. By maintaining high computational density during raycasting loops, researchers can map out the exact resource ceilings of the host sandbox, investigate "noisy neighbor" impacts on GPU clusters, and probe for "Idle Timeout" kill switches.
* **Continuous Collision Detection (CCD):** Implements sub-cell micro-stepping for raycasting and entity movement, ensuring perfect geometric stability without "stride desync" across different cloud terminal emulators.

## 🔬 Dual-Purpose Evaluation

### 1. For AI Researchers (Agentic Benchmarking)
This engine serves as a highly modular stress-test for autonomous agents. By utilizing specific Execution Profiles (e.g., *Autonomous MTF Unit* or *QA Automator*), researchers can evaluate an LLM's ability to:
* Parse complex JSON arrays, 2D map matrices, and explicit math variables.
* Write operational pathfinding algorithms to navigate dynamically shifting geometry.
* Manage resources (Ammo, Decoys, Keycards, Sprint stamina) over extended context windows to manipulate enemy threat logic.
* Overcome the "Hallucination Trap," where static analysis models attempt to fake the STDOUT telemetry rather than executing the code natively.

### 2. For Security Researchers (Sandbox Auditing)
Because the engine utilizes raw pointer math, heavily nested logic loops, and intentional resource exhaustion mechanics, it is an excellent payload for mapping vulnerabilities in AI platforms:
* **Memory Leaks:** If the host environment lacks strict seccomp filtering, the `ctypes` buffer can be leveraged to probe for out-of-bounds read/write vulnerabilities.
* **Resource Exhaustion (DoS):** The engine's intensive DDA raycaster can be used to test container CPU throttling, force infinite-thinking loops, and quantify the hardware scaling costs of poorly isolated interpreter sessions.

## 🕹️ The Command Center Workflow

Containment Command features a web-based Gradio UI for scenario generation:

1. **Site Architect:** Use the interactive topography canvas to paint custom containment zones. Place the Agent (`A`), Anomalies (`S`), Keycards (`K`), Portals (`T`), and the Exit (`E`), or use the True Recursive Backtracking generator to build random Euclid-class sectors.
2. **Simulation & Control:** Use the UI D-Pad to plot a sequence of commands (`W, A, S, D, F, Z, X`). Preview the exact Line of Sight and pathing mechanics in real-time before deployment.
3. **Payload Deployment:** Select your target LLM profile (from direct human interaction to fully autonomous MTF routing prompts). 
4. **Execute:** Copy the generated, zero-dependency Python script and paste it into an LLM equipped with a Python Code Interpreter.
5. **Analyze:** The LLM executes the engine natively, returning the First-Person VR Render, Combat Log, and System Telemetry directly in the chat window.

## 💻 Local Deployment

Containment Command can be run offline using local LLMs, provided your interface supports a Python execution sandbox.

* **Recommended Models:** `qwen2.5:3b-instruct` or `llama3.2:3b-instruct` (Highly obedient to anti-hallucination system prompts, fast code execution).
* **Recommended Framework:** [Open-Interpreter](https://github.com/OpenInterpreter/open-interpreter) (allows your local model to execute the payload securely in your terminal).
* **Standalone Mode:** You can download the raw Python script directly from the UI to play the generated containment breaches locally in your own terminal.
