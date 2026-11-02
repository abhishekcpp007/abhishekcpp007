# Hi, I'm Abhishek 👋

**AI Engineer · RL environments and LLM evaluation · Python, Docker, AWS**

I build the environments that LLM coding agents train and get graded in. My day job is turning real merged GitHub pull requests into reproducible Docker tasks with hidden tests, then checking that agents actually solve them instead of gaming the grader. I've shipped 2,000+ of these environments and 2,000+ agent trajectories for SFT and RL post-training.

I'm open to AI engineer, LLM eval and Python backend roles, remote or relocation.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-abhisekverma007-0A66C2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/abhisekverma007/)
[![Email](https://img.shields.io/badge/Email-abhishek1pw%40gmail.com-D14836?logo=gmail&logoColor=white)](mailto:abhishek1pw@gmail.com)
[![LeetCode](https://img.shields.io/badge/LeetCode-akvikramaditya007cppcoder-FFA116?logo=leetcode&logoColor=black)](https://leetcode.com/u/akvikramaditya007cppcoder/)

---

## 🏗️ Gauntlet: leak-free RL environments from fresh GitHub PRs

My main open-source project. It mines PRs merged *after* a model's cutoff, rebuilds each repo at the base commit in Docker, and grades agents the way SWE-bench style benchmarks do. Then it tries hard to cheat its own grader.

| Repo | What it does |
|---|---|
| [**gauntlet-harness**](https://github.com/abhishekcpp007/gauntlet-harness) | The core. PR mining, 3-run F2P/N2P/S2P/P2P test classification, an 8-check leak scan, rubric judging, a Gymnasium env (`gauntlet/SWE-v0`) and exports for SWE-bench, SFT, GRPO and DPO |
| [**gauntlet-cheatcatcher**](https://github.com/abhishekcpp007/gauntlet-cheatcatcher) | 11 reward-hacking rules that flag test tampering, conftest tricks and hardcoded outputs |
| [**gauntlet-repo2env**](https://github.com/abhishekcpp007/gauntlet-repo2env) | Turns a repo into env images and SWE-style tasks, with grading hardened against test edits |
| [**gauntlet-sandbox**](https://github.com/abhishekcpp007/gauntlet-sandbox) | Docker sandboxes that record every agent step as a trajectory |
| [**gauntlet-timemachine**](https://github.com/abhishekcpp007/gauntlet-timemachine) | Replay, branch and diff trajectories, plus an HTML viewer |
| [**gauntlet-arena**](https://github.com/abhishekcpp007/gauntlet-arena) | FastAPI app where a human and an AI agent race on the same task, with a leaderboard |
| [**gauntlet**](https://github.com/abhishekcpp007/gauntlet) | Umbrella repo. One `docker compose up` runs the whole thing |

**Gauntlet Live (Nov 2026):** 53 verified tasks out of 186 PRs across 10 repos. The oracle solves 53/53 and the cheater policies get caught 53/53. Red-teaming my own grader found a "stealth" cheat that scored 7/10, so I rebuilt the canary tests until it dropped to 0/60. CI runs a nightly calibration on random tasks.

---

## 🤝 Open-source contributions

Bugs I found and fixed myself, mostly in LLM eval and interpretability libraries.

**Merged**
- [decoderesearch/SAELens#776](https://github.com/decoderesearch/SAELens/pull/776): draw fresh firing probabilities when no seed is given
- [EleutherAI/delphi#192](https://github.com/EleutherAI/delphi/pull/192): spread the quantile sample remainder instead of dropping it
- [ndif-team/nnsight#800](https://github.com/ndif-team/nnsight/pull/800): rebuild a batched skip's output as its own container type

**In review**
- [TransformerLensOrg/TransformerLens#1965](https://github.com/TransformerLensOrg/TransformerLens/pull/1965): run the eval helpers on the model's own device instead of a hardcoded `"cuda"`
- [huggingface/lighteval#1465](https://github.com/huggingface/lighteval/pull/1465): give the LiveCodeBench sandbox's fake stdout a binary buffer, so correct solutions stop failing
- [EleutherAI/sparsify#146](https://github.com/EleutherAI/sparsify/pull/146): let `int()` decide what an int is when parsing CLI args

**Issues filed:** [langchain-ai/deepagents](https://github.com/langchain-ai/deepagents) #7472 (timeout leaves orphan processes), #7474 (non-atomic file writes), #7475 (unused required dependency)

---

## 🧰 Tech I use

**Daily:** Python · Docker · pytest · Git · AWS (ECR, S3, Lambda, Glue) · Linux · GitHub Actions

**LLM and RL:** Claude, GPT and GLM APIs · LLM-as-judge · Hugging Face · PyTorch · Terminal-Bench / Harbor · Multi-SWE-bench · LangChain

**Backend and data:** FastAPI · PostgreSQL · Redis · SQL · Snowflake · ETL pipelines

---

## 💼 Experience

- **Ethara AI** (via Quess Corp) · Software Engineer, RL Environments and Evaluation · 2026 to now
- **NavAdr Technologies** · Software Engineer (Data) · 2025 to 2026. Python ETL into Snowflake, 200K+ records a day
- **GlobalLogic** · Associate Analyst · 2024 to 2025. CI/CD with Docker and GitHub Actions on AWS

---

## 🎮 Side projects

- [**quizbuzz-night**](https://github.com/abhishekcpp007/quizbuzz-night): live multiplayer trivia buzzer. 2 to 8 players join from their phones with a room code, no login
- [**neetcode-submissions**](https://github.com/abhishekcpp007/neetcode-submissions): my DSA practice in Python
