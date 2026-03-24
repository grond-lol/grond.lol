# 🟩 GROND ENGINE: Explicit Simulation Framework

**Grond** is a headless, stateless 2.5D Raycasting engine designed to execute entirely inside the Python code-interpreter sandboxes of Large Language Models (like Grok, ChatGPT, or Claude). 

Because LLM execution containers suffer from "state amnesia" (they wipe memory between prompts) and strict timeouts, traditional Interactive World Simulation inside an LLM is extremely difficult. Most research attempts to solve this via *Implicit Simulation*—forcing neural networks to hallucinate frame states (e.g., GameNGen, Oasis).

The Grond Engine solves this via **Explicit Simulation and Direct Memory Access**. It leverages a deterministic "Movement Tape" architecture alongside C-level memory manipulation to force the cloud infrastructure to mathematically prove the game state on every execution, generating un-hallucinated 3D ASCII renders of exact spatial topography in O(1) final string generation time.

## ⚙️ Core Architectural Features

* **Stateless Command Tape:** Bypasses LLM container amnesia by compiling all user inputs (`W, A, S, D, F, P`) into an execution array. On every prompt, the engine reconstructs the entire universe's history from `t=0` in milliseconds.
* **Direct Memory Access (DMA) VGA Emulation:** Bypasses Python's list-boxing penalty by exploiting `ctypes` to allocate a 1D contiguous Unicode buffer (`ctypes.create_unicode_buffer`). This allows hardware-level O(1) memory dumping, drastically reducing compute time to avoid sandbox timeouts.
* **Continuous Collision Detection (CCD):** Implements sub-cell micro-stepping to prevent fast-moving entities (or AI agents) from tunneling through collision boundaries.
* **Fast Heuristics:** Replaces heavy `math.sqrt()` Euclidean distance checks with optimized squared-distance (`dist_sq`) thresholds for AI pathfinding, hitscan weaponry, and trigger volumes.
* **Terminal MUD Telemetry:** Outputs a rich, text-adventure-style combat log and JSON state dictionary that is specifically formatted to be parsed by an LLM's attention mechanism, turning the engine into a perfect Multi-User Dungeon (MUD) benchmark.

## 🕹️ The Simulation Loop

You play Grond by "correspondence." You do not move in real-time; you program a sequence of moves, send them to the LLM, and await the visual snapshot.

1. **Design:** Use the Architect Map (web UI) to paint your level, place Guards (`G`), Medkits (`+`), Ammo (`=`), and secret Illusory Walls (`?`). Includes a default orthogonal demake of DOOM (1993) E1M1: Hangar.
2. **Plot:** Use your keyboard or the UI buttons to chart your path in the Live Tactical Preview.
3. **Generate:** Click `🚀 GENERATE INJECTION PAYLOAD` to compile your map and movement tape into a single, zero-dependency Python script.
4. **Execute:** Paste the generated markdown block into an LLM equipped with a Python Code Interpreter.
5. **Analyze:** The LLM will execute the C-level buffer natively and return a First-Person 3D View, a Minimap, and your Telemetry status.
6. **Iterate:** Read the telemetry, add more moves to your queue in the web UI (do **not** clear the queue unless you want to respawn!), and generate the next payload.

## 🔬 For AI Researchers

Grond Engine serves as a highly modular stress-test for autonomous agents (similar to Voyager). 
By prompting an LLM to generate its own "Movement Tapes" and evaluating the resulting JSON telemetry, researchers can test an agent's spatial reasoning, object permanence, and ability to navigate deterministic physical constraints without the hallucination issues present in TextWorld or purely generative models.

## 💻 Local Deployment

Grond can be run entirely offline using local LLMs. However, your local interface **must** support a Python execution sandbox.

* **Recommended Models:** `qwen2.5:3b-instruct` or `llama3.2:3b-instruct` (Highly obedient to anti-hallucination system prompts, easily fits in 4GB VRAM).
* **Recommended Framework:** [Open-Interpreter](https://github.com/OpenInterpreter/open-interpreter) (allows your local model to execute the payload securely in your terminal).

## ⚠️ Anti-Simulation Override

LLMs will occasionally try to "guess" or hallucinate the ASCII output instead of actually running the code. The Grond payload includes a strict `[EXECUTION DIRECTIVE]` prompt that forces the model to use its Python tool and return the exact `stdout`. If your render looks jagged or the minimap loses its orthogonal geometry, remind the LLM to *run the code natively*.
