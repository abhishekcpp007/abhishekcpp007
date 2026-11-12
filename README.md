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
[![Email](https://img.shields.io/badge/Email-abhishek1pw%40gmail.com-D14836?logo=gmail&logoColor=white)](mailto:abhishek1pw@gmail.com)
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

[![Merged PRs](https://img.shields.io/badge/merged_PRs-15-8957e5?logo=github)](https://github.com/pulls?q=is%3Apr+author%3Aabhishekcpp007+is%3Amerged+-user%3Aabhishekcpp007)
[![Open PRs](https://img.shields.io/badge/in_review-30-1f6feb?logo=github)](https://github.com/pulls?q=is%3Apr+author%3Aabhishekcpp007+is%3Aopen+-user%3Aabhishekcpp007)
[![Issues](https://img.shields.io/badge/bug_reports-8-d29922?logo=github)](https://github.com/issues?q=is%3Aissue+author%3Aabhishekcpp007+-user%3Aabhishekcpp007)

| Project | ⭐ | PR | Status | What I fixed |
|---|---|---|---|---|
| [**virtualenv**](https://github.com/pypa/virtualenv) <br><sub>pypa</sub> | 5k | [#3514](https://github.com/pypa/virtualenv/pull/3514) | ![status](https://img.shields.io/github/pulls/detail/state/pypa/virtualenv/3514?label=) | The csh activator never unset `PYTHONHOME`, so the activated interpreter died with `No module named 'encodings'` before running anything |
| [**tox-uv**](https://github.com/tox-dev/tox-uv) <br><sub>tox-dev</sub> | 356 | [#418](https://github.com/tox-dev/tox-uv/pull/418) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/tox-uv/418?label=) | `system_site_packages` was missing from `python_cache`, so changing it never recreated the environment and the setting had no effect in either direction |
| [**tox**](https://github.com/tox-dev/tox) <br><sub>tox-dev</sub> | 4k | [#4393](https://github.com/tox-dev/tox/pull/4393) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/tox/4393?label=) | The same stale-environment gap upstream in `VirtualEnv.python_cache`, found while checking whether the tox-uv one was plugin specific |
| [**pyproject-api**](https://github.com/tox-dev/pyproject-api) <br><sub>tox-dev</sub> | 25 | [#354](https://github.com/tox-dev/pyproject-api/pull/354) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/pyproject-api/354?label=) | `ensure_empty_dir` gated on `exists()`, which follows symlinks: a dangling link raised `FileExistsError` and a link to a directory emptied its target |
| [**SAELens**](https://github.com/decoderesearch/SAELens) <br><sub>decoderesearch</sub> | 1.6k | [#776](https://github.com/decoderesearch/SAELens/pull/776) | ![status](https://img.shields.io/github/pulls/detail/state/decoderesearch/SAELens/776?label=) | `random_firing_probabilities` built a fresh `torch.Generator()`, which starts from a fixed seed, so unseeded calls returned identical probabilities every time |
| [**delphi**](https://github.com/EleutherAI/delphi) <br><sub>EleutherAI</sub> | 280 | [#192](https://github.com/EleutherAI/delphi/pull/192) | ![status](https://img.shields.io/github/pulls/detail/state/EleutherAI/delphi/192?label=) | `split_quantiles` floored the per-quantile count, so 25 samples over 10 quantiles gave 20, and fewer samples than quantiles gave 0 with no warning |
| [**nnsight**](https://github.com/ndif-team/nnsight) <br><sub>ndif-team</sub> | 1.1k | [#800](https://github.com/ndif-team/nnsight/pull/800) | ![status](https://img.shields.io/github/pulls/detail/state/ndif-team/nnsight/800?label=) | Reassembling a multi-invoke `.skip()` lost the container type: namedtuple outputs raised `TypeError` and `ModelOutput`/`OrderedDict` came back as plain dicts |
| [**TransformerLens**](https://github.com/TransformerLensOrg/TransformerLens) <br><sub>TransformerLensOrg</sub> | 4k | [#1965](https://github.com/TransformerLensOrg/TransformerLens/pull/1965) | ![status](https://img.shields.io/github/pulls/detail/state/TransformerLensOrg/TransformerLens/1965?label=) | Eval helpers hardcoded `"cuda"`, which crashed on CPU and Apple MPS machines |
| [**lighteval**](https://github.com/huggingface/lighteval) <br><sub>huggingface</sub> | 2.6k | [#1465](https://github.com/huggingface/lighteval/pull/1465) | ![status](https://img.shields.io/github/pulls/detail/state/huggingface/lighteval/1465?label=) | The LiveCodeBench sandbox's fake stdout had no binary buffer, so correct solutions were graded as wrong |
| [**sparsify**](https://github.com/EleutherAI/sparsify) <br><sub>EleutherAI</sub> | 740 | [#146](https://github.com/EleutherAI/sparsify/pull/146) | ![status](https://img.shields.io/github/pulls/detail/state/EleutherAI/sparsify/146?label=) | `handle_arg_string` used `str.isnumeric()`, so `-5` silently became `-5.0` and Unicode numerals like `½` crashed |
| [**pluggy**](https://github.com/pytest-dev/pluggy) <br><sub>pytest-dev</sub> | 1.7k | [#827](https://github.com/pytest-dev/pluggy/pull/827) | ![status](https://img.shields.io/github/pulls/detail/state/pytest-dev/pluggy/827?label=) | A 1.7.0 regression let `subset_hook_caller` call plugins it was told to exclude |
| [**filelock**](https://github.com/tox-dev/filelock) <br><sub>tox-dev</sub> | 986 | [#908](https://github.com/tox-dev/filelock/pull/908) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/filelock/908?label=) | Read-write locks took `blocking=0` as blocking and waited the full timeout |
| [**Gymnasium-Robotics**](https://github.com/Farama-Foundation/Gymnasium-Robotics) <br><sub>Farama</sub> | 2.0k | [#362](https://github.com/Farama-Foundation/Gymnasium-Robotics/pull/362) | ![status](https://img.shields.io/github/pulls/detail/state/Farama-Foundation/Gymnasium-Robotics/362?label=) | `get_joint_qvel` read 4 velocities for a MuJoCo ball joint instead of 3 |
| [**Shimmy**](https://github.com/Farama-Foundation/Shimmy) <br><sub>Farama</sub> | 932 | [#169](https://github.com/Farama-Foundation/Shimmy/pull/169) | ![status](https://img.shields.io/github/pulls/detail/state/Farama-Foundation/Shimmy/169?label=) | OpenSpiel `reset()` dropped a game's parameters, crashing or silently changing the game |
| [**platformdirs**](https://github.com/tox-dev/platformdirs) <br><sub>tox-dev</sub> | 1.0k | [#686](https://github.com/tox-dev/platformdirs/pull/686) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/platformdirs/686?label=) | Media and fonts functions couldn't take `use_site_for_root` like their properties |
| [**TransformerLens**](https://github.com/TransformerLensOrg/TransformerLens) <br><sub>TransformerLensOrg</sub> | 4k | [#1976](https://github.com/TransformerLensOrg/TransformerLens/pull/1976) | ![status](https://img.shields.io/github/pulls/detail/state/TransformerLensOrg/TransformerLens/1976?label=) | `stack_head_results` silently returned the wrong residual stream for a negative layer, unlike its neuron sibling |
| [**Minigrid**](https://github.com/Farama-Foundation/Minigrid) <br><sub>Farama</sub> | 2.5k | [#551](https://github.com/Farama-Foundation/Minigrid/pull/551) | ![status](https://img.shields.io/github/pulls/detail/state/Farama-Foundation/Minigrid/551?label=) | `MissionSpace` rejected valid missions when two placeholders shared exactly one character |
| [**PettingZoo**](https://github.com/Farama-Foundation/PettingZoo) <br><sub>Farama</sub> | 3.5k | [#1538](https://github.com/Farama-Foundation/PettingZoo/pull/1538) | ![status](https://img.shields.io/github/pulls/detail/state/Farama-Foundation/PettingZoo/1538?label=) | Random rollout helpers ignored an action mask passed in `info` and took illegal actions |
| [**MO-Gymnasium**](https://github.com/Farama-Foundation/MO-Gymnasium) <br><sub>Farama</sub> | 1.2k | [#172](https://github.com/Farama-Foundation/MO-Gymnasium/pull/172) | ![status](https://img.shields.io/github/pulls/detail/state/Farama-Foundation/MO-Gymnasium/172?label=) | `breakable-bottles` returned rewards and observations outside its declared spaces |
| [**more-itertools**](https://github.com/more-itertools/more-itertools) <br><sub>more-itertools</sub> | 4.1k | [#1346](https://github.com/more-itertools/more-itertools/pull/1346) | ![status](https://img.shields.io/github/pulls/detail/state/more-itertools/more-itertools/1346?label=) | Type stubs for `concurrent_tee` and `serialize` disagreed with the runtime code |
| [**tox**](https://github.com/tox-dev/tox) <br><sub>tox-dev</sub> | 4k | [#4371](https://github.com/tox-dev/tox/pull/4371) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/tox/4371?label=) | A `re.VERBOSE` regex dropped a literal space, so commented-out PEP 723 lines were read as live metadata |
| [**SWE-bench**](https://github.com/SWE-bench/SWE-bench) <br><sub>SWE-bench</sub> | 6.1k | [#711](https://github.com/SWE-bench/SWE-bench/pull/711) | ![status](https://img.shields.io/github/pulls/detail/state/SWE-bench/SWE-bench/711?label=) | A bare `FAIL:` line crashed the Django log parser and killed grading for that instance |
| [**Gymnasium**](https://github.com/Farama-Foundation/Gymnasium) <br><sub>Farama</sub> | 12.8k | [#1827](https://github.com/Farama-Foundation/Gymnasium/pull/1827) | ![status](https://img.shields.io/github/pulls/detail/state/Farama-Foundation/Gymnasium/1827?label=) | `MaxAndSkipObservation` returned the previous step's frames when an episode ended mid-skip |
| [**circuit-tracer**](https://github.com/decoderesearch/circuit-tracer) <br><sub>decoderesearch</sub> | 2.9k | [#124](https://github.com/decoderesearch/circuit-tracer/pull/124) | ![status](https://img.shields.io/github/pulls/detail/state/decoderesearch/circuit-tracer/124?label=) | A bare `squeeze()` broke single-token prompts and let real batches through unchecked |
| [**BrowserGym**](https://github.com/ServiceNow/BrowserGym) <br><sub>ServiceNow</sub> | 1.4k | [#421](https://github.com/ServiceNow/BrowserGym/pull/421) | ![status](https://img.shields.io/github/pulls/detail/state/ServiceNow/BrowserGym/421?label=) | `hide_bid_if_invisible` crashed with an AttributeError instead of the clear error its sibling flags give |
| [**pytest-mock**](https://github.com/pytest-dev/pytest-mock) <br><sub>pytest-dev</sub> | 2.0k | [#661](https://github.com/pytest-dev/pytest-mock/pull/661) | ![status](https://img.shields.io/github/pulls/detail/state/pytest-dev/pytest-mock/661?label=) | `mocker.spy()` on an inherited `classmethod`/`staticmethod` raised `TypeError` when called through an instance, a regression since 3.13.0 |
| [**TransformerLens**](https://github.com/TransformerLensOrg/TransformerLens) <br><sub>TransformerLensOrg</sub> | 4.1k | [#2012](https://github.com/TransformerLensOrg/TransformerLens/pull/2012) | ![status](https://img.shields.io/github/pulls/detail/state/TransformerLensOrg/TransformerLens/2012?label=) | `sample_logits` checked `top_k` and `top_p` only in the sampling branch, so greedy calls accepted any value |
| [**MOMAland**](https://github.com/Farama-Foundation/MOMAland) <br><sub>Farama</sub> | 381 | [#111](https://github.com/Farama-Foundation/MOMAland/pull/111) | ![status](https://img.shields.io/github/pulls/detail/state/Farama-Foundation/MOMAland/111?label=) | `RecordEpisodeStatistics` raised `KeyError` once one agent finished early, and lost the episode entry on a mixed ending |
| [**MOMAland**](https://github.com/Farama-Foundation/MOMAland) <br><sub>Farama</sub> | 381 | [#112](https://github.com/Farama-Foundation/MOMAland/pull/112) | ![status](https://img.shields.io/github/pulls/detail/state/Farama-Foundation/MOMAland/112?label=) | The AEC wrappers module imported `RunningMeanStd` from a gymnasium path that no longer exists, so it never imported |
| [**SuperSuit**](https://github.com/Farama-Foundation/SuperSuit) <br><sub>Farama</sub> | 495 | [#276](https://github.com/Farama-Foundation/SuperSuit/pull/276) | ![status](https://img.shields.io/github/pulls/detail/state/Farama-Foundation/SuperSuit/276?label=) | Wrappers took out-of-range arguments and failed later inside the library; `frame_stack_v2` asserted an f-string, which is always true |
| [**pytest-randomly**](https://github.com/pytest-dev/pytest-randomly) <br><sub>pytest-dev</sub> | 724 | [#755](https://github.com/pytest-dev/pytest-randomly/pull/755) | ![status](https://img.shields.io/github/pulls/detail/state/pytest-dev/pytest-randomly/755?label=) | xdist workers re-read the cache for `--randomly-seed=last`, so with `--cache-clear` each got its own seed and collection crashed |
| [**sphinx-autodoc-typehints**](https://github.com/tox-dev/sphinx-autodoc-typehints) <br><sub>tox-dev</sub> | 588 | [#1124](https://github.com/tox-dev/sphinx-autodoc-typehints/pull/1124) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/sphinx-autodoc-typehints/1124?label=) | A parameter named `lambda_` lost the type its docstring gave it: the `:param` line was renamed to escape the underscore but its `:type` twin was not, so the lookup missed |
| [**pipdeptree**](https://github.com/tox-dev/pipdeptree) <br><sub>tox-dev</sub> | 3.0k | [#882](https://github.com/tox-dev/pipdeptree/pull/882) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/pipdeptree/882?label=) | Graphviz output with `--reverse --depth` drew every edge out of a missing requirement regardless of the limit, and packages below it came out as bare unlabeled nodes |
| [**mdit-py-plugins**](https://github.com/executablebooks/mdit-py-plugins) <br><sub>executablebooks</sub> | 50 | [#172](https://github.com/executablebooks/mdit-py-plugins/pull/172) | ![status](https://img.shields.io/github/pulls/detail/state/executablebooks/mdit-py-plugins/172?label=) | A tab after `[ ]` counted as a task but dropped the checkbox, and `label_after` leaked raw `id=` text |
| [**pyproject-hooks**](https://github.com/pypa/pyproject-hooks) <br><sub>pypa</sub> | 131 | [#247](https://github.com/pypa/pyproject-hooks/pull/247) | ![status](https://img.shields.io/github/pulls/detail/state/pypa/pyproject-hooks/247?label=) | `build-backend = "mod:obj"` with a missing object gave a bare `CalledProcessError`, not `BackendUnavailable` |
| [**pytest-timeout**](https://github.com/pytest-dev/pytest-timeout) <br><sub>pytest-dev</sub> | 261 | [#220](https://github.com/pytest-dev/pytest-timeout/pull/220) | ![status](https://img.shields.io/github/pulls/detail/state/pytest-dev/pytest-timeout/220?label=) | after one pdb stop, no later test in the session could time out |
| [**readme_renderer**](https://github.com/pypa/readme_renderer) <br><sub>pypa</sub> | 176 | [#392](https://github.com/pypa/readme_renderer/pull/392) | ![status](https://img.shields.io/github/pulls/detail/state/pypa/readme_renderer/392?label=) | spanning header cells lost `colspan`/`rowspan`, so those tables broke on PyPI |
| [**sphinx-argparse-cli**](https://github.com/tox-dev/sphinx-argparse-cli) <br><sub>tox-dev</sub> | 28 | [#405](https://github.com/tox-dev/sphinx-argparse-cli/pull/405) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/sphinx-argparse-cli/405?label=) | help using `%(default)s` showed the default value twice |
| [**markdown-it-py**](https://github.com/executablebooks/markdown-it-py) <br><sub>executablebooks</sub> | 1.4k | [#468](https://github.com/executablebooks/markdown-it-py/pull/468) | ![status](https://img.shields.io/github/pulls/detail/state/executablebooks/markdown-it-py/468?label=) | a backslash before a space in a link destination broke the whole link, against CommonMark |
| [**MyST-Parser**](https://github.com/executablebooks/MyST-Parser) <br><sub>executablebooks</sub> | 902 | [#1230](https://github.com/executablebooks/MyST-Parser/pull/1230) | ![status](https://img.shields.io/github/pulls/detail/state/executablebooks/MyST-Parser/1230?label=) | `and` instead of `or` let bad `url_schemes` classes through, crashing the build later |
| [**pyproject-metadata**](https://github.com/pypa/pyproject-metadata) <br><sub>pypa</sub> | 44 | [#352](https://github.com/pypa/pyproject-metadata/pull/352) | ![status](https://img.shields.io/github/pulls/detail/state/pypa/pyproject-metadata/352?label=) | `License-File` leaked the absolute build path into METADATA on 2.4+ |
| [**sphinx-autobuild**](https://github.com/sphinx-doc/sphinx-autobuild) <br><sub>sphinx-doc</sub> | 612 | [#218](https://github.com/sphinx-doc/sphinx-autobuild/pull/218) | ![status](https://img.shields.io/github/pulls/detail/state/sphinx-doc/sphinx-autobuild/218?label=) | reload script spliced into 206 Range responses, corrupting partial downloads |
| [**flake8-bugbear**](https://github.com/PyCQA/flake8-bugbear) <br><sub>PyCQA</sub> | 1.1k | [#633](https://github.com/PyCQA/flake8-bugbear/pull/633) | ![status](https://img.shields.io/github/pulls/detail/state/PyCQA/flake8-bugbear/633?label=) | B021 never ran on `async def`, so f-string docstrings there were missed |
| [**nox**](https://github.com/wntrblm/nox) <br><sub>wntrblm</sub> | 1.6k | [#1234](https://github.com/wntrblm/nox/pull/1234) | ![status](https://img.shields.io/github/pulls/detail/state/wntrblm/nox/1234?label=) | `--report` crashed on `Path` parametrize values; under `-j` passing sessions showed as failed |
| [**sphinx-design**](https://github.com/executablebooks/sphinx-design) <br><sub>executablebooks</sub> | 231 | [#318](https://github.com/executablebooks/sphinx-design/pull/318) | ![status](https://img.shields.io/github/pulls/detail/state/executablebooks/sphinx-design/318?label=) | `tab-set-code` silently dropped code blocks with a `:caption:` |

**Bug reports**
- [langchain-ai/deepagents#7477](https://github.com/langchain-ai/deepagents/issues/7477): `execute` timeout leaves the command's child processes running (fix ready on my fork)
- [langchain-ai/deepagents#7478](https://github.com/langchain-ai/deepagents/issues/7478): `FilesystemBackend` writes truncate in place, so a crash mid-write destroys the file
- [langchain-ai/deepagents#7479](https://github.com/langchain-ai/deepagents/issues/7479): `langchain-google-genai` is a required dependency but never imported
- [huggingface/lighteval#1464](https://github.com/huggingface/lighteval/issues/1464): LCB grader fails correct solutions that write via `sys.stdout.buffer`

---

## 📚 Books I wrote

Three free textbooks with measured experiments and runnable projects:

- [**FastAPI: Basics to Production**](https://github.com/abhishekcpp007/fastapi-book): 745 pages, 7 projects up to a deployed microservice
- [**Machine Learning and RL Environments**](https://github.com/abhishekcpp007/ml-rl-envs-book): 594 pages, from transformers and DPO to PPO and Docker coding envs
- [**Data Engineering and Agentic AI Evaluation**](https://github.com/abhishekcpp007/de-agentic-eval-book): 634 pages, from CDC and Spark to pass@k, LLM judges and reward-hacking checks

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
