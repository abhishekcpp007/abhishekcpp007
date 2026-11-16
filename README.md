# Abhishek Verma 👋

**AI Engineer in Gurugram, India · RL environments and LLM evaluation · Python, Docker, AWS**

🌐 **Website:** [abhishekcpp007.github.io](https://abhishekcpp007.github.io)

I build the environments that LLM coding agents train and get graded in, and then I try to
break my own grader. My day job is turning real merged GitHub pull requests into reproducible
Docker tasks with hidden tests, then checking that agents actually solve them instead of
gaming the scorer. I've shipped 2,000+ of these environments and 2,000+ agent trajectories
for SFT and RL post-training.

**The thing I keep finding:** a grader you haven't attacked is a grader you can't trust. When
I red-teamed my own, a stealth cheat policy scored 7/10 before I rebuilt the canary tests and
dropped it to 0/60. Details below.

I'm open to AI engineer, LLM eval and Python backend roles, remote or relocation.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-abhisekverma007-0A66C2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/abhisekverma007/)
[![LeetCode](https://img.shields.io/badge/LeetCode-akvikramaditya007cppcoder-FFA116?logo=leetcode&logoColor=black)](https://leetcode.com/u/akvikramaditya007cppcoder/)

---

## 🏗️ Gauntlet: leak-free RL environments from fresh GitHub PRs

My main open-source project, and the fastest way to see how I work. It mines PRs merged *after* a model's cutoff, rebuilds each repo at the base commit in Docker, and grades agents the way SWE-bench style benchmarks do. Then it tries hard to cheat its own grader.

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

I read the code of LLM eval and interpretability libraries I use, find real bugs, and send fixes with regression tests. Every one of these started as a bug I hit or spotted myself.

[![Merged PRs](https://img.shields.io/badge/merged_PRs-20-8957e5?logo=github)](https://github.com/pulls?q=is%3Apr+author%3Aabhishekcpp007+is%3Amerged+-user%3Aabhishekcpp007)
[![Issues](https://img.shields.io/badge/bug_reports-8-d29922?logo=github)](https://github.com/issues?q=is%3Aissue+author%3Aabhishekcpp007+-user%3Aabhishekcpp007)

| Project | ⭐ | PR | Status | What I fixed |
|---|---|---|---|---|
| [**virtualenv**](https://github.com/pypa/virtualenv) <br><sub>pypa</sub> | 5k | [#3514](https://github.com/pypa/virtualenv/pull/3514) | ![status](https://img.shields.io/github/pulls/detail/state/pypa/virtualenv/3514?label=) | The csh activator never unset `PYTHONHOME`, so the activated interpreter died with `No module named 'encodings'` before running anything |
| [**tox-uv**](https://github.com/tox-dev/tox-uv) <br><sub>tox-dev</sub> | 356 | [#418](https://github.com/tox-dev/tox-uv/pull/418) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/tox-uv/418?label=) | `system_site_packages` was missing from `python_cache`, so changing it never recreated the environment and the setting had no effect in either direction |
| [**pyproject-api**](https://github.com/tox-dev/pyproject-api) <br><sub>tox-dev</sub> | 25 | [#354](https://github.com/tox-dev/pyproject-api/pull/354) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/pyproject-api/354?label=) | `ensure_empty_dir` gated on `exists()`, which follows symlinks: a dangling link raised `FileExistsError` and a link to a directory emptied its target |
| [**SAELens**](https://github.com/decoderesearch/SAELens) <br><sub>decoderesearch</sub> | 1.6k | [#776](https://github.com/decoderesearch/SAELens/pull/776) | ![status](https://img.shields.io/github/pulls/detail/state/decoderesearch/SAELens/776?label=) | `random_firing_probabilities` built a fresh `torch.Generator()`, which starts from a fixed seed, so unseeded calls returned identical probabilities every time |
| [**delphi**](https://github.com/EleutherAI/delphi) <br><sub>EleutherAI</sub> | 280 | [#192](https://github.com/EleutherAI/delphi/pull/192) | ![status](https://img.shields.io/github/pulls/detail/state/EleutherAI/delphi/192?label=) | `split_quantiles` floored the per-quantile count, so 25 samples over 10 quantiles gave 20, and fewer samples than quantiles gave 0 with no warning |
| [**nnsight**](https://github.com/ndif-team/nnsight) <br><sub>ndif-team</sub> | 1.1k | [#800](https://github.com/ndif-team/nnsight/pull/800) | ![status](https://img.shields.io/github/pulls/detail/state/ndif-team/nnsight/800?label=) | Reassembling a multi-invoke `.skip()` lost the container type: namedtuple outputs raised `TypeError` and `ModelOutput`/`OrderedDict` came back as plain dicts |
| [**TransformerLens**](https://github.com/TransformerLensOrg/TransformerLens) <br><sub>TransformerLensOrg</sub> | 4k | [#1965](https://github.com/TransformerLensOrg/TransformerLens/pull/1965) | ![status](https://img.shields.io/github/pulls/detail/state/TransformerLensOrg/TransformerLens/1965?label=) | Eval helpers hardcoded `"cuda"`, which crashed on CPU and Apple MPS machines |
| [**filelock**](https://github.com/tox-dev/filelock) <br><sub>tox-dev</sub> | 986 | [#908](https://github.com/tox-dev/filelock/pull/908) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/filelock/908?label=) | Read-write locks took `blocking=0` as blocking and waited the full timeout |
| [**platformdirs**](https://github.com/tox-dev/platformdirs) <br><sub>tox-dev</sub> | 1.0k | [#686](https://github.com/tox-dev/platformdirs/pull/686) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/platformdirs/686?label=) | Media and fonts functions couldn't take `use_site_for_root` like their properties |
| [**TransformerLens**](https://github.com/TransformerLensOrg/TransformerLens) <br><sub>TransformerLensOrg</sub> | 4k | [#1976](https://github.com/TransformerLensOrg/TransformerLens/pull/1976) | ![status](https://img.shields.io/github/pulls/detail/state/TransformerLensOrg/TransformerLens/1976?label=) | `stack_head_results` silently returned the wrong residual stream for a negative layer, unlike its neuron sibling |
| [**more-itertools**](https://github.com/more-itertools/more-itertools) <br><sub>more-itertools</sub> | 4.1k | [#1346](https://github.com/more-itertools/more-itertools/pull/1346) | ![status](https://img.shields.io/github/pulls/detail/state/more-itertools/more-itertools/1346?label=) | Type stubs for `concurrent_tee` and `serialize` disagreed with the runtime code |
| [**tox**](https://github.com/tox-dev/tox) <br><sub>tox-dev</sub> | 4k | [#4371](https://github.com/tox-dev/tox/pull/4371) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/tox/4371?label=) | A `re.VERBOSE` regex dropped a literal space, so commented-out PEP 723 lines were read as live metadata |
| [**TransformerLens**](https://github.com/TransformerLensOrg/TransformerLens) <br><sub>TransformerLensOrg</sub> | 4.1k | [#2012](https://github.com/TransformerLensOrg/TransformerLens/pull/2012) | ![status](https://img.shields.io/github/pulls/detail/state/TransformerLensOrg/TransformerLens/2012?label=) | `sample_logits` checked `top_k` and `top_p` only in the sampling branch, so greedy calls accepted any value |
| [**pytest-randomly**](https://github.com/pytest-dev/pytest-randomly) <br><sub>pytest-dev</sub> | 724 | [#755](https://github.com/pytest-dev/pytest-randomly/pull/755) | ![status](https://img.shields.io/github/pulls/detail/state/pytest-dev/pytest-randomly/755?label=) | xdist workers re-read the cache for `--randomly-seed=last`, so with `--cache-clear` each got its own seed and collection crashed |
| [**mdit-py-plugins**](https://github.com/executablebooks/mdit-py-plugins) <br><sub>executablebooks</sub> | 50 | [#172](https://github.com/executablebooks/mdit-py-plugins/pull/172) | ![status](https://img.shields.io/github/pulls/detail/state/executablebooks/mdit-py-plugins/172?label=) | A tab after `[ ]` counted as a task but dropped the checkbox, and `label_after` leaked raw `id=` text |
| [**flake8-bugbear**](https://github.com/PyCQA/flake8-bugbear) <br><sub>PyCQA</sub> | 1.1k | [#633](https://github.com/PyCQA/flake8-bugbear/pull/633) | ![status](https://img.shields.io/github/pulls/detail/state/PyCQA/flake8-bugbear/633?label=) | B021 never ran on `async def`, so f-string docstrings there were missed |
| [**wcmatch**](https://github.com/facelessuser/wcmatch) <br><sub>facelessuser</sub> | 169 | [#280](https://github.com/facelessuser/wcmatch/pull/280) | ![status](https://img.shields.io/github/pulls/detail/state/facelessuser/wcmatch/280?label=) | With `MINUSNEGATE`, an exclusion like `-~/*.py` never expanded `~`, so it excluded nothing |
| [**hist**](https://github.com/scikit-hep/hist) <br><sub>scikit-hep</sub> | 140 | [#766](https://github.com/scikit-hep/hist/pull/766) | ![status](https://img.shields.io/github/pulls/detail/state/scikit-hep/hist/766?label=) | `ChunkedHist.to_hist()` set category labels to the axis name, so adding the result to its source raised `axes not mergable` |
| [**bracex**](https://github.com/facelessuser/bracex) <br><sub>facelessuser</sub> | 33 | [#64](https://github.com/facelessuser/bracex/pull/64) | ![status](https://img.shields.io/github/pulls/detail/state/facelessuser/bracex/64?label=) | Ranges whose span overflows int64 were expanded, where Bash 5.3 keeps them literal |
| [**parse**](https://github.com/r1chardj0n3s/parse) <br><sub>r1chardj0n3s</sub> | 1.8k | [#286](https://github.com/r1chardj0n3s/parse/pull/286) | ![status](https://img.shields.io/github/pulls/detail/state/r1chardj0n3s/parse/286?label=) | The `e` and `g` types rejected `+nan` and `" inf"`, which `str.format()` itself writes |

**Bug reports**
- [langchain-ai/deepagents#7477](https://github.com/langchain-ai/deepagents/issues/7477): `execute` timeout leaves the command's child processes running (fix ready on my fork)
- [langchain-ai/deepagents#7478](https://github.com/langchain-ai/deepagents/issues/7478): `FilesystemBackend` writes truncate in place, so a crash mid-write destroys the file
- [langchain-ai/deepagents#7479](https://github.com/langchain-ai/deepagents/issues/7479): `langchain-google-genai` is a required dependency but never imported
- [huggingface/lighteval#1464](https://github.com/huggingface/lighteval/issues/1464): LCB grader fails correct solutions that write via `sys.stdout.buffer`

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
