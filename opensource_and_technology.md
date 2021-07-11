# 开源社区 & 技术

社区以及参与社区的人，一直在做如下3件事情，并且各个方向都有：

## 1. make git understandable

git 本身是一个复杂的工具，需要专门的培训和学习，因此公司内部如果在这方面做好宣传和资料的丰富，会极大提高人员能力，减少支撑工作：

### 1.1 从社区收集的文档来看，很多大师都在不遗余力的进行布道:
- 介绍 git 的发展历史
	* https://www.welcometothejungle.com/en/articles/btc-history-git
- 在学校就进行相关的培训
	* [Lecture 6: Version Control (Git) is a part of “The Missing Semester of Your CS Education” class at MIT](https://missing.csail.mit.edu/2020/version-control/)
	* https://opensource.com/article/20/4/get-started-git
- 介绍使用 git 的优秀实践和方式
	* [Commit Often, Perfect Later, Publish Once: Git Best Practices by Seth Robertson (2012)](http://sethrobertson.github.io/GitBestPractices/)
- 如何写出好的 commit message
	* https://dev.to/yvonnickfrin/a-guide-on-commit-messages-d8n
	* https://www.freecodecamp.org/news/a-beginners-guide-to-git-how-to-write-a-good-commit-message/
- 开发者要了解的一些知识点
	* https://www.sitepoint.com/git-techniques-to-know-before-you-join-a-team/
	* https://www.freecodecamp.org/news/10-important-git-commands-that-every-developer-should-know/
	* https://www.smashingmagazine.com/make-life-easier-when-using-git/
	* https://dev.to/milu_franz/git-explained-the-basics-igc
	* https://dev.to/milu_franz/git-explained-an-in-depth-comparison-18mk
	* https://dev.to/milu_franz/git-explained-proper-team-etiquette-1od
	* https://dev.to/milu_franz/git-explained-an-umbrella-structure-using-git-submodules-20dl
	* https://dev.to/milu_franz/git-explained-tips-and-tricks-4299
	* [How to resolve a git merge conflict](https://opensource.com/article/20/4/git-merge-conflict)
	* https://www.alchemists.io/articles/git_rebase/

### 1.2 社区平台，技术博客，分享讨论

类似 https://forum.githubs.cn/categories:
- git 技术文档
- 建议 & 反馈
- 开源分享
- 技术交流
- 公告广告

## 2. make git easier to use

如果与服务器交互，变成和输入命令一样快捷，那么对于开发人员来讲，避免频繁切换界面，一键式命令带来的是效率的巨大提升.

### 2.1 cli 工具或者插件
- [github cli](https://cli.github.com/) 是经典的把 web 操作简化为命令行的案例，更适合于开发场景和自动化场景，有极大市场.
- [4 Git scripts](https://opensource.com/article/20/4/git-extras) I can’t live without by Vince Power on Opensource.com.
- [Onefetch](https://github.com/o2sh/onefetch) is a command line tool that displays summary information about your Git repository directly on your terminal.

### 2.2 Web 工具或者插件
WebIDE 是非常有用的避免开发人员进行复杂的 `git clone/checkout/push` 等操作，并且能够方便的进行三方工具集成:
- github:
	* https://thenextweb.com/news/github-codespace-lets-you-code-in-your-browser-without-any-setup
- gitlab:
	* https://docs.gitlab.com/ee/user/project/web_ide/
- plugin marketplace
	* https://github.com/marketplace，基于 github 实现扩展，共享成果
- 网站收藏夹
	* 类似 github 上的 start 功能，快速定位到具体的仓库
- 网站消息操作界面
	* 如 https://github.com/notifications, 统一界面处理所有消息

### 2.3 手机应用 app

通过手机完成更加快速的操作, github 和 gitlab 都可以实现手机处理事务。

### 2.4 针对 gitattributes 进行能力拓展
git 强大的 gitattributes，可以让服务器针对特定的文件进行 diff 对比，产生更合适的 diff 内容:
- https://blog.afoolishmanifesto.com/posts/improve-git-diffs-structured-data

### 2.5 替开发人员完成一些自动化工具
- 自动查找废弃代码:
	* Piranha by Uber is an Open Source tool for automated clean up of stale code caused by feature flags that are no longer required. It currently supports Java, Swift, and Objective-C.
- github 自动检查依赖项目的更新
	* https://docs.github.com/cn/code-security/supply-chain-security/keeping-your-dependencies-updated-automatically

## 3. make git faster

git 仓库主要可以分为两种常用的内容：commit 和其它的 objects，针对 commit 和其它的 objects 查找都有相应的技术在发展：

### 3.1 commit-graph
commit-graph 是从 v2.24.0 正式引入，能够提高查找 commit 的速度，加速 commit 遍历和关系计算，提高 `git log` 等命令的速度。
- 讲解 commit-graph 的主要工作机制: https://devblogs.microsoft.com/devops/updates-to-the-git-commit-graph-feature/

### 3.2 multi-pack-index
git 仓库中有很多 pack-files，multi-pack-index 可以加速对象遍历和查找，同时和 commit-graph 一样，repack 命令可以实现借助 multi-pack-index 的增量压缩。

### 3.3 partial-clone & sparse checkout
partial clone 用来只下载仓库的部分内容，用来替代 git-lfs，加速仓库上传下载. partial clone 已经出现几年, Gitlab, Github, Microsoft, Google 等都进行了贡献。Gitlab, Github 都已经支持.
- https://about.gitlab.com/blog/2020/03/13/partial-clone-for-massive-repositories/
- partial clone 能够提高至少 50% 速度，减少 70% 的数据传输。
- git merge 2020 会议，Microsoft 介绍了 [scalar](https://devblogs.microsoft.com/devops/introducing-scalar/), 其中提到了对下载方式的对比: `git clone < GVFS < partical clone`
- 可以提供多地域的 `git primisor` 来加速下载

### 3.4 git v2 protocol
增强 git 交互的作用域，提高 push 与 clone 的效率。

## 4. 个人总结

### 4.1 建设技术分享渠道，参与布道

- 创建维护技术论坛: 社区大佬都一直在不断的分享，讨论，一个是不断的培养人员的能力，另外一个也是通过讨论发现新的场景和方法。我们也需要在这个方向进行努力，用户的水平提高，平台的压力就减少了。

### 4.2 增强 web 页面和手机 app

- 集成 webIDE: 社区重点在发现基于 WebIDE 的一站式工作模式。如果开发一个 git 仓库的文件系统监听器 (能分析 git 仓库的文件和状态), 让 git 命令更快，结合 sparse-checkout，让 WebIDE 成为利器。
- 开发手机 app: 让代码平台扩展到手机客户端
- 学习 github 引入智能作业: 与其它团队合作，提供一系列的自动化工具，让平台为开发完成一些工作; 
- 建设插件市场: 让用户参与进来，进行平台建设

### 4.3 开发 cli 工具

- 让平台操作简化到命令行，让扩展能为一条命令那么简单

### 4.4 增量 git 性能

- 启用新特性: commit-graph 和 multi-pack-index 是增高 commit 遍历和 Object 遍历的工具，开发一些 post-receive 任务，利用好它们。
- 集成 v2 protocol: 让引用发现等更快。
- 测试开启 partial clone: 社区新趋势，Gitlab, Gitub, Microsoft, Google 重点关注和贡献的特性。
