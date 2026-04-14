---
title: Grond
emoji: 🌖
colorFrom: yellow
colorTo: pink
sdk: gradio
sdk_version: 5.16.0
app_file: app.py
pinned: false
license: mit
short_description: 2.5D Stealth Engine & Sandbox Security Benchmark for LLM Agents
---

# 📡 GROND ENGINE: Tactical Espionage Action

**Grond** is a headless, high-performance 2.5D raycasting stealth engine designed to execute natively inside the Python code-interpreter sandboxes of Large Language Models (like Grok, ChatGPT, Gemini, and Claude). 

Traditional Interactive World Simulation inside an LLM is extremely difficult due to strict execution timeouts, restricted system calls, and "state amnesia" (wiping memory between prompts). Grond solves this via **Explicit Simulation**, forcing the cloud infrastructure to mathematically compute physical states, Line of Sight (LoS), and enemy AI routines, outputting un-hallucinated 3D ASCII renders directly to STDOUT.

Beyond spatial reasoning, Grond doubles as a **Sandbox Security Auditor**. Its architecture is intentionally designed to stress-test container isolation, memory safety, and computational density thresholds in AI platforms.



## ⚙️ Core Architectural Features

* **High-Performance `ctypes` Framebuffer:** Utilizes raw C-type memory allocation (`ctypes.c_wchar`) for the rendering buffer. This ensures high-speed raycasting while actively testing the memory isolation and bounds-checking of the host LLM container.
* **Hybrid Execution State:** Bypasses LLM container amnesia by coupling a "Command Tape" injection array with local filesystem persistence. The engine attempts to serialize the simulation state to `/dev/shm/grond_save.dat` via `pickle`, testing the host's ephemeral storage policies across chat turns.
* **Advanced Entity AI & Stealth Mechanics:** Features a robust 2D matrix evaluating Guard vision cones, Camera sweeps, and auditory triggers. Implements complex pathfinding, Evasion phases, and Close Quarters Combat (CQC).
* **Infrastructure Telemetry:** Dynamically profiles `os.cpu_count()` to scale rendering resolution. Critically, it tracks peak memory usage via `resource.getrusage` and enforces internal execution timeouts, allowing researchers to map the exact resource ceilings of the host sandbox.
* **Continuous Collision Detection (CCD):** Implements sub-cell micro-stepping for raycasting and entity movement, ensuring perfect geometric stability without "stride desync" across different cloud terminal emulators.

## 🔬 Dual-Purpose Evaluation

### 1. For AI Researchers (Agentic Benchmarking)
Grond serves as a highly modular stress-test for autonomous agents. By utilizing specific Execution Profiles (e.g., *Autonomous AI Solver* or *Temporal Trap*), researchers can evaluate an LLM's ability to:
* Parse complex JSON arrays and 2D matrices.
* Write operational pathfinding algorithms to avoid enemy LoS.
* Manage resources (Ammo, Keys, Rations) over extended context windows.
* Overcome the "Hallucination Trap," where static analysis models attempt to fake the STDOUT telemetry rather than executing the code natively.

### 2. For Security Researchers (Sandbox Auditing)

Because the engine utilizes raw pointer math, heavily nested logic loops, and filesystem persistence, it is an excellent payload for mapping vulnerabilities in AI platforms:
* **Memory Leaks:** If the host environment lacks AppArmor or strict seccomp filtering, the `ctypes` buffer can be leveraged to probe for out-of-bounds read/write vulnerabilities.
* **Computational Density:** The engine's DDA raycaster can be used to test container CPU throttling and forced-kill timeouts.
* **Stateful Persistence:** Tests if the cloud container correctly sanitizes `/tmp/` and `/dev/shm` mounts between sequential user prompts.

## 🕹️ The Command Center Workflow

Grond features a web-based Tactical Command Center for payload generation:

1. **Mission Architect:** Use the interactive grid to paint custom stealth scenarios. Place the Agent (`A`), Guards (`G`), Cameras (`C`), Keycards (`K`), and the Exit (`E`).
2. **Simulation & Control:** Use the UI D-Pad to plot a sequence of commands (`W, A, S, D, F, K, X`). Preview the exact Line of Sight and pathing mechanics in real-time.
3. **Payload Deployment:** Select your target LLM profile (from direct human interaction to fully autonomous agent prompts). 
4. **Execute:** Copy the generated, zero-dependency Python script and paste it into an LLM equipped with a Python Code Interpreter.
5. **Analyze:** The LLM executes the engine natively, returning the First-Person VR Render, Orthogonal Minimap, Combat Log, and System Telemetry directly in the chat window.

## 💻 Local Deployment

Grond can be run offline using local LLMs, provided your interface supports a Python execution sandbox.

* **Recommended Models:** `qwen2.5:3b-instruct` or `llama3.2:3b-instruct` (Highly obedient to anti-hallucination system prompts, fast code execution).
* **Recommended Framework:** [Open-Interpreter](https://github.com/OpenInterpreter/open-interpreter) (allows your local model to execute the Grond payload securely in your terminal).
* **Standalone Mode:** You can download the raw Python engine directly from the UI to play the generated maps in your local terminal.
