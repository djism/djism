<p align="center">
  <img src="assets/terminal.svg" width="100%" alt="Terminal: I build systems, then I try to break them. Shardis chaos test: failover 3.1s median, 0 client errors across 1.2M operations, 0 of 2.1M acknowledged writes lost on kill -9." />
</p>

<img align="right" src="assets/avatar.svg" width="230" alt="Animated avatar of Dhananjay coding at his desk" />

### Hi, I'm Dhananjay 👋

I'm a software engineer with 5+ years of shipping production software. Lately I build systems from scratch, then spend just as long trying to break them.

**If a number on this page looks good, there's a test behind it that tried to make it look bad.**

📍 New Jersey · open to NYC and SF<br>
🌐 [Portfolio](https://djism.github.io/) · [LinkedIn](https://www.linkedin.com/in/dsharma2496/) · [Email](mailto:dhananjay.ism24@gmail.com)

<br clear="right"/>

<p align="center">
  <img src="assets/status.svg" width="100%" alt="Project status: Shardis healthy, Atlas localized, Behavision building" />
</p>

## 🔧 What I'm building

### [Shardis](https://djism.github.io/shardis/) · a Redis Cluster compatible distributed store, written in Go
Sharding, replication, gossip-based failure detection, automatic failover, and an append-only log. Unmodified `redis-cli` and `go-redis` clients work against it. Then I attacked it with 7 chaos scenarios.

| What I tested | Result |
|---|---|
| **Failover** | 3.1s median, 0 client errors across 1.2M operations |
| **Durability** | `kill -9` lost 0 of 2.1M acknowledged writes |
| **Throughput** | 1.46M SET/s pipelined, 45% above Redis 8.10 on the same machine |
| **The honest part** | ~3x Redis's memory per key, and 9% slower without pipelining |

<sub>[code](https://github.com/djism/shardis) · [project site](https://djism.github.io/shardis/)</sub>

### [Atlas](https://djism.github.io/atlas/) · LiDAR localization and odometry, in C++17 with zero external libraries
ICP scan matching, scan-to-map localization, and 3D odometry on the KITTI driving dataset, all written from scratch.

| What I tested | Result |
|---|---|
| **Accuracy** | 3 to 11mm worst-case error, vs 2 to 19cm for scan-to-scan tracking, across 5 seeds |
| **KITTI 3D** | 3.7 to 5.2cm median per-frame error (a first baseline) |
| **Hardest bug** | a localization runaway that failed 40 of 40 runs under CPU throttling, now 0 of 40 |
| **The honest part** | my best single result (3.4cm) was the best of 20 seeds, so I report the range |

<sub>[code](https://github.com/djism/atlas) · [project site](https://djism.github.io/atlas/)</sub>

### [Behavision](https://github.com/djism/behavision) · computer vision for animal behavior videos · 🚧 in progress
SAM2 and Grounding DINO tracking across 36k frames, plus an MCP agent running a local Qwen3 model through Ollama.

## 🐛 Bugs I'm proud of finding

Good numbers are easy. These are the ones that taught me something.

- **Blind retries doubled 32 of 32 in-flight `INCR`s.** Now the client only retries commands that are safe to repeat.
- **"0 errors" isn't "0 data loss."** A consistency checker I wrote flagged 2,029 rolled-back writes during failover testing.
- **Async replication lost 4 of 2.4M writes** when a primary crashed. I measured it instead of assuming, and `WAIT` brings it to 0.
- **A 0.37° sensor tilt moved a trajectory by 2.5m.** Small angles are not small.
- **413 automated checks in CI** caught 2 bugs in Atlas before they shipped.

## 🏢 Before all this

- **RegArt** · Software Engineer (Amsterdam, remote). Owned core subsystems of a compliance platform used by HSBC, EY, and Rabobank, serving 400K to 500K API requests a day at 99.9% uptime. Shipped LLM search that only answers from cited sources.
- **Stony Brook University** · Graduate Research Assistant. GPU deep learning pipelines on HPC (10TB of data, 40+ concurrent jobs). Co-author on a Nature manuscript.
- **CGI** · Software Engineer. Built features for an FX derivatives trading portal in Java, C++, and Angular.

## 🧰 Toolbox

**Systems** `Go` `C++17` `Java` · `Kubernetes` `Docker` `Prometheus` `Grafana`<br>
**Backend** `Python` `TypeScript` `Node.js` `FastAPI` · `MongoDB` `PostgreSQL` `Redis` `Kafka`<br>
**ML** `PyTorch` `Hugging Face` `LangGraph` `MLflow` · `RAG` `LLM evals`

<details>
<summary><b>📦 More projects</b></summary>
<br>

- [**FinSight**](https://github.com/djism/finsight) · multi-agent LangGraph pipeline that writes investment memos from SEC filings, with a Critic agent that flags hallucinated claims
- [**NeuroAssist**](https://github.com/djism/neuroassist) · GraphRAG assistant (RAGAS faithfulness 0.9 to 1.0) with golden-set evals that block bad deploys
- [**LLMOps Pipeline**](https://github.com/djism/llmops-pipeline) · QLoRA fine-tuning of Phi-3-mini with MLflow eval gates, published to Hugging Face

</details>

## 📡 Right now

- 🔨 Building Behavision
- 📖 Learning how the infrastructure under AI agents actually works, and reading papers to keep up
- 💼 **Open to software engineering roles in NYC and SF.** [Say hi](mailto:dhananjay.ism24@gmail.com).
