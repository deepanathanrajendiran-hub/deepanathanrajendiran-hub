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

### 🔬 The result I'm proudest of is a negative one

I built a multi-agent CVE triage system, then built the harness that proved it shouldn't ship.

A deterministic semver-containment check matched the agent on **every metric** — delta `0.0000`,
95% CI `[0, 0]` — and ran about **278x faster**. I wrote up the null result and recommended the
script.

The instrument worked. That's the point.

---

### Projects

#### [depguard](https://github.com/deepanathanrajendiran-hub/depguard) &nbsp;·&nbsp; CVE triage agent + eval harness
LangGraph planner/executor, six tools published over **MCP**, and a four-predicate mechanical
checker that grades every verdict with **no model in the correctness path**. The eval is
merge-blocking in CI — a one-line planner regression turns the build red. Every run traced with
OpenTelemetry into Langfuse. Ablation and reproduction steps in the repo.

#### [sft-code-review](https://github.com/deepanathanrajendiran-hub/sft-code-review) &nbsp;·&nbsp; post-training a 7B code reviewer
LoRA fine-tune of Qwen2.5-Coder-7B on 11,309 distilled reasoning traces. A blind three-vote judge
preferred it over the base model in **86% of 200** head-to-heads, with **632 records from 88
repositories** held out of training. Hallucinated identifiers halved by checking every identifier
the model named against the actual diff — a string match, not another model.

> **Read the RL arc.** Three runs regressed. I wrote the conclusion *"RL is dead for this task"* —
> then found five silent pipeline defects behind it: TRL's `GRPOConfig` left-truncating ~87% of
> prompts, and PEFT computing the KL reference with adapters disabled, anchoring to the base model
> instead of my SFT policy. The conclusion wasn't wrong so much as unearned. The re-run and the
> retraction are both in the repo.

#### [socratic-ot-tutor](https://github.com/deepanathanrajendiran-hub/socratic-ot-tutor) &nbsp;·&nbsp; Socratic tutor, shipped
Built for a graduate NLP course and used by **50 students** at UB. LangGraph over a Corrective RAG
pipeline that grades and reranks its own sources before answering. FastAPI + SSE on Cloud Run,
Next.js on Vercel. Cold start cut from ~4 min to ~20 s by baking weights into the image.

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
