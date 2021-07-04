# rev news

## https://git.github.io/rev_news/2019/11/20/edition-57/
- https://devblogs.microsoft.com/devops/updates-to-the-git-commit-graph-feature/
- LockGit is a CLI tool for storing encrypted secrets in a git repo.
- Onefetch is a command line tool that displays summary information about your Git repository directly on your terminal.

## https://git.github.io/rev_news/2020/02/19/edition-60/
- Lecture 6: Version Control (Git) is a part of “The Missing Semester of Your CS Education” class at MIT.
- Commit Often, Perfect Later, Publish Once: Git Best Practices by Seth Robertson (2012).
- https://dev.to/yvonnickfrin/a-guide-on-commit-messages-d8n
- https://www.freecodecamp.org/news/10-important-git-commands-that-every-developer-should-know/
- OneDev is an all-in-one DevOps platform, with issue tracking, Git management, pull requests, and build farm; written in Java.

## https://git.github.io/rev_news/2020/03/25/edition-61/
- https://git-repo.info/en/2020/03/agit-flow-and-git-repo/
- https://about.gitlab.com/blog/2020/03/13/partial-clone-for-massive-repositories/
- https://www.freecodecamp.org/news/a-beginners-guide-to-git-how-to-write-a-good-commit-message/
- https://stolee.dev/docs/git-merge-2020.pdf
- https://www.infoworld.com/article/3528008/microsofts-scalar-speeds-up-git.html
- https://www.sitepoint.com/git-techniques-to-know-before-you-join-a-team/

## append

### github cli

use `gh xxx` to do most github operations directly in command lines.

### forum for developers

扩大平台影响力。开发者通过实例来分享高阶用法。

https://www.githubs.cn/
- 开发者榜单
- 技术博客

### https://gitea.io/zh-cn/

Gitea 是一个开源社区驱动的轻量级代码托管解决方案，后端采用 Go 编写，采用 MIT 许可证.

### 页面通知中心

创建页面通知中心，快速查看自己要处理的内容, 或者类似邮件一样来处理自己的业务

### 个人收藏位置 & 最近访问列表

快速到达自己的感兴趣的位置

### 统计仓库操作的地图信息, 个人统计页面

通过显示仓库的操作信息来源，让业务更好的进行仓库位置创建决策

### web 市场

https://github.com/marketplace，基于 github 实现扩展，共享成果

### mobile apps

通过手机完成更多的操作

### make git faster
- v2 protocol
- sparse checkout
- partical clone: https://about.gitlab.com/blog/2020/03/13/partial-clone-for-massive-repositories/
    * Partial Clone is a new feature of Git that replaces Git LFS and makes working with very large repositories better by teaching Git how to work without downloading every file. Partial Clone has been years in the making, with code contributions from GitLab, GitHub, Microsoft and Google. Today it is experimentally available in Git and GitLab, and can be enabled by administrators (docs).
    * Partial Clone speeds up fetching and cloning because less data is transferred, and reduces disk usage on your local computer. For example, cloning gitlab-com/www-gitlab-com using Partial Clone (--filter=blob:none) is at least 50% faster, and transfers 70% less data.
    * Large files are necessary for many projects, and Git will soon support this natively, without the need for extra tools. Although Partial Clone is still an experimental feature, we are making improvements with every release and the feature is now ready for testing.
    * git clone < GVFS < partical clone
    * use git primisor to faster fetch
- commit graph
    * accelerates commit walks and reachability calculations, speeding up commands like git log
- multi-pack-index
    * enables fast object lookups across many pack-files.
    * Incremental repack: Repacks the packed Git data into fewer pack-file without disrupting concurrent commands by using the multi-pack-index.

### use .gitattributes in server
- get better diff output
