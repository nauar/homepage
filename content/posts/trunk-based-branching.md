---
author: "Arnau Oncins"
title: "Trunk-based branching"
description: "Analysis and suitability of trunk-based branching"
comments: true
tags: ["devops", "git", "branching"]
date: "2021-12-29"
showToc: true
TocOpen: false
---

## Definitions

* **SCM**: Acronym for **S**ource **C**ode **M**anamgement. A source code management system is a system which stores code of applications (and possibly their configurations, their infrastructure definitions, their security policies, etc.). Files are stored in repositories in an aggregated way (modifications are new copies of the original files and deletions preserve the content of original files) and in an auditable way (each change keeps the author, the date, the modified files, and their modified content). These systems can be classified as centralized, such as SVN, or distributed, like Git.
* **Release Process**: Process that defines how a component is released from its development stage (even before) to production. It defines the different stages, the stakeholders in each of these stages, and how stakeholders interact in order to deliver the solutions to a final live environment.
* **Branch**: In a SCM, a branch is an independent set of consecutive temporal ordered changes. Branches can be duplicated, merged, etc.

## Introduction

In order to make all members of the development teams work in a standarized way, it's necessary to have a common understanding of the development process and the development tools and processes. One of them is the branching strategy.

The branching strategy defines not only how to structure the updates in the code base, it also defines the process to be followed to define how they are merged and released. Therefore, it impacts in the development and the release processes.

## Branching Strategies

Regarding the cycle of the development branches, the branching strategies can be categorized in two groups:

* **Multi-branching**: it allows the persistence of more than one mainline/long-living branch. Examples: GitFlow [1].
* **Single-branching**: it allows the persistence of only on mainline/long-living branch. Examples: trunk-based branching [2]).

### Selection criteria

Both options have their ow advantages and drawbacks.

A multi-branching strategy provides strict controls and ease the collaboration with less experienced (and/or less trusted) developers. However, it makes a bit harder to quickly iterate and it can generate micromanagement. However, these strict controls make this branching strategy more suitable for running an open-source project, due to the inherent missing trustfulness among unknown world-wide collaborators. On the other hand, the addition of all these controls generates a more complex continuous integration framework, with multiple merges and approvals until the code is ready to be in the release branch. For these reasons, it is not recommended to use this strategy in closed-source enterprise projects.

A single-branching strategy provides a direct way of implementing and integrating changes and it removes all this bureaucracy. Nonetheless, it requires a sufficient trustfulness among the members of development teams, having to perform only one single merge to the mainline. In top of this constraint, it is necessary to provide a way of enabling and disabling features that are still on development or not planned to be shipped to production, such as **feature flags** in **trunk-based branching**. Even so, single-branching strategies improve the productivity of the development teams, due to the reduction of the number of merges (remember that the time dedicated to merge code from different branches is not development productive time).

To illustrate the previous explanations above, let me grab some exampes form Microsoft [3]:

![Typical merge related problem in a multi-branching setup](/img/multibranching.png#center) **Figure 1**: Typical merge related problem in a multi-branching setup.

![Single-branching way of managing merges](/img/singlebranching.png#center) **Figure 2**: Single-branching way of managing merges.

As it most cases, there is not a silver-bullet option that can be applied in all situations. It depends on the context. I have seen successful setups in the open source world using single-branching methodologies. However, there are also enterprise projects that work well with multi-branching methodologies (not so many, though).

## General recomendation

**Trunk-based branching** is a branching methodology that allows accelerating continuous integration loop and decreasing lead time to production. It improves the continuous integration and continuous delivery loops avoiding the merge-hell situations. For achieve its implementation, the trustfulness constraint must be respected and the development teams must be able to use **feature flags** (also known as **feature toggles**). **Note**: I will dedicate a post for feature flags.

## References

1. DRIESSEN, Vincent. A successful Git branching model. NVIE personal blog. January 05, 2010. (Online). Accessed at: 2019-10-11. Available at: https://nvie.com/posts/a-successful-git-branching-model/.
2. HUMBLE, Jez. Continuous Integration. Continuous Delivery Web Page. Copyright © 2010-2017. (Online). Accessed at: 2019-10-11. Available at: https://continuousdelivery.com/foundations/continuous-integration/.
3. HENDERSON, Nathan. A Git Workflow for Continuous delivery. Microsoft blogs. June 21, 2016. (Online). Accessed at: 2019-10-11. Available at: https://docs.microsoft.com/es-es/archive/blogs/technet/devops/a-git-workflow-for-continuous-delivery.
4. GADZINOWSKI,Konrad. Trunk-based Development vs. Git Flow. Topical Developers, Engineering Blog. Copyright © 2010-2019. (Online).  Accessed at: 2019-11-13. Available at: https://www.toptal.com/software/trunk-based-development-git-flow
5. GOVENDER, Yuveshen. Trunks are not just for trees: from git flow to trunk-based development, Medium, SafelyCulture Engineering. Copyright © 2019 Medium. (Online). Accessed at: 2019-11-13. Available at: https://medium.com/safetycultureengineering/trunks-are-not-just-for-trees-from-git-flow-to-trunk-based-development-949d580697ef
6. HAMMANT, Paul. Trunk Based Development Trunk Based Development Website. Copyright © 2017-2018. (Online). Accessed at: 2019-11-13. Available at: https://trunkbaseddevelopment.com/






