## STRICT MODE DEVELOPMENT PROCESS

This document describes a process of development. 
It requires each member of the team follow its requirement strictly.
Its purpose is delivering high quality of code with minimum of bugs,
includes potential bugs, which is really hard to be found with testers.
Who normally are lacking of coding skills.

I do not advise we approve this process for every project we are working on.
You should decide your project is fit or not with this process.

### 1. GIT Standards
* **Protected branches:** We should have protected branches.
Which is always not easy to be merged. They can be different name in different projects.
For example, in this document, we have branches: `master` and `product`.
`master` should include well tested code,
feature branches need to be reviewed by other devs before merged into `master`.
And `product` should be the final result after each milestone we reach
and be ready for production.
* **Feature branches:** the branches the developers be working on it. 
Include bug fix, new feature. 
Every feature branch should be corresponding with an issue be created on git server
(github ,gitlab , etc...). A `feature branch` should be named as a standard format.
I would love to propose a standard: `{issue_id}_{issue_name}` in this document.
For example: `1_init_source_base`, `205_fix_bug_when_send_marketing_email`, ...
* **Issue:** an issue should be full detail and informative. If it is a bug.
It should give the link to the bug, describe how to reproduce the bug,
the old state and the expected state.
* **Pull request:** (or `merge request` in other word. In this doc I call it be `pr`.
See [an example](https://github.com/decred/politeiagui/pull/2628))
A `pr` is a proposal for merging a `feature branch` into `protected branch`. 
The `pr` should be fully informative of what issue it solves, what it does,
what different it makes. A `pr` should be merged after code review and be tested by testers.
This process ensure the code on `master` is always well structure and deliver correct features.
* **Review:** Everyone is advised to review other member's code. 
A full experience developer can help a newbie when he is reviewing the newbie's `pr`. 
While a newbie can learn from the senior dev's `pr`. But keep in mind that everyone can make mistake.
So everyone is advised for reviewing.
