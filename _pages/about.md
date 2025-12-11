---
permalink: /
title: "Yuqi Guo's Homepage"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

I'm a Ph.D. candidate in Software Engineering at Institute of Software, Universify of Chinese Academy of Sciences. I am advised by Prof. [Yan Cai](https://yancai.site/). I expect to graduate in 2027.

My recent research focuses on AI-assisted software engineering, where I explore approaches for combining AI's code semantics comprehension with rule-based software analysis techniques for effective software developing/testing. Previously, my research interests centered on developing algorithms for detecting concurrency bugs in large-scale programs, and testing approaches for detecting non-correspondences in cross-architectural software porting.



Education
======

|--------|-------------|-------|------|
| Degree | Institution | Major | Year |
|--------|-------------|-------|------|
| B.S.   | Peking University | Electronics Engineering and Computer Science | 2017-2021 |
| Ph.D.  | University of Chinese Academy of Sciences | Software Engineering | 2021-2027 (expected) |
|--------|-------------|-------|------|

Recent Research Practices
======
1. Application of Reinforcement Learning for Data Race Detection
**TL;DR:** We trained a 4B model with GRPO algorithm, which resolved up to 65% of data races that were missed by the SOTA rule-based race detectors. Besides, it outperformed Claude-Sonnet-4.5 (and many other SOTA closed-source LLMs) by detecting 33.48% more data races while reducing 65.23% token consumption.

**Detailed Introduction:** Due to the extremely large search space in the thread interleaving of concurrent programs, the data race detection problem is known to be NP-complete. 
Existing rule-based dynamic data race detection techniques often struggle to balance between soundness (all reports are true positive) and completeness (all data races can be detected).
The LLM-based approaches, however, can guarantee neither soundness nor completeness due to their inherent probabilistic nature.
In this research, we propose a novel approach that leverages reinforcement learning (RL) to train a customized LLM for sound data race detection.
Specifically, we formalize the data race detection problem as a topological sorting problem on a directed acyclic graph (DAG), where nodes represent program operations and edges represent the "happens-before" relationships.
We transform the target of data race detection as finding an linearization of the DAG that exposes data races.
To ensure soundness, we model the program semantics as constraints on DAG topological sorting, thus guaranting that all generated linearizations correspond to valid thread interleavings.
As a mathematical problem, the solution of constrained topological sorting can be efficiently verified, i.e., whether a generated linearization satifies all the "happens-before" constraints.
Inspired by the recent advances in RL for mathematical problem solving, we utilize the GRPO algorithm to train a 4B LLM to solve this constrained topological sorting problem.
We study the data generation strategies, training process, and reward signal design for effectively training the model.
The experimental results on a real-world concurrent programs demonstrate that our approach can effectively outperform existing rule-based and LLM-based data race detection techniques.

1. Automated Non-correspondence Detection in Cross-architectural Software Porting




Site-wide configuration
------
The main configuration file for the site is in the base directory in [_config.yml](https://github.com/academicpages/academicpages.github.io/blob/master/_config.yml), which defines the content in the sidebars and other site-wide features. You will need to replace the default variables with ones about yourself and your site's github repository. The configuration file for the top menu is in [_data/navigation.yml](https://github.com/academicpages/academicpages.github.io/blob/master/_data/navigation.yml). For example, if you don't have a portfolio or blog posts, you can remove those items from that navigation.yml file to remove them from the header. 

Create content & metadata
------
For site content, there is one Markdown file for each type of content, which are stored in directories like _publications, _talks, _posts, _teaching, or _pages. For example, each talk is a Markdown file in the [_talks directory](https://github.com/academicpages/academicpages.github.io/tree/master/_talks). At the top of each Markdown file is structured data in YAML about the talk, which the theme will parse to do lots of cool stuff. The same structured data about a talk is used to generate the list of talks on the [Talks page](https://academicpages.github.io/talks), each [individual page](https://academicpages.github.io/talks/2012-03-01-talk-1) for specific talks, the talks section for the [CV page](https://academicpages.github.io/cv), and the [map of places you've given a talk](https://academicpages.github.io/talkmap.html) (if you run this [python file](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.py) or [Jupyter notebook](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.ipynb), which creates the HTML for the map based on the contents of the _talks directory).

**Markdown generator**

The repository includes [a set of Jupyter notebooks](https://github.com/academicpages/academicpages.github.io/tree/master/markdown_generator
) that converts a CSV containing structured data about talks or presentations into individual Markdown files that will be properly formatted for the Academic Pages template. The sample CSVs in that directory are the ones I used to create my own personal website at stuartgeiger.com. My usual workflow is that I keep a spreadsheet of my publications and talks, then run the code in these notebooks to generate the Markdown files, then commit and push them to the GitHub repository.

How to edit your site's GitHub repository
------
Many people use a git client to create files on their local computer and then push them to GitHub's servers. If you are not familiar with git, you can directly edit these configuration and Markdown files directly in the github.com interface. Navigate to a file (like [this one](https://github.com/academicpages/academicpages.github.io/blob/master/_talks/2012-03-01-talk-1.md) and click the pencil icon in the top right of the content preview (to the right of the "Raw | Blame | History" buttons). You can delete a file by clicking the trashcan icon to the right of the pencil icon. You can also create new files or upload files by navigating to a directory and clicking the "Create new file" or "Upload files" buttons. 

Example: editing a Markdown file for a talk
![Editing a Markdown file for a talk](/images/editing-talk.png)

For more info
------
More info about configuring Academic Pages can be found in [the guide](https://academicpages.github.io/markdown/), the [growing wiki](https://github.com/academicpages/academicpages.github.io/wiki), and you can always [ask a question on GitHub](https://github.com/academicpages/academicpages.github.io/discussions). The [guides for the Minimal Mistakes theme](https://mmistakes.github.io/minimal-mistakes/docs/configuration/) (which this theme was forked from) might also be helpful.
