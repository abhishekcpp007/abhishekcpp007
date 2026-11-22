# Abhishek Verma

**AI Engineer in Gurugram, India. RL environments and LLM evaluation.**

Website: [abhishekcpp007.github.io](https://abhishekcpp007.github.io)

I build the test environments that AI coding agents are trained and graded in. Since January 2026
at Ethara AI I've authored 2,000+ of them from real merged GitHub pull requests, plus 203 harness
configs across 15 open source projects. Outside work, 32 of my pull requests are merged in 28 open
source projects.

I'm open to AI engineer, LLM evaluation, RL environment and Python backend roles. Remote, or with
relocation.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-abhisekverma007-0A66C2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/abhisekverma007/)
[![LeetCode](https://img.shields.io/badge/LeetCode-akvikramaditya007cppcoder-FFA116?logo=leetcode&logoColor=black)](https://leetcode.com/u/akvikramaditya007cppcoder/)

---

## Gauntlet

My main open source project: [**gauntlet-bench**](https://github.com/abhishekcpp007/gauntlet-bench). It turns freshly
merged pull requests into sandboxed, leak-checked coding tasks, then grades every run with a grader I
attacked on purpose.

- **Task sets:** 147 tasks from 26 repos, built from freshly merged pull requests. The real fix passes 146.
- **Red team:** I wrote nine cheating agents against my own grader. Across 899 cheat runs on the shipped tasks, none solved a task or scored above 0.
- **Cheat detector:** 11 static rules, with no cheating verdict on any of the 147 real merged fixes.
- **Every night:** the cheats run again on 4 random tasks, and the build fails if one scores above 0.

## rag-harness

[**rag-harness**](https://github.com/abhishekcpp007/rag-harness) is a retrieval service and the harness that grades it: 42 labelled questions across 11 retrieval configurations. Bootstrap intervals took several of my own findings away, and the README says so.

---

## Open source

32 pull requests merged across 28 upstream projects. Each one is a bug I found by running the
library and fixed with a regression test.

[![Merged PRs](https://img.shields.io/badge/merged_PRs-32-8957e5?logo=github)](https://github.com/pulls?q=is%3Apr+author%3Aabhishekcpp007+is%3Amerged+-user%3Aabhishekcpp007)

| Project | Stars | PR | Status | What I fixed |
|---|---|---|---|---|
| [**OpenEnv**](https://github.com/openenv/OpenEnv) <br><sub>openenv</sub> | 2.9k | [#1631](https://github.com/openenv/OpenEnv/pull/1631) | ![status](https://img.shields.io/github/pulls/detail/state/openenv/OpenEnv/1631?label=) | The FinQA reward cut `\boxed{}` answers at the first `}`, so a correct answer with `\text{}` inside scored 0 |
| [**virtualenv**](https://github.com/pypa/virtualenv) <br><sub>pypa</sub> | 5k | [#3514](https://github.com/pypa/virtualenv/pull/3514) | ![status](https://img.shields.io/github/pulls/detail/state/pypa/virtualenv/3514?label=) | The csh activator never unset `PYTHONHOME`, so the activated interpreter died with `No module named 'encodings'` before running anything |
| [**tox-uv**](https://github.com/tox-dev/tox-uv) <br><sub>tox-dev</sub> | 356 | [#418](https://github.com/tox-dev/tox-uv/pull/418) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/tox-uv/418?label=) | `system_site_packages` was missing from `python_cache`, so changing it never recreated the environment and the setting had no effect in either direction |
| [**pyproject-api**](https://github.com/tox-dev/pyproject-api) <br><sub>tox-dev</sub> | 25 | [#354](https://github.com/tox-dev/pyproject-api/pull/354) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/pyproject-api/354?label=) | `ensure_empty_dir` gated on `exists()`, which follows symlinks: a dangling link raised `FileExistsError` and a link to a directory emptied its target |
| [**filelock**](https://github.com/tox-dev/filelock) <br><sub>tox-dev</sub> | 986 | [#908](https://github.com/tox-dev/filelock/pull/908) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/filelock/908?label=) | Read-write locks took `blocking=0` as blocking and waited the full timeout |
| [**platformdirs**](https://github.com/tox-dev/platformdirs) <br><sub>tox-dev</sub> | 1.0k | [#686](https://github.com/tox-dev/platformdirs/pull/686) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/platformdirs/686?label=) | Media and fonts functions couldn't take `use_site_for_root` like their properties |
| [**more-itertools**](https://github.com/more-itertools/more-itertools) <br><sub>more-itertools</sub> | 4.1k | [#1346](https://github.com/more-itertools/more-itertools/pull/1346) | ![status](https://img.shields.io/github/pulls/detail/state/more-itertools/more-itertools/1346?label=) | Type stubs for `concurrent_tee` and `serialize` disagreed with the runtime code |
| [**tox**](https://github.com/tox-dev/tox) <br><sub>tox-dev</sub> | 4k | [#4371](https://github.com/tox-dev/tox/pull/4371) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/tox/4371?label=) | A `re.VERBOSE` regex dropped a literal space, so commented-out PEP 723 lines were read as live metadata |
| [**pytest-randomly**](https://github.com/pytest-dev/pytest-randomly) <br><sub>pytest-dev</sub> | 724 | [#755](https://github.com/pytest-dev/pytest-randomly/pull/755) | ![status](https://img.shields.io/github/pulls/detail/state/pytest-dev/pytest-randomly/755?label=) | xdist workers re-read the cache for `--randomly-seed=last`, so with `--cache-clear` each got its own seed and collection crashed |
| [**mdit-py-plugins**](https://github.com/executablebooks/mdit-py-plugins) <br><sub>executablebooks</sub> | 50 | [#172](https://github.com/executablebooks/mdit-py-plugins/pull/172) | ![status](https://img.shields.io/github/pulls/detail/state/executablebooks/mdit-py-plugins/172?label=) | A tab after `[ ]` counted as a task but dropped the checkbox, and `label_after` leaked raw `id=` text |
| [**flake8-bugbear**](https://github.com/PyCQA/flake8-bugbear) <br><sub>PyCQA</sub> | 1.1k | [#633](https://github.com/PyCQA/flake8-bugbear/pull/633) | ![status](https://img.shields.io/github/pulls/detail/state/PyCQA/flake8-bugbear/633?label=) | B021 never ran on `async def`, so f-string docstrings there were missed |
| [**wcmatch**](https://github.com/facelessuser/wcmatch) <br><sub>facelessuser</sub> | 169 | [#280](https://github.com/facelessuser/wcmatch/pull/280) | ![status](https://img.shields.io/github/pulls/detail/state/facelessuser/wcmatch/280?label=) | With `MINUSNEGATE`, an exclusion like `-~/*.py` never expanded `~`, so it excluded nothing |
| [**hist**](https://github.com/scikit-hep/hist) <br><sub>scikit-hep</sub> | 140 | [#766](https://github.com/scikit-hep/hist/pull/766) | ![status](https://img.shields.io/github/pulls/detail/state/scikit-hep/hist/766?label=) | `ChunkedHist.to_hist()` set category labels to the axis name, so adding the result to its source raised `axes not mergable` |
| [**bracex**](https://github.com/facelessuser/bracex) <br><sub>facelessuser</sub> | 33 | [#64](https://github.com/facelessuser/bracex/pull/64) | ![status](https://img.shields.io/github/pulls/detail/state/facelessuser/bracex/64?label=) | Ranges whose span overflows int64 were expanded, where Bash 5.3 keeps them literal |
| [**parse**](https://github.com/r1chardj0n3s/parse) <br><sub>r1chardj0n3s</sub> | 1.8k | [#286](https://github.com/r1chardj0n3s/parse/pull/286) | ![status](https://img.shields.io/github/pulls/detail/state/r1chardj0n3s/parse/286?label=) | The `e` and `g` types rejected `+nan` and `" inf"`, which `str.format()` itself writes |
| [**decaylanguage**](https://github.com/scikit-hep/decaylanguage) <br><sub>scikit-hep</sub> | 43 | [#650](https://github.com/scikit-hep/decaylanguage/pull/650) | ![status](https://img.shields.io/github/pulls/detail/state/scikit-hep/decaylanguage/650?label=) | `DescriptorFormat` saved the config when built, so nested `with` blocks restored the wrong format on exit |
| [**backrefs**](https://github.com/facelessuser/backrefs) <br><sub>facelessuser</sub> | 13 | [#220](https://github.com/facelessuser/backrefs/pull/220) | ![status](https://img.shields.io/github/pulls/detail/state/facelessuser/backrefs/220?label=) | A null escape at the end of a replace template raised `PatternError` where `re` returns `\x00` |
| [**nox**](https://github.com/wntrblm/nox) <br><sub>wntrblm</sub> | 1.6k | [#1234](https://github.com/wntrblm/nox/pull/1234) | ![status](https://img.shields.io/github/pulls/detail/state/wntrblm/nox/1234?label=) | `nox --report` crashed on a `Path` parametrize value and left the report file cut off |
| [**pymdown-extensions**](https://github.com/facelessuser/pymdown-extensions) <br><sub>facelessuser</sub> | 1.1k | [#3052](https://github.com/facelessuser/pymdown-extensions/pull/3052) | ![status](https://img.shields.io/github/pulls/detail/state/facelessuser/pymdown-extensions/3052?label=) | Keys swallowed escaped backslashes in quoted keys, so only the last escaped character survived |
| [**tox**](https://github.com/tox-dev/tox) <br><sub>tox-dev</sub> | 4k | [#4393](https://github.com/tox-dev/tox/pull/4393) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/tox/4393?label=) | Changing `system_site_packages` on an existing environment did nothing, so it kept the old value until `tox -r` |
| [**sphinx-autodoc-typehints**](https://github.com/tox-dev/sphinx-autodoc-typehints) <br><sub>tox-dev</sub> | 589 | [#1124](https://github.com/tox-dev/sphinx-autodoc-typehints/pull/1124) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/sphinx-autodoc-typehints/1124?label=) | A parameter ending in an underscore, like `lambda_`, lost the type its docstring gave it |
| [**sphinx-argparse-cli**](https://github.com/tox-dev/sphinx-argparse-cli) <br><sub>tox-dev</sub> | 28 | [#405](https://github.com/tox-dev/sphinx-argparse-cli/pull/405) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/sphinx-argparse-cli/405?label=) | Help that already used `%(default)s` got a second `(default: ...)` appended |
| [**pipdeptree**](https://github.com/tox-dev/pipdeptree) <br><sub>tox-dev</sub> | 3k | [#882](https://github.com/tox-dev/pipdeptree/pull/882) | ![status](https://img.shields.io/github/pulls/detail/state/tox-dev/pipdeptree/882?label=) | With `--reverse` and `--depth`, Graphviz output put missing requirements at the wrong depth, unlike the text tree |
| [**sqlacodegen**](https://github.com/agronholm/sqlacodegen) <br><sub>agronholm</sub> | 2.4k | [#491](https://github.com/agronholm/sqlacodegen/pull/491) | ![status](https://img.shields.io/github/pulls/detail/state/agronholm/sqlacodegen/491?label=) | A column named `registry` wasn't renamed like `metadata`, so generated code warned on import |
| [**exceptiongroup**](https://github.com/agronholm/exceptiongroup) <br><sub>agronholm</sub> | 51 | [#169](https://github.com/agronholm/exceptiongroup/pull/169) | ![status](https://img.shields.io/github/pulls/detail/state/agronholm/exceptiongroup/169?label=) | `subgroup()` and `split()` didn't check what `derive()` returned, so a broken override got an `AttributeError` or no error at all |
| [**exceptiongroup**](https://github.com/agronholm/exceptiongroup) <br><sub>agronholm</sub> | 51 | [#170](https://github.com/agronholm/exceptiongroup/pull/170) | ![status](https://img.shields.io/github/pulls/detail/state/agronholm/exceptiongroup/170?label=) | A class that isn't an exception type, like `bool`, was used as a predicate and quietly matched everything |
| [**SAELens**](https://github.com/decoderesearch/SAELens) <br><sub>decoderesearch</sub> | 1.6k | [#776](https://github.com/decoderesearch/SAELens/pull/776) | ![status](https://img.shields.io/github/pulls/detail/state/decoderesearch/SAELens/776?label=) | `random_firing_probabilities` built a fresh `torch.Generator()`, which starts from a fixed seed, so unseeded calls returned identical probabilities every time |
| [**delphi**](https://github.com/EleutherAI/delphi) <br><sub>EleutherAI</sub> | 280 | [#192](https://github.com/EleutherAI/delphi/pull/192) | ![status](https://img.shields.io/github/pulls/detail/state/EleutherAI/delphi/192?label=) | `split_quantiles` floored the per-quantile count, so 25 samples over 10 quantiles gave 20, and fewer samples than quantiles gave 0 with no warning |
| [**nnsight**](https://github.com/ndif-team/nnsight) <br><sub>ndif-team</sub> | 1.1k | [#800](https://github.com/ndif-team/nnsight/pull/800) | ![status](https://img.shields.io/github/pulls/detail/state/ndif-team/nnsight/800?label=) | Reassembling a multi-invoke `.skip()` lost the container type: namedtuple outputs raised `TypeError` and `ModelOutput`/`OrderedDict` came back as plain dicts |
| [**TransformerLens**](https://github.com/TransformerLensOrg/TransformerLens) <br><sub>TransformerLensOrg</sub> | 4k | [#1965](https://github.com/TransformerLensOrg/TransformerLens/pull/1965) | ![status](https://img.shields.io/github/pulls/detail/state/TransformerLensOrg/TransformerLens/1965?label=) | Eval helpers hardcoded `"cuda"`, which crashed on CPU and Apple MPS machines |
| [**TransformerLens**](https://github.com/TransformerLensOrg/TransformerLens) <br><sub>TransformerLensOrg</sub> | 4k | [#1976](https://github.com/TransformerLensOrg/TransformerLens/pull/1976) | ![status](https://img.shields.io/github/pulls/detail/state/TransformerLensOrg/TransformerLens/1976?label=) | `stack_head_results` silently returned the wrong residual stream for a negative layer, unlike its neuron sibling |
| [**TransformerLens**](https://github.com/TransformerLensOrg/TransformerLens) <br><sub>TransformerLensOrg</sub> | 4.1k | [#2012](https://github.com/TransformerLensOrg/TransformerLens/pull/2012) | ![status](https://img.shields.io/github/pulls/detail/state/TransformerLensOrg/TransformerLens/2012?label=) | `sample_logits` checked `top_k` and `top_p` only in the sampling branch, so greedy calls accepted any value |

---

## Skills

**Evaluation:** RL environments, hidden PyTest suites, deterministic verifiers, reward-hacking detection

**Languages and tools:** Python (primary), SQL, Bash, JavaScript, PyTest, Git, GitHub Actions, Linux

**Infrastructure and data:** Docker, AWS (S3, Glue, Lambda, ECR), Snowflake, Hugging Face datasets

---

## Experience

- **Full Stack Developer, RL Environments and Evaluation**, Ethara AI (via Quess Corp Limited). Jan 2026 to Present
- **Software Engineer (Data)**, NavAdr Technologies Solutions. Dec 2024 to Jan 2026
