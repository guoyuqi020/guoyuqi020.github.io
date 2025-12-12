---
permalink: /
title: "Yuqi Guo's Homepage"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

I'm a Ph.D. candidate in Software Engineering at Institute of Software, Universify of Chinese Academy of Sciences. I am advised by Prof. [Yan Cai](https://yancai.site/). I expect to graduate in 2027.

My recent research focuses on AI-assisted software testing, where I explore approaches for combining AI's code semantics comprehension with rule-based software analysis techniques for effective software testing. Previously, my research interests centered on developing algorithms for detecting concurrency bugs in large-scale programs and designing testing approaches for detecting non-correspondences in cross-architectural software porting.



Education
======

|--------|-------------|-------|------|
| Degree | Institution | Major | Year |
|--------|-------------|-------|------|
| B.S.   | Peking University | Electronics Engineering and Computer Science | 2017-2021 |
| Ph.D.  | University of Chinese Academy of Sciences | Software Engineering | 2021-2027 (expected) |
|--------|-------------|-------|------|


Awards
------

|--------|-------------|-------|
| Awards | Year | 获奖 |
|--------|-------------|-------|
| Merit Student, UCAS | 2025 & 2023 | 中国科学院大学三好学生 |
| First class scholarship of the Chinese Academy of Sciences | 2024-2025 | 中国科学院一等奖学金 |
|--------|-------------|-------|

Competitions
------

|--------|-------------|-------|
| Competitions | Year | 竞赛 |
|--------|-------------|-------|
| National College Student Mathematical Modeling Competition - National First Prize | 2018 | 全国大学生数学建模大赛 - 国家级一等奖 |
| CPhO - Silver Medal | 2015 | 全国中学生物理竞赛 - 银牌 |
|--------|-------------|-------|


Publications
------
Please also refer to [Google Scholar](https://scholar.google.com/citations?user=guNAr_QAAAAJ) for a complete list of my research papers.

|--------|-------------|-------|-------|
| No. | Title | Venue | Role |
|--------|-------------|-------|-------|
| 1 | Reduce Dependence for Sound Concurrency Bug Prediction | ICSE 2025 (CCF-A) | Second Author |
| 2 | Reorder Pointer Flow in Sound Concurrency Bug Prediction | ICSE 2024 (CCF-A) | First Author |
| 3 | Tolerate Control-flow Changes for Sound Data Race Prediction | ICSE 2023 (CCF-A) | Co-first Author (ranked 2nd) |
| 4 | Sound Predictive Fuzzing for Multi-threaded Programs | COMPSAC 2023 (CCF-C) | First Author |
|--------|-------------|-------|-------|

Recent Research Practices
======
**Application of Reinforcement Learning for Data Race Detection**

**TL;DR:** We train a 4B model with GRPO algorithm, which resolves up to 65% of data races that were missed by the SOTA rule-based race detectors. Besides, it outperforms Claude-Sonnet-4.5 (and many other SOTA closed-source LLMs) by detecting 33.48% more data races while reducing 65.23% token consumption.

**Detailed Introduction:** Due to the extremely large search space in the thread interleaving of concurrent programs, the data race detection problem is known to be NP-complete. 
Existing rule-based dynamic data race detection techniques often struggle to balance between *soundness* (all reports are true positives) and *completeness* (all data races can be detected).
In this research, we propose a novel approach that leverages reinforcement learning (RL) to train a customized LLM for sound data race detection.
Specifically, we formalize the data race detection problem as a topological sorting problem on a directed acyclic graph (DAG), where nodes represent program operations and edges represent the "happens-before" relationships. 
We transform the target of data race detection to finding a linearization of the DAG.
To ensure soundness, we model the program semantics as constraints on DAG topological sorting, thus guaranteeing that all generated linearizations correspond to valid thread interleavings.
As a mathematical problem, the solution of constrained topological sorting can be efficiently verified.
Inspired by the recent advances in RL for mathematical problem solving, we utilize the GRPO algorithm to train a 4B LLM to solve this constrained topological sorting problem.
We study the data generation strategies, training process, and reward signal design for effectively training the model.
The experimental results on real-world concurrent programs demonstrate that our approach can effectively outperform existing rule-based and LLM-based data race detection techniques.

------

**Automated Non-correspondence Detection in Cross-architectural Software Porting**


**TL;DR:** We develop a novel approach that combines rule-based trace alignment with LLM-based code comprehension to automatically detect non-correspondences in cross-architectural software porting. Our tool identifies 13 RISC-V-related functionality bugs or performance optimization opportunities in real-world Github repositories, including libjpeg-turbo, xz, and Zstandard.

**Detailed Introduction:** Cross-architectural software porting involves extending the existing software developed for the legacy architecture to ensure compatibility with a new one. Detecting porting-related bugs on large codebases can be challenging because manual code reviewing and debugging are time-consuming and labor-intensive. 
In this research project, we propose a novel system designed to automatically detect the control flow non-correspondences between the legacy and the new architectures with minimal human intervention. 
It first leverages a rule-based trace alignment algorithm to identify and locate the control flow non-correspondences. 
Subsequently, it utilizes coding agents to analyze the root cause analysis and filter out the non-buggy non-correspondences.
Finally, it reports the unique control flow non-correspondences for manual bug review.
