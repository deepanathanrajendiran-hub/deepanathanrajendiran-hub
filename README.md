<h1 align="center">Deepanathan Rajendiran</h1>

<p align="center">
  <a href="https://github.com/deepanathanrajendiran-hub">
    <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=20&duration=3200&pause=900&color=6E7681&center=true&vCenter=true&width=620&lines=I+build+LLM+agents;and+the+evals+that+decide+whether+to+trust+them;sometimes+the+eval+says+don't+ship" alt="I build LLM agents, and the evals that decide whether to trust them" />
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/MS%20Artificial%20Intelligence-University%20at%20Buffalo%20'26-2b3137?style=flat-square" />
  <img src="https://img.shields.io/badge/Buffalo,%20NY-open%20to%20relocation-2b3137?style=flat-square" />
</p>

---

### What I actually do

Post-training and evaluation. Supervised fine-tuning and verifiable-reward RL on open-weight
models, and the harnesses that tell you whether a change helped or whether you got lucky: golden
sets, held-out splits, merge-blocking CI gates, tracing.

I care most that a result survives someone checking it. Most of what I know came from finding out
my own numbers were wrong.

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white" />
  <img src="https://img.shields.io/badge/Hugging%20Face-FFD21E?style=flat-square&logo=huggingface&logoColor=black" />
  <img src="https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langchain&logoColor=white" />
  <img src="https://img.shields.io/badge/MCP-000000?style=flat-square&logo=anthropic&logoColor=white" />
  <img src="https://img.shields.io/badge/SFT%20%2F%20LoRA-5A5A5A?style=flat-square" />
  <img src="https://img.shields.io/badge/RLVR%20%2F%20GRPO-5A5A5A?style=flat-square" />
  <img src="https://img.shields.io/badge/OpenTelemetry-425CC7?style=flat-square&logo=opentelemetry&logoColor=white" />
  <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/ONNX-005CED?style=flat-square&logo=onnx&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" />
</p>

---

### 🔬 The result I'm proudest of is one I tried hard to break

I built **Refine**, a learning loop for Claude Code and Codex that turns each finished task into a
small, reusable note. Then I tested whether those notes help a *different* agent.

In a pre-registered SWE-bench Pro study, notes written in Claude Code were frozen and handed to
mini-swe-agent (DeepSeek V4 Flash, 20 steps). On 44 held-out tasks, pass rate went from
**58% to 78%**, p = `0.0001`. Every patch was re-graded on a pristine image (264 of 264 agreed),
and when an audit flagged 13 runs, I scored all 13 as failures: still p = `0.0003`.

The same rules stopped both Claude Code studies before testing, because those agents already
passed nearly everything. I wanted a result that was allowed to fail. That's the point.

---

### Projects

#### [continual-harness](https://github.com/deepanathanrajendiran-hub/continual-harness) &nbsp;·&nbsp; coding agents that learn from finished tasks
A harness that runs inside Codex and Claude Code as two skills: **refine**, the learning loop, and
**horizon**, which keeps goal, verification and next-action state across sessions. One shared
Python implementation, standard library only. In a pre-registered SWE-bench Pro study, notes
Refine wrote in Claude Code were frozen and given to a different agent, mini-swe-agent with
DeepSeek V4 Flash capped at 20 steps. On 44 held-out openlibrary tasks, run 3 times each, pass rate
went **58% → 78%** (77 vs 103 of 132 runs), mean per-task gain +0.197 (95% CI +0.11 to +0.28),
**p = 0.0001**. Every run was re-graded on a pristine image with only its patch applied: 264 of 264
agreed. A hidden-test audit, not pre-registered, flagged 13 runs; scoring all 13 as failures still
gives p = 0.0003. Scope: one repository, one model, a 20-step cap. Pre-registered gates stopped
both Claude Code studies (Sonnet 29/30, Haiku 30/30 on practice tasks) before the test phase,
because there was no room to improve. The skills now live in
[refine](https://github.com/deepanathanrajendiran-hub/refine) and
[horizon](https://github.com/deepanathanrajendiran-hub/horizon); this repo is the research record.

#### [depguard](https://github.com/deepanathanrajendiran-hub/depguard) &nbsp;·&nbsp; CVE triage agent + eval harness
LangGraph planner/executor, six tools published over **MCP**, and a four-predicate mechanical
checker that grades every verdict with **no model in the correctness path**. The eval is
merge-blocking in CI — a one-line planner regression turns the build red. Every run traced with
OpenTelemetry into Langfuse. The agent is differential-tested against a deterministic semver
reference, a verifier with no model to hallucinate: **38 of 38** verdicts agree, against 0.6842 for
the same model as a single ReAct agent. Where the affected range exists only in advisory prose and
the reference can't answer, the LLM extractor recovers it at **0.6259** vs 0.4490 for regex.
Reproduction steps in the repo.

#### [sft-code-review](https://github.com/deepanathanrajendiran-hub/sft-code-review) &nbsp;·&nbsp; post-training a 7B code reviewer
LoRA fine-tune of Qwen2.5-Coder-7B on 11,309 distilled reasoning traces. A blind three-vote judge
preferred it over the base model in **86% of 200** in-distribution head-to-heads, and in **79.0%**
of **632 records from 88 unseen repositories** (95% CI [75.8%, 82.1%]). Hallucinated identifiers halved by checking every identifier
the model named against the actual diff — a string match, not another model.

> **Read the RL arc.** Three runs regressed. I wrote the conclusion *"RL is dead"* —
> then found five silent pipeline defects behind it: TRL's `GRPOConfig` left-truncating ~87% of
> prompts, and PEFT computing the KL reference with adapters disabled, anchoring to the base model
> instead of my SFT policy. The conclusion wasn't wrong so much as unearned. The clean GRPO re-run,
> with a verifiable reward, cut false flagging on clean diffs from 0.749 to 0.658 at recall parity.
> The re-run and the retraction are both in the repo.

#### [socratic-ot-tutor](https://github.com/deepanathanrajendiran-hub/socratic-ot-tutor) &nbsp;·&nbsp; Socratic tutor, shipped
Built for a graduate NLP course and used by **50 students** at UB. LangGraph over a Corrective RAG
pipeline that grades and reranks its own sources before answering. FastAPI + SSE on Cloud Run,
Next.js on Vercel. Cold start cut from 3–4 min to ~15–25 s by baking weights into the image.

#### [eia-energy-mcp](https://github.com/deepanathanrajendiran-hub/eia-energy-mcp) &nbsp;·&nbsp; MCP server
US power-plant data (EIA-860, EIA-923) exposed as tools an agent can call.

#### [carla-rl-autonomous-driving](https://github.com/deepanathanrajendiran-hub/carla-rl-autonomous-driving) &nbsp;·&nbsp; safe RL
PPO driving policy trained through a three-stage curriculum, with a rule-based safety shield that
overrides the policy at stop signs and red lights — plus the shield-on/shield-off harness that
measured what the shield was worth. YOLOv8 perception exported to ONNX. From my research
assistantship at UB.

---

<p align="center">
  <a href="https://linkedin.com/in/deepanathan-rajendiran"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white" /></a>
  <a href="mailto:deepanathanrajendiran@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white" /></a>
</p>
