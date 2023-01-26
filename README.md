# Exercises for Publishing Python Packages: Test, share, and automate your projects 🐍 📦 ⬆️

[![Documentation Status](https://readthedocs.org/projects/publishing-python-packages/badge/?version=latest)](https://publishing-python-packages.readthedocs.io/en/latest/?badge=latest)

Fork of 《Publishing Python Packages》book.

## 笔记

目录说明：

- .github
- ch05

  初具模型，基础的 tox 的使用
- ch06

  重构解耦代码，模块化，SOLID 原则。增加 typecheck(mypy)、lint(flake8)、format(black) 、测试 hello 配置。
- ~~ch07/ src 和 test 代码和 ch06 一致，删除 ~~
- ch08/
  - 增加 sphinx 文档构建配置。默认主题 alabaster 非常简陋。** 添加自定义 sphinx-rtd-theme 主题后，注意在 cfg 文件中添加对应依赖 **。
  - 托管到 read the docs 网站。注册 read the docs 账号，可以使用 github 互联。
    - 0.保证 project 根目录下存在正确配置的.readthedocs.yaml
    - 1.import 特定的 github project；
    - 2.填写元信息，勾选 advanced setting。
    - 3.填写 Project Extra Details。
  - Running sphinx-apidoc on Read the Docs。配置对应 conf.py，利用 build doc 的生命周期的 builder-inited
  - update per pull-request:
    - visit https://readthedocs.org/dashboard/publishing-python-packages/edit/
    - click `Admin`,click `advanced setting`.
    - select `Build pull requests for this project`, then save.
    - push a change(must be pr, not push) to this repo to check if works as expected.
    - 配置文档查阅：https://docs.readthedocs.io/en/stable/pull-requests.html
    - 构造测试 pr 的步骤：在 main 分支创建一个 pr，拉取 pr 到本地，在本地做一些变更，例如更改文档。push 到 github，发起对 main 的合并 pr， 此时 pull request 页面就会触发
      readthedocs 的文档构建预览。可以点击查看效果。
  - sphinx 出来 rst 格式，也可以通过扩展支持 markdown 格式。也可以考虑 mkdocs
  - doctest（文档驱动的测）/pytest（用例驱动的测试）
- ch09/
  - 关于依赖库版本和自身版本。
    - 不固定特定版本: package-a==1.0.0。
    - 限定上下界版本范围: package-a>=1.0.0,<2。
    - 限定下界: package-a>=1.0.0。
    - 不限范围: package-a。
  - 依赖库就是在寻找合适的交集。有时，会陷入依赖 diamond 地狱。[参阅](https://livebook.manning.com/book/publishing-python-packages/chapter-9/v-10)
  - 限制下界的意义：某个 package 在某个版本才引入某个你需要的功能，因此需要指定下界。
  - 限制上界的意义：一般是基于兼容性考虑，版本过高的库可能 API 大改，会破坏你已有的代码库。
  - 利用 github 的代码扫描服务（Code security and analysis）。
    - Dependabot alerts surface known security vulnerabilities in some dependency manifest files.
    - Dependabot security updates automatically keep your application up-to-date by updating dependencies in response to
      these alerts.
    - Dependabot version updates can also help keep dependencies updated.
    - Code scanning: scan your project code for vulnerabilities as well.
    - Secret scanning: scans your code for potentially leaked passwords, API keys, and so on to protect you from
      attackers who scrape and use the information.
- use [pre-commit](https://pre-commit.com/) hook in .pre-commit-config.yaml
  - pre-commit一般使作用于 staged -> repository这个阶段。如果文件变更还没有staged（还没有git add），那么pre-commit会先：
     - Stashing unstaged files.
     - do tasks.
     - Restore changes.
    这个预演功能很好，非常适合本地排查问题，而不是在commit时半天无法通过。
  - pyupgrade for python syntax up to date
  - install: `pip install pre-commit`
  - setup git hooks: `pre-commit install` => .git\hooks\pre-commit
  - manually run all pre-commit hooks on a repository: `pre-commit run --all-files`
  - temporarily disabling hooks: `SKIP=[hook-id] prep-commit run`
  - run single hook: `pre-commit run [hook-id]`
- git command:
  - git revert XXX :

    假设当前提交为意外的提交，想要撤销，可以使用 revert，但是会新增一个 commit 记录（表示撤销）。 审查需要保留撤销记录时可以使用， 其余时刻不建议使用。
  - git reset --soft vs --mixed vs --hard: https://stackoverflow.com/a/3528483

- 让 pre-commit 通过：
  - 当 pre-commit 定义的检测范围的文件格式混乱，此时 pre-commit 或者 git commit + run hooks（例如使用 IDE 勾选框 ) 都会无限失败。
  - 使用 tox 任务执行格式化，然后重试 commit，直到通过。
  - 这里会遇到pre-commit中例如black和flake8的配置问题。
  - flake8: `args: ['--config=ch09/first-python-package/setup.cfg', '--ignore=E303']` 可以读取配置。
  - black: 
    ```bash
    black....................................................................Failed
    - hook id: black
    - files were modified by this hook
    
    reformatted ch08\first-python-package\docs\conf.py
    
    All done! \u2728 \U0001f370 \u2728
    1 file reformatted.
    
    [WARNING] Stashed changes conflicted with hook auto-fixes... Rolling back fixes...
    ```
    - 问题分析：black8指定了ch09的配置，但是却检测了ch08的代码。
    - 参阅[这个问题](https://stackoverflow.com/a/74046827) ，可以手动git add 出现冲突的文件，之后再次检测。
    - 或者指定black排除的检测范围：在pre-commit中 1.使用exclude排除部分文件夹。2.使用files指定文件夹。

- ch10 的项目模板生成不实用，暂缓。
